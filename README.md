# テーブル設計

## usersテーブル（ユーザー管理機能）

Column              | Type    | Options      |
------------------- | ------- | ------------ |
email               | string  | unique: true |
nick_name           | string  | not null     |
encrypted_password  | string  | not null     |
first_name          | string  | not null     |
last_name           | string  | not null     |
first_name_japanese | string  | not null     |
last_name_japanese  | string  | not null     |
date                | integer | not null     |

### Association
- has_many :item
- has_many :purchase


## itemsテーブル（商品出品機能）

Column        | Type       | Options           |
------------- | ---------- | ----------------- |
text          | text       | not null          |
title         | string     | not null          |
category      | string     | not null          |
condition     | string     | not null          |
region        | string     | not null          |
user_id       | references | foreign_key: true |
date_shipment | integer    | not null          |
price_id      | integer    | not null          |
delivery_fee  | integer    | not null          |

### Association
- belongs_to :user
- has_one :purchase


## addressテーブル（商品購入機能）

Column      | Type    | Options  |
----------- | ------- | -------- |
title       | string  | not null |
address     | string  | not null |
price       | integer | not null |
user_id     | integer | not null |
item_id     | integer | not null |

### Association
- belongs_to :user
- belongs_to :item


## commentsテーブル（コメント機能）

Column  | Type   | Options           |
------- | ------ | ----------------- |
text    | text   | not null          |
user    | string | foreign_key: true |
item    | string | foreign_key: true |