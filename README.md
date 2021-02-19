# テーブル設計

## usersテーブル（ユーザー管理機能）

Column    | Type    | Options  |
--------- | ------- | -------- |
nick_name | string  | not null |
email     | string  | not null |
password  | string  | not null |
name      | string  | not null |
birthday  | integer | not null |


## exhibitsテーブル（商品出品機能）

Column        | Type    | Options           |
------------- | ------- | ----------------- |
text          | text    | not null          |
title         | string  | not null          |
category      | string  | not null          |
condition     | string  | not null          |
region        | string  | not null          |
user          | string  | foreign_key: true |
date_shipment | integer | not null          |
price         | integer | not null          |
delivery_fee  | integer | not null          |


## purchasesテーブル（商品購入機能）

Column      | Type    | Options  |
----------- | ------- | -------- |
title       | string  | not null |
credit_card | string  | not null |
address     | string  | not null |
price       | integer | not null |


## commentsテーブル（コメント機能）

Column  | Type   | Options           |
------- | ------ | ----------------- |
text    | text   | not null          |
user    | string | foreign_key: true |
exhibit | string | foreign_key: true |