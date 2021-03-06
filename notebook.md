# 1.1 JavaScriptの歴史

JavaScriptフレームワークが登場するにいたる歴史的経緯を振り返る。

### JavaScriptの盛り上がり～不遇の時代
- 1990年代，JavaScriptベースのダイナミックHTMLという技術が流行った
	- 画面にアニメーション画像が走る
	- ページ切り替えにエフェクトがかかる
- しかし，これらが過剰に使われ，ページが重かった
- セキュリティホールが見つかったため，かなり限定的な環境じゃないと動かないようになった
- しばらくJavaScriptは不遇の時代を経る

### JavaScriptの復権
- 2005年，**Ajax**が登場した。
	- デスクトップ上で，デスクトップライクなページをつくれる
	- HTML，JavaScriptという標準的な技術でリッチなコンテンツが作れる
- ECMAによる標準化もあって，JavaScriptの見直しが図られた
- 2000年代後半にHTML5が登場，JavaScript APIが強化されていく
### JavaScriptライブラリから，JavaScriptフレームワークへ
- JavaScriptは生産性が高い言語とは言えない
	- ブラウザによって挙動が異なる問題
	- 特有の癖：プロトタイプベースと呼ばれる特殊なオブジェクト指向構文
	- 型の制約が緩い
- jQueryが一世を風靡，UI開発が容易になる。ただし，大規模開発は苦手
	- あくまでページ操作をサポートするライブラリである。例えば，見た目とビジネスロジックを明確に分離するようなアプリの構造化はできない。
➡ **以上の経緯から，大規模開発に向いた本格的なフレームワークが求められてきた**

# 1.2 フレームワークとは？
- フレームワークとは
>問題に対する定石（イディオム），または設計面での方法論を「再利用可能なクラス」という形でまとめたもの。
>言い換えると，アプリのコードを相互につなげるベース

- アプリ開発者は，フレームワークの基盤に沿って独自のコードを加えることで，一定の品質をもったアプリを作ることができる
- ライブラリとフレームワークはどう違うの？
	- **ライブラリ**：ユーザコードによって呼び出される。
	- **フレームワーク**：ユーザコードを呼び出す。
	- 後者は，アプリのライフサイクル（初期化から実処理，終了までの流れ）を管理しており，その要所要所で「なにをすべきか」をユーザコードに問い合わせる

## フレームワーク導入の利点
 - 開発生産性の向上
	- 同じルールを強制する。一貫性が保たれる
	- ユーザコードは機能ごとに相互に独立しているので，機能単位での役割分担をしやすく，大規模開発に向いている
- メンテナンス性に優れる
	- アプリの可読性が高い。問題個所の特定がしやすい
	- 同一のアーキテクチャを採用していれば，統合なども楽になる
	- 開発ノウハウを容易に引き継げる
- 先端の技術トレンドにも対応しやすい
	- フレームワークは日々更新される
	- セキュリティにも対応してくれる
- 一定以上の品質が期待できる
	- 自作アプリより「信頼性が高い」
	- 利用実績が長い
	- フレームワークを用いるということは，現在のベストプラクティスを導入するということ

## なぜAngularか
- 現時点でもっとも注目されるフレームワークのひとつである
- Googleが開発に携わっており，継続的なバージョンアップが期待できる
> ”人気やシェアは，フレームワークとしての良しあしを左右する決定的な基準ではありませんが，重要な要素ではあります。というのも，シェアの大きさは，様々なユーザの目にさらされ，実績を積み，支援されていることの証であり，そのまま「品質の高さ」「資料の豊富さ」「実績の蓄積」を物語っているからです”

## Angularの特徴
- フルスタックのフレームワーク
	- HTMLベースのテンプレートエンジン
	- ビジネスロジックを実装するためのサービス
	- URLに応じてページを振り分けるルーティング機能
	- 単体テスト・シナリオテストを支援するテストフレームワーク
	- など
- コンポーネント指向
	- コンポーネントは画面に複数配置できるし，階層構造にも出来る
	- Angularアプリとは，１つ以上のコンポーネントの集合である
	- コンポーネントは，ビュー，クラス，メタ情報の複合体
- JSの派生言語をサポートしているものの，TypeScriptで開発するのが無難
- Angularバージョンポリシー
	- バージョン番号は，「`メジャーバージョン`.`マイナーバージョン`.`パッチ`」で表現
	- パッチ：バグフィックスなどの微小な変更
	- マイナーバージョン：機能追加を伴うが，互換性は保たれる
	- メジャーバージョン：互換性が保たれないことがある破壊的な変更
- Angularは半年に一度バージョンアップする

