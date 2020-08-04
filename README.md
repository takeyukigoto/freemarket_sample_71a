# アプリ概要    
## フリーマーケットアプリ    
![メイン画像](readfuri2.jpg)    
### 詳細説明  
チームでフリマーケットアプリを作成しました。  
・URL http://18.181.155.100/  
・ID: admin  
・Pass: 2222  
### テスト用アカウント  
■購入者用  
・メールアドレス: buyer_user@gmail.com  
・パスワード: buyer_user  
■購入用カード情報  
・番号： 4242424242424242  
・期限： Sun Dec 20 2020 00:00:00 GMT+0900 (日本標準時)  
・セキュリティコード：123  
■出品者用  
・メールアドレス名: seller_user1@gmail.com  
・パスワード: seller_user  
■開発状況  
◯開発環境  
・Ruby/Ruby on Rails/MySQL/Github/AWS/Visual Studio Code  
■開発期間と平均作業時間  
・開発期間：5/16~7/29  
・1日あたりの平均作業時間：3  
■開発体制  
・人数：4  
。アジャイル型開発（スクラム）  
・Trelloによるタスク管理  

■動作確認方法  
・Chromeの最新版を利用してアクセスしてください。  
・ただしデプロイ等で接続できないタイミングもございます。その際は少し時間をおいてから接続ください。  
・接続先およびログイン情報については、上記の通りです。  
・同時に複数の方がログインしている場合に、ログインできない可能性がございます。  
・テストアカウントでログイン→トップページから出品ボタン押下→商品情報入力→商品出品  
・確認後、ログアウト処理をお願いします。  

## usersテーブル
|Column|Type|Options|
|------|----|-------|
|nickname|string|null: false|
|last_name|string|null: false|
|first_name|string|null: false|
|last_name_kana|string|null: false|
|first_name_kana|string|null: false|
|birthday|date|null: false|
|email|string|null: false, unique: true|
|encrypted_password|string|null: false|
|telnum|integer |null: false|
|gender|integer |null: false|
|year|integer|null: :false|
|month|integer|null: :false|
|day|integer|null: :false|
### Association
has_one :address</br>
has_one :card</br>
has_many :items</br>

## itemsテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false|
|detail|text|null: false|
|price|integer|null: false|
|category_id|reference|null: false, foreign_key: true|
|brand|string||
|condition_id|integer|null: false|
|shipping_cost_id|integer|null: false|
|shipping_days_id|integer|null: false|
|shipping_area_id|integer|null: false|
|user_id|integer|null: false, foreign_key: true|
|costomer|integer||
### Association
belongs_to :user</br>
belongs_to :category</br>
has_many :item_images</br>

## addressesテーブル
|Column|Type|Options|
|------|----|-------|
|postal_code|string|null: false|
|prefecture_id|integer|null: false|
|city|string|null: false|
|street|string|null: false|
|building|string||
|phone|string||
|user_id|reference|null: false, foreign_key: true|
### Association
belongs_to :user</br>

## cardテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|customer_id|string|null: false|
|card_id|string|null: false|
### Association
belongs_to :user</br>

## categoriesテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false|
|ancestry|string||
### Association
has_many :items</br>

## item_imagesテーブル
|Column|Type|Options|
|------|----|-------|
|image|string|null: false|
|item_id|references|null: false, foreign_key: true|
### Association
belongs_to :item




