# libuv 튜토리얼

[상위 폴더로](../index.md)

## 코드
`libuv/docs/code`에 documentation에 포함되어 있는 코드가 있다.  

## 빌드
```bash
$ gcc main.c `pkg-config --cflags --libs libuv`
$ ./a.out
```

## 예제
- [helloworld](helloworld.md) : 첫 예제
- [idle-basic](idle-basic.md) : idle 예제
- [uvcat](uvcat.md) : filesystem 예제
- [uvtee](uvtee.md) : pipe, stream 예제
