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

## userテーブル
|Column|Type|Options|
|------|----|-------|
|first_name|string|null: false|
|last_name|string|null: false|
|nickname|string|null: false, unique: true|
|mail|string|null: false|
|content|text||
|avatar_image|string||
|phone_number|integer|null: false|
|birth_year|integer|null: false|
|birth_month|integer|null: false|
|birth_day|integer|null: false|

### Association
- has_many :items
- has_many :orderings
- has_many :credit_cards
- has_one :address

## addressテーブル
|Column|Type|Options|
|------|----|-------|
|postal_code|integer|null: false|
|prefectures|string|null: false|
|city_name|string|null: false|
|house_number|string|null: false|
|building_name|string||
|user_id|references|null: false, foreign_key: true|

### Association
- belongs_to :user

## credit_cardテーブル
|Column|Type|Options|
|------|----|-------|
|card_number|integer|null: false|
|expiration_month|integer|null: false|
|expiration_year|integer|null: false|
|security_code|integer|null: false|
|user_id|references|null: false, foreign_key: true|

### Association
- belongs_to :user

## itemテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false|
|price|integer|null: false|
|state|integer|null: false|
|content|text|null: false|
|user_id|references|null: false, foreign_key: true|
|brand_id|references|foreign_key: true|
|category_id|references|null: false, foreign_key: true|
|subcategory_id|references|null: false, foreign_key: true|
|further_category_id|references|null: false, foreign_key: true|

### Association
- has_many :item_image
- has_one :brand
- has_one :category
- has_one :subcategory
- has_one :further_category
- belongs_to :user

## item_imageテーブル
|Column|Type|Options|
|------|----|-------|
|image_url|string|null: false|
|item_id|references|null: false, foreign_key: true|

### Association
- belongs_to :item

## brandテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false|

### Association
- belongs_to :item

## categoryテーブル
|Column|Type|Options|
|------|----|-------|
|name|string|null: false|
|ancestry|string|index: true|

### Association
- belongs_to :item

## orderingテーブル
|Column|Type|Options|
|------|----|-------|
|user_id|references|null: false, foreign_key: true|
|item_id|references|null: false, foreign_key: true|


### Association
- belongs_to :item
- belongs_to :user


* ...
