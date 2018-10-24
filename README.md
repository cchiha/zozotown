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

|Column|Type|Options|
|------|----|-------|
|first_name|string|null: false|
|last_name|string|null: false|
|gender|string|null: false|
|birth_year|integer|null: false|
|birth_month|integer|null: false|
|birth_day|integer|null: false|
|postal_cord|integer|null: false|
|address|text|null: false|
|phone|integer|null: false|
|email|string|null: false, unique: true|
|password|string|null: false|

### Association
- has_many :itmes
- has_many :favorite_item
- has_many :favorite_brand
- has_many :favorite_shop
- has_one :cart
- has_many :delivery
- has_many :credit_card
- has_many :order
- has_many :payment
- has_many :check_itmes
- has_many :check_shops

## itemsテーブル

|name|string|null: false|
|shop_id|integer|null: false, foreign_key: true, add_index|
|brand_id|integer|null: false, foreign_key: true, add_index|
|image_id|integer|null: false, foreign_key: true, add_index|
|price|integer|null: false|
|description|text||
|stock_id|integer|null: false, foreign_key: true, add_index|
|color|string|null: false|
|category_id|integer|null: false, foreign_key: true, add_index|
|sub_category_id|integer|null: false, foreign_key: true, add_index|

### Association
- has_many :users
- has_many :images
- has_many :stocks
- has_many :favorite_item
- has_many :cart
- belongs_to :brand
- belongs_to ;shop
- belongs_to :category
- belongs_to :sub_category
- has_many :order
- has_many :check_items

## imagesテーブル

|image_url|string|null: false|
|item_id|integer|null: false, foreign_key: true, add_index|

### Association
- belongs_to :items

## stocksテーブル

|stock|integer|null: false|
|item_id|integer|null: false, foreign_key: true, add_index|
|color|string|null: false|
|size|string|null: false|
|image_id|integer|null: false, foreign_key: true, add_index|

### Association
- belongs_to :items
- has_one :images

## favorite_itemテーブル

|item_id|integer|null: false, foreign_key: true, add_index|
|user_id|integer|null: false, foreign_key: true, add_index|

### Association
- belongs_to :items
- belongs_to :users

## favorite_brandテーブル

|brand_id|integer|null: false, foreign_key: true, add_index|
|user_id|integer|null: false, foreign_key: true, add_index|

### Association
- belongs_to :brand
- belongs_to :users

## favorite_shopテーブル

|shop_id|integer|null: false, foreign_key: true, add_index|
|user_id|integer|null: false, foreign_key: true, add_index|

### Association
- belongs_to :shop
- belongs_to :user

## cartテーブル

|user_id|integer|null: false, foreign_key: true, add_index|
|item_id|integer|null: false, foreign_key: true, add_index|
|total_price|integer|null: false|

### Association
- belongs_to :users
- has_many :items
- belongs_to :order

## brandテーブル

|name|string|null: false, unique: true|
|description|text||
|item_id|integer|null: false, foreign_key: true, add_index|

### Association
- has_many :items
- has_many :favorite_brand

## shopテーブル

|name|string|null: false, unique: true|
|description|text||
|item_id|integer|null: false, foreign_key: true, add_index|

### Association
- has_many :items
- has_many :favorite_shop

## categoryテーブル

|name|string|null: false, unique: true|

### Association
- has_many :items
- has_many :sub_category

## sub_categoryテーブル

|name|string|null: false, unique: true|
|category_id|integer|null: false, foreign_key: true, add_index|

### Association
- has_many :items
- belongs_to category

## deliveryテーブル

|name|string|null: false|
|postal_cord|integer|null: false|
|address|text|null: false|
|phone|integer|null: false|

### Association
- belongs_to :users

## credit_cardテーブル

|user_id|integer|null: false, foreign_key: true, add_index|
|name|string|null: false|
|card_number|integer|null: false|
|security_code|integer|null: false|
|limit_month|integer|null: false|
|limit_year|integer|null: false|

### Association
- belongs_to :users

## orderテーブル

|user_id|integer|null: false, foreign_key: true, add_index|
|cart_id|integer|null: false, foreign_key: true, add_index|
|delivery_id|integer|null: false, foreign_key: true, add_index|
|delivery_day|iteger||
|delivery_hour|integer||
|delivery_method|string|null: false|
|payment_id|intger|null: false, foreign_key: true, add_index|

### Association
- belongs_to :users
- has_many :items
- has_one :cart
- has_one :delivory
- has_one :payment

## paymentテーブル

|method|string|null: false|
|price|integer|null: false|
|coupon|integer||

### Association
- belongs_to :order

## check_itmesテーブル

|user_id|integer|null: false, foreign_key: true, add_index|
|itme_id|integer|null: false, foreign_key: true, add_index|

### Association
- belongs_to :users
- belongs_to :items

## check_shopsテーブル
|user_id|integer|null: false, foreign_key: true, add_index|
|shop_id|integer|null: false, foreign_key: true, add_index|

### Association
- belongs_to :users
- belongs_to :shop
