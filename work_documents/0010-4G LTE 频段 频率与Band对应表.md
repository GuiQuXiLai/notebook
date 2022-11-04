# 0010-4G LTE 频段 频率与Band对应表



## 中国运营商4G频段、网络制式、Band号如下：

| 4G频段 | 频段范围 | 网络制式 | 备注 |
| ------ | -------- | -------- | ---- |
| Band1  | 上行：1920~1980MHz<br>下行：2110~2170MHz | LTE FDD、WCDMA |      |
| Band2  | 上行：1850~1910MHz<br>下行：1930~1990MHz | GSM、WCDMA |      |
| Band3  | 上行：1710~1785MHz<br>下行：1805~1880MHz | GSM、LTE FDD |      |
| Band4  | 上行：1710~1755MHz<br>下行：2110~2155MHz | LTE FDD |      |
| Band5  | 上行：824~849MHz<br>下行：869~894MHz | GSM、WCDMA |      |
| Band7  | 上行：880~915MHz<br>下行：925~960MHz | LTE FDD |      |
| Band8  | 上行：880~915MHz<br>下行：925~960MHz | GSM |      |
| Band17      | 上行：704~716MHz<br>上行：734~746MHz |LTE FDD||
| Band20 | 上行：832~862MHz<br>下行：791~821MHz | LTE FDD |      |
| Band34 | 2010~2025MHz | TD-LTE、TD-SCDMA | A频段 |
|Band38|2570~2620MHz|TD-LTE、TD-SCDMA|D频段|
| Band39 | 1880~1920MHz | TD-LTE | F频段 |
| Band40 | 2300~2400MHz | TD-LTE | E频段 |
| Band41 | 2496~2690MHz | TD-LTE |      |
| Band42 | 3.5G | TD-LTE |      |
| Band43 | 3.6G | TD-LTE |      |



## 制式与Band

| 制式     | Band               |      |      |
| -------- | ------------------ | ---- | ---- |
| LTE FDD  | 1、3、4、7、17、20 |      |      |
| TD-LTE   | 34、38、39、40、41 |      |      |
| WCDMA    | 1、2、5            |      |      |
| GSM      | 2、3、5、8         |      |      |
| TD-SCDMA | 34、38             |      |      |

## 三大运营商与TD-LTE与LTE FDD频段

| 运营商 | TD-LTE频段                                     | LTE FDD频段                        | BAND                                                         |
| ------ | ---------------------------------------------- | ---------------------------------- | ------------------------------------------------------------ |
| 移动   | 2320~2370MHz<br>2575~2635MHz<br>(130MHz频段)   |                                    | 2320~2370落在Band40（2300~2400MHz）<br>2575~2635落在Band41（2496~2690MHz） |
| 联通   | 2300~2320MHz<br>2555~2575MHz<br>(联通几乎不用) | UL:1955~1980MHz<br>DL:2145~2170MHz | 2300~2320落在Band40（2300~2400MHz）<br>2555~2575落在Band41（2496~2690MHz）<br>落在Band1  上行 1920~1980MHz <br>                     下行 2110~2170MHz |
| 电信   | 2370~2390MHz<br>2635~2655MHz<br>(电信几乎不用) | UL:1755~1785MHz<br>DL:1850~1880MHz | 2320~2370落在Band40（2300~2400MHz）                          |
|        |                                                |                                    |                                                              |

> 可以看到，TD-LTE上都在Band40和Band41，但联通和电信几乎不建TD-LTE网，只用LTE FDD网 LTE FDD联通在Band1 （2.1G频段）而电信在Band3（1.8G频段）

## 三大运营商的3G频段

![image-20221104163308090](https://wjx-pic.oss-cn-hangzhou.aliyuncs.com/images/image-20221104163308090.png)
