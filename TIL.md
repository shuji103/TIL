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

## September 15
- JS, frontend
- UIタグの処理手順
    - 先に、html, cssでナビゲーション要素のクラスにis-activeをつけてアクティブな状態の時だけのスタイルを設定、コンテンツ要素は非表示のスタイルを設定
    - 以下、JS
    1. documentを取得
    2. 全体を囲うdivタグにつけたid名（js-tab）の要素を取得
    3. データ属性とquerySelectorAllを用いて、ナビゲーションエリア（4つのaタグ部分）、コンテンツエリア（4つのdivタグを取得
    4. 初期化（関数initで、1つ目の要素のみを表示）
    5. クリックしたらタブが切り替わる命令を定義
        1. ナビゲーション要素がクリックされたら、まずイベントを殺す（引数にeを渡して、e.preventDefault();でaタグのページ遷移を無効化）
        2. e.target, datasetを用いて、targetVal（クリックされた要素の設定したデータ属性の値）を取得
        3. 対象外のnav,content全てリセット（ループ文で、コンテンツエリアを非表示、ナビゲーション要素のis-activeというクラスを排除）
        4. 2で取ってきた情報をもとに、対象のコンテンツエリアのみの要素を取得して、アクティブ化（その要素に対して、見える化、is-activeというクラスを付け加えてスタイル適応）
    6. 全nav要素に対して関数を適応・発火

## September 16
- JS, frontend
- クラスとインスタンス
    - クラスは構造の部分で、インスタンスはこの構造をもとに固有の値を入れて出力していったもの
    - クラスをまず作って、そこからAさんの投稿、Bさんの投稿というインスタンスを作っていく
    - class クラス名 {
        // 初期化
        constructor(obj){
            // 要素の取得 (obj.◯◯)
            // 実行部分
            this.関数名();
        }
        // 関数の定義
        関数名(){}
      }
      // インスタンスの生成
      const インスタンス名 = new クラス名({オブジェクトのkey: '値'});

- AccordionUIの処理手順（クラスとインスタンスなしver.）
    html
    1. js-accordionというidのdivタグを作成
    2. accordion-trigger（コンテンツを展開するクリックする部分）とaccordion-contentsというクラス作成
    css
    1. display: none;で、contentsの初期表示を非表示に
    js
    1. DOM要素の取得(#js-accordion, aタグ)
    2. 実行部分（addEventListenerで、triggerがクリックされたら、関数clickHandlerの引数にeを渡して実行）
    3. 関数の定義（クリックしたら、イベントを殺し（aタグのページ遷移の無効化し）、currentTargetとnextElementSiblingで、クリックされた要素の次の要素(コンテンツ部分)を取得し、そのスタイルが表示状態なら非表示に、非表示状態なら表示させる）

- AccordionUIの処理手順（クラスとインスタンスありver.）
    js
    1. クラス内のconstructorを実行
        1. DOM要素の取得（引数にobjを渡し、インスタンスで指定した部分(hookName, tagName)を呼び、obj.hookName, obj.tagNameで指定した要素(id名, タグ名)を取得）
        2. 実行部分（this.clickHandlerで、クラス内の関数の定義部分を呼んで実行）
        3. 関数の定義
    html
    1. 同じ構造のhtmlをコピペし、id, タグをインスタンスと対応させる
    js
    1. インスタンスの生成部分で、インスタンスの名前、hookName、tagNameを対応させる