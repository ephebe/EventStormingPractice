# EventStormingPractice
  這是使用以下專案，來做事件風暴的練習。

  https://github.com/kgrzybek/modular-monolith-with-ddd

  事件風暴的介紹，可參考這個。

  https://ithelp.ithome.com.tw/articles/10219177

## 一、排事件 ##
先把事件以過去式表達，並依事件先後順序排出
1. User註冊，核可後產生User,Member,Payer
2. Member提出產生Meeting Group,經Administrator確認，就產生Meeting Group
3. 若Member是Meeting Group的Organizer，就可以建立會議，加入會議成員、候補成員，不參加的Meeting Group成員，指定會議主席
4. 會議成員加入後，都要支付Meeting Fee
5. 一般成員可以訂閱Meeting Group，並支付訂閱的費用

![排事件](Images/EventStorming/1_排事件.svg?v=1)

## 二、角色命令流程 ##
加上事件對應的指令，為指令加上角色，當事件觸發指令通常有個規則，再補上外部系統
1. User Admin負責審核User Register
2. Member提出Meeting Group Proposal，Admin負責審核Proposal
3. Meeting Group Organizer加入會議成員，根據Meeting Fee Policy，建立應該支付的費用
4. 凡是要付錢的都是Payer, 不分Member or User。Payer支付會議費用透過一個Payment System的外部系統

![角色命令流程](Images/EventStorming/2_角色命令流程.svg?v=1)

## 三、決定Aggregate ##
關於Aggregate的概念請看這個，與DDD的概念是相同。

https://ithelp.ithome.com.tw/articles/10223936

![決定Aggregate](Images/EventStorming/3_決定Aggregate.svg?v=1)

## 四、劃分限界上下文 ##
根據原作者的建議，拆成User Access、Administrator、Meetings、Payments。Meetings是核心域、Payment與Administrator是支撐域、User Access算通用域。

https://ithelp.ithome.com.tw/articles/10216798

![劃分限界上下文](Images/EventStorming/4_劃分限界上下文.svg?v=1)

# FourColorAnalysis
我必須承認用事件風暴來分析，看來是非常繁瑣的。DomainEvent不但是接下來的Aggregate、UseCase、還是不同UC間的溝通方式。我嘗試用另一種分析法-四色原型分析法，再跑一下。圖形如下，也許這不是非常符合分析法的精神，但看來非常清楚。

![四色原型分析](Images/FourColor/FourColorAnalysis.svg)

再補上Use-Case Diagram，Use Case也算是一種分析去，兩相配合，我覺得很不錯。

![UseCase分析](Images/FourColor/UseCaseAnalysis.svg)