## bus-op对外消息接口

消息会根据vin进行分区，保证同一vin下的消息在同一个分区，保证消费顺序。

### 报警状态更新事件

报警被创建或更新时，发出报警状态更新事件

```json
{
  "flag": "EVENT",
  "event": "ALERT_UPDATED",
  "vin": "LJM6GCDC9JAS02731",
  "ns": "/pudongbus/0rzjz8/yxd0yd",
  "body": {
    "alert": "5d774a01bb2e3e0011804aed",
    "type": "整车",
    "lastAt": "2019-09-10T07:00:13.000Z",
    "startedAt": "2019-09-10T07:00:13.000Z",
    "window": "20190910",
    "action": "NONE",
    "code": "10100003",
    "count": 1,
    "level": 3,
    "name": "整车控制器系统故障",
    "state": "OPEN",
    "vehicle": "LJM6GCDC9JAS02731",
    "vehiclePlate": "沪A-05278D",
    "vehicleNo": "L0E-017",
    "ns": "/pudongbus/0rzjz8/yxd0yd",
    "vehicleLine": "5d43a8ada2549f0013f5586e",
    "vehicleProducer": "申龙",
    "vehicleModel": "SLK6101UBEVN1",
    "vehicleModelBrief": "L0E",
    "updatedAt": "2019-09-10T07:00:17.674Z",
    "createdAt": "2019-09-10T07:00:17.674Z",
    "id": "5d774a01bb2e3e0011804aed"
  }
}
```

### 报警删除事件

报警被删除时，发出报警删除事件

```json
{
  "flag": "EVENT",
  "event": "ALERT_DELETED",
  "vin": "LJM6GCDC9JAS02731",
  "ns": "/pudongbus/0rzjz8/yxd0yd",
  "body": {
    "alert": "5d774a01bb2e3e0011804aed",
    "deleteBy": "5d23016a11288c0012ef9a18",
    "type": "整车",
    "lastAt": "2019-09-10T07:00:13.000Z",
    "startedAt": "2019-09-10T07:00:13.000Z",
    "window": "20190910",
    "action": "NONE",
    "code": "10100003",
    "count": 1,
    "level": 3,
    "name": "整车控制器系统故障",
    "state": "OPEN",
    "vehicle": "LJM6GCDC9JAS02731",
    "vehiclePlate": "沪A-05278D",
    "vehicleNo": "L0E-017",
    "ns": "/pudongbus/0rzjz8/yxd0yd",
    "vehicleLine": "5d43a8ada2549f0013f5586e",
    "vehicleProducer": "申龙",
    "vehicleModel": "SLK6101UBEVN1",
    "vehicleModelBrief": "L0E",
    "updatedAt": "2019-09-10T07:00:17.674Z",
    "createdAt": "2019-09-10T07:00:17.674Z",
    "id": "5d774a01bb2e3e0011804aed"
  }
}
```

### 报警信息广播

定期对过去一段时间的三级报警信息进行广播。
消息会根据vin进行分区，保证同一vin下的消息在同一个分区，保证消费顺序。

```json
{
    "flag": "EVENT",
    "event": "ALERT_SNAPSHOT",
    "vin": "LSFD13204KC000428",
    "ns": "/shanghaibus/c5/0vyx24",
    "body": {
        "type": "整车",
        "lastAt": "2019-11-03T16:52:42.000Z",
        "startedAt": "2019-11-03T16:52:42.000Z",
        "window": "20191104",
        "action": "NONE",
        "code": "100aa703",
        "count": 1,
        "level": 3,
        "name": "高压绝缘严重故障",
        "state": "OPEN",
        "vehicle": "LSFD13204KC000428",
        "vehiclePlate": "沪A-56206D",
        "vehicleNo": "S2Y-0089",
        "ns": "/shanghaibus/c5/0vyx24",
        "vehicleLine": "5d90aa4a29730200135430a0",
        "vehicleProducer": "申沃",
        "vehicleModel": "SWB6129BEV38",
        "vehicleModelBrief": "S2Y",
        "updatedAt": "2019-11-03T16:54:21.052Z",
        "createdAt": "2019-11-03T16:54:21.052Z",
        "id": "5dbf063d8077f00011f1c0be"
    }
}
```

### 关闭报警命令

```json
{
  "flag": "COMMAND",
  "command": "CLOSE_ALERT",
  "vin": "LJM6GCDC3JAS02742",
  "ns": "/bus/test",
  "body": {
    "alert": "AlertId",
    "actionBy": "111",
    "actionAt": "2019-08-26T06:18:22.323Z",
    "action": "TICKET",
    "ticket": "ticketId"
  },
  "id": "5d6379aede32a50d2acccab0"
}
 ```

### 异常产生事件

异常被创建时，发出异常产生事件

```json
{
    "flag": "EVENT",
    "event": "EXCEPTION_CREATED",
    "vin": "LZYTAGBW7G1042727",
    "ns": "/shanghaibus/c3/o4v3aj",
    "body": {
        "exception": "5dbac12f777d3c0011e23fb7",
        "type": "INSULATION",
        "code": "RESISTANCE_BETWEEN_500_1000000",
        "startedAt": "2019-10-31T11: 10: 40.000Z",
        "lastAt": "2019-10-31T11: 10: 40.000Z",
        "window": "20191031",
        "count": 1,
        "vehicle": "LZYTAGBW7G1042727",
        "ns": "/shanghaibus/c3/o4v3aj",
        "vehiclePlate": "沪D-Q1408",
        "vehicleNo": "Z2E-0400",
        "vehicleLine": "5d90aaa42973020013543338",
        "vehicleProducer": "宇通",
        "vehicleModel": "ZK6125BEVG12",
        "vehicleModelBrief": "Z2E",
        "id": "5dbac12f777d3c0011e23fb7"
    }
}
```

### 异常删除事件

异常被删除时，发出异常删除事件

```json
{
    "flag": "EVENT",
    "event": "EXCEPTION_DELETED",
    "vin": "LZYTAGBW7G1042727",
    "ns": "/shanghaibus/c3/o4v3aj",
    "body": {
        "exception": "5dbac12f777d3c0011e23fb7",
        "deleteBy": "5d23016a11288c0012ef9a18",
        "type": "INSULATION",
        "code": "RESISTANCE_BETWEEN_500_1000000",
        "startedAt": "2019-10-31T11: 10: 40.000Z",
        "lastAt": "2019-10-31T11: 10: 40.000Z",
        "window": "20191031",
        "count": 1,
        "vehicle": "LZYTAGBW7G1042727",
        "ns": "/shanghaibus/c3/o4v3aj",
        "vehiclePlate": "沪D-Q1408",
        "vehicleNo": "Z2E-0400",
        "vehicleLine": "5d90aaa42973020013543338",
        "vehicleProducer": "宇通",
        "vehicleModel": "ZK6125BEVG12",
        "vehicleModelBrief": "Z2E",
        "id": "5dbac12f777d3c0011e23fb7"
    }
}
```
