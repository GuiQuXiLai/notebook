# 001-访问控制 （ac-Barring、SSAC、EAB、Cell Barring）

## 访问控制

这幺多UE尝试访问同一个单元(小区)（eNB，NB，BTS等）会发生什幺？

在最坏的情况下，来自不同UE的信号相互干扰，不会被单元解码（信号被感知为噪声）。即使它们足够幸运地到达并被小区解码，也可能在小区和网络上造成过载。

在这种情况下，小区（网络）会怎幺做？我会尝试控制（限制）来自UE的访问量。这种控制过程称为“访问控制”。

访问控制有几种不同的方法，但就整体逻辑而言，我们可以想到下面列出的两种不同的机制。

- 类型1： 接受来自 UE 的初始请求，但网络发送拒绝消息
- 类型2：防止 UE 尝试初始访问它本身。（此类型称为“禁止”）
  - 情形1：禁止每个UE进行任何类型的访问，即使是紧急调用（由SIB1配置）
  - 情形2：仅禁止来自特定服务（由 SIB2 配置）的特定 UE（在 USIM 中具有特定标记）

类型1如果发生在RRC层通常由 RRC 连接拒绝，如果在 NAS 层的情况下则附加拒绝。

类型 2 通常由各种 SIB 设置完成，同样在类型2中，随着蜂窝技术的发展，已经发展了数个不同的方式。

在本文中，我将重点介绍类型2访问控制，以下是文章目录：

[TOC]

##  访问控制的因素（Factors）/消息（Message）/参数（Parameters）

首先，让我们考虑访问控制中涉及的所有因素（无线电消息(Radio Messages)和参数(Parameters)）。

这些参数在访问控制中如何发挥作用？

我稍后会发布解释。但我认为你可以自己想象。

请参阅 3GPP 22.011 4.Access Control和 36.331 将为您提供每个参数的详细含义。我同时强烈建议您在参考规范之前尝试根据自己的思考作出自己的描述。

一个重要的提示，这些消息中的大多数都具有一个以位图（bitmap）为形式的参数。这些位图表示访问控制类（每个位表示一个特定的访问控制类）。

UE 如何知道它是属于哪个访问控制类呢？它在 USIM 的EF_ACC字段中指定。

以下是与各种类型的禁止（barring）相关的所有SIBs和信息元素（Information Elements）。禁止机制的细节可能很复杂和令人困惑，但我会尽力描述清晰。

### LTE SIB1

![image-20221013121343012](https://wjx-pic.oss-cn-hangzhou.aliyuncs.com/images/image-20221013121343012.png)

### LTE SIB2

![image-20221013121428227](https://wjx-pic.oss-cn-hangzhou.aliyuncs.com/images/image-20221013121428227.png)

### LTE SIB2 - Rel 12, 13

在 Rel 12、13 中，访问控制机制变得更加复杂。为了实现这一点，添加了许多其他IE，如红色中突出显示的那样。

![image-20221013122428783](https://wjx-pic.oss-cn-hangzhou.aliyuncs.com/images/image-20221013122428783.png)

### LTE SIB14

![image-20221013122448218](https://wjx-pic.oss-cn-hangzhou.aliyuncs.com/images/image-20221013122448218.png)



### LTE Paging

![image-20221013122515421](https://wjx-pic.oss-cn-hangzhou.aliyuncs.com/images/image-20221013122515421.png)



## SIB1的访问控制：Cell Barring

我根据36.304 5.3.1小区状态和小区保留创建了下表

| 信息元素设置                                                 | 禁止行为                                                     |
| ------------------------------------------------------------ | ------------------------------------------------------------ |
| cellBarred = not Barred<br>cellReservedForOperatorUse = not reserved | 允许此小区下的任意 UE 选择/重新选择此小区                    |
| cellBarred = not Barred<br>cellReservedForOperatorUse = reserved | ·允许分配给在其 HPLMN/EHPLMN 中运行的接入类 11 或 15 的 UEs 选择或重新选择此小区<br>· 分配给 0 到 9、12 到 14 范围内的访问类的 UEs将被禁止（不允许选择/重新选择此小区） |
| cellBarred = Barred<br>cellReservedForOperatorUse = Any      | UE不允许选择/重新选择此小区，甚至不允许用于紧急调用，并且必须选择另一个小区 |



##  SIB2的访问控制：ac-Barring

您可能很容易猜到SIB2的访问控制机制。您将看到以下结构的几个不同副本。只需查看参数的名称，您就可以猜到“这是为了仅允许（或禁止）某个UE组（Access Class）仅具有一定概率地访问某个服务”。

ac-BarringForXXXXXX

​		ac-BarringFactor: pXY (0)

​		ac-BarringTime: sA (0)

​		ac-BarringForSpecialAC: ABCDE (bitmap)

- 此处的 XXXXX 表示服务（应用进程）的名称。
- ac-BarringFactor表示允许访问的概率。
- ac-BarringForSpecialAC表示 UE 的访问类。A = 11， B = 12， C = 13， D = 14， E = 15



例如:

假设 pXY 设置为 p50，而特殊特定 AC 设置为 01000。 此位图指示每个访问类的状态，如下所示

![image-20221013124438481](https://wjx-pic.oss-cn-hangzhou.aliyuncs.com/images/image-20221013124438481.png)

因此，此限制仅适用于在其 USIM 中将访问类 12 被设置为“1”的 UE。

使用此 SIB 设置时，如果属于访问类 12 的 UE 看到此 SIB 参数，则会生成一个介于 0 和 1 之间的随机数。如果数字小于 0.5 （p50），则允许其访问。如果该数字大于 0.5，则不应访问。必要时，UE 可以在ac-BarringTime中设置的“A 秒”的常量间隔重试此操作。

## SIB2的访问控制：ssac-Barring

ssac 代表服务特定的访问控制。ac-Barring主要用于控制对一般信令和数据以及cs调用（在UMTS的情况下）的访问，但引入了通过LTE的语音和视频。有必要为LTE上的语音和视频通话提供访问控制机制，这就是ssac限制的动机。ssac-Barring被描述为TR 22.986。这种类型的访问控制的主要动机基于以下用户情形:

- 用户情形1

日本运营商在发生地震、海啸或台风等重大灾害时提供“灾害留言板”服务。这项服务使大量订阅者能够访问留言板，以便在发生重大灾害期间用手机张贴或检索有关受灾地区个人安全的信息。

人类的心理行为是在紧急情况下发出语音调用。因此，增加的语音流量消耗了太多的带宽来访问其他服务，例如灾难留言板和/或数据服务（例如SMS）。

因此，需要一种限制机制来区分带宽消耗的实时服务（例如语音）与带宽效率高的数据服务，以访问例如灾难留言板。

- 用户情形2

如上面的用例 1 中所述，订阅者可能希望拨打语音电话以检查个人的安全，这可能会导致拥塞。在这种情况下，优先用户（例如政府，军事、民政当局）和（发布施行国家法规的机构）访问紧急服务仍应被允许访问EPS，而其他用户的语音调用则受到限制。