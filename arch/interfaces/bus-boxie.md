## bus-boxie对外消息接口

bus-boxie对外消息有以下几类

### 路单外部事件

从外部系统获取运营路单事件

支持的类型有
* SHANGHAI_BANCI
* CHONGMING_BANCI

```json
{
    "type": "SHANGHAI_BANCI",
    "payload": {
        "id": "40271594",
        "vehicleNo": "Z9D-0016",
        "date": "2019-09-26",
        "company": "巴士一公司",
        "convoy": "三车队",
        "line": "80",
        "plate": "沪A-05546D",
        "driverNo": "01-06905",
        "driverName": "汪宗辰",
        "departAt": "2019-09-26T01:00:00.000Z",
        "arriveAt": "2019-09-26T01:42:00.000Z",
        "drpartPlace": "怀德路杨树浦路",
        "arrivePlace": "安波路营口路",
        "mileage": 9.325,
        "remark": "",
        "type": "全程",
        "sfyy": "营业公里",
        "ldlx": "路线车",
        "sxx": "0"
    }
}
```
