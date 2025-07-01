# 第１章
## Flutterとは？
Flutterは、マルチプラットフォームのための開発環境です。  
あらゆるプラットフォームを１つのコードだけですべて作れるようにするそれがFlutterが目指すところ。

### Flutterのメリット・デメリット
|メリット||
|---|---|
|マルチプラットフォーム対応|Android、iOS、Web、Windows、macOS、Linuxまで1つのコードで動く|
|高速な開発（Hot Reload）|画面の変更が即反映される|
|洗練されたUIデザイン|Material DesignもCupertinoも対応だから、Google風にもApple風にもできる|
|パフォーマンスが高い|ネイティブ並みに動作が軽快。Dartで直接コンパイルするから高速|

|デメリット||
|---|---|
|アプリサイズが大きめ|Webやデスクトップ向けに出すとファイルが大きくなりがち|
| ネイティブ機能へのアクセスがやや面倒|カメラやBluetoothなど、細かいデバイス機能はプラグインやネイティブコードが必要。|
|Webサポートはまだ発展途上|対応はしてるけど、パフォーマンスや動作の安定性はまだまだこれから。|
|Dart言語の習得が必要|ちょっとマイナーな言語だから、慣れるまで戸惑う|

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

# 第２章
## ウィジェットの基本レイアウト

"https://flutterstudio.app/"　←　Flutter Studioの画面を表示し、レイアウトを作成できる

こんな感じの画面です。
![Flutter Studio](../../png/Flutter_Studio.png)

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
|||
|---|---|
|0x|進数|
|ff・00など|明度 , ff = 100% ・ 00 = 0%|
|00ffff・9acd32など|RGB・カラーコード|

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

### TextButtonの利用
FlatButtonを使った例です。 **↓**
```
class _MyHomePageState extends State<MyHomePage> {
  static var _message = 'ok.';
  static var _janken = <String>['グー', 'チョキ', 'パー'];

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('App Name'),
      ),
      body: Center(
        child: Column(
          mainAxisAlignment: MainAxisAlignment.start,
          mainAxisSize: MainAxisSize.max,
          crossAxisAlignment: CrossAxisAlignment.stretch,
          children: <Widget>[
            Padding(
              padding: EdgeInsets.all(20.0),
              child: Text(
                _message,
                style: TextStyle(
                  fontSize: 32.0,
                  fontWeight: FontWeight.w400,
                  fontFamily: "Roboto"),
              ),
            ),
            TextButton(
              onPressed: buttonPressed,
              child: Padding(
                padding: EdgeInsets.all(10.0),
                child: Text(
                  "Push me!",
                  style: TextStyle(
                    fontSize: 32.0,
                    color: const Color(0xff000000),
                    fontWeight: FontWeight.w400,
                    fontFamily: "Roboto"),
                )
              )
            )
          ]
        ),
      ),
    );
  }

  void buttonPressed() {
    setState(() {
      _message = (_janken..shuffle()).first;
    });
  }
}

```


このコードはボタンを押すとランダムにじゃんけんの手が出てきます。  
ここでは_messageに_janken...shuffle()シャッフルしたListの最初の項目を取り出している。shuffleに、Listの項目をランダムに入れ替えるものですが、voidなので値は返しません。そこで **カスケード記法(..演算子)** をつかい、元のオブジェクトからfirstで最初の要素を取り出す。
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
表示方法は以下の通り
```
TextButton(
    onPressed:buttonPressed,
    child: Padding(
        padding: EdgeInsets.all(10.0),
        child:Icon (
            Icons.android,
            size: 50.0,
        )
    )
)
```

これを実行すると、テキストではなく、Androidのアイコンが表示される。

### buttonPressedメソッドについて
クリックした時の処理については、「onPressed:buttonPressed」とメソッドを設定している。このメソッドは、以下のように定義している。

```
void buttonPressed(){
    setState((){
        _message = (_janken..shuffle()).first;
    });
}
```
引数無し、戻り値なしのシンプルなメソッドです。

### Paddingについて
先ほどのソースコードにTextButtonのほかにも新しいクラスが使わています。それは「Padding」というものです。
```
children: <Widget>[
            Padding(
              padding: EdgeInsets.all(20.0),
              child: Text(
                _message,
                style: TextStyle(
                  fontSize: 32.0,
                  fontWeight: FontWeight.w400,
                  fontFamily: "Roboto"),
              ),
            ),
            TextButton(
              onPressed: buttonPressed,
              child: Padding(
                padding: EdgeInsets.all(10.0),
                child: Text()
```

### ElvatedButtonについて
TextButtonと同じような働きをするものに「**ElevatedButton**」というものもあります。
同じボタンだけどこっちのボタンは立体的に表示される。
Flutter Studioでは、「Material」の中の「RaisedButton」としてアイコンが用意されている～～♪

