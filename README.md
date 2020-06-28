# フリマアプリ
テックキャンプの最終課題にて、フリーマーケットアプリを作成しました。

## URL
http://18.177.199.123/
* ID/Pass
  * ID: team_d_osaka
  * Pass: ID: team_d_osaka76
* テスト用アカウント等
  * 購入者用  
    ・メールアドレス: buyeruser@gamil.com  
    ・パスワード: buyeruser
  * 購入用カード情報
    ・番号： 4242424242424242  
    ・期限： 12/20  
    ・セキュリティコード：123  
  * 出品者用  
    ・メールアドレス名: testuser@gmail.com  
    ・パスワード: testuser  

## 動作確認方法
* Chromeの最新版を利用してアクセスしてください。
* 接続先およびログイン情報については、上記の通りです。
* テストアカウントでログイン→トップページから出品ボタン押下→商品情報入力→商品出品
* 確認後、ログアウト処理をお願いします。

## ER図
<img width="442" alt="ce974b8162d728e6af93f73b4eadb93e" src="https://user-images.githubusercontent.com/64832157/85948046-64249a80-b989-11ea-8c9e-476507a3ab5b.png">

## usersテーブル
|Column|Type|Options|
|------|----|-------|
|nickname|string|null: false|
|email|string|null: false, index: true|
|encrypted_password|string|null: false|
|user_image|string||
|introduction|text||
|family_name|string|null: false|
|first_name|string|null: false|
|family_name_kana|string|null: false|
|first_name_kana|string|null: false|
|birth_day|date|null: false|

### Association
- has_many :items
- has_one :destination
- has_one :card

## destinationsテーブル
|Column|Type|Options|
|------|----|-------|
|destination_family_name|string|null: false|
|destination_first_name|string|null: false|
|destination_family_name_kana|string|null: false|
|destination_first_name_kana|string|null: false|
|post_code|string|null: false|
|prefecture|string|null: false|
|city|string|null: false|
|address|string|null: false|
|building_name|string||
|phone_number|string||
|user_id|integer|null: false, foreign_key: true, index: true|
### Association
- belongs_to :user

## cardsテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|customer_id|string|null: false|
|card_id|string|null: false|
### Association
- belongs_to :user

## itemsテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false|
|price|string|null: false|
|description|string|null: false|
|status|string|null: false|
|size|string|null: false|
|shipping_cost|integer|null: false|
|shipping_method|integer|null: false|
|shipping_date|sinteger|null: false|
|prefecture_id|integer|null: false|
|category_id|integer|null: false, foreign_key: true|
|brand_id|integer|null: false, foreign_key: true|
|user_id|integer|null: false, foreign_key: true|
### Association
- has_many :images
- belongs_to :user
- belongs_to :category
- belongs_to :brand

## categorysテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false|
|ancestry|string||
### Association
- has_many :items

## imagesテーブル
|Column|Type|Options|
|------|----|-------|
|image|string|null: false|
|item_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :item

## brandsテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|index: true|
### Association
- has_many :items

## likesテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|integer|null: false, foreign_key: true|
|item_id|integer|null: false, foreign_key: true|
### Association
- belongs_to :user
- belongs_to :item
