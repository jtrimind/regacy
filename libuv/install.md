# libuv 설치

[상위 폴더로](index.md)

## 공식 사이트 링크
- [Build Instructions](https://github.com/libuv/libuv#build-instructions)

## 사용환경
- Ubuntu 18.04.3 LTS

## pkg-config 설치
이미 설치되어 있을 거 같지만 혹시 모르니 확인해보세요.
```bash
$ sudo apt-get install pkg-config
```

## libuv 소스 다운로드
```bash
$ git clone https://github.com/libuv/libuv.git
```

## libuv 설치
```bash
$ cd libuv
$ sh autogen.sh
$ ./configure
$ make
$ make check
$ make install
```

make check를 하니 아래와 같은 화면이 나왔다.
```
...
ok 370 - watcher_cross_stop
ok 371 - we_get_signal
ok 372 - we_get_signal_one_shot
ok 373 - we_get_signals
ok 374 - we_get_signals_mixed
PASS: test/run-tests
=============
1 test passed
=============
```

## 설치확인
``` bash
$ pkg-config --cflags --libs libuv # output : -I/usr/local/include -L/usr/local/lib -luv -lrt -lpthread -lnsl -ldl
```
