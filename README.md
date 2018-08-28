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





SaaS: 何気なく使っているクラウドサービス

	ex: グーグルのapps github







# 調べたいもの　興味のあるもの

* firebase
* Elasticsearch
* Back blaze



# 無料APIお手軽提供環境

* flask + ngrok + (docker)
* Flask + heroku + (docker)

