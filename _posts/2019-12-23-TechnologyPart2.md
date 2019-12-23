---
layout : post
title : スクメロを作ってみた (技術編 その2)
---

この記事は[『スクールガールストライカーズ2 Advent Calendar 2019』](https://adventar.org/calendars/4503) の12/23分の記事です。


UnityとC#でスクメロを作ってみた記録です。
今日は技術編 その2です。

- エディタ

![エディタ]({{ site.baseurl }}/assets/images/posts/20191223_1.png)

WPF + C# 製です。
データバインディングの勉強がてら作ってみました。
画面の中央でノートの配置を行い、画面下側でノートのタイミングを調整します。
基本的な操作はマウスだけで完結できるようにしています。


- 実装について
  - シリアライズ / デシリアライズ

  XMLReaderクラスとXMLWriterクラスを使う

<pre>

var xmlSerializer = new XmlSerializer(typeof(ProjectInfomations));

using (var streamReader = new StreamReader(openedFileName, Encoding.UTF8))
{
  ~~
}
</pre>

<pre>
var xmlSerializer = new XmlSerializer(typeof(ProjectInfomations));

using (var streamWriter = new StreamWriter(saveDialog.FileName, false, Encoding.UTF8))
{
    xmlSerializer.Serialize(streamWriter, projectInfomations);
    streamWriter.Flush();
} 
</pre>

  - 更新処理
  DispacherTimerのTickイベントでメソッドを呼び出す

<pre>
private System.Windows.Threading.DispatcherTimer dispatcherTimer;
</pre>

<pre>
dispatcherTimer = new System.Windows.Threading.DispatcherTimer(System.Windows.Threading.DispatcherPriority.Input);
dispatcherTimer.Interval = new TimeSpan(0, 0, 0, 0, 0);
dispatcherTimer.Tick += new EventHandler(Update);
dispatcherTimer.Start();
</pre>

<pre>
private void Update (object sender, EventArgs e)
{
    ~~
}
</pre>

- 作ってみて

  やっぱり楽しい。ついでに勉強になる~~からみんなもやろう。~~
  やはり勉強としての模倣は偉大だなと思う。


- プロジェクトの公開について

  スクメロは現在サービスは終了していますが、アプリ自体は保存版が配信されているのでまだ著作権はスクエアエニックス社かR-Force社が保持されているのかなと思います。

  画像や効果音の著作権が引っかかりそうなものを排除した上でコードだけを公開するのもありだと思いますけど今のところは特に公開する予定はないです。 ~~需要も特になさそうですし~~
  
  この辺りの知識が乏しいのでなんとも言えないですが……
