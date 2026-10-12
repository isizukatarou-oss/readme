# webの仕組み

１．ユーザ（クライアント）はWebに対してHTTPリクエストを送る。

２．リクエストを受けたWebサーバはデータ（HTMLやJSON）を返す。

# HTTPリクエスト

具体的にWebブラウザから送っているHTTPリクエストは以下の3要素で構成されている。

	リクエストライン
	リクエストヘッダー
	リクエストボディー

### リクエストライン

　HTTPリクエストの中身であるリクエストラインは以下のようになっている。

	GET /index.html HTTP/1.1

　リクエストラインでは「何を、どうしたい」が書かれており、構成は以下のようになっている。

	メソッド
	リクエストURI
	HTTPバージョン

　メソッドは具体的にGET（データ取得）、POST（データ登録）、PUT（データ更新）、DELETE（データ削除）等がある。

### リクエストヘッダー

　リクエストヘッダーはリクエストについての情報や属性（メタデータ）について記載されている。

	Host: localhost:8080
	Connection: keep-alive
	User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_11_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/54.0.2840.98 Safari/537.36
	Accept: */*
	Referer: http://localhost:8080/
	Accept-Encoding: gzip, deflate, sdch, br
	Accept-Language: ja,en-US;q=0.8,en;q=0.6
	Cookie: user_id=12345678

### リクエストボディー

　HTTPリクエストを送ったときにレスポンスは以下の構成になっている。

# レスポンス

HTTPリクエストを送ったときにレスポンスは以下の構成になっている。

	ステータスライン
	レスポンスヘッダー
	レスポンスボディー

### ステータスライン

　ステータスラインの中身は以下のようになっている。

	HTTP/1.1 200 OK

　ステータスラインは以下の構成になっている。

	HTTPバージョン
	ステータスコード
	フレーズ

　ステータスコードをまとめると以下のようになっている。

	2xx:リクエストが成功した
	4xx:リクエストに誤りがある
	5xx:サーバ側のエラー

### レスポンスヘッダー

　レスポンスヘッダーはメタ情報が含まれている。

	alt-svc: quic=":443"; ma=2592000; v="44,43,39,35"
	cache-control: private, max-age=0
	content-encoding: br
	content-type: text/html; charset=UTF-8
	date: Thu, 23 Aug 2018 15:37:28 GMT
	expires: -1
	server: gws
	status: 200
	x-frame-options: SAMEORIGIN
	x-xss-protection: 1; mode=block

### レスポンスボディー

　具体的なサーバ側からの応答データが返却される。

# RESTについて

RESTとは以下のように説明されている。

	RESTとは、分散システムにおいて複数のソフトウェアを連携させるのに適した設計原則の一つ。
	2000年にロイ・フィールディング氏が提唱した。
	狭義には、それをWebシステムに適用したソフトウェアの設計様式を差し、一般にはこの意味で用いられることがほとんとである。

　⇒簡単にいうと、RESTとは「設計ルール」を意味している。

### RESTful

　RESTfulとはRESTで求められいてる原則に従っていることを指す。

　RESTful APIは、RESTの原則に基づいて設計されているAPIのことを表す。

### RESTの原則

	クライアント・サーバ制約
	ステートレス
	キャッシュ（クライアントサイド）
	統一インターフェース
	レイヤーシステム
	コードオンデマンド

### クライアント・サーバ制約

　クライアントとサーバは依存することなく独立し、お互い影響なく改良できるような構造にすべきという考え方。

　つまり、クライアント（画面UI）とサーバ（データ）で関心を分離する。

### ステートレス

　前の状態は保持せず、それぞれのリクエストが独立して成立していることを意味する。

　つまり、

	サーバに保持されチエルコンテキスト情報は使わない（サーバセッションは使わない）
	状態はクライアント上に保存される（リクエストにすべて含める）

### キャッシュ（クライアントサイド）

　クライアントはレスポンスをキャッシュすることができる。

　適切なキャッシュを行うことで、クライアントとサーバ間の通信を減らしユーザ体験の工場および、リソースの向上を見込むことができる。

### 統一インターフェース

　同じリソースに対するAPIアクセスは、すべて同じ形式で統一する（一意なURIでアクセス可能）。

　また、HTTPプロトコルのメソッド（GET,POST,PUT,DELETE等）でのみ、データ操作を可能にする。

　URIへの操作（GETやPOST）を統一することで、全体構成をシンプルにすることができる。

### レイヤーシステム

　複数の役割を持つサーバを組み合わせることでAPIを実現するアーキテクチャーのことをいう。

　具体的には、リクエストを受けるレイヤー、応答を返すレイヤー、セキュリティ処理を行うレイヤー等に分ける。

　レイヤーシステムは、各々の役割を独立させることで、再利用性をあげることができる。

### コードオンデマンド

　クライアントコードをダウンロードして実行することでができる。

　コードオンデマンドを組み込むことで、リリース済みのクライアントに対してサーバ主導で機能追加をすることができ、クライアント側に処理の実装を寄せるので、サーバへの負荷を下げることができる。

# Web API設計

### URI設計

	短くて入力がしやすい
	省略しない
	大文字と小文字が混ざっていない（基本は小文字）
	単語はハイフン繋ぎ
	単語は複数形を使う
	エンコードが必要な文字を使わない
	更新がしやすい
	ルールが統一されている

### 短くて入力がしやすい

　無駄な情報（重複情報）を省いて簡潔なURIにする。

　NG

	https://example.com/service/api/search

　OK

	https://example.com/search

### 省略しない

　NG

	https://example/com/ja/u

　OK

	https://example.com/users

### 大文字と小文字が混ざっていない（基本は小文字）

　NG

	https://example.com/Posts

　OK

	https://example.com/posts

### 単語はハイフン繋ぎ

　NG

	https://example.com/favorite_contents

　OK

	https://example.com/faborite/contents
	※そもそも単語を連結する必要がある場合はURI設計から見直す場合もある

### 単語は複数形を使う

　NG

	https://example.com/post/1

　OK

	https://example.com/posts/1

### エンコードが必要な文字は使わない

　エンコードがあると可読性が下がり、URIから処理が推測できない

　NG

	https://example.com/%TENFLOJFL$JSF3352nb%scd%

### 更新がしやすい

　NG

	https://example.com/alpha/contents/1
	https://example.com/beta/contents/1

　OK

	https://example.com/contents/1

### ルールが統一されている

　パラメタをパスパラメタで渡すのか、クエリパラメタで渡すかなどのルールを統一させる。

	https://example.com/beta/contents/1 ## パスパラメタ
	https://example.com/alpha/contents/?id=1 ## クエリパラメタ

# HTTPメソッド

URIはリソースを表し、HTTPメソッドはリソースに対しての操作を示す。

具体的に以下の場合は、`/api/v1/posts/1`というリソースに対してデータを取得（GET）するようにリクエストを送っている。

	GET /api/v1/posts/1

同じURIに対してメソッドをかえることで操作も変えることができる。

|操作|API|
|---|---|
|記事一覧の取得|GETメソッド/ http://example.com/api/v1/posts|
|記事単体の取得|GETメソッド/ http://example.com/api/v1/posts/1|
|記事の新規作成|POSTメソッド/ http://example.com/api/v1/posts|
|記事の更新|PUTメソッド/ http://example.com/api/v1/posts/1|
|記事の削除|DELETEメソッド/ http://example.com/api/v1/posts/1|

# クエリパラメーターとパスパラメーター

|種類|API|
|---|---|
|クエリパラメーター|http://example.com/api/v1/posts?id=1|
|パスパラメーター|http://example.com/api/v1/posts/1|

クエリパラメーターとパスパラメーターの使い分け

	一意なリソースを表す場合はパスパラメーターを利用
	省略して良い場合はクエリパラメーターを利用

クエリパラメーターは具体的にいうと、検索する際のリクエストは一意にパスが定まらないのでクエリパラメーターを利用する。

	http:///example.com/api/v1/users?name="suzuki"

### レスポンスデータのフォーマット

　主要なレスポンスデータは以下のフォーマットとなっている。

	XML
	JSON

### XML

　XMLの特徴は以下の通り。

	テキスト形式
	タグで記述されている
	タグは入れ子
	タグに属性が付与されている

	<login>
	 <username>useremail@company.com</username>
	 <password>mypassword</password>
	</login>

　JSONの特徴は以下の通り。

	テキスト形式
	JavaScriptを基にしたフォーマット
	XMLと比較するとデータ量が削減できる
	オブジェクトは入れ子にできる

	{
	 user:{ "id" : "1" , "name" : "tanaka" }
	}

　なお、データフォーマットをしているする際はリクエストヘッダーに記載することがお作法的とされている。

	GET http://example.com/users
	HOST : example.com
	Acceot : application/json # JSON形式と指定した場合

# データ内部後続の設計

	エンベロープを使わない
	ネスト構造を減らす
	プロパティの命名規則を統一する
	日付指定

### エンベロープを使わない

　JSONを返却するAPIの共通部分であるエンベロープは使わないようにする。

　下記のレスポンスに含まれている"header"部分に関してはリクエストヘッダーで受け渡される記載と共通しているので、不要（情報がかぶっている）。

　NG（エンベロープを含んだ場合）

	{
		"header" : {
			"code" : "0",
			"message" : "success"
	 	},
	 	"result" : {
	 		"books" : [
	 			{
	 				"id" : 1,
	 				"name" : "初めてのJavaScript",
	 				"price" : 3000
	 			},
	 			{
	 				"id" : 2,
	 				"name" : "はじめてのAPI入門",
	 				"price" : 1500
	 			}
	 		]
	 	}
	 }


　OK（エンベロープを省いた場合）

	{
		"books" : [
			{
				"id" : 1,
	 			"name" : "初めてのJavaScript",
	 			"price" : 3000
	 		},
	 		{
	 			"id" : 2,
	 			"name" : "はじめてのAPI入門",
	 			"price" : 1500
	 		}
	 	]
	 }

### ネスト構造を減らす

　ネストがあるとレスポンス容量が増えてしまうので、無駄なネストを減らすようにレスポンスを設計する。

　NG（不要なネストがある場合）

	{
		"id" : 2,
		"name" : "はじめてのAPI入門",
		"info" : {
			"author" : "tanaka",
			"price" : 1500
		}
	}

　OK（不要なネストを省いた場合）

	{
		"id" : 2,
		"name" : "はじめてのAPI入門",
		"author" : "tanaka",
		"price" : 1500
	}

### プロパティの命名規則を統一する

　基本的にはスネークケースかキャメルケースを採用する。

|名前|例|
|---|---|
|スネークケース|snake_case|
|キャメルケース|camelCase|
|パスカルケース|PascalCase|

### 日付指定

　日付はRFC3339（W3C-DTF）形式を使うようにする。

	2022-10-31T18:00:00+09:00

### エラー

　エラー詳細はレスポンスボディに追記する。

	{
		"code" : "12345",
		"message" : "認証エラーです"
	}

　また、エラーの際はHTML形式でレスポンスをしないようにする。

　※フォーマットによってはクライアントサイドで処理ができない可能性もあるため。

# その他の設計

### 認証

### JSON Web Token

　JSON Web Token（JWT）はジョットと呼び、JSON形式のデータで署名による改ざんチェックを行う。

　JWTを利用することで、認証結果をサーバ側で保持せずにクライアントで保持することができ、ステートレスな通信を行うことができる。

　JWTの構成は以下のようになっている。

	ヘッダー
	ペイロード
	署名

　JWTのサンプル

	eyJhbGcGKOWJIUzI1NiI&3Hf5cCI6IkpXVCJ9.
	eyJzdWIiOiIxMjMPqfwibmFtZSIfksjDTW3nwoAOCWQ0IjoxNTE2MjM5MDIyfQ.
	t42p4AHef69Tyyi880842bDTTOADINW93ncs7Zffs
	
	※.で結合されており、実際は以下の構成となっている。
	[ヘッダー].
	[ペイロード].
	[署名]

　ヘッダー

　ヘッダーでは具体的に署名で利用するアルゴリズムが定義されている。

	{
		"alg" : "HS256",
		"typ" : "JWT"
	}

　ペイロード

　ペイロードは保存したいデータの実態が入っている。

	{
		"sub" : "123456789", # subは同一Issuer内での識別子（ユーザID等）
		"iat" : 1516239022   # iatはjwtが発行された日時を表す
	}

　署名

　署名はデータが改ざんされていないかを確認する。

### Authorizationヘッダー

　認証で利用するヘッダーとしてAuthorizationヘッダーがあります。

　JWTを利用する場合にAuthorizationヘッダーにトークンを格納し、リクエストを送ります。

　以下のような形で記述をします。

	Authorization : [type] [credentials]

　[type]の種類は以下。

|名前|説明|
|---|---|
|Basic|ベーシック認証でIDとパスワードを平文で送る|
|Bearer|OAuth2.0でJWTはこれを使う|
|Digest|ダイジェスト認証でIDとパスワードをハッシュ化して送る|
|OAuth|OAuth1.0|

　また[credentials]には具体的な認証情報を入れる。

# セキュリティ

以下の脆弱性対策について記載する。

	XSS
	CSRF
	HTTP
	JWT

### XSS

　XSSは悪意あるユーザが席のサイトに不正なスクリプトを埋め込み、正規ユーザの情報を不正に抜き出すことができる。

　対策としてはレスポンスヘッダーに以下を追加する。

	X-XSS-Protection : 1 # これでXSSフィルタリングが有効化
	X-Frame-Options : DENY # これでframeタグの呼び出しを拒否
	X-Content-Type-Options : nosniff #これでIEの脆弱性を対応

### CSRF

　本来拒否すべきアクセスもとからのリクエストを処理してしまう。

　対策としては以下がある。

	アクセス許可していないリクエストを拒否する
		X-API-Key
		Authentication
	悪意のある攻撃者が推測しずらいトークンを発行し、照合処理を行う
		X-CSRF-TOKEN

### HTTP

　HTTPは通信経路が暗号化されていないので盗聴されやすい。

　対策方法としてはHTTPSを利用する。

### JWT

　JWTはクライアント側で編集ができるので、サーバ側での検証が不十分だった場合、改ざんされた情報を受け入れてしまう可能性がある。

　対策方法としてはヘッダーのアルゴリズム（alg）にnoneを指定しない。



