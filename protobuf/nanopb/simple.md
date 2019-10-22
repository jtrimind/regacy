# Nanopb simple example

[상위 폴더로](index.md)

## simple example 실행하기
### 코드 받기
```bash
$ git clone https://github.com/nanopb/nanopb.git
```

### simple example 빌드하기
```bash
$ cd nanopb/examples/simple
$ make
```

### simple 실행하기
```bash
$ ./simple
Your lucky number was 13!
```

## simple example 분석
### simple.protobuf
```c++
// A very simple protocol definition, consisting of only
// one message.

syntax = "proto2";

message SimpleMessage {
    required int32 lucky_number = 1;
}
```
SimpleMessage라는 메시지는 lucky_number라는 int32 필드를 가지고 있다.

### simple.c
#### encode
```c++
/* SimpleMessage 초기화. */
SimpleMessage message = SimpleMessage_init_zero;

/* stream을 만들어서 buffer에 씀. */
pb_ostream_t stream = pb_ostream_from_buffer(buffer, sizeof(buffer));

/* lucky_number 필드에 13을 넣음. */
message.lucky_number = 13;

/* message를 SimpleMessage 필드에 맞춰 encode하고 stream에 집어넣음. */
status = pb_encode(&stream, SimpleMessage_fields, &message);
```

#### decode
```c++
/* SimpleMessage 초기화. */
SimpleMessage message = SimpleMessage_init_zero;

/* stream을 만들어서 buffer로부터 읽어옴. */
pb_istream_t stream = pb_istream_from_buffer(buffer, message_length);

/* stream에서 SimpleMessage 필드에 맞춰 decode한 후 message에 집어넣음 */
status = pb_decode(&stream, SimpleMessage_fields, &message);

/* message의 lucky_number를 출력 */
printf("Your lucky number was %d!\n", (int)message.lucky_number);
```
