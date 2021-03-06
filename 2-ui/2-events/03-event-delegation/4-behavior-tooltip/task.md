importance: 5

---

# ツールチップの振る舞い

ツールチップの振る舞いのための JSコードを書いてください。

マウスが `data-tooltip` を持つ要素上に来たら、ツールチップがその上に現れます。そしてマウスが過ぎると隠れます。


注釈付きのHTMLの例です:
```html
<button data-tooltip="the tooltip is longer than the element">Short button</button>
<button data-tooltip="HTML<br>tooltip">One more button</button>
```

このように動作します:

[iframe src="solution" height=200 border=1]

このタスクでは `data-tooltip` を持つすべての要素は内側にテキストだけと想定します。入れ子のタグはありません。

詳細:

- ツールチップはウィンドウの端は超えません。通常、ツールチップは要素の上にありますが、もし要素がページ上部にあり、ツールチップのスペースが無い場合、下に位置します。
- ツールチップは`data-tooltip` 属性の中で与えられます。それは任意のHTMLです。

ここでは2つのイベントが必要になります:
- ポインタが要素の上にきたとき、`mouseover` をトリガします。
- ポインタが要素を離れたとき、`mouseout` をトリガします。

イベント移譲を使用してください: `data-tooltip` を持つ要素からすべての "イン" と "アウト" を追跡するため、`document` 上に2つのハンドラを設定し、そこでツールチップを管理してください。

振る舞いが実装できたら、JavaScriptに精通していない人でも注釈付き要素を追加できます。

P.S. 自然でシンプルなものを保つために、一度に表示できるツールチップは1つだけです。
