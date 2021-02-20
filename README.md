# テーブル設計

## usersテーブル（ユーザー管理情報）

Column              | Type    | Options                |
------------------- | ------- | ---------------------- |
email               | string  | not null, unique: true |
nick_name           | string  | not null               |
encrypted_password  | string  | not null               |
first_name          | string  | not null               |
last_name           | string  | not null               |
first_name_japanese | string  | not null               |
last_name_japanese  | string  | not null               |
birthday            | date    | not null               |

### Association
- has_many :items
- has_many :purchases


## itemsテーブル（商品出品情報）

Column           | Type       | Options           |
---------------- | ---------- | ----------------- |
text             | text       | not null          |
title            | string     | not null          |
category_id      | integer    | not null          |
condition_id     | integer    | not null          |
delivery_fee_id  | integer    | not null          |
region_id        | integer    | not null          |
date_shipment_id | integer    | not null          |
price            | integer    | not null          |
user             | references | foreign_key: true |

### Association
- belongs_to :user
- has_one :purchase
- has_one :delivery


## purchasesテーブル（商品購入情報）

Column      | Type    | Options  |
----------- | ------- | -------- |
title       | string  | not null |
price       | integer | not null |
user_id     | integer | not null |
item_id     | integer | not null |

### Association
- belongs_to :user
- belongs_to :item
- has_one :delivery


## deliveriesテーブル（配送先情報）

Column         | Type    | Options  |
-------------- | ------- | -------- |
postal_code    | integer | not null |
prefectures_id | integer | not null |
municipality   | string  | not null |
address        | string  | not null |
building_name  | string  | not null |
phone_number   | string  | not null |

### Association
- belongs_to :item
- belongs_to :purchase


## commentsテーブル（コメント機能）

Column  | Type   | Options           |
------- | ------ | ----------------- |
text    | text   | not null          |
user    | string | foreign_key: true |
item    | string | foreign_key: true |