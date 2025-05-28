# 第１章
## Flutterとは？
Flutterは、マルチプラットフォームのための開発環境です。  
あらゆるプラットフォームを１つのコードだけですべて作れるようにするそれがFlutterが目指すところ。

### 専用 SDK による開発
Flutterは、AndroidやiOSのプラットフォーム上にFlutter独自のフレームワークを用意し、  
これを利用してアプリを作成することができる。  
プラットフォームによってUIなどは微妙に違いがある。  
|||
|---|---|
|**Android**|「**マテリアルデザイン**」をベースにUIを設計が採用されている。|
|**iOS**|ルック＆フィールを持たせた「**クパティーノ**」というUIフレームワークが採用されている。|
これらを利用すれば**iPhone**らしい見た目にすることができる。

### 開発言語はDart言語
Flutterの開発には、「**Dart**」というプログラミング言語を利用する。  
JavaScriptに非常に近い言語だからJavaScriptの経験があれば比較的簡単に使えるようになる。

### ネイティブコード
Dartは、JavaScriptに近い言語だけどアプリがそのまま動くわけではない。  
Flutterはそれぞれのプラットフォームごとにプログラムをネイティブコードにコンパイルする。  

ネイティブコードとは？  
- CPUが直接理解して実行できる機械語（バイナリ）のこと
- **コンパイル言語（C、C++など）**で書いたプログラムを、コンパイラがネイティブコードに変換する
- 超高速で動作するけど、OSやCPUに依存する（＝他の環境では動かない）
- JavaやPythonのような中間コード（バイトコード）やスクリプトとは違い、直接ハードウェアを叩けるコード

### Flutter開発に必要なもの
|||
|---|---|
|**JDK**|AndroidのSDKや開発ツールのAndroid Studioを利用する上で必要となる|
|**Dart**|flutterで使うプログラミング言語|
|**Flutter SDK**|Flutterの本体部分|
|**Intellij(Android Studio)/VScode**|開発ツール、これがなくてもいいがあった方が遥かにに効率的になる|
|**Visual Studio**|Windows用のアプリ開発を行う場合、C++環境開発が必要になるし、しかもネイティブコードにビルドができない|
|**XCode**|macOS用のiOS向けのアプリ開発を行う場合、XCodeがないとビルドができない|

これらの中で特に必要なのがFlutter SDK、これがないと始まらない。
### JDKを用意する
Androidの開発をするには**JDK**が必須。  

**JDK**をダウンロードするためのアドレスがこれ　**→**
https://www.oracle.com/java/technologies/downloads/

続いて**Flutter SDK**をダウンロードするためのアドレスがこちら　**→**
https://docs.flutter.dev/set-started/install

続いては、**Android Studio**をダウンロードするためのアドレスがこちら　**→**
https://developer.android.com/studio/?hl=ja

### プロジェクト実行


# 第２章
## ウィジェットの基本レイアウト

"https://flutterstudio.app/"　←　Flutter Studioの画面を表示し、レイアウトを作成できる

### レイアウトのソースコード
レイアウトのソースコードをコピーしてVSCodeで作成していたプロジェクトのソースコードを差し替えて実行し、動かしてみるとちゃんとレイアウトされてるか正確に確認ができるようになる。

**注意!**
レイアウトのソースコードコピペしてもエラーが起こる場合があります！

#### 例
- **誤**  ```MyHomePage({Key key}) : super(key: key);```

- **正** ```MyHomePage({Key? key}) : super(key: key);```

この例の場合は**正**のように```Key```の後に```?```をつければ直る！

### テキストスタイルについて
Textウィジェットを作成する際に、**Style**という値を使って設定している。  
値は**TextStyle**というクラスとして用意されている

インスタンスを作成する際に必要なスタイル情報を引数として用意する。  
主なものとして以下のようなものがある。  

|引数|説明|
|---|---|
| **fontSize** | フォントサイズ。double値で指定 |
| **fontWeight** | フォントの太さ。 FontWeightというクラスのW100 ~ W900、あるいはboldという定数で指定 |
|**fontFamily**|フォントファミリー。テキスト（String）で指定|
|**fontStyle**|フォントスタイル。FontStyle列拳型のnormal、italicという値で指定|
|**color**|テキスト色。Colorクラスで指定|

#### **例**
```
style: TextStyle(fontSize:32.0,
color: const Color(0xff000000),
fontWeight: fontWeight.w700,
fontFamily: "Roboto"),
```

### Colorについて
```color: const Color(0x000000),```  
引数には６または８桁の１６進数で指定する。  これにより**RGB**または**ARGB**の値を指定できる。

この他にも**ARBG**の値を個別で引数で指定してインスタンスを作成するメソッドも用意されている。  
```Color.fromARGB(アルファ, 赤, 緑, 青 )```  
引数には、**ARGB**の各地を０～２５５の整数で指定する。

# 第３章
## ボタン・ウィジェット
### TextButtonについて
「**TextButton**」というクラスとして用意されています。Flutter Studioでは「**Material**」ジャンルの中にある。
>ちなみに「Flutter Studio」では、**TextButton**のことを**FlatButton**とも呼ぶらしぃ。

「FlatButton」というアイコンがTextButtonに相当する。これをプレビューにドラック＆ドロップするとフラットボタンが配置できる。  
TextButtonのプロパティとしては「**Size**」、「**Weight**」があり、これはTextButtonの言葉のテキストフォントのサイズと太さを指定するプロパティがある。

### TextButtonの基本形

```
TextButton(key:null,
    onPressed: 関数,
    child: ウィジェット
)
```
**onPressed**は、このTextButtonをクリックした時に実行される処理を指定するための値。  
今回の例では、**buttonPressed**と設定されているので、ボタンをクリックすると**buttonPressedメソッド**が呼び出されるようになる
### アイコンを表示する
TextButtonにテキストが表示されているのは内部にテキストが読み込まれているから、なのでTextの代わりに別のウィジェットを組み込めば、表示が変えられる。




