
# libuv 튜토리얼 - uvcat

[상위 폴더로](index.md)

## 코드

```c++
#include <assert.h>
#include <stdio.h>
#include <fcntl.h>
#include <unistd.h>
#include <uv.h>

void on_read(uv_fs_t *req);

uv_fs_t open_req;
uv_fs_t read_req;
uv_fs_t write_req;

static char buffer[1024];

static uv_buf_t iov;

void on_write(uv_fs_t *req) {
    if (req->result < 0) {
        fprintf(stderr, "Write error: %s\n", uv_strerror((int)req->result));
    }
    else {
        uv_fs_read(uv_default_loop(), &read_req, open_req.result, &iov, 1, -1, on_read);
    }
}

void on_read(uv_fs_t *req) {
    if (req->result < 0) {
        fprintf(stderr, "Read error: %s\n", uv_strerror(req->result));
    }
    else if (req->result == 0) {
        uv_fs_t close_req;
        // synchronous
        uv_fs_close(uv_default_loop(), &close_req, open_req.result, NULL);
    }
    else if (req->result > 0) {
        iov.len = req->result;
        uv_fs_write(uv_default_loop(), &write_req, 1, &iov, 1, -1, on_write);
    }
}

void on_open(uv_fs_t *req) {
    // The request passed to the callback is the same as the one the call setup
    // function was passed.
    assert(req == &open_req);
    if (req->result >= 0) {
        iov = uv_buf_init(buffer, sizeof(buffer));
        uv_fs_read(uv_default_loop(), &read_req, req->result,
                   &iov, 1, -1, on_read);
    }
    else {
        fprintf(stderr, "error opening file: %s\n", uv_strerror((int)req->result));
    }
}

int main(int argc, char **argv) {
    uv_fs_open(uv_default_loop(), &open_req, argv[1], O_RDONLY, 0, on_open);
    uv_run(uv_default_loop(), UV_RUN_DEFAULT);

    uv_fs_req_cleanup(&open_req);
    uv_fs_req_cleanup(&read_req);
    uv_fs_req_cleanup(&write_req);
    return 0;
}
```

- `uv_fs_open`으로 file system handle을 열 수 있다.
- `uv_fs_close`로 file system handle을 닫을 수 있다.
- `uv_fs_t`의 `result`에는 요청의 결과값이 들어간다.
  - `uv_fs_open`의 경우 `result` >= 0이면 성공적으로 열렸다는 것이다.
  - `uv_fs_read`의 경우 `preadv`와 동일한 결과가 `result`에 저장된다.
  - `uv_fs_write`의 경우 `pwritev`와 동일하다.
- 예제는 `uv_fs_open`이 성공하면,
  - `uv_fs_read`를 호출해서
    - 읽을 것이 없으면 `uv_fs_close`를 호출한다.
    - 읽을 것이 남아있으면 `uv_fs_write`를 호출해서
	  - 다시 `uv_fs_read`를 호출한다.
- 작업이 끝난 후 `uv_fs_req_cleanup`을 이용하여 내부에 할당된 메모리를 해제한다.
