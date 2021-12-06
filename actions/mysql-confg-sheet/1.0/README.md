## 使用说明

```yaml
version: "1.1"
stages:
  - stage:
      - mysql-confg-sheet:
          alias: mysql-confg-sheet
          description: 连接 mysql 执行 sql 语句且可以断言和出参
          version: "1.0"
          params:
            database: erda
            executors:
              - sql: use xxx
              - asserts:
                  - arg: name
                    operator: =
                    value: 1
                out_params:
                  - expression: .rowsAffected
                    key: name
                sql: drop procedure if exists xxx
            host: xxx
            password: xxx
            port: xxx
            username: xxx
```

### 参数说明

```test
host: mysql host
password: mysql client password
port: mysql client port
username: mysql client username
executors:
 - sql: 执行的 sql
   out_params: 出参表达式
     - expression: 出参表达式
       key: 出参名称
   asserts: 出参的断言
     - arg: 出参名称
       operator: 断言表达式, 可填写 等于:=,不等于:!=,小于等于:<=,大于等于:>=,大于:>,小于:<,包含:contains,不包含:not_contains,属于:belong,不属于:not_belong,为空:empty,不为空:not_empty,存在:exist,不存在:not_exist
       value: 断言的值

```
