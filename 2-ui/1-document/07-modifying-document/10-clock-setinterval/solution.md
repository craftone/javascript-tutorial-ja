まず、HTML/CSS を作りましょう。

時間の各要素は独自の `<span>` ではっきり見えます:

```html
<div id="clock">
  <span class="hour">hh</span>:<span class="min">mm</span>:<span class="sec">ss</span>
</div>
```

またそれらを色付けするために CSS が必要です。

`udpate` 関数は時計をリフレッシュし、毎秒 `setInterval` によって呼び出されます:

```js
function update() {
  let clock = document.getElementById('clock');
*!*
  let date = new Date(); // (*)
*/!*
  let hours = date.getHours();
  if (hours < 10) hours = '0' + hours;
  clock.children[0].innerHTML = hours;

  let minutes = date.getMinutes();
  if (minutes < 10) minutes = '0' + minutes;
  clock.children[1].innerHTML = minutes;

  let seconds = date.getSeconds();
  if (seconds < 10) seconds = '0' + seconds;
  clock.children[2].innerHTML = seconds;
}
```

行 `(*)` で、毎回現在の日付をチェックします。`setInterval` の呼び出しは信頼できません: 遅延が発生する可能性があります。

時計管理の関数です:

```js
let timerId;

function clockStart() { // run the clock
  timerId = setInterval(update, 1000);
  update(); // (*)
}

function clockStop() {
  clearInterval(timerId);
  timerId = null;
}
```

`update()` の呼び出しは `clockStart()` でスケジュールされるだけでなく、行 `(*)` でも即時実行さることに注意してください。それ以外の場合は、訪問者は`setInterval`の最初の実行まで待つ必要があります。また、時計はそれまで空です。
