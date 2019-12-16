# libuv 튜토리얼 - helloworld

[상위 폴더로](index.md)

## 코드

```c++
/* libuv/docs/code/helloworld */
#include <stdio.h>
#include <stdlib.h>
#include <uv.h>

int main() {
    uv_loop_t *loop = malloc(sizeof(uv_loop_t));
    uv_loop_init(loop);

    printf("Now quitting.\n");
    uv_run(loop, UV_RUN_DEFAULT);

    uv_loop_close(loop);
    free(loop);
    return 0;
}
```

- 아무 것도 하지 않고, 루프를 시작하자마자 종료하는 예제이다.
- libuv 이벤트루프는 API 함수를 사용하여 이벤트를 감시해야한다.
- 유저는 loop를 위한 메모리를 할당 -> `uv_loop_init` -> `uv_loop_close` -> 메모리 해제를 해야한다.
