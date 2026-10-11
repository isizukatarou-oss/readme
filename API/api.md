# webの仕組み

１．ユーザ（クライアント）はWebに対してHTTPリクエストを送る。

２．リクエストを受けたWebサーバはデータ（HTMLやJSON）を返す。

# HTTPリクエスト

具体的にWebブラウザから送っているHTTPリクエストは以下の3要素で構成されている。

	リクエストライン
	リクエストヘッダー
	リクエストボディー

・リクエストライン

　HTTPリクエストの中身であるリクエストラインは以下のようになっている。

	GET /index.html HTTP/1.1

　リクエストラインでは「何を、どうしたい」が書かれており、構成は以下のようになっている。

	メソッド
	リクエストURI
	HTTPバージョン

　メソッドは具体的にGET（データ取得）、POST（データ登録）、PUT（データ更新）、DELETE（データ削除）等がある。

・リクエストヘッダー

　リクエストヘッダーはリクエストについての情報や属性（メタデータ）について記載されている。

	Host: localhost:8080
	Connection: keep-alive
	User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_11_4) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/54.0.2840.98 Safari/537.36
	Accept: */*
	Referer: http://localhost:8080/
	Accept-Encoding: gzip, deflate, sdch, br
	Accept-Language: ja,en-US;q=0.8,en;q=0.6
	Cookie: user_id=12345678

・リクエストボディー

　HTTPリクエストを送ったときにレスポンスは以下の構成になっている。

# レスポンス

HTTPリクエストを送ったときにレスポンスは以下の構成になっている。

	ステータスライン
	レスポンスヘッダー
	レスポンスボディー

・ステータスライン

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

・レスポンスヘッダー

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

・レスポンスボディー

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

