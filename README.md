# URLについて
## URLとは
URLはWEBサイトの場所を示す際に用いられる文字列のこと。

## URLの構文
![image](https://github.com/Mie-ee/github-handson/assets/146546228/bfb39a36-94f2-4051-945b-91d4ac914eb4)
1. スキーム名
> https:

  プロトコルを指定します。 
  
2. ホスト名（ドメイン名）
> raise-tech.net
   
   接続先のサーバーをしてします
   IPアドレスで指定することも可能です。  

3. ポート番号  
   省略可能で、通常は指定しません。
   指定しない場合、プロトコルが *https* の場合は *443* が適用されます。  

4. パス名
> courses-lp/java-full-course
   
   接続先のサーバー上のディレクトリやファイルを指定します。

## URLパラメータとは
サーバーに情報を送るためにURLに付け加える変数のことを指します。  
パラメータには __アクティブパラメータ__ と __パッシブパラメータ__ の2種類があります。

### クエリパラメータとは
特定のリソース操作して取得する際に必要な情報。  
サーバーへ送りたいデータを指定するためにURLの最後に追加する文字列です。    
別名として、次のような呼び方をされるケースも少なくありません。  
- URLパラメータ
- クエリ文字列
- クエリストリング  

## パス変数とは
特定のリソースを識別するために必要な情報。  
URLのパス（URI）内に含まれ、通常、パスの一部として表現されます。  

## クリエ文字列とパス変数と違い
要するに、クエリ文字列とパス変数はリクエストに情報を渡すための異なる手段です。  
クエリ文字列はリクエストパラメータを指定するために使用され、パス変数はリソースの識別や操作を指定するために使用されます。  
選択肢は特定の使用ケースや設計に依存し、どちらを使用するかはコンテキストによります。  
例:

> `https://example.com/user?name=John&age=3`

URIでドメインの後、？の前に来るものがパスパラメータです。  
そして、?の後に来るのがクエリパラメータです。  



# HTTPについて
HTTP は、 HTML 文書などのリソースを読み取るためのプロトコルです。  
これはウェブにおけるデータ交換の基礎をなし、クライアントサーバープロトコルであり、リクエストは受け取り者（一般にはウェブブラウザー）が生成します。   
文書全体は、テキスト、レイアウトの定義、画像、動画、スクリプトなど、取り込まれたさまざまなサブ文書から再構成されます。  
![image](https://github.com/Mie-ee/github-handson/assets/146546228/4af27a24-0df9-4865-9f16-c8850d81df8c)

## HTTPメッセージ 
HTTP メッセージは、サーバーとクライアントがデータを交換する手段です。  
クライアントが送信してサーバーにアクションを起こさせる __リクエスト__ と、サーバーの回答である __レスポンス__ の、2 種類のメッセージがあります。  

### HTTPリクエスト
HTTP リクエストは、アクションを始めるためにクラアントからサーバーへ送られます。その開始行には、3 つの要素が含まれています。  
1. HTTP メソッド
   実行するアクションを表わす動詞 (GET、PUT、POST など) または名詞 (HEAD、OPTIONS)。  
   例えば GET はリソースを取り込むこと、POST はデータをサーバーへ送信すること (リソースを作成または変更する、あるいは返送する一時的なドキュメントを生成する) ことを示します。  
2. リクエスト対象  
   通常は URL ですが、プロトコル、ポート番号、ドメインの絶対パスは通常、リクエストの状況から明らかにされます。  
   リクエスト対象の形式は、HTTP メソッドにより異なります。  
3. HTTP バージョン
   これはメッセージの残りの部分の構造を定義しており、レスポンスで使用することを想定しているバージョンを示す役割もあります。  

### HTTPメソッド
HTTP では多様な操作を実現することができます。  
一般的な GET や POST だけでなく、OPTIONS や DELETE、TRACE などのあまり一般的ではないリクエストも包括しています。  
| メソッド名 | 説明 |
----|---- 
|  GET | 指定したリソースの表現をリクエストします。 GET を使用するリクエストは、データの取り込みに限ります。 |
| POST | 指定したリソースに実体を送信するために使用するメソッドであり、サーバー上の状態を変更したり、副作用が発生したりすることがよくあります。 |
| PUT | 対象リソースの現在の表現全体を、リクエストのペイロードで置き換えます。 |
| PATCH | リソースを部分的に変更するために使用します。 |
| DELETE | 指定したリソースを削除します。 |

### HTTPレスポンス
 __ステータス行__   
HTTP レスポンスの開始行はステータス行と呼ばれ、以下の情報を持ちます。  
1. プロトコルバージョン
   通常 HTTP/1.1 です。
2. ステータスコード
   リクエストが成功したか失敗したかを示します。一般的なステータスコードは 200, 404, 302 です。
3. ステータステキスト
   手短な単なる情報ですが、人間が HTTP メッセージを理解するのを助けるために、ステータスコードをテキストで説明します。  

一般的に、ステータス行は HTTP/1.1 404 Not Found. のようになります。  

 __レスポンスヘッダー__   
[HTTPヘッダー](#HTTPヘッダー)参照  

 __レスポンスボディ__ 
レスポンスの最後の部分が本体です。  
本体を持たないレスポンスもあります。   
本体は、大きく 3 種類に分類されます。  
- 大きさが判明している 1 個のファイルで構成される、単一リソースの本体
  Content-Type と Content-Length の 2 つのヘッダーで定義されます。
- 大きさが不明な 1 個のファイルで構成される、単一リソースの本体
  Transfer-Encoding を chunked に設定して、 chunked 形式でエンコードされます。
- 複数リソースの本体
  マルチパートの本体で構成され、それぞれが異なる情報のセクションを持ちます。これは比較的まれです。

### HTTPステータスコード
"HTTP レスポンスステータスコード"ともいいます。    
特定の HTTP リクエストが正常に完了したどうかを示します。   
### ステータスコードの分類
- 100番台　Informational
  -  __100__  contuine リクエスト継続中を通知する。 
- 200番台 Success
  -  __200__  OK リクエストが正常に受理されたことを通知する。
- 300番台 Recdirection
  - __301__ Moved Parmanently　リクエストされたコンテンツが移動したことを通知する。
  - __302__ Found　リクエストされたコンテンツが一時的に移動（別の場所で発見）したことを通知する。
  - __304__ Not Modified  リクエストされたコンテンツが未更新であることを通知する。
- 400番台
  - __400__ Bad Request　リクエストが不正であることを通知する
  - __404__ Not Found　リクエストされたコンテンツが未検出であることを通知する。
- 500番台
  - __500__ Internal Server Error　リクエスト処理中にサーバー内部でエラーが発生したことを通知する。
  - __503__ Service Unavailable　アクセス集中やメンテナンスなどの理由で一時的に処理不可であることを通知する。 

## HTTPヘッダー
HTTP リクエストおよび HTTP レスポンスのフィールドで、メッセージや本文のセマンティクスを変更したり、より詳細に説明したりするための追加情報を渡します。  
ヘッダーは大文字と小文字を区別せず、行の先頭から始まり、直後に ':' とヘッダー自体に依存する値が続きます。  
値は、次の CRLF またはメッセージの最後で終了します。  
従来より、ヘッダーはカテゴリ分けされてきましたが、この分類は仕様書では定義されていません。  
- 一般ヘッダー
  リクエストとレスポンスの両方に適用され、最終的に本文の中で送信されるデータとは関係のないヘッダー。
- リクエストヘッダー
  HTTP リクエストで使用される HTTP ヘッダーであり、メッセージの内容には関連しないものです。
- レスポンスヘッダー
  レスポンスに関する追加情報、例えば場所や提供しているサーバーに関する情報を保持します。
- 表現ヘッダーは
  リソースの本体に関する情報、例えば MIME タイプや適用されるエンコード／圧縮方式などについての情報を持ちます。
- ペイロードヘッダー (en-US)
  転送されるデータの表現から独立した情報、例えばコンテンツの長さや転送に使われるエンコード方式などを持ちます。
  
# JSONとは 
JSONはJavaScript オブジェクトの構文に従ったテキストベースのデータ形式で、Douglas Crockford によって普及されました。  
JSONはJavaScript オブジェクトの構文に似ていますが、JavaScript とは独立して扱われることがあり、多くのプログラミング言語環境にはJSONを読み取ったり（解釈したり）生成したりする機能があります。  
JSON は文字列として存在します。  
ですので、ネットワークを通してデータを転送したい場合に便利です。   
JSON データへアクセスしたい場合は、JavaScript オブジェクトへ変換する必要があります。  
JavaScript にはこれらを相互に変換できるメソッドを持った JSON というグローバルなオブジェクトがあるので、変換は難しくありません。  

## JSONの構造
上で説明したように、JSON は JavaScript オブジェクトにとても似ている形式の文字列です。  
JSON では通常の JavaScript オブジェクトと同様な基本データ型（文字列、数値、配列、論理型やその他のリテラル型）を使うことができます。  
これにより、以下のように階層的にデータを構成することができます。  
```
{
  "squadName": "New student squad",
  "School": "Hogwarts",
  "formed": 1991,
  "active": true,
  "members": [
    {
      "name": "Deaco Lucius Malfoy",
      "house": "Slytherin",
      "bloodType": "Pure",
     },
    {
      "name": "Harry James Potter",
      "house": "Gryffindor",
      "bloodType": "Half"
    },
    {"name": "Hermione Jean Granger",
      "house": "Gryffindor",
      "bloodType": "Muggle"
     }
   }
 ]
}
```
 *[サイト](https://di-pri.github.io/Hacked-Hogwarts-Student-List) を参照しました。* 

 # 参考資料
 参考になる資料を載せておきます。
 
- MDN:　https://developer.mozilla.org/ja/docs/Web
- わわわ:　https://wa3.i-3-i.info/
- 書籍：Web技術の基本[Amazon](https://amzn.asia/d/6F2nbIO)


