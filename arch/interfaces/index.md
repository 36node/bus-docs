## 服务间对外接口

服务间的Web API接口通过各个SDK保证契约。

服务间有些时候通过发送消息进行信息交换，这部分消息格式记录在这里。

## 格式风格

消息分为COMMAND和EVENT两类。
COMMAND用来触发其他系统的操作，EVENT用来广播自己系统的变化。

建议新需求定义消息采用以下风格，可能有部分老系统没有使用以下风格。

### COMMAND格式

```json
{
    "flag": "string",
    "command": "string",
    "vin": "string",
    "ns": "string",
    "body": {},
}
```

例如

```json
{
    "flag": "COMMAND",
    "command": "CLOSE_ALERT",
    "vin": "TESTSHIFTRIGHT001",
    "ns": "/bus/test",
    "body": {
        "id": "5d5b9d147f2e6f159cd825ae",
    },
}
```

### EVENT格式

```json
{
    "flag": "string",
    "event": "string",
    "vin": "string",
    "ns": "string",
    "body": {},
}
```

例如
```json
{
    "flag": "EVENT",
    "event": "ALERT_CREATED",
    "vin": "TESTSHIFTRIGHT001",
    "ns": "/bus/test",
    "body": {
        "id": "5d5b9d147f2e6f159cd825ae",
        "at": "2019-08-19T13:39:13.000Z",
        "code": 53510,
        "level": 2,
        "type": 16,
    }
}
```

## 消息格式

* [bus-tbox](./bus-tbox.md)
* [bus-core](./bus-core.md)
* [bus-op](./bus-op.md)
* [bus-pile](./bus-pile.md)
* [bus-boxie](./bus-boxie.md)
* [bus-telaidian](./bus-telaidian.md)
