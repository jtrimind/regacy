# libuv 튜토리얼 - idle-basic

[상위 폴더로](index.md)

## 코드

```c++
/* libuv/docs/code/idle-basic */
#include <stdio.h>
#include <uv.h>

int64_t counter = 0;

void wait_for_a_while(uv_idle_t* handle) {
    counter++;

    if (counter >= 10e6)
        uv_idle_stop(handle);
}

int main() {
    uv_idle_t idler;

    uv_idle_init(uv_default_loop(), &idler);
    uv_idle_start(&idler, wait_for_a_while);

    printf("Idling...\n");
    uv_run(uv_default_loop(), UV_RUN_DEFAULT);

    uv_loop_close(uv_default_loop());
    return 0;
}
```

- `uv_default_loop`를 이용하면 default loop를 사용할 수 있다.
- idle handle은 이벤트 루프의 매 턴마다 콜백을 호출한다.
- `uv_idle_t`는 idle handle이다.
- `uv_idle_init`을 이용하여 default loop의 idle handle를 초기화한다.
- `uv_idle_start`를 통해 idle handle을 callback과 함께 시작시킨다.
- `uv_idle_stop`을 통해 idle handle을 정지시킨다.
- 예제는 idle handle이 callback과 함께 시작되었다가 idle callback이 10e6번 호출된 뒤 정지된다.
- 그 뒤 활성화된 이벤트 감시자가 없으므로 `uv_run`이 종료된다.
