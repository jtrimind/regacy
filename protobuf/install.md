# Protobuf 설치

[상위 폴더로](index.md)

## 공식 사이트 링크
- [README](https://github.com/protocolbuffers/protobuf/blob/master/src/README.md)

## 사용환경
- Ubuntu 18.04.3 LTS
- C++

## pkg-config 설치
이미 설치되어 있을 거 같지만 혹시 모르니 확인해보세요.
```bash
$ sudo apt-get install pkg-config
```

## 디펜던시 설치
```bash
$ sudo apt-get install autoconf automake libtool curl make g++ unzip
```

## 소스 다운로드
```bash
$ git clone https://github.com/protocolbuffers/protobuf.git
$ cd protobuf
$ git submodule update --init --recursive
$ ./autogen.sh
```

## protobuf 설치
```bash
$ ./configure
$ make
$ make check
$ sudo make install
$ sudo ldconfig # refresh shared library cache.
```

make check를 하니 아래와 같은 화면이 나왔다.
```
...
============================================================================
Testsuite summary for Protocol Buffers 3.9.1
============================================================================
# TOTAL: 7
# PASS:  7
# SKIP:  0
# XFAIL: 0
# FAIL:  0
# XPASS: 0
# ERROR: 0
============================================================================
```

## 설치확인
``` bash
$ pkg-config --cflags protobuf # output : -pthread -I/usr/local/include
$ pkg-config --libs protobuf # output : -L/usr/local/lib -lprotobuf
$ pkg-config --cflags --libs protobuf # output : -pthread -I/usr/local/include -L/usr/local/lib -lprotobuf
```
