# Protobuf 튜토리얼

[상위 폴더로](index.md)

## 공식 사이트 링크
- [Basics: C++](https://developers.google.com/protocol-buffers/docs/cpptutorial?hl=ko)

## 튜토리얼
gihub에서 직접 파일을 가져오던지, 아니면 필요한 파일만 넣은 `tutorial.zip`을 다운받고 적당한 위치에 풀어준다.
### github
- [Makefile](https://github.com/protocolbuffers/protobuf/blob/master/examples/Makefile)
- [addressbook.proto](https://github.com/protocolbuffers/protobuf/blob/master/examples/addressbook.proto)
- [add_person.cc](https://github.com/protocolbuffers/protobuf/blob/master/examples/add_person.cc)
- [list_people.cc](https://github.com/protocolbuffers/protobuf/blob/master/examples/list_people.cc)

### tutorial.zip
- [tutorial.zip](tutorial.zip)

### 빌드
```bash
$ make cpp
```

### 실행
```bash
$ ./add_person_cpp addressbook.data
$ ./list_people_cpp addressbook.data
```
