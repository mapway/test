# 设备和网关的通讯协议

关于数据传输的分包，每次通过（WIFI 433 USB ZIGBEE BLUETOOTH）传输通道传输数据的数据包有必要进行数据包的长度验证，其基础格式为

|数据包长度，最大65535，包括这2个字节|通讯包的加密方法|通讯包的协议格式和版本|通讯数据包|
|---|---|---|---|
|2个字节|1个字节|1个字节|长度可变|	 
|PACK_LENGTH|PACK_ENC_TYPE|高位4BIT表示协议格式<br>地位2BIT表示协议版本|共有 (PACKAGE_LENGTH-3）个字节长度	 |	
|0x000F<br>(共16个字节)|0x00–>不加密<br>0x01->AES加密<br>加密部分不包括前三个字节|PACK_FORMART 协议格式<br>PACK_VERSION 协议版本<br>PACK_FORMART 目前有2种<br>0x10 ->二进制格式<br>0x20 ->JSON格式<br>PACK_VERSION 目前都为<br>0x01 ->第一版<br>|参加下面的数据<br>1.JSON数据格式<br>2.二进制格式描述|

## 通用数据包
此协议共定义5个基本的通讯指令

|索引|指令名称|二进制数值|描述|
|---|---|---|--|
|1|DEVICE_INFO_QUERY|0x0001	查询设备制造商信息|
|2|DEVICE_INFO_REPORT|0x0002|设备报告自己的信息|
|3|DEVICE_CONTROL|0x0003|设备控制指令|
|4|DEVICE_CONTROL_RESPONSE|0x0004|控制响应指令|
|5|DEVICE_STATE_NOTIFY|0x0005|设备状态发生变化通知消息|