## Angularアプリの構成部品：モジュール
### モジュールとは
- 関連するクラスをまとめて，モジュールとして扱う
	- **Angularアプリ**
		- `ルートモジュール`
			- コンポーネント，UI部品
			- サービス，ビジネスロジック
			- パイプ
			- ディレクティブ
		- `サブモジュール`
			- コンポーネント
			- サービス
		- `Angularモジュール`
			- Common Module
			- Http Module ...
			
	- アノテーション`@`：クラスを定義しただけでは，モジュールとはみなされない。`@NgModule`デコレータ―でモジュールとしての情報を宣言する必要がある。**デコレータ**とは，クラスやプロパティ，メソッド，引数などに対して，構成情報を付与するためのしくみ。

### サンプルアプリに含まれる構成物
- `app.component.ts`: ページを構成するUI部品を記述するコード
- `main.ts`: Angularアプリを起動するためのスタートアップコード
- `index.html`: メインページを準備する
- 設定ファイル:
	- `package.json`: Angular，またはアプリ本体で利用するライブラリ情報などを定義
	- `tsconfig.json`: TypeScriptコンパイラの動作を定義
	- `systemjs.config.js`: モジュールローダー(SystemJS)の設定情報
		- 呼び出したファイルの拡張子を省略したときの挙動の記述
		- `baseURL`などの設定

### サンプルアプリの利用方法


# 3. データバインディング
データバインディングとは？
>Angularアプリで画面（コンポーネント）を制御するうえで欠かせない仕組み。データバインディングを使用することで，コンポーネントの値をテンプレートに反映したり，テンプレートの変化をコンポーネントに伝達したり，といった仕掛けを限りなくコーディングレスで実装できます。

言い換えると，コンポーネントとテンプレート（ビュー）とを紐づけるための仕組み。

データバインディング構文

| データの方向 | 種類        | 記法 |
|--   |--                  |--          |
| C→V | Interpolation(補間) | `{{...}}` |
| C→V |プロパティ・属性バインディング|`[property]="value"`|
| C←V |イベントバインディング|`(event)="handler"`|
| C⇔V |双方向バインディング|`[(target)]="value"`|

ポイント：**バインド方式によって記法が異なる**

## 3.2 Interpolation構文

### ・`{{...}}`式
- テンプレートに埋め込む値を，コンポーネントのプロパティとして定義する
例：①で定義した`name`プロパティを②で`{{name}}`として参照する
```javascript
import { Component } from  '@angular/core';
@Component({
	selector:  'my-app',
	template:  `<h1>Hello {{name}}</h1>`, //②
})
export  class  AppComponent { name  =  'Angular'; } //①
```

補間の中身では，JavaScriptの構文が使える。ただし，以下の点に注意：
- 式が副作用を伴わない；ほかの値に影響が出ない
- 短時間で実行できる
- シンプルである
- 冪等である；同じ操作を繰り返して実行しても同じ結果を返す

`{{...}}`は何度も繰り返されるので，アプリが重くなる原因になることを避ける。

### ・`?.`演算子(Safe Navigation Operator)
```javascript
import { Component } from  '@angular/core';
@Component({
	selector:  'my-app',
	template:  `<h1>Hello {{member.name}}</h1>`, //①
})
export  class  AppComponent { 
	member = {
		name = '山田太郎',
		age = 30
	};
}
```
`member`プロパティをコメントアウトした状態で，これを実行すると，①で例外が発生する。
例外に対処するためには，nglfディレクティブを使って，あらかじめundefined/nullチェックを行えばよいが，コードが冗長になってしまう。ここで，①を次のように書き換えると，例外が発生しなくなる。
```javascript
	template:  `<h1>Hello {{member?.name}}</h1>`, //①'
```
これによって，オブジェクト`member`が空であるかどうかを確認し，から出ない場合のみに`name`プロパティにアクセスするので「安全」である。

## 3.3 プロパティバインディング
プロパティバインディングによって，要素のプロパティに対して値をバインドできる。
要素とは，例えばHTML要素などがある。

```javascript
import { Component } from  '@angular/core';
@Component({
	selector:  'my-app',
	//ブラケット構文
	template:  `<img [src]="image" />` //①
	//bind-xxxxx属性
	//template: `<img bind-src="image" />`　//②
	//Interpolation
	//template: `<img src="{{image}}" />` //③
})
export  class  AppComponent {
	image  =  'http://www.wings.msn.to/image/wings.jpg';
}
```
①では，`"image"`は文字列ではなく，プロパティを表す変数となる。
他にも，②，③などの書き方があるが，プロジェクトで統一するのが良い。