### ElevatedButtonの利用
利用した例
```
ElevatedButton(
    onPressed:buttonPressed,
    child: Padding(
        padding: EdgeInsets.all(10.0),
        child:Icon (
            Icons.android,
            size: 50.0,
        )
    )
)
```
# 第４章

## AppBerについて
ここまでのアプリの基本画面は、Scaffoldをベースにして来ました。  
Scaffoldはアプリの画面を構成する基本的な要素を一通り備えています。  
ここまでのサンプルは**appBer**に***アプリケーションバー***、**body**に***アプリのコンテンツ*** を設定してきた。

### AppBerの基本形
AppBerではtitleにTextを用意することでタイトルの表示が行えます。  
AppBerが用意されているプロパティは他にもあり、それらを含めたインスタンス作成の基本形をまとめたものがこちらになります♪
```
Appber(
  title: ウィジェット,
  leading: ウィジェット,
  actions: <Widget>[ ウィジェットのリスト ]
  bottom:　《PreferredSize》,
)
```
|||
|--|--|
|title|タイトル表示部分。通常はTextを用意|
|leading|左端に表示される。通常はボタンかアイコンを表示|
|actions|タイトルの右側に表示される。ボタン・アイコン・などのリストを用意。|
|bottom|上記の下に追加表示される部分。PreferredSizeインスタンスを用意。|

bottomは特別な用途などがない限りあまり使わない。  
bottomを使うには**PreferredSize**というクラスを使います。これはデバイスの画面サイズなどに応じた最適なサイズを調整が出来る。

### AppBerをカスタマイズする
前章から利用しているサンプルを使い、_MyHomePageStateクラスを以下のリストのように書き換えてください。
```
class _MyHomePageState extends State<MyHomePage> {
  static var _message = 'ok';
  static var _stars = '☆☆☆☆☆';
  static var _star = 0;

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('My App'),
        leading: BackButton(
          color: Colors.white,
        ),

        actions: <Widget>[
          IconButton(
            icon: Icon(Icons.android),
            tooltip: 'add star...',
            onPressed: iconPressedA,
          ),
          IconButton(
            icon: Icon(Icons.favorite),
            tooltip: 'subtract star...',
            onPressed: iconPressedB,
          ),
        ],

        bottom: PreferredSize(
          preferredSize: const Size.fromHeight(30.0),
          child: Center(
            child: Text(_stars,
              style: TextStyle(
                fontSize: 22.0,
                color:Colors.white,
              ),
            ),
          ),
        ),
      ),

      body: Center(
          child: Text(
            _message,
            style: const TextStyle(
              fontSize: 28.0,
            ),
          )
      ),
    );
  }

  void iconPressedA() {
    _message = 'tap "android".';
    _star++;
    update();
  }
  void iconPressedB() {
    _message = 'tap "favorite".';
    _star--;
    update();
  }

  void update() {
    _star = _star < 0 ? 0 : _star > 5 ? 5 : _star;
    setState(() {
      _stars = '★★★★★☆☆☆☆☆'.substring(5 - _star, 5 - _star + 5) ;
      _message = _message + '[$_star]';
    });
  }
}
```
### BackButtonについて
leadingは以下のようにウィジェットが設定されている。
```
leading: BackButton(
  color: Colors.white,
)
```
ここで使っている「**BackButton**」というのは「前に戻る」ための専用ボタンです。  
BackButtonは、colorでアイコンの色を指定するだけで、他には特にプロパティはありません。

### actionsのアイコンについて
**actions**はウィジェットのリストを用意します。
```
actions: <Widget>[
  IconButton(
    icon: Icon(Icons.android),
    tooltip: 'add ster...',
    onPressed: iconPressedA,
  ),
  -----略-----
],
```
### bottom の表示
**bottom**は、★マークのテキストを表示させている。作る場合は以下のように

```
bottom: PreferredSize(
  preferredSize: const Size.fromHeight(30.0),
  child: Canter(
    child: Text(_stars,
      style: TextStyle(
        fontSize: 22.0,
        color:Colors.white,
      ),
    ),
  ),
),
```

**PreferredSize**はサイズを示すpreferredSizeと、中に組み込むchildを用意します。  
preferredSizeにはSizeクラスの「fromHeight」というものを使い高さ30の大きさに設定してる  
chileにはTextを用意しています。

### BottomNavigationBarについて
Scaffoldでは、AppBerのように画面の上部だけではなく、下部にもバーを表示することができる。  
これを実現するのが「**BottomNavigationBar**」です。  
**BottomNavigationBar**というウィジェットを組み込むことで、アイコンを表示し、クリックして操作ができるようになる。

### BottomNavigationBarの利用
例として「_MyHomePageState」というクラスにして以下のように書いてください。

