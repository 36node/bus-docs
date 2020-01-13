## bus-core对外消息接口

bus-core对外消息有以下几类

### 报警事件

收到bus-tbox的消息后，如果含有报警，则发出报警事件。
消息会根据vin进行分区，保证同一vin下的消息在同一个分区，保证消费顺序。

例如
```json
{
    "flag": "EVENT",
    "event": "ALERT",
    "vin": "LJM6GCDC8KA000125",
    "ns": "/pudongbus/r1d5nr",
    "body": {
        "code": 53510,
        "level": 2,
        "type": 16,
        "at": "2019-08-19T13:39:13.000Z",
        "vehicle": {
            "id": "LJM6GCDC8KA000125",
            "no": "L0E-055",
            "line": "5d4bef7f38762b00138e40e6",
            "plate": "备用",
            "model": "SLK6101UBEVN1",
            "modelBrief": "L0E",
            "producer": "申龙"
        }
    }
}
```

### 车辆信息广播

定期对车辆信息进行广播，每天至少1次。
消息会根据vin进行分区，保证同一vin下的消息在同一个分区，保证消费顺序。

例如
```json
{
    "flag": "EVENT",
    "event": "VEHICLE_SNAPSHOT",
    "vin": "LSFD03209KC000282",
    "ns": "/pudongbus/r1d5nr",
    "body": {
        "ns": "/pudongbus/r1d5nr",
        "receivedAt": "2019-09-09T06:56:52.966Z",
        "beatAt": "2019-09-09T06:56:30.711Z",
        "loginAt": "2019-09-09T05:45:24.000Z",
        "chargeAt": "2019-09-08T05:48:12.000Z",
        "reportedAt": "2019-09-09T06:56:40.000Z",
        "onsite": true,
        "no": "S0P-097",
        "line": "5d4bef7f38762b00138e40e6",
        "model": "SWB6108BEV32",
        "modelBrief": "S0P",
        "photos": [],
        "plate": "沪A50325D",
        "producer": "申沃",
        "scrapped": false,
        "at": "2019-09-09T06:56:40.000Z",
        "sn": 4,
        "iccid": "89860318482062053416",
        "alert": {
            "maxLevel": 0,
            "items": []
        },
        "id": "LSFD03209KC000282",
        "customExt": {
            "pressure1": 948,
            "pressure2": 0,
            "batteryVoltage": 27.5,
            "acTemp": 44,
            "cv": 593.7,
            "rc": 12.4,
            "cp": 0,
            "totalCharge": 20539.6,
            "totalDischarge": 19911.5,
            "instantPower": 0,
            "airMode": "OFF",
            "middleDoorStatus": "CLOSE",
            "frontDoorStatus": "CLOSE",
            "handbrakeStatus": "OFF",
            "keyPosition": "ON"
        },
        "extreme": {
            "maxVoltageSubSysNo": 1,
            "maxVoltage": 3.3,
            "minVoltageSubSysNo": 1,
            "minVoltage": 3.285,
            "maxNtcSubSysNo": 1,
            "maxNtcNo": 26,
            "maxNtc": 38,
            "minNtcSubSysNo": 1,
            "minNtcNo": 17,
            "minNtc": 33
        },
        "location": {
            "state": 0,
            "lng": 121.70714908910453,
            "lat": 31.1175557514747
        },
        "motors": [
            {
                "no": 1
            }
        ],
        "overall": {
            "chargeStatus": "UNCHARGED",
            "speed": 42.9,
            "mileage": 15973,
            "voltage": 591.9,
            "current": 12.5,
            "soc": 0.68,
            "shift": "D",
            "resistance": 6500,
            "aptv": 0,
            "brake": 0
        },
        "tenSeconds": [
            {
                "accPedal": 0,
                "brake": 0,
                "speed": 42.9,
                "totalCurrent": 12.5
            },
            {
                "totalCurrent": 12.3,
                "accPedal": 0,
                "brake": 0,
                "speed": 42.9
            },
            {
                "brake": 0,
                "speed": 41.9,
                "totalCurrent": 13,
                "accPedal": 0
            },
            {
                "brake": 0,
                "speed": 41.9,
                "totalCurrent": 12.8,
                "accPedal": 0
            },
            {
                "accPedal": 0,
                "brake": 0,
                "speed": 41.9,
                "totalCurrent": 12.8
            },
            {
                "accPedal": 0,
                "brake": 0,
                "speed": 40.9,
                "totalCurrent": 12.8
            },
            {
                "accPedal": 0.34,
                "brake": 0,
                "speed": 40.9,
                "totalCurrent": 20.6
            },
            {
                "speed": 41.9,
                "totalCurrent": 126.7,
                "accPedal": 0.63,
                "brake": 0
            },
            {
                "brake": 0,
                "speed": 42.9,
                "totalCurrent": 130.1,
                "accPedal": 0.62
            },
            {
                "speed": 43.9,
                "totalCurrent": 93.7,
                "accPedal": 0.47,
                "brake": 0
            }
        ],
        "adas": [],
        "energy": {
            "heatingTotal": 1,
            "heatingReverse": 0,
            "compressor": 1.8,
            "turn": 1,
            "reverseTotal": 29416.9,
            "motor": 24.4,
            "dcdc": 3.6,
            "compressorTotal": 2499.5,
            "heatingReverseTotal": 0,
            "heating": 0,
            "turnTotal": 1351.9,
            "dcdcTotal": 3551.6,
            "air": 0,
            "length": 74,
            "defrostTotal": 887.5,
            "defrost": 0,
            "motorTotal": 0
        },
        "updatedAt": "2019-09-09T06:56:52.966Z",
        "createdAt": "2019-08-12T08:16:23.866Z"
    }
}
```

