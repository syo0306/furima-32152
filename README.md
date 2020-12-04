# DB 設計

## users table

| Column               | Type   | Options                  |
| ---------------------| ------ | -------------------------|
| nickname             | string | null: false              |
| email                | string | unique: true,null: false |
| encrypted_password   | string | null: false              |
| first_name           | string | null: false              |
| first_name_kana      | string | null: false              |
| last_name            | string | null: false              |
| last_name_kana       | string | null: false              |
| birthday             | date   | null: false              |

### Association

* has_many :items
* has_many :orders



## items table

| Column                         | Type       | Options           |
|--------------------------------|------------|-------------------|
| name                           | string     | null: false       |
| price                          | integer    | null: false       |
| detail_item_id                 | integer    | null: false       |
| detail_value_id                | integer    | null: false       |
| item-scheduled-delivery_id     | integer    | null: false       |
| postage_id                     | integer    | null: false       |
| collection_select_id           | integer    | null: false       |
| item-sell                      | integer    | null: false       |
| user                           | references | foreign_key: true |

### Association

- belongs_to :user 
* has_one :order

item-sell                 

## orders table

| Column      | Type        | Options           |
|-------------|-------------|-------------------|
| item        | references  | foreign_key: true |
| user        | references  | foreign_key: true |

## Association

- belongs_to :item
- belongs_to :user
- has_one :address


## address table

| Column             | Type        | Options             |
|--------------------|-------------|---------------------|
| prefecture_id      | integer     | null: false         |
| postal_code        | string      | null: false         |
| city               | string      | null: false         |
| address            | string      | null: false         |
| house number       | string      | null: false         |
| building           | string      |                     |
| order              | references  | foreign_key: true   |

## Association

- belongs_to :order