### HTML文字列をバインディングする
```javascript
import { Component } from '@angular/core';

@Component({
  selector: 'my-app',
  template: `<div>{{msg}}</div>`
})
export class AppComponent {
  msg: string = `Hello World!`　// ①
}
```
ここで仮に，①をHTMLのコードにした場合，HTML文字列はエスケープされて生の文字列が表示される。これは，意図しないタグを埋め込まれたりする脆弱性を残してしまうためである。このような攻撃をクロスサイトスクリプティングという。

ただし，HTMLを埋め込みたいときもある。その時は，
```javascript
@Component({
  selector: 'my-app',
  template: `<div [innerHTML]="msg"></div>`
})
```
とする。

ただし，HTMLのタグなどはそのままうめこまれるわけではなく，できるだけ脆弱性が残らないようにサニタイズされる。自分が意図したHTMLタグをすべて埋め込みたいなら，信頼済みマークを付ける必要がある。(参照：`bypassSecurityTrustHtml`メソッド)

### イベントバインディング
- マウスクリックなどに対応したバインディング。
- キーボード操作に関するイベント取得もできる。

#### イベントのデフォルト動作のキャンセリング：
- ふつうは，キーが入力されたら文字が画面に出てくる
- でも，入力フォームが郵便番号入力フォームだったら，数字以外入力ができないようにできる
- 参照：`e.preventDefault();`

#### バブリング
- 下位要素の操作が，上位要素に伝播すること
- 時に望ましくないので，`e.stopPropagation()`でブロックできる

>**コラム**
>`log.console("log output")`で，開発者ツールのコンソール出力を得られる。

#### Enterキーのイベント：`keyup.enter`
エンターキーは使用頻度が高いので，それ専用のイベントが存在。

### 双方向バインディング
- ビューへの変更がコンポーネントに伝わり，かつ，コンポーネントの変更もビューに伝わる。
- 実装方法はいろいろあるが，その一つが`ngModel`を用いる方法。
	- `[(ngModel)]="myName"`・・・`myName`オブジェクトに値が入ると，コンポーネントへの代入が行われる。逆も起こる。

# 4. 標準パイプ/ディレクティブ
とは？
>パイプ/ディレクティブとは，テンプレートで利用できるAngularの構文である。パイプは，与えられた式の値を加工・成形する機能，ディレクティブは条件分岐・繰り返し，スタイル定義など，文書ツリーを操作する機能を，それぞれ提供する。

## パイプ
- `{{price | currency: 'JPY'}}`: `price=1444`のとき，`JPY1,444`に加工される。
- さらにパイプをつけて，それに対して追加の処理を行うことができる。

Angular標準パイプ：
- lowercase, percent, number, slice ...
- `i18nPlural`: 数値によって場合分け
- `i18nSelect`: 文字列によって場合分け　

>もっとマシなパイプ名はなかったのか？

## ディレクティブ
ページに付加するカスタムの機能・要素。
- コンポーネント：テンプレートを伴ったディレクティブ
- 構造ディレクティブ：要素を追加・削除することで，文書ツリーを変更
- 属性ディレクティブ：属性の形式で，要素・コンポーネントの見た目や動作を変更

### スタイルの変更
ボタンを押すと，コンポーネントの背景色と文字色が変更される：
```javascript
import { Component } from '@angular/core';

@Component({
  selector: 'my-app',
  template: `
    <input type="button" (click)="back=!back;fore=!fore" value="Background"/>
    <div [ngStyle]="styles">
    {{msg}}
    </div>`
})

export class AppComponent {
  msg: string = `Hello World!`;
  back = false;
  fore = false;
  get styles(){
    return {
      'background-color': this.back ? '#12346b': '',
      'color': this.fore ? '#fff': '',
      fontWeight: 'bold',
      margin: '15px',
      padding: '15px'
    };
  };
}
```
ボタン押す前：
# TODO: add pictures

# 5. フォーム開発
> フロントエンド開発において，フォームはエンドユーザからの入力を受け取る代表的な手段です。Angularはユーザからの入力を受けて，処理を開始し，その結果をテンプレートに反映する。

## 5.1 フォーム開発の基本
- Angularでは，`<form>/<input>`要素が拡張されており，リッチなフォームを簡単なコードで実装できる。
- 入力内容の検証などもできる
- 

# 6. コンポーネント開発
Angularは，コンポーネント指向のフレームワークである。コンポーネントは以下の役割を受け持つ：
- ビューを整形する
- バックエンドにビューの情報を引き渡す
- バックエンドの情報をビューに引き渡す
- 本章では，複数のコンポーネントを連携させる方法を学ぶ

