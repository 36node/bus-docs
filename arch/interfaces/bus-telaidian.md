## bus-telaidian对外消息接口

### 充电站信息

```
{
  flag: "TELAIDIAN_CHARGING_INFO", // 日志flag，表示这条日志是特来电充电信息
  type: "STATION_INFO", // 数据类型
  payload: {
    id: "3102300002", // 充电站id
    operatorId: "395815801", // 运营商id
    equipmentOwnerId: "MA1G5G530", // 设备所属商id
    stationName: "上海崇明堡镇电厂公交充电站", // 充电站名称
    countryCode: "CN", // 充电站国家代码
    areaCode: "310151", // 充电站省市辖区编码 GB/T 2260-2007
    address: "上海市市辖区崇明区堡镇电力路1号", // 详细地址
    stationTel: "", // 站点电话
    serviceTel: "13697985777", // 服务电话
    stationType: 100, // 站点类型 1:公共, 50:个人, 100:公交(专用), 101:环卫(专用), 102:物流（专用）, 103: 出租车（专用）, 255: 其他
    stationStatus: 50, // 站点状态 0:未知, 1:建设中, 5:关闭下线, 6:维护中, 50:正常使用
    parkNums: 0, // 车位数量
    stationLng: 121.226528, // 经度 GCJ-02 坐标系
    stationLat: 31.739049, // 维度 GCJ-02 坐标系
    siteGuide: "", // 站点引导
    construction: 2, // 建设场所 1:居民区, 2:公共机构, 3:企事业单位, 4:写字楼, 5:工业园区, 6:交通枢纽, 7:大型文体设施, 8:城市绿地, 9:大型建筑配建停车场, 10:路边停车位, 11:城际高速服务区, 255:其他
    pictures: [
      //站点照片
      "https://resource.teld.cn/teldimage/115/53a43bed90ee44d0a79b1a84c451d074.jpg",
      "https://resource.teld.cn/teldimage/115/0bd9895220e2471b94fc93ea3396e18e.jpg",
      "https://resource.teld.cn/teldimage/115/730415f9163746bca7097a21a16734a2.jpg",
      "https://resource.teld.cn/teldimage/115/979e4b95c29e49ce9e0a9e7c950578bc.png",
    ],
    matchCars: "", // 使用车型描述
    parkInfo: "", // 车位楼层及数量描述
    busineHours: "周一至周日00:00-24:00", // 营业时间描述
    electricityFee: "电费:00:00~24:00:0.0000", // 充电费描述
    serviceFee: "服务费:00:00~24:00:0.0000", // 服务费率描述
    parkFee: "免费", // 停车费
    payment: "线上", // 支付方式
    supportOrder: 0, // 是否支持预约 0:不支持， 1:支持
    remark: "", // 备注
  }
}
```

### 充电桩信息格式

```
{
  type: "PILE_INFO",
  flag: "TELAIDIAN_CHARGING_INFO",
  payload: {
    id: "3102300002324", // 充电设备id
    equipmentName: "324号直流", // 充电设备名称
    manufacturerId: "395815801", // 设备生产商编码
    manufacturerName: "青岛特锐德电气股份有限公司", // 设备生产商名称
    equipmentModel: "3907060140040053", // 设备型号
    productionDate: "", // 生产日期
    equipmentType: 1, // 设备类型 1:直流设备, 2:交流设备, 3:交直流一体设备, 4:无线设备, 5:其他
    equipmentLng: 121.226528, // 设备经度 GCJ-02 坐标系
    equipmentLat: 31.739049, // 设备维度 GCJ-02 坐标系
    power: 150, // 充电设备总功率 kW
    connectorInfos: [
      // 充电设备接口信息
      {
        connectorId: "3102300002324", // 接口id
        connectorName: "324号直流", // 接口名称
        connectorType: 4, // 接口类型 1:家用插座, 2:交流接口插座（模式3, 连接方式C）, 3:交流接口插头（带枪线，模式3, 连接方式C）, 4:直流接口长枪头（带枪线，模式4）, 5:无线充电座, 6:其他
        voltageUpperLimits: 750, // 额定电压上限 V
        voltageLowerLimits: 250, // 额定电压下限 V
        current: 200, // 额定电流 A
        power: 150, // 额定功率 kW
        parkNo: "", // 车位号
        nationalStandard: 2, //国家标准 1: 2011, 2:2015
      },
    ],
  }
}
```

### 订单信息

```
{
  type: "CHARGING_ORDER",
  flag: "TELAIDIAN_CHARGING_INFO",
  payload: {
    id: "OCCRG201912259514705879", // 订单id
    billCode: "201912240300185993", // 订单编号
    way: "车枪识别充", // 充电启动方式
    endReason: "平台终止", // 充电结束原因
    staCode: "3102300002", // 电站id
    staName: "上海崇明堡镇电厂公交充电站", // 电站名称
    pileCode: "3102300002311", // 充电桩id
    pileName: "311号直流", // 充电桩名称
    startAt: "2019-12-24T23:55:57", // 充电开始
    endAt: "2019-12-25T00:04:09.86", // 充电结束
    power: 13.74, // 充电电量 kw/h
    ecTaxInPrice: 0, // 电费
    scTaxInPrice: 0, // 服务费
    orderAmount: 0, // 订单金额
    cardNo: "", // 充电卡号
    cardUser: "", // 充电卡使用人
    driverName: "", // 司机
    busSubsidiary: "", // 公交子公司
    carLineNo: "", // 公交线路
    vehiclePlate: "沪DQ1267", // 车牌号
    vin: "LWXCD5E40GD600479", // vin码
    carNo: "", // 车辆号
    orderDetail: {
      sharpPower: 0, // 尖时电量
      sharpTime: 0, // 尖时时长
      sharpEc: 0, // 尖时电费
      sharpSc: 0, // 尖时服务费
      sharpTotalPrice: 0, // 尖时费用
      peakPower: 0, // 峰时电量
      peakTime: 0, //峰时时长
      peakEc: 0, //峰时电费
      peakSc: 0, //峰时服务费
      peakTotalPrice: 0, //峰时费用
      flatPower: 13.74, //平时电量
      flatTime: 8, //平时时长
      flatEc: 0, //平时电费
      flatSc: 0, //平时服务费
      flatTotalPrice: 0, //平时费用
      valleyPower: 0, //谷时电量
      valleyTime: 0, //谷时时长
      valleyEc: 0, //谷时电费
      valleySc: 0, //谷时服务费
      valleyTotalPrice: 0, //谷时费用
    },
  }
}
```