### 车辆删除事件

```json
{
    "flag": "EVENT",
    "event": "VEHICLE_DELETED",
    "vin": "LSFD03209KC000282",
    "ns": "/pudongbus/r1d5nr",
    "body": {
        "id": "LSFD03209KC000282",
        "deleteBy": "5d23016a11288c0012ef9a18",
        "ns": "/pudongbus/r1d5nr",
        "no": "S0P-097",
        "line": "5d4bef7f38762b00138e40e6",
        "model": "SWB6108BEV32",
        "modelBrief": "S0P",
        "plate": "沪A50325D",
        "producer": "申沃"
    }
}
```

### 电池异常事件

收到bus-tbox的消息后，如果含有电池异常，则发电池异常事件。
消息会根据vin进行分区，保证同一vin下的消息在同一个分区，保证消费顺序。

细分```code```类型包括4类
* TEMP_OVER_55
* TEMP_BETWEEN_45_55
* SOC_BELOW_20_PERCENT
* SOC_BETWEEN_20_30_PERCENT

```json
{
  "flag": "EVENT",
  "event": "EXCEPTION",
  "vin": "LSFD03206KC000918",
  "ns": "/shanghaibus/c4/lb9jk",
  "body": {
    "at": "2019-10-28T07:31:31.000Z",
    "type": "BATTERY",
    "code": "TEMP_OVER_55",
    "maxNtc": 203,
    "maxNtcNo": 101,
    "soc": 0.72,
    "vehicle": {
      "id": "LSFD03206KC000918",
      "no": "S0Q-0005",
      "line": "5d90aa3ac542e60013c2694f",
      "plate": "沪A53970D",
      "model": "SWB6109BEV63",
      "modelBrief": "S0Q",
      "producer": "申沃"
    }
  }
}
```

### 绝缘异常事件

收到bus-tbox的消息后，如果含有绝缘异常，则发绝缘异常事件。
消息会根据vin进行分区，保证同一vin下的消息在同一个分区，保证消费顺序。

细分```code```类型包括2类
* RESISTANCE_BELOW_500
* RESISTANCE_BETWEEN_500_1000

```json
{
  "flag": "EVENT",
  "event": "EXCEPTION",
  "vin": "LSFD03206KC000918",
  "ns": "/shanghaibus/c4/lb9jk",
  "body": {
    "at": "2019-10-28T07:31:31.000Z",
    "type": "INSULATION",
    "code": "RESISTANCE_BELOW_500",
    "resistance": 0.4,
    "vehicle": {
      "id": "LSFD03206KC000918",
      "no": "S0Q-0005",
      "line": "5d90aa3ac542e60013c2694f",
      "plate": "沪A53970D",
      "model": "SWB6109BEV63",
      "modelBrief": "S0Q",
      "producer": "申沃"
    }
  }
}
```

### 轮胎异常事件

收到bus-tbox的消息后，如果含有轮胎异常，则发轮胎异常事件。
消息会根据vin进行分区，保证同一vin下的消息在同一个分区，保证消费顺序。

细分```code```类型包括3类
* TEMP_OVER_40
* PRESSURE_OVER_1100
* PRESSURE_BELOW_900

```json
{
  "flag": "EVENT",
  "event": "EXCEPTION",
  "vin": "LSFD03206KC000918",
  "ns": "/shanghaibus/c4/lb9jk",
  "body": {
    "at": "2019-10-28T07:31:31.000Z",
    "type": "TYRE",
    "code": "TEMP_OVER_40",
    "tyre": "rr1",
    "tt": 41,
    "tp": 1000,
    "vehicle": {
      "id": "LSFD03206KC000918",
      "no": "S0Q-0005",
      "line": "5d90aa3ac542e60013c2694f",
      "plate": "沪A53970D",
      "model": "SWB6109BEV63",
      "modelBrief": "S0Q",
      "producer": "申沃"
    }
  }
}
```

### 终端异常事件

后台定期检查，如果含有终端异常，则发终端异常事件。
消息会根据vin进行分区，保证同一vin下的消息在同一个分区，保证消费顺序。

细分```code```类型包括
* TERMINAL_DISCONNECTED

