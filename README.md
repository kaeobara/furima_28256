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
#　テーブル設計

## users テーブル

| Column          | Type   | Options     |
| --------------- | ------ | ----------- |
| nickname        | string | null: false |
| email           | string | null: false |
                           |unique: true |#重複を防ぐ
                           |index: true  |#外部キー
| password        | string | null: false |
| first_name      | string | null: false |
| family_name     | string | null: false |
| first_name_kana | string | null: false |
| family_name_kana| string | null: false |
| birth_year      | date   | null: false |
| birth_month     | date   | null: false |
| birth_day       | date   | null: false |
### Association

- has_many :items, dependent::destroy #一緒に消える
- has_one :shipping_address, dependent::destroy
- has_one :credit_card, dependent::destroy
- 

##  Itemsテーブル

| Column            | Type      | Options          |
| ----------------- | --------- | -----------      |
| item_image_id     | references| null: false      |
|                   |             foreign_key:true |
| name              | string    | null: false      |
| introduction      | text      | null: false      |
| category_id       | references| null: false      |
|                   |             foreign_key:true |
| item_condition_id | references| null: false      |
|                   |             foreign_key:true |
| postage_payer_id  | references| null: false      |
|                   |             foreign_key:true |
| shipping_region_id| references| null: false      |
| shipping_days_id  | references| null: false      |
|                   |             foreign_key:true |
| price             | integer   | null: false      |

### Association

- belongs_to :user

##  Credit_cardテーブル

| Column          | Type       | Options              |
| --------------  | ---------- | -------------------- |
| card_number     | integer    | null: false          |
| expiration_year | integer    | null: false          |
| expiration_month| integer    | null: false          |
| security_code   | integer    | null: false          |
| user_id         | references | null: false          |
|                 |              foreign_key: true

### Association

- belongs_to :user

## Shipping_adress テーブル

| Column      | Type       | Options               |
| ----------- | ---------- | --------------------- |
| postal_code | string     | null: false           |
| prefecture  | references | null: false           |
|             |              foreign_key: true     |
| city        | integer    | null: false           |
| adress      | integer    | null: false           |
|bilding_name | integer    | null: false           |
|phone_number | string     | null: false           |
|user_id      | references | null: false           |
|             |              foreign_key: true     |

### Association

- belongs_to :user