[参考：BFF（Backends For Frontends）超入門](https://www.atmarkit.co.jp/ait/articles/1803/12/news012.html)
>マイクロサービス/API時代のフロントエンド開発に求められる技術の1つBackends For Frontends（BFF）について解説する連載。初回は「超入門」としてBFFの概要や事例を中心に紹介する。

## 階層的なコンポーネント
- 基盤となる`AppComponent`の中で，子`ChildComponent`を呼び出すような入れ子構造を作れる。
- 複数コンポーネントが相互にコミュニケーションする場合がある。そうしたとき，子コンポーネントは，親コンポーネントへの入出力時に，`@Input`，`@Output`アノテーションを用いることができる。
- **テンプレート参照変数**を用いる方法でも子コンポーネントを参照できる。

## コンポーネントのライフサイクル
大まかな流れ：
>コンポーネントは，まず最初に生成された後，プロパティ・子コンポーネントの経k名を受けて状態（表示）を変化させていき，非表示になるタイミングで破棄される。

- Angularには，ライフサイクルの変化を受けて呼び出される様々なメソッドがあり，**ライフサイクルメソッド**と呼ばれる。
- `ngOnInit()`，`ngOnDestroyed()` －ページの初期化，終了処理－などが内部的に行われて，画面の生成などが管理される。でも，これらを明示的に呼び出すこともできる。
- 明示的に呼び出すことのメリットは，ライフサイクルの切り替わり時に，特定の処理を呼び出せるようになること。

### `ngOnChanges()`
プロパティが変化したときに呼び出される。

```typescript:明示的に実装した例
ngOnChanges(changes: SimpleChanges) {
  console.log('［child］ngOnChanges');
  for (let prop in changes) {
    let change = changes[prop];
    console.log(`${prop}：${change.previousValue} => ${change.currentValue}`);   
  }
}
```
- `SimpleChanges`
	- 「`プロパティ名：変更情報`」のハッシュ。
	- `.previousValue`, `.currentValue`などのメンバーを持っている。

### `ngAfterViewInit(), ngAfterViewChecked()`
ビューの初期化・変更時の処理を実装する。
- `ngAfterViewInit()`：ビューが初期化されるときにのみ呼び出される
- `ngAfterViewChecked()`：ビューが変更されるときに呼び出される
- `<ng-content></ng-content>`：呼び出し元のコンポーネントから，子コンポーネントへの埋め込みを行うときに使う。細かい使い方は`p.200`参照。
- `@ViewChild()`：現在のビューに配置された子コンポーネントを参照するためのデコレータ。子コンポーネントが複数ある場合は`@ViewChildren()`を使う。

### `ngAfterContentInit(), ngAfterContentChecked()`
外部コンテンツの初期化・変更時の処理を実装する。
- `ngAfterContentInit()`：ビューが初期化されるときにのみ呼び出される
- `ngAfterContentChecked()`：ビューが変更されるときに呼び出される
- `@ViewContent()`：外部コンテンツで定義された子コンポーネントを参照するためのデコレータ。

## 6.3 コンポーネントのスタイル定義
- `@Component`デコレータのstyle・styleUrlsパラメータを指定することで，コンポーネントのスタイルを変えられる。
- コンポーネントの中で定義されたスタイルは，閉じており，他のところで定義されたものと衝突しない。
- つまり，`app.component.ts`のテンプレート内で定義された`<p>`には反映されても，`index.html`で定義された`<p>`にはスタイルは反映されない。
- スタイル定義は`app.component.css`として外部化することができ，`styleUrls`パラメータで指定することもできる。

**スタイル指定のベストプラクティス**:
望ましい順に，
- `template`の`style`・`styleUrls`パラメータで指定する
- `@import`ディレクティブを用いる。
```javascript
@import 'app.component.ext.css';
```


# Snipets

## Modal表示に関する諸々

```html
<div class="modal-header">
	<h4 class="modal-title">{{'E.APIKEY.WORK.CONFIRM_MODAL.TITLE' | translate}}</h4>
</div>
<div class="modal-body">
	<p>{{'E.APIKEY.WORK.CONFIRM_MODAL.MODAL_MSG' | translate}}</p>
</div>
<div class="modal-footer">
	<button type="button" class="btn btn-outline-secondary" (click)="activeModal.close(false)">
	{{'E.APIKEY.WORK.CONFIRM_MODAL.MODAL_NG_BTN' | translate}}</button>
	<button type="button" class="btn btn-danger" (click)="activeModal.close(true)">
	{{'E.APIKEY.WORK.CONFIRM_MODAL.MODAL_OK_BTN' | translate}}</button>
</div>
```
- `<p>`：１つの段落であることを示すタグ，いい感じの改行がなされる。
- `<div>`：<DIV>タグはそれ自身は特に意味を持っていないが、<DIV>～</DIV>で囲んだ範囲をひとかたまりとして、 align属性で位置を指定したり、スタイルシートを適用するのに用いる。
- `<span>`：単体では特に意味を持たないタグだが、<span>～</span>で囲った部分をインライン要素としてグループ化することができる。