```
class _MyHomePageState extends State<MyHomePage> {
  static var _message = 'ok';
  static var _index = 0;

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('My App'),
      ),
      body: Center(
        child: Text(
          _message,
          style: const TextStyle(
            fontSize: 28.0,
          ),
        )
      ),
      bottomNavigationBar: BottomNavigationBar(
        currentIndex: _index,
        backgroundColor: Colors.lightBlueAccent,
        items: <BottomNavigationBarItem>[
          BottomNavigationBarItem(
            label: 'Android',
            icon: Icon(Icons.android,color: Colors.black, size: 50),
          ),
          BottomNavigationBarItem(
            label: 'Favorite',
            icon: Icon(Icons.favorite,color: Colors.red, size: 50),
          ),
          BottomNavigationBarItem(
            label: 'Home',
            icon: Icon(Icons.home,color: Colors.white, size: 50),
          ),
        ],
        onTap: tapBottomIcon,
      ),
    );
  }

  void tapBottomIcon(int value) {
    var items = ['Android', 'Heart', 'Home'];
    setState(() {
      _index = value;
      _message = 'you tapped: "' + items[_index] + '".';
    });
  }
}

```
実行すると、下部に3つのアイコンを表示したバーが表示されます。  
アイコンをクリックするとそのアイコンが選択され、「you tapped: "〇〇"」とメッセージが表示されます。

### BottomNavigationBarの仕組み
このBottomNavigationBarはAppBerのように、ただアイコンやボタンを追加してイベント処理を書けばいいというわけではありません。  
BottomNavigationBarインスタンスの作成をどのように行っているのか整理すると以下のようになります。

```
BototomNavigationBer(
  currentIndex: 《int値》,
  items: <BottomNavigationBerItem>[ リスト ],
  onTap: 関数
)
```
|||
|---|---|
|**currentIndex**|現在、選択されている項目のインデックス。これの設定されたインデックスのアイコン（BottomNavigationBarItem）が選択状態で表示される。|
|**items**|表示する項目。BottomNavigationBarItemインスタンスのリストとして用意|
|**onTap**|バーに表示されているアイコンをクリックしたときに呼び出される処理|

# 第6章
## ファイルアクセス
### Fileクラスとファイナルアクセス
Dart言語には、アプリに必要な情報をテキストファイルに保存したり読み込んだりする機能が用意されている。  
これを利用すれば、そう難しくなくファイルアクセス処理を実装できます。  
(**※ファイルアクセスを行うFileクラスは、Webアプリでは正常に動作できません。
これを利用したサンプルは、スマートフォンかPC用のアプリで動作確認をしてください**)  

#### Fileクラスについて
ファイルを扱うためには、「**File**」というクラスを利用します。以下のようにしてインスタンスを作成します。
```
File( ファイルパス )
```
このFileには、ファイルへの読み書きを行うためのメソッドです。

#### ファイルへの書きだし
ファイルへの値の書き出しは、Fileクラスの「**WriteAsString**」というメソッドを利用します。以下のように行う

```
Future<File> writeAsString( [String] );
```
引数には、保存するテキストの値を指定します。  
これだけで、指定のテキストファイルにテキストを書きだします。  
このメソッドは非同期で実行されるため、戻り値には保存されたFileが**Future**<**File**>という形で返されます。  
同期処理した場合は以下のようなメソッドもあります。
```
void writeAsStringSync( [String] );
```
こちらはvoidなので戻り値はありません。  
ただ実行するだけでファイルにテキストが保存されます。
#### ファイルからの読み込み
ファイルからの読み込みには、Fileクラスの「**readAsString**」というメソッドを使います。
```
try {
  変数 = await [File].readAsString();
} catch (e) {}
```
このreadAsStringメソッドは、例外を発生させるため、try内で実行するのが基本です。  
戻り値はファイルから読み込んだテキストの値(String)になります。  
これも非同期メソッドです。そして戻り値からthenでテキストを取り出します。
```
[Future<File>].then((String value){.....valueを利用する処理.....});
```
thenの関数の引数に、取り出されたテキストが渡されるので、あとはそれを利用して処理をすればいいでしょう。  

これも、同期で読み込みを行うメソッドが用意されています。
```
try {
  変数 = [File].readAsStringSync();
} catch (e) {}
```
こちらは、戻り値として読み込んだテキストが返されるので、これをそのまま利用すればいいです。

