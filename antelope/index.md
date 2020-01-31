# Antelope

## Antelope
Antelope is a lightweight, relational database management system for resource-constrained IoT devices.

## Documentation
https://github.com/contiki-ng/contiki-ng/wiki/Documentation:-Antelope

## Source Code
https://github.com/contiki-ng/contiki-ng/tree/develop/os/storage/antelope

## API
![api](./api.svg)

### antelope.h
```c++
void db_init(void);
```
db를 초기화한다.  
  
```c++
void db_set_output_function(db_output_function_t f);
```
출력함수를 지정한다. 기본적으로 printf로 되어있다.  
  
```c++
const char *db_get_result_message(db_result_t code);
```
db_result_t와 매칭되는 문자열을 돌려준다. ex) DB_OK -> "Operation succeeded"  
  
```c++
db_result_t db_print_header(db_handle_t *handle);
```
handle의 헤더를 출력한다.  
  
```c++
db_result_t db_print_tuple(db_handle_t *handle);
```
handle의 현재 행을 출력한다.  
  
```c++
int db_processing(db_handle_t *handle);
```
handle이 현재 processing 상태인지 확인한다. 0이면 processing 상태가 아니다.  
