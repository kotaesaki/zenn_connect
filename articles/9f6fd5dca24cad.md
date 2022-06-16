---
title: "GoogleAnalytics 4でボタンにイベントを仕込む"
emoji: "🐥"
type: "tech" # tech: 技術記事 / idea: アイデア
topics: ["googleanalytics", "javascript", "typescript"]
published: false
---

# 自己紹介
エンジニア1年生(25)🐣

# はじめに
create-react-app環境でボタンをクリックしたらイベントを発生させる方法を備忘録として残します！
※GoogleAnalyticsの初期設定は済ませている前提です。
**※バージョン4の方法なのでそれ以外だとやり方違うと思いますので注意です！**

# 手順1 GoogleAnalyticsからイベントを追加
https://analytics.google.com/analytics/　から
**設定（左サイドバー） > イベント > イベントを作成** 
でイベントを作成します。

![](https://storage.googleapis.com/zenn-user-upload/b4f106066d92-20220616.png)

作成フォームが出るので、任意の名前をつけます。

注意点としては、カスタムイベント名と値を同じにしておくことです。
これで準備OKです。


# 手順2 gtagでイベントを送信する関数を作成
```ts
export const onClick = () => {
  window.gtag("event", "test", {
    event_category: "任意カテゴリー名をつけれます！",
    event_label: "ユーザーのIDとかつけてユーザーを特定できたりもします！",
  });
};
```

第二引数に先ほど設定したイベント名をつけることで、analyticsにイベント送信できます！
第三引数はoptionalで、```event_category```をつかって分類したり```event_label```でその他情報を付与することができます。
第三引数を入れない場合はanalyticsで(not set)と出るみたいです(?)


# 参考文献
https://developers.google.com/analytics/devguides/collection/gtagjs/events?hl=ja