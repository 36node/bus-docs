## bus-tbox对外消息接口

bus-tbox对外消息只有一种，即COMMAND，其中request里具体command和body定义参考32960。

计划中同一个vin对应消息应该保证消费顺序与发送顺序一致，但没有配置根据vin进行分区，目前没有顺序保证。

```json
{
  "time": number,
  "session": "string",
  "seq": number,
  "request": {
    "flag": "COMMAND",
    "command": "string",
    "vin": "string",
    "body": {},
  },
  "data": "string",
}
```

例如
```json
{
  "time": 1547609015380,
  "session": "_H2wm5nd2C",
  "seq": 3934572,
  "request": {
    "command": "REALTIME_REPORT",
    "flag": "COMMAND",
    "vin": "LJM6GCDB8GAS01165",
    "encrypt": "NONE",
    "length": 582,
    "body": {
      "at": "2019-01-16T03:23:33.000Z",
      "items": [
        {
          "type": "OVERALL",
          "status": "ON",
          "chargeStatus": "UNCHARGED",
          "mode": "ELECTRIC",
          "speed": 0,
          "mileage": 124185,
          "voltage": 548.4,
          "current": 11.1,
          "soc": 0.55,
          "dcStatus": "ON",
          "shift": "D",
          "resistance": 7394,
          "aptv": 0,
          "brake": 0.3
        },
        {
          "type": "MOTOR",
          "count": 1,
          "motors": [
            {
              "no": 1,
              "status": "GENERATION",
              "controlTemp": 43,
              "speed": 0,
              "torque": -37,
              "temp": 86,
              "voltage": 548.4,
              "current": 0
            }
          ]
        },
        { "type": "LOCATION", "state": 0, "lng": 121.452021, "lat": 31.38529 },
        {
          "type": "EXTREME",
          "maxVoltageSubSysNo": 1,
          "maxVoltageSingNo": 165,
          "maxVoltage": 3.296,
          "minVoltageSubSysNo": 1,
          "minVoltageSingNo": 121,
          "minVoltage": 3.265,
          "maxNtcSubSysNo": 1,
          "maxNtcNo": 11,
          "maxNtc": 22,
          "minNtcSubSysNo": 1,
          "minNtcNo": 66,
          "minNtc": 13
        },
        {
          "type": "ALARM",
          "maxLevel": 0,
          "uas": {
            "ressChargeOver": 0,
            "motorTemp": 0,
            "highVolMuteStatus": 0,
            "motorControlTemp": 0,
            "dcdcStatus": 0,
            "brake": 0,
            "dcdcTemp": 0,
            "insulation": 0,
            "batteryBadConsistency": 0,
            "ressNotMatch": 0,
            "socJump": 0,
            "socOver": 0,
            "batteryLow": 0,
            "batteryOver": 0,
            "socLow": 0,
            "ressVolLow": 0,
            "ressVolOver": 0,
            "batteryTempOver": 0,
            "tempDiff": 0
          },
          "ressLen": 0,
          "ressList": [],
          "mortorLen": 0,
          "mortorList": [],
          "engineLen": 0,
          "engineList": [],
          "otherLen": 0,
          "otherList": []
        },
        {
          "type": "RESS_VOLTAGE",
          "subCount": 1,
          "subSystems": [
            {
              "no": 1,
              "voltage": 1,
              "current": 0,
              "batteryCount": 255,
              "frameStartBatteryNo": 1,
              "frameBatteryCount": 200,
            }
          ]
        },
        {
          "type": "RESS_TEMPERATURE",
          "subCount": 1,
          "subSystems": [
            {
              "no": 1,
              "probeCount": 66,
            }
          ]
        }
      ]
    },
  },
  "data": "232302fe4c4a4d36474344423847415330313136350102461301100b17210101030100000012f2fa156c277f37011e1ce2001e02010102534e204cae7e156c27100500073d35f501dee6ca0601a50ce001790cc1010b3e01423507000000000000000000080101000a271000ff0001c80cc60cc60cc70cc70cc60cc70cc80cc70cc60cc60cc70cc60cc70cc70cc80cc70cc70cc70cc80cc80cc60cc70cc70cc70cc70cc70cc80cc70cc70cc70cc80cc70cc60cc70cc80cc80cc70cc70cc80cc80cc80cc70cc80cc80cc60cc70cc80cc70cc60cc60cc70cc60cc70cc80cc80cc70cc70cc70cc70cc70cc70cc70cc80cc70cc70cc70cc80cc80cc60cc70cc70cc70cc10cc20cc20cc10cc10cc20cc30cc20cc10cc10cc20cc20cc10cc10cc20cc10cc20cc20cc30cc20cc10cc20cc20cc10cc10cc20cc30cc20cc20cc20cc30cc20cc20cc20cc20cc20cc20cc20cc20cc10cc20cc30cc40cc30cc10cc20cc20cc20cc10cc20cc20cd60cdc0cd70cd30cd50cd60cd70cd20cd40cd10cd60cd10cd30cd40cd50cd20cd50cda0cd50cd10cd30cd10cd70cd20cd40cd60cd70cd20cd60cdb0cd70cd20cd40cd10cd80cd20cd50cd50cd80cd20cd60ce00cd70cd20cd50cd20cd60cd20cd40cd90cd70cd20cd50cd60cd80cd30cd60cd30cd80cd30cd60cd80cd90cd40cd70cd90cd60cd40cd70cd00cd50cd10cd30cd90cd60cd10cd309010100423c3c3c3c3d3d3c3d3c3d3e3d3b3d3c3c3c3c363636353636363736363636353635353636353636353535353635353635353635353635353635353636353635353635d00014000000000000000000000000000000000010f2652d",
}
```