### Path Providerのインストール
実際にファイルアクセスを行うには、実はパッケージを1つ追加する必要があります。  
「**Path Provider**」というもんで、これはプロジェクトのpubspec.yamlファイルに設定を記述します。  
このファイル内に、dependenciec:という記述があります。その後に、インデントをしてPath Providerを記述します。  
```
dependencies:
  flutter:
    sdk: flutter
  path_provider: any
```
これで、ビルド時にPath Providerが追加され利用できるようになります。  
このPath Providerは、アプリのファイルを保存する場所を調べる機能を追加します。  
ちなみにパソコンは問題ないんだけどスマホの場合は適当な場所にファイルを保存しようとしても失敗します。  
### ファイルアクセスの例
```
import 'package:flutter/material.dart';
import 'dart:ui' as ui;
import 'dart:io';
import 'package:path_provider/path_provider.dart';

void main()=> runApp(MyApp());

class MyApp extends StatelessWidget {

  @override
  Widget build(BuildContext context) {
    return MaterialApp(
      title: 'Generated App',
      theme: ThemeData(
        primarySwatch: Colors.blue,
        primaryColor: const Color(0xff2196f3),
        canvasColor: const Color(0xfffafafa),
      ),
      home: MyHomePage(),
    );
  }
}

class MyHomePage extends StatefulWidget {
  const MyHomePage({Key? key}) : super(key: key);

  @override
  _MyHomePageState createState() => _MyHomePageState();
}

class _MyHomePageState extends State<MyHomePage> {
  final _controller = TextEditingController();
  final _fname = 'flutter_sampledata.txt';

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text('Home'),
      ),
      body: Padding(
        padding: EdgeInsets.all(20.0),
        child:Column(
          children:<Widget>[
            Text('FILE ACCESS.',
              style: TextStyle(fontSize: 32,
                fontWeight: ui.FontWeight.w500),
            ),
            Padding(padding: EdgeInsets.all(10.0)),
            TextField(
              controller: _controller,
              style: TextStyle(fontSize: 24),
              minLines: 1,
              maxLines: 5,
            )
          ],
        ),
      ),
      bottomNavigationBar: BottomNavigationBar(
        backgroundColor: Colors.blue,
        selectedItemColor: Colors.white,
        unselectedItemColor: Colors.white,
        currentIndex: 0,
        items: <BottomNavigationBarItem>[
          BottomNavigationBarItem(
            label: 'Save',
            icon: Icon(Icons.save, color: Colors.white, size:32),
          ),
          BottomNavigationBarItem(
            label: 'Load',
            icon: Icon(Icons.open_in_new, color: Colors.white, size:32),
          ),
        ],
        onTap: (int value) async {
          switch (value) {
            case 0:
              saveIt(_controller.text);
              setState(() {
                _controller.text = '';
              });
              showDialog(
                context: context,
                builder: (BuildContext context) => AlertDialog(
                  title: Text("saved!"),
                  content: Text("save message to file."),
                )
              );
              break;
            case 1:
            String value =  await loadIt();
            setState(() {
              _controller.text = value;
            });
            showDialog(
              context: context,
              builder: (BuildContext context) => AlertDialog(
                title: Text("loaded!"),
                content: Text("load message from file."),
              )
            );
            break;
            default:
              print('no defalut.');
          }
        },
      ),
    );
  }

  Future<File> getDataFile(String filename) async {
    final directory = await getApplicationDocumentsDirectory();
    return File(directory.path + '/' + filename);
  }

  void saveIt(String value) async {
    final file = await getDataFile(_fname);
    file.writeAsString(value);
  }

  Future<String> loadIt() async {
    try {
      final file = await getDataFile(_fname);
      return file.readAsString();
    } catch (e) {
      return '*** no data ***';
    }
  }
}

```
### ファイルアクセスの流れを整理する
３つのファイル関連のメソッドを追加し、それらを呼びだして読み書きを行っています。
#### getDataFile メソッドについて
これらはファイルアクセスの前に必要となる「**File**」インスタンスを得るための処理を行っている。
```
Future<File> getDataFile(Storing filename) async {
  file directory = await getApplicationDocumentsDirectory();
  return File(directory.path + '/' + filename);
}
```
見て分かるように、これは非同期メソッドとして定義してあります。  
内部で利用しているのが非同期関数であるため、このメソッド自体も非同期になっています。  
#### 割り当てられたフォルダパスの取得
```
file directory = await getApplicationDocumentsDirectory();
```
まず最初が**getApplicationDocumentsDirectory**という関数の呼び出しです。  
これが、Path Providerにより使えるようになった機能です。  
これは、アプリに割り当てられているドキュメントフォルダを調べて返すものです。  
戻り値は**Future<**Directory**>**、すなわち**Directory**というクラスのインスタンスを戻り値として返すFutureになっています。

#### ファイルパスの取得
```
return File(directory.path + '/' + filename);
```
Directoryでは、**path**プロパティでパスをStringとして取り出すことができる。  
その後にfilenameをファイル名として追加し、Fileでインスタンスを作成します。  
このFileをreturnし、そこから必要な処理を行います。

#### savelt メソッドについて