# EventStormingPractice
  這是使用以下專案，來做事件風暴的練習。

  https://github.com/kgrzybek/modular-monolith-with-ddd

  事件風暴的介紹，可參考這個。

  https://ithelp.ithome.com.tw/articles/10219177

## 一、找出事件 ##
第1步驟就是找出事件，根據專案提供的需求，可以找出以下幾類事件
1. 關於Member的，建立，Member可以建立Meeting Group
2. 關於Meeting Group的，提出要求、認可或取消
3. 關於Meeting的，建立、加入會議成員、加入候補人員，加入不參加會議人員
4. 關於參加費用的，建立與支付
5. 關於系統的，User建立、User再選擇要當Member還是Player