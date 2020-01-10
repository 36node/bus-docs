## bus-pile对外消息接口

### 充电站设备状态

```json
{
    "flag": "EXT_EVENT",
    "event": "TELAIDIAN_STATION_STATUS_SNAPSHOT",
    "vin": "TELAIDIAN",
    "ns": "/bus/station/telaidian",
    "body": {
        "ConnectorStatusInfo": {
            "ConnectorID": "3102300002217",
            "Status": 1,
            "LockStatus": 0,
            "ParkStatus": 0
        }
    }
}
```