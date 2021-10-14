ISO 11898-1:2015 协议详细定义了CAN网络报文的格式，包含了传统CAN与CANFD帧格式。CAN网络的帧类型共有4种，分别为数据帧、远程帧、错误帧、过载帧。本章将主要介绍CAN网络数据帧报文的格式，CAN网络中数据帧报文共有4种类型，分别为传统标准帧、传统扩展帧、CANFD标准帧、CANFD扩展帧，其数据帧报文的格式由如下字段域组成：

![img](D:\software\typora\work\CAN\CAN CANFD format.assets\20190708180228298-163420272507417.png)

SOF：为帧的开头，该字段由一个显性位组成，当一个节点要往CAN总线上传输报文时，总线上的所有节点要同步该标志位当检测到SOF的上升边沿，这样就可以为后面的报文仲裁提供统一的时间参考。



Arbitration field:为仲裁域，用于判断总线上哪个报文可优先进行传输，当节点传输一个隐性位（该逻辑值为1）时，会采样CAN总线上的电平，如果采集到的为显性电平（该逻辑值为0），则该节点丢失仲裁，不能继续往总线上发送数据，因此ID越小的报文其优先级越高。该域主要由报文的ID组成。



Control field:为控制域，主要控制报文数据域数据的长度。

 

Data field:为数据域，主要由上层传输的数据组成。

 

CRC field:为CRC校验域，主要用于校验帧报文数据的正确性，对于CANFD报文而言，不同数据长度的报文其采取的CRC多项式是不一样的。

 

ACK field:为ACK域，主要用于告知发送方接收方已经正确收到该报文。

 

EOF：为帧的结束标志。

 

在进一步介绍CAN数据帧的格式时，有必要先介绍如下一些术语与缩写及说明：

SOF(Start Of Frame)：帧开头，用于指示帧报文的开始。

 

CRC(Cyclic Redundancy Check)：循环冗余校验，用于校验CAN报文的正确性。

 

ACK(Acknowledgement)：应答，用于指示CAN报文已经被目标节点接收。

 

EOF(End Of Frame)：帧结束，用于指示帧报文的结束。

 

RTR(Remote Transmission Request)： 远程传输请求，该标志用于区分数据帧还是远程帧报文。

 

IDE(Identifier Extension) ：ID扩展，该标志用于区分标准帧还是扩展帧报文。

 

FDF(FD Format indicator) ：FD格式标志，该标志用于区分传统CAN还是CANFD报文。

 

RRS(Remote Request Substitution)： 远程帧请求替代，该标志只用于CANFD报文中。

 

BRS(Bit Rate Switch)： 位速率开关，该标志只用于CANFD报文中，用于CANFD报文中数据域传输速率的切换

 

ESI(Error State Indicator)： 错误状态标志，该标志只用于CANFD报文中，用于指示节点的错误状态（error active或error passive）

 

SRR(Substitute Remote Request) 替代远程请求， 该标志只用于扩展帧中且只能传输隐性电平。

 

r0： 传统扩展帧里面的保留位。

 

res ：FD 帧的保留位。

 

下面将介绍CAN数据帧的报文格式

传统标准数据帧的格式如下所示：

![img](D:\software\typora\work\CAN\CAN CANFD format.assets\watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQxMjU2MjEy,size_16,color_FFFFFF,t_70-16342020996843)

 

传统扩展数据帧的格式如下所示：

![img](D:\software\typora\work\CAN\CAN CANFD format.assets\20190708180349590.png)

 

CAN FD标准数据帧（数据长度最大为16字节）格式如下所示：

![img](D:\software\typora\work\CAN\CAN CANFD format.assets\watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQxMjU2MjEy,size_16,color_FFFFFF,t_70-16342021222586)

 

CAN FD标准数据帧（数据长度为20~64字节）格式如下所示：

![img](D:\software\typora\work\CAN\CAN CANFD format.assets\watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQxMjU2MjEy,size_16,color_FFFFFF,t_70-16342021259948)

CAN FD扩展数据帧（最大字节长度为16）格式如下所示：

![img](D:\software\typora\work\CAN\CAN CANFD format.assets\watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQxMjU2MjEy,size_16,color_FFFFFF,t_70-163420212818610)

 

CAN FD扩展数据帧（数据长度为20~64字节）格式如下所示：

![img](D:\software\typora\work\CAN\CAN CANFD format.assets\watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQxMjU2MjEy,size_16,color_FFFFFF,t_70-163420213014112)

 

传统CAN报文与CANFD报文的DLC长度区别如下所示：

![img](D:\software\typora\work\CAN\CAN CANFD format.assets\watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3FxXzQxMjU2MjEy,size_16,color_FFFFFF,t_70-163420270733615)

 

总结：

传统CAN报文与CANFD报文的最大区别有2点，

​	1、CANFD可以传输更多的数据，

​	2、CANFD报文在传输中由2种传输速率完成传输，一种是标称的CAN总线速率（用于传输非数据域的字段），另一种是数据域传输速度（用于传输数据域的字段）
————————————————
版权声明：本文为CSDN博主「qq_41256212」的原创文章，遵循CC 4.0 BY-SA版权协议，转载请附上原文出处链接及本声明。
原文链接：https://blog.csdn.net/qq_41256212/article/details/95080176

