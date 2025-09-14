## September 10
- JS
- 変数と宣言は、const 変数名 = 値;
- 変数を使えば、コードの意味を簡略化でき、修正も効率的にできる
- データ型は6つあって、数値、文字列、論理値、未定義、null、オブジェクト
- 配列は、値を並列に管理するもの。array = []
- ループ文は、同じ動作を繰り返すもの。for (初期値; 条件式; 増減式) {}

## September 11
- JS
- callback関数は、関数の引数に渡されて、連続した処理を可能にする関数

## September 12
- JS
- 標準組み込み関数にはparseInt()、標準組み込みオブジェクトにはMathがある。
- ブラウザーAPIは、ブラウザやユーザーの動作に応じて、動的にwebページを操作することを可能にするAPI。windowの動きを制御するwindowオブジェクトとhtml,cssを制御するdocumentオブジェクトがある。イベントでは、要素を取得した後、それに対してhtmlを操作するきっかけを追加する。
- JSのデバック方法では、console.log()を用いて、原因を細かく切り分けて考える。

## September 13
- JS, frontend
- カウンタープログラムの処理手順
    1. getElementById()の引数にjs-counterを指定し、htmlのカウンターの数字を表示する要素を取得して、変数$counterに代入
    2. document.getElementById("js-button").addEventListener()で、ボタンがクリックされた時に、カウンターの数字を取得し、それに1を足した値を再度カウンターの数字に代入
- カウンタープログラム2の処理手順
    1. counter.jsでは、まず、getElementsByClassName()で、クラス名でhtml要素を取得。「クリックイベントそのもののオブジェクト」を意味するeという引数をaddEventListener()に渡して、クリックされた単独の要素だけを返すcurrentTargetを用いる。currentTargetとカウンター要素を取得して、ボタン要素が持つテキストが+なら＋1、-なら-1する
    2. reset.jsでは、ボタン要素がクリックされたら、カウンターのテキストの値を0にする

## September 14
- JS, frontend
- クイズゲームの処理手順
    定数の文字列をhtmlに反映
    1. 問題文、選択肢、答えを定義
    2. htmlのテキスト要素を取得して、問題文に書き換え
    3. htmlボタン要素を取得して、選択肢に書き換え
    *(2.3.は関数setupQuiz()にする)
    ボタンをクリックしたら正誤判定
    1. ボタンに対してaddEventListenerを設定して、クリックされたらcorrectとtextContentが一致したら正解・しなかったら不正解
    2. quizIndexとquizLengthを定義して、正誤判定後にこの2つが一致するまでquizIndexを+1してsetupQuiz()の処理をループさせることで、クイズの数分繰り返せるようにする
    結果画面
    1. scoreを定義
    2. 正誤判定で正解したらscoreに+1
    3. quizIndexとquizLengthが一致したらテキストとして出力
