# awesome_stack_free
強力なossを見つける　堅牢性とかは置いておいて**無料** でプロダクト作ろう

目標はAWSを使わずに最強のインフラ環境を構築することです

開発言語は主にpython、rubyを想定しております

APIサーバーの想定Flamework: flask,tornado,sanic,pyramid,bottle,django,sinatra,ror etc..なんでもいいでしょう





## OSS

* [minio](https://www.minio.io/)




無料で使えるオブジェクトストレージ  

dockerはもちろん、amazon simple storage service（以降S3）ライクなobjstrage

なんとS3の互換性を謳っておりS3ライクのAPIが叩くことができる

kubernetesにも対応して、これからどんどん普及して行くことだろう



##### 持論

**とりあえずオフジェクトストレージはPUT（バケットに入れる）とGET（引っ張り出す）メソッドが機能すれば（個人開発なら）どうでもいい**



* [ngrok](https://ngrok.com/)



ローカルで開発したAPIやアプリケーションを無料で公開することができる

ささっとwebアプリを組みたい時やapiを公開したい時に使える

apiendpoint（http://{ここ}/hoge/apiとか）は自動で割り当てられる

それがダサい人はドメインを取得しよう　でもngrokでもendpointのドメイン切り替えに金取られる

もちろんドメインとるのにも金かかる



# DB

DBは基本無料ですが（オラ◯クル）みたいな~~ぼったくり~~ も存在します

いかに環境に特化した効率の良いDBの選択が重要です

* [Postgresqul](https://www.postgresql.jp/)



mysqlとほぼ同じアーキテクチャのDB

お好みで使い分けるのがいいかもしれない（理想はどっちも使いこなせる）

herokuのデフォはこれなので惰性で使うのもあり

psycopg2などのpythonにおける強力なアダプタライブラリも存在していて強い



* [mysql](https://www.mysql.com/jp/)



sqliteからステップアップするビギナーの方やmysqlと共に長年過ごしてきたエリートエンジニア御用達

ビギナーの方はphpmyadminのような超便利webGUIを使わずにコンソールからsql直打ちをオススメしたい

SQLがちゃんとわかっていると今後とてもよく役に立つ（SQLをなあなあにしてしまった私のようになってほしくない）



* [MongoDB](https://www.mongodb.com/)



NoSQLで多分一番有名

NoSQL大好きマンは使うといいかもしれない

redisは全くわかりません　ごめんなさい



# IaaS PaaS SaaS



IaaS: 仮想鯖やストレージ、ネットワーク環境を自由に設定できる

	そこに丸投げできる。つまりオンプレより楽にインフラが組める

	最近はapacheがIaaSをリリースしたり頑張っているらしい

	ex: EC2 GCE



タダ利用はキツイか…？

と思ったがGCEは無料でEC2のしょぼい版インスタンスを立てたりドメイン取ったり証明書発行（https）が行えるそうです　https://qiita.com/ndxbn/items/7ef0a96e409a5b5837bd

ただ、ちょっとミスってアクセス負荷とかかかると従量課金が発生するらしい



個人、少人数開発レベルでは少々オーバースペックか？

そこで…



PaaS: IaaSからハードウェアやOSを残し切り抜いたようなクラウド

	IaaSに比べ学習コストが低い、pushからのdeployがわかりやすいのが利点

	ex: GAE heroic



* [heroku](https://jp.heroku.com/)



クラウド初心者おすすめ

ngrokの次くらいに簡単にサービスやAPIを提供できる

アドオンも無料で魅力的なものが多い

弱点は無料枠だと30分アクセスがないとスリープしてしまう（起きるまで10秒くらいかかる）

アクセスが大量に集まると1dynoでは対応しきれなくなる

くらいである

前者はどうしようもないが後者は大量の複垢を作成することでうまく分散させることができる



* [IBM Bluemix]()



月512Mまでタダ

herokuに比べスリープしないため、そんなにアクセスの多くないサービスの運用に向いている

APIは知らん



* [GCP]()



無料でガチるならおすすめ

世界最強企業グーグルの強さを存分に体感しよう

グーグル産のクーベももちろん備わっている

本当にすごいなこの企業

無料版を使い続けるのもあり　ていうかよっぽど大規模プロジェクトじゃないなら無料版でいい

有料でやる場合は、引っ越ししやすいファイル構築や環境変数、データの保管などをしておいて、無料期間が終わったら新しく垢作ってそっちにサッと移行するのもあり？やったことないからわからん





SaaS: 何気なく使っているクラウドサービス

	ex: グーグルのapps github



* [Google Drive]()



みんな使ってるGD、実はRESTapiが備わっていて使いやすいがこれをオブジェクトストレージがわりにするのはあまりオススメできない

GAS好きならオススメ

スプレッドシートと親和性が非常によろしい



* [Gitlab]()



webベースgit管理倉永遠の二番手

しかし見やすいUI、洗礼されたUXなど使用満足度は個人的にgithubより勝る

なにより強いのが、プライベートプロジェクト（labは1ソース群をプロジェクト、hubはリポジトリと呼ぶ）が無料で作れるところである

そもそも、どうしてgithubは見えなくするのに金をとるのかわからない

欠点としては、githubに比べて看板キャラがひじょ〜に弱い

オクトキャットはゴーファーくんに次ぐくらい界隈でメジャーなのに対しgitlabの謎のキツネは名前すら知らない

あと転職、就活の際はgithubのid提出を求められることがある　今までこの提出を求めてくるところで、gitlabのidでも可、というところは見たことない





# 機械学習・深層学習

* [ワトソン]()



タダで使えないこともないらしい

使うより使い道を考える方が難しい





# ドメイン・レンタル鯖

クラウドに株を奪われながらもなお生きる昔ながらのレンタル鯖

無料なものには大体きつい容量制限があり、ウェブページを作ろうものならヘッダーフッターにセンスのないゴミみたいなアドセンスがついてくる

FTPでファイルを鯖にアップする渋い豪の者にはおすすめ



* [.tk]()



ご存知トケラウ共和国の無料ドメイン

でも取得手順が少し面倒くさいためドメイン取得が初めてという方はGMOとかでやっすいドメインを取得することをおすすめする

SEOは悪い



# 調べたいもの　興味のあるもの

* firebase
* Elasticsearch
* Back blaze



# 無料APIお手軽提供環境

* flask + ngrok + (docker)
* Flask + heroku + (docker)

随時追加



# Google API上限

| Service                                          | Request limitation          |
| ------------------------------------------------ | --------------------------- |
| Ad Exchange Buyer API                            | 1,000 リクエスト数/日       |
| Ad Exchange Seller API                           | 10,000 リクエスト数/日      |
| Admin SDK                                        | 150,000 リクエスト数/日     |
| AdSense Host API                                 | 100,000 リクエスト数/日     |
| AdSense Management API                           | 10,000 リクエスト数/日      |
| Analytics API                                    | 50,000 リクエスト数/日      |
| Apps Activity API                                | 10,000,000 リクエスト数/日  |
| Audit API                                        | 10,000 リクエスト数/日      |
| BigQuery API                                     | 200,000 リクエスト数/日     |
| Blogger API v3                                   | 10,000 リクエスト数/日      |
| Books API                                        | 1,000 リクエスト数/日       |
| CalDAV API                                       | 1,000,000 リクエスト数/日   |
| Calendar API                                     | 1,000,000 リクエスト数/日   |
| Chrome Web Store API                             | なし                        |
| Cloud Network Performance Monitoring API         | なし                        |
| Contacts API                                     | 20,000,000 リクエスト数/日  |
| Content API for Shopping                         | なし                        |
| Custom Search API                                | 1,000 リクエスト数/日       |
| DCM/DFA Reporting And Trafficking API            | 50,000 リクエスト数/日      |
| Debuglet Controller API                          | 100,000 リクエスト数/日     |
| Directions API                                   | 2,500 リクエスト数/日       |
| Distance Matrix API                              | 2,500 リクエスト数/日       |
| DoubleClick Search API                           | 100,000 リクエスト数/日     |
| Drive API                                        | 10,000,000 リクエスト数/日  |
| Drive SDK                                        | なし                        |
| Elevation API                                    | 2,500 リクエスト数/日       |
| Enterprise License Manager API                   | 10,000 リクエスト数/日      |
| Fitness API                                      | 86,400 リクエスト数/日      |
| Freebase API                                     | 100,000 リクエスト数/日     |
| Fusion Tables API                                | 25,000 リクエスト数/日      |
| Genomics API                                     | 50,000,000 リクエスト数/日  |
| Geocoding API                                    | 2,500 リクエスト数/日       |
| Gmail API                                        | 1,000,000,000 ユニット数/日 |
| Google Affiliate Network API                     | 1,000 リクエスト数/日       |
| Google Apps Marketplace API                      | 10,000 リクエスト数/日      |
| Google Apps Marketplace SDK                      | なし                        |
| Google Apps Reseller API                         | 10,000 リクエスト数/日      |
| Google Civic Information API                     | 25,000 リクエスト数/日      |
| Google Cloud Datastore API                       | 10,000,000 リクエスト数/日  |
| Google Cloud Deployment Manager API              | 10,000 リクエスト数/日      |
| Google Cloud DNS API                             | 50,000 リクエスト数/日      |
| Google Cloud Messaging for Android               | なし                        |
| Google Cloud Messaging for Chrome                | 10,000 リクエスト数/日      |
| Google Cloud Monitoring API                      | 50,000 リクエスト数/日      |
| Google Cloud Pub/Sub                             | なし                        |
| Google Cloud SQL                                 | なし                        |
| Google Cloud SQL API                             | 10,000 リクエスト数/日      |
| Google Cloud Storage                             | なし                        |
| Google Cloud Storage JSON API                    | なし                        |
| Google Compute Engine                            | 無制限                      |
| Google Compute Engine Autoscaler API             | 50,000 リクエスト数/日      |
| Google Compute Engine Instance Group Manager API | 50,000 リクエスト数/日      |
| Google Compute Engine Instance Groups API        | 1,000,000 リクエスト数/日   |
| Google Contacts CardDAV API                      | 20,000,000 リクエスト数/日  |
| Google Container Engine API                      | 1,000,000 リクエスト数/日   |
| Google Maps Android API v2                       | なし                        |
| Google Maps Coordinate API                       | 1,000 リクエスト数/日       |
| Google Maps Embed API                            | 2,000,000 リクエスト数/日   |
| Google Maps Engine API                           | 10,000 リクエスト数/日      |
| Google Maps Geolocation API                      | 100 リクエスト数/日         |
| Google Maps JavaScript API v3                    | 1,000,000 リクエスト数/日   |
| Google Maps SDK for iOS                          | なし                        |
| Google Maps Tracks API                           | なし                        |
| Google Mirror API                                | 1,000 リクエスト数/日       |
| Google Picker API                                | 10,000 リクエスト数/日      |
| Google Play Android Developer API                | 200,000 リクエスト数/日     |
| Google Play Game Management                      | 1,000,000 リクエスト数/日   |
| Google Play Game Services                        | 50,000,000 リクエスト数/日  |
| Google Play Game Services Publishing API         | 1,000,000 リクエスト数/日   |
| Google Spectrum Database API                     | 1,000 リクエスト数/日       |
| Google Webmaster Tools API                       | 1,000,000 リクエスト数/日   |
| Google+ API                                      | 10,000 リクエスト数/日      |
| Google+ Domains API                              | 10,000 リクエスト数/日      |
| Google+ Hangouts API                             | なし                        |
| Groups Migration API                             | 500,000 リクエスト数/日     |
| Groups Settings API                              | 100,000 リクエスト数/日     |
| Identity Toolkit API                             | 1,000,000 リクエスト数/日   |
| Orkut REST API                                   | 250 リクエスト数/日         |
| PageSpeed Insights API                           | 25,000 リクエスト数/日      |
| Places API                                       | 100,000 リクエスト数/日     |
| Prediction API                                   | 10,000 リクエスト数/日      |
| QPX Express Airfare API                          | 50,000 リクエスト数/日      |
| Safe Browsing API                                | 10,000 リクエスト数/日      |
| Site Verification API                            | 100,000 リクエスト数/日     |
| Static Maps API                                  | 1,000,000 リクエスト数/日   |
| Street View Image API                            | 1,000,000 リクエスト数/日   |
| Tag Manager API                                  | 10,000 リクエスト数/日      |
| Tasks API                                        | 50,000 リクエスト数/日      |
| Time Zone API                                    | 2,500 リクエスト数/日       |
| Translate API                                    | 2,000,000 characters/day    |
| URL Shortener API                                | 1,000,000 リクエスト数/日   |
| Web Fonts Developer API                          | 10,000 リクエスト数/日      |
| YouTube Analytics API                            | 100,000 リクエスト数/日     |
| YouTube Data API v3                              | 50,000,000 ユニット数/日    |
| Zync Render API                                  | 1,000,000 リクエスト数/日   |

