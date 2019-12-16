
# libuv 튜토리얼 - uvtee

[상위 폴더로](index.md)

## 코드

```c++
#include <stdio.h>
#include <fcntl.h>
#include <unistd.h>
#include <string.h>
#include <stdlib.h>

#include <uv.h>

typedef struct {
    uv_write_t req;
    uv_buf_t buf;
} write_req_t;

uv_loop_t *loop;
uv_pipe_t stdin_pipe;
uv_pipe_t stdout_pipe;
uv_pipe_t file_pipe;

void alloc_buffer(uv_handle_t *handle, size_t suggested_size, uv_buf_t *buf) {
    *buf = uv_buf_init((char*) malloc(suggested_size), suggested_size);
}

void free_write_req(uv_write_t *req) {
    write_req_t *wr = (write_req_t*) req;
    free(wr->buf.base);
    free(wr);
}

void on_stdout_write(uv_write_t *req, int status) {
    free_write_req(req);
}

void on_file_write(uv_write_t *req, int status) {
    free_write_req(req);
}

void write_data(uv_stream_t *dest, size_t size, uv_buf_t buf, uv_write_cb cb) {
    write_req_t *req = (write_req_t*) malloc(sizeof(write_req_t));
    req->buf = uv_buf_init((char*) malloc(size), size);
    memcpy(req->buf.base, buf.base, size);
    uv_write((uv_write_t*) req, (uv_stream_t*)dest, &req->buf, 1, cb);
}

void read_stdin(uv_stream_t *stream, ssize_t nread, const uv_buf_t *buf) {
    if (nread < 0){
        if (nread == UV_EOF){
            // end of file
            uv_close((uv_handle_t *)&stdin_pipe, NULL);
            uv_close((uv_handle_t *)&stdout_pipe, NULL);
            uv_close((uv_handle_t *)&file_pipe, NULL);
        }
    } else if (nread > 0) {
        write_data((uv_stream_t *)&stdout_pipe, nread, *buf, on_stdout_write);
        write_data((uv_stream_t *)&file_pipe, nread, *buf, on_file_write);
    }

    // OK to free buffer as write_data copies it.
    if (buf->base)
        free(buf->base);
}

int main(int argc, char **argv) {
    loop = uv_default_loop();

    uv_pipe_init(loop, &stdin_pipe, 0);
    uv_pipe_open(&stdin_pipe, 0);

    uv_pipe_init(loop, &stdout_pipe, 0);
    uv_pipe_open(&stdout_pipe, 1);
    
    uv_fs_t file_req;
    int fd = uv_fs_open(loop, &file_req, argv[1], O_CREAT | O_RDWR, 0644, NULL);
    uv_pipe_init(loop, &file_pipe, 0);
    uv_pipe_open(&file_pipe, fd);

    uv_read_start((uv_stream_t*)&stdin_pipe, alloc_buffer, read_stdin);

    uv_run(loop, UV_RUN_DEFAULT);
    return 0;
}
```

- `uv_pipe_t`는 pipe handle type이다.
- named pipe를 이용하여 프로세스 간 통신을 하기 위해서는 `uv_pipe_init`의 3번째 인자를 1로 설정해야 한다.
- `uv_pipe_open`으로 file descriptor와 연계시킬 수 있는데, 예제에서는 0(stdin), 1(stdout)을 넘겼다.
- `uv_stream_t`는 stream handle type이다.
- `uv_read_start`는 스트림으로부터 데이터를 읽는다.
  - `uv_alloc_cb`에서는 메모리를 할당하고 `uv_buf_t`로 공급해야한다. 예제의 alloc_buffer 참조
  - 스트림으로 부터 데이터를 읽으면 `uv_read_cb`이 호출된다. 예제의 read_stdin 참조
    - nread 파라미터가 0보다 크면, 읽을 것이 있다는 것으로 예제에서는 파일과 stdout에 데이터를 쓴다.
    - nread 파라미터가 0보다 작으면, 에러인데 보통 EOF이다. 그 경우 스트림을 닫는다.