```json
{
    "flag": "EVENT",
    "event": "EXCEPTION",
    "vin": "LZYTCGBW9H1037220",
    "ns": "/bus/shanghai/chongming/c1",
    "body": {
        "type": "TERMINAL",
        "code": "TERMINAL_DISCONNECTED",
        "at": "2019-12-13T04:51:07.000Z",
        "departAt": "2019-12-13T04:51:07.000Z",
        "arriveAt": "2019-12-13T05:59:09.000Z",
        "vehicleAt": "2019-12-10T17:08:21.000Z",
        "reportedAt": "2019-12-10T17:08:21.000Z",
        "vehicle": {
            "id": "LZYTCGBW9H1037220",
            "no": "Z9D-0073",
            "line": "5dcc187046dae2001303dad8",
            "plate": "沪A-01320D",
            "model": "ZK6935BEVG2",
            "modelBrief": "Z9D",
            "producer": "宇通"
        }
    }
}
```

### 电池预警外部事件

定期从CATL获取电池预警信息，每天至少1次。
消息会根据vin进行分区，保证同一vin下的消息在同一个分区，保证消费顺序。

例如
```json
{
    "flag": "EXT_EVENT",
    "event": "WARNING",
    "vin": "LZYTUGEWXG1059511",
    "body": {
        "id": "1675558",
        "vin": "LZYTUGEWXG1059511",
        "type": "SOC跳变",
        "frequency": 1,
        "abnormalValues": 86,
        "abnormalLocation": "3250",
        "warningAt": "2019-10-22T10:07:11.000Z"
    }
}
```

### 电池预警事件

收到电池预警外部事件后，会发出对内的电池预警事件

例如
```json
{
    "flag": "EVENT",
    "event": "CATL_WARNING",
    "vin": "LZYTUGEWXG1059511",
    "ns": "/shanghaibus/c4/lb9jk",
    "body": {
        "id": "1734484",
        "type": "SOC虚高",
        "frequency": 1,
        "abnormalValues": 10.09272,
        "abnormalLocation": "76",
        "warningAt": "2019-11-27T06:49:08.000Z",
        "usedYear": "1年",
        "vehicle": {
            "id": "LZYTUGEWXG1059511",
            "ns": "/shanghaibus/c4/lb9jk",
            "no": "S0Q-0005",
            "line": "5d90aa3ac542e60013c2694f",
            "plate": "沪A53970D",
            "model": "SWB6109BEV63",
            "modelBrief": "S0Q",
            "producer": "申沃",
            "overall": {
                "mileage": 1200
            }
        }
    }
}
```

### 班次事件

收到外部的班次事件后，会发出对内的班次事件

例如
```json
{
    "flag": "EVENT",
    "event": "BANCI",
    "vin": "LSFD13206KC000995",
    "ns": "/bus/shanghai/chongming/c3",
    "body": {
        "id": "99DDE09FD370768AE0533370580A899A",
        "banciSource": "CHONGMING_BANCI",
        "vehicle": "LSFD13206KC000995",
        "vehicleNo": "V2B-0006",
        "ns": "/bus/shanghai/chongming/c3",
        "date": "2019-12-16T16:00:00.000Z",
        "line": "5dcc0f56a53b420013eb2bf8",
        "plate": "沪A00800D",
        "driverNo": "10-01966",
        "driverName": "张永昌",
        "departAt": "2019-12-17T02:09:31.000Z",
        "arriveAt": "2019-12-17T03:04:28.000Z",
        "departPlace": null,
        "arrivePlace": null,
        "mileage": 50,
        "type": "全程"
    }
}
```

### 充电订单事件

```json
{
    "flag": "EVENT",
    "event": "CHARGING_ORDER",
    "vin": "LWXCD5E45GD600476",
    "ns": "/bus/shanghai/chongming/c2",
    "body": {
        "id": "OCCRG202001125282431285",
        "billCode": "202001110300169103",
        "way": "车枪识别充",
        "endReason": "平台终止",
        "station": "3102300002",
        "stationName": "上海崇明堡镇电厂公交充电站",
        "pile": "3102300002305",
        "pileName": "305号直流",
        "startAt": "2020-01-11T22:00:48",
        "endAt": "2020-01-12T00:23:47.983",
        "power": 178.24,
        "ecTaxInPrice": 0,
        "scTaxInPrice": 0,
        "orderAmount": 0,
        "cardUser": "",
        "ns": "/bus/shanghai/chongming/c2",
        "vehiclePlate": "沪DQ1256",
        "vehicleNo": "W1C-0411",
        "vehicleLine": "5d8e0b7e7e9ba80013ed7696",
        "vehicle": "LWXCD5E45GD600476",
        "orderDetail": {
            "valleyPower": 0,
            "peakEc": 0,
            "peakSc": 0,
            "sharpTime": 0,
            "flatTime": 143,
            "sharpEc": 0,
            "flatPower": 178.24,
            "sharpPower": 0,
            "flatTotalPrice": 0,
            "valleyEc": 0,
            "valleySc": 0,
            "flatEc": 0,
            "sharpSc": 0,
            "valleyTotalPrice": 0,
            "sharpTotalPrice": 0,
            "flatSc": 0,
            "valleyTime": 0,
            "peakTime": 0,
            "peakPower": 0,
            "peakTotalPrice": 0
        }
    }
}
```
