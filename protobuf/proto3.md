# proto3 언어 가이드

[상위 폴더로](index.md)

## 공식 사이트 링크
- [Language Guide(proto3)](https://developers.google.com/protocol-buffers/docs/proto3?hl=ko)

## 목차
- [Defining A Message Type](defining-a-message-type)
- [Scalar Value Types](scalar-value-types)
- [Default Values](default-values)
- [Enumerations](enumerations)
- [Using Other Message Types](using-other-message-types)
- [Nested Types](Nested-Types)
- [Updating A Message Type](updating-a-message-type)
- [Unknown Fields](unknown-fields)
- [Any](any)
- [Oneof](oneof)
- [Maps](maps)
- [Packages](packages)
- [Defining Services](defining-services)
- [JSON Mapping](json-mapping)
- [Options](options)
- [Generating Your Classes](generating-your-classes)

### Defining A Message Type
```
syntax = "proto3";

message SearchRequest {
  string query = 1;
  int32 page_number = 2;
  int32 result_per_page = 3;
}
```
- `syntac = "proto3";` : proto3 문법을 쓰고 있다는 뜻
- `SearchRequest` message는 3개의 필드를 가지고 있음

#### 필드 타입 지정
- `query` : string 타입
- `page_number`, `result_per_page` : int32 타입

#### 필드 번호 할당
- 메시지의 각 필드는 *고유한 번호*를 가짐
- 1~15는 1바이트, 16~2047는 2바이트를 소모
- 1~536,870,911까지 지정 가능
- 19000~19999는 사용불가

#### 필드 법칙 지정
- singular(디폴트) : 0 또는 1개의 값을 가질 수 있음
- `repeated` : 0개 이상의 값을 가질 수 있음.

#### 더 많은 메시지 타입
- 하나의 `.proto` 파일은 여러개의 메시지 타입이 정의될 수 있음

```
message SearchRequest {
  string query = 1;
  int32 page_number = 2;
  int32 result_per_page = 3;
}

message SearchResponse {
 ...
}
```

#### 주석 추가
- C/C++ 스타일 주석 사용 가능

```c++
/* SearchRequest represents a search query, with pagination options to
 * indicate which results to include in the response. */

message SearchRequest {
  string query = 1;
  int32 page_number = 2;  // Which page number do we want?
  int32 result_per_page = 3;  // Number of results to return per page.
}
```

#### 필드 예약
- 메시지를 업데이트해서 필드를 삭제 -> 나중에 그 필드 번호를 이용한 필드 추가 -> 옛날 버전 쓰던 사람은 버그남
- 필드 번호와 필드 이름을 `reserved` 처리할 수 있음
- 필드 번호랑 이름을 섞어서 한줄에 `reserved` 할 수는 없음

```
message Foo {
  reserved 2, 15, 9 to 11;
  reserved "foo", "bar";
}
```

#### .proto로 무엇이 만들어지나?
- C++은 `.pb.h`와 `.pb.cc`가 만들어짐

### Scalar Value Types

| .proto Type | C++ Type | Notes                                             |
|-------------|----------|---------------------------------------------------|
| double      | double   |                                                   |
| float       | float    |                                                   |
| int32       | int32    | 가변길이 인코딩. 음수가 빈번하면 sint32 쓸 것     |
| int64       | int64    | 가변길이 인코딩. 음수가 빈번하면 sint64 쓸 것     |
| uint32      | uint32   | 가변길이 인코딩                                   |
| uint64      | uint64   | 가변길이 인코딩                                   |
| sint32      | int32    | 가변길이 인코딩                                   |
| sint64      | int64    | 가변길이 인코딩                                   |
| fixed32     | uint32   | 4 바이트. 2^28보다 큰 값이 빈번하면 효율적        |
| fixed64     | uint64   | 8 바이트. 2^56보다 큰 값이 빈번하면 효율적        |
| sfixed32    | int32    | 4 바이트                                          |
| sfixed64    | int64    | 8 바이트                                          |
| bool        | bool     |                                                   |
| string      | string   | UTF-8이나 7-bit ASCII여야 함. 2^32보다 길 수 없음 |
| bytes       | string   | 2^32보다 길 수 없음                               |

### Default Values
- string : empty string
- bytes : empty bytes
- bool : false
- numeric : 0
- enums : 첫 enum 값(0)
- message : not set. 정확한 값은 언어에 따라 다름.
- repeated : 빈 리스트

### Enumerations
```
message SearchRequest {
  string query = 1;
  int32 page_number = 2;
  int32 result_per_page = 3;
  enum Corpus {
    UNIVERSAL = 0;
    WEB = 1;
    IMAGES = 2;
    LOCAL = 3;
    NEWS = 4;
    PRODUCTS = 5;
    VIDEO = 6;
  }
  Corpus corpus = 4;
}
```
enum의 첫 상수 값은 0으로 해야한다.(디폴트 값 및 proto2 호환을 위해)  
`allow_alias` 옵션을 `true`로 설정하면, 같은 값을 가진 enum 상수를 할당할 수 있다.
```
enum EnumAllowingAlias {
  option allow_alias = true;
  UNKNOWN = 0;
  STARTED = 1;
  RUNNING = 1;
}
enum EnumNotAllowingAlias {
  UNKNOWN = 0;
  STARTED = 1;
  // RUNNING = 1;  // Uncommenting this line will cause a compile error inside Google and a warning message outside.
}
```
enum 상수는 32비트 정수 범위 내에 있어야 한다. 음수값은 비효율적이므로 권장되지 않는다.

#### 예약 값
```
enum Foo {
  reserved 2, 15, 9 to 11, 40 to max;
  reserved "FOO", "BAR";
}
```

### Using Other Message Types
다른 메시지 타입을 필드 타입으로 사용할 수 있다.
```
message SearchResponse {
  repeated Result results = 1;
}

message Result {
  string url = 1;
  string title = 2;
  repeated string snippets = 3;
}
```

#### 정의 import하기
다른 `.proto` 파일에 사용하고 싶은 필드 타입이 정의되어 있다면 파일 상단에 impot 문을 추가한다.
```
import "myproject/other_protos.proto";
```

### Nested Types
```
message SearchResponse {
  message Result {
    string url = 1;
    string title = 2;
    repeated string snippets = 3;
  }
  repeated Result results = 1;
}
```
```
message SomeOtherMessage {
  SearchResponse.Result result = 1;
}
```

### Updating A Message Type

### Unknown Fields

### Any
`Any` 메시지 타입은 .proto 정의 없이 임베디드 타입처럼 사용할 수 있게 해준다.  
`Any`는 `bytes`처럼 임의로 직렬화된 메시지와 URL을 가지고 있다. URL은 전역 고유 식별자처럼 동작하고, 메시지의 타입을 확인한다.  
`Any` 타입을 사용하기 위해서는 `import "google/protobuf/any.proto"`를 추가해야 한다.
```
import "google/protobuf/any.proto";

message ErrorStatus {
  string message = 1;
  repeated google.protobuf.Any details = 2;
}
```

### Oneof
메시지가 많은 필드를 가지는데, 한 필드만이 설정된다면, oneof 기능을 이용하여 메모리를 절약할 수 있다.  
oneof 필드는 공유된 메모리에 있다는 것 외에는 일반적인 필드와 동일하다.

### Using Oneof
```
message SampleMessage {
  oneof test_oneof {
    string name = 4;
    SubMessage sub_message = 9;
  }
}
```

### Maps

### Packages
```
package foo.bar;
message Open { ... }
```

### Defining Services
메시지 타입을 RPC(Remote Procedure Call)과 함께 쓸 수 있다.  
RPC 서비스 인터페이스를 `.proto` 파일에 정의하면 프로토콜 버퍼 컴파일러가 선택한 언어로 서비스 인터페이스 코드와 스텁을 생성한다.

```
service SearchService {
  rpc Search (SearchRequest) returns (SearchResponse);
}
```

#### Services in C++ Generated Code
`.proto` 파일에 아래와 같은 라인이 있으면,
```
option cc_generic_services = true;
```
프로토콜 버퍼 컴파일러는 파일에 서술된 서비스 정의에 기반하여 코드를 생성할 것이다.  
하지만, 생성된 코드는 특정 RPC 시스템에 부적합할 수도 있다. 따라서 더 많은 레벨의 코드 수정이 필요할 것이다.  
이 코드가 생성되길 원하지 않으면, 아래 라인을 추가한다.
```
option cc_generic_services = false;
```
기본 값은 `false`로 지정되어 있다.(2.4.0까지는 `true`로 되어있음)