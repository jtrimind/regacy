# Nanopb string encode/decode

[상위 폴더로](index.md)

### simple.protobuf
```c++
// A very simple protocol definition, consisting of only
// one message.

syntax = "proto2";

message SimpleMessage {
    required string str = 2;
}

```
SimpleMessage라는 메시지는 str이라는 string 필드를 가지고 있다.

### simple.c
#### encode
```c++
static bool write_string(pb_ostream_t *stream, const pb_field_t *field, void * const *arg)
{
    return pb_encode_tag_for_field(stream, field) &&
           pb_encode_string(stream, *arg, strlen(*arg));
}
```
write_string은 str 필드가 encode될 때 수행될 함수이다.  

```c++
/* SimpleMessage 초기화. */
SimpleMessage message = SimpleMessage_init_zero;

/* stream을 만들어서 buffer에 씀. */
pb_ostream_t stream = pb_ostream_from_buffer(buffer, sizeof(buffer));

/* str 필드가 encode될 때 수행될 함수와 인자를 넣음. */
message.str.funcs.encode = &write_string;
message.str.arg = "asd";

/* message를 SimpleMessage 필드에 맞춰 encode하고 stream에 집어넣음. */
status = pb_encode(&stream, SimpleMessage_fields, &message);
```

#### decode
```c++
static bool read_string(pb_istream_t *stream, const pb_field_t *field, void **arg)
{
    size_t len = stream->bytes_left;
    pb_byte_t *str = (pb_byte_t *)calloc(len + 1, sizeof(pb_byte_t));
    *arg = str;
    
    if (!pb_read(stream, str, len))
        return false;

    return true;
}
```
read_string으로 들어오는 stream는 substream이다.  
stream->bytes_left는 '\0'을 제외한 길이가 들어온다.  

```c++
/* SimpleMessage 초기화. */
SimpleMessage message = SimpleMessage_init_zero;
message.str.funcs.decode = &read_string;

/* stream을 만들어서 buffer로부터 읽어옴. */
pb_istream_t stream = pb_istream_from_buffer(buffer, message_length);

/* stream에서 SimpleMessage 필드에 맞춰 decode한 후 message에 집어넣음 */
status = pb_decode(&stream, SimpleMessage_fields, &message);

/* message의 str를 출력 */
printf("Your str was %s!\n", (char *)message.str.arg);
free(message.str.arg);
```
