# 设备和网关的通讯协议

关于数据传输的分包，每次通过（WIFI 433 USB ZIGBEE BLUETOOTH）传输通道传输数据的数据包有必要进行数据包的长度验证，其基础格式为

|数据包长度，最大65535，包括这2个字节|通讯包的加密方法|通讯包的协议格式和版本|通讯数据包|
|---|---|---|---|
|2个字节|1个字节|1个字节|长度可变|	 
|PACK_LENGTH|PACK_ENC_TYPE|高位4BIT表示协议格式<br>地位2BIT表示协议版本|共有 (PACKAGE_LENGTH-3）个字节长度	 |	
|0x000F<br>(共16个字节)|0x00–>不加密<br>0x01->AES加密<br>加密部分不包括前三个字节|PACK_FORMART 协议格式<br>PACK_VERSION 协议版本<br>PACK_FORMART 目前有2种<br>0x10 ->二进制格式<br>0x20 ->JSON格式<br>PACK_VERSION 目前都为<br>0x01 ->第一版<br>||


