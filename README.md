# README

This README would normally document whatever steps are necessary to get the
application up and running.

Things you may want to cover:

* Ruby version

* System dependencies

* Configuration

* Database creation

* Database initialization

* How to run the test suite

* Services (job queues, cache servers, search engines, etc.)

* Deployment instructions

* ...

## usersテーブル
|Columm|Type|Options|
|:------|:----|:-------|
|family_name|string|null: false|
|first_name|string|null: false|
|family_name_kana|string|null: false|
|first_name_kana|string|null: false|
|nickname|string|null: :false|
|e-mail|string|null: ：false|
|number|string|null: :false|
|encrypted_password|string|null: :false|
|password_confirmation|string|null: :false|
|gender|integer|null: :false|
|year|integer|null: :false|
|month|integer|null: :false|
|day|integer|null: :false|
|introduction|text||
|user_image|string||

## Association
has_many :cards
has_many :addresses
has_many :items
has_many :comments


## index
add_index: [:nickname, :gender]




## addressesテーブル
|colum|type|Opsion|
|:------|:----|:-------|
|family_name|string|null: false|
|first_name|string|null: false|
|family_name_kana|string|null: false|
|first_name_kana|string|null: false|
|postal_code|string|null: false|
|city|string|null: false|
|local|string|null: false|
|block|string|null: false|
|building|string||
|number|integer||
|user_id|references|null: false, foreign_key: true|

## Association
belongs_to :user

## index
add_index: [:city, :user_id]




## Cardsテーブル
|Column|Type|Options|
|:------|:----|:-------|
|user_id|integer|null: false, foreign_key: true|
|customer_id|string|null: false|
|card_id|string|null: false|

## Association
belongs_to :user

## index
add_index: :user_id




## commentsテーブル
|Column|Type|Options|
|:------|:----|:-------|
|user_id|integer|null: false,foreign_key: true|
|item_id|integer|null: false,foreign_key: true|
|text|text|null: :false|

## Association
belongs_to :user
belongs_to :item

## index
add_index: [:user_id, :item_id]




## itemsテーブル
|Column|Type|Options|
|:------|:----|:-------|
|user_id|integer|foreign_key: true|
|name|string|null:：false|
|description|text|null: :false|
|price|integer|null:：false|
|buyer_id|integer||
|size|string||
|condition|string|null: :false|
|wait|string|null: :false|
|postage|integer|null: :false|
|category_id|integer|null: :false|
|brand_id|integer|null: :false|
|prefecture_id|integer|null: :false|

## Association
belongs_to :user, optional: true
has_many :comments
has_many :images
belongs_to :brand
belongs_to :category
has_many :images, dependent: :destroy
accepts_nested_attributes_for :images, allow_destroy: true
belongs_to_active_hash :prefecture
belongs_to_active_hash :category
belongs_to_active_hash :brand
## index
add_index: [:name, :price]




## imagesテーブル
|Column|Type|Options|
|:------|:----|:-------|
|src|string|null: false|
|item_id|integer|null: false, foreign_key: true|

## Association
belongs_to :item, optional: true




## Brandsテーブル
|Column|Type|Options|
|:------|:----|:-------|

## Association
has_many :items




## Categoriesテーブル
|Column|Type|Options|
|:------|:----|:-------|
|name|string|null: false|
|ancestry|string||

## Association
has_many :items

## index
add_index: [:gender, :name]

