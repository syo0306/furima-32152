# DB 設計

## users table

| Column               | Type   | Options     |
| ---------------------| ------ | ----------- |
| nickname             | string | null: false |
| email                | string | null: false |
| encrypted_password   | string | null: false |
| first_name           | string | null: false |
| first_name_kana      | string | null: false |
| last_name            | string | null: false |
| last_name_kana       | string | null: false |
| birthday             | date   | null: false |

### Association

* has_many :items



## items table

| Column                         | Type       | Options           |
|--------------------------------|------------|-------------------|
| name                           | string     | null: false       |
| price                          | integer    | null: false       |
| detail_item_id                 | string     | null: false       |
| detail_value_id                | string     | null: false       |
| weight-bold-text_id            | string     | null: false       |
| item-sell_id                   | string     | null: false       |
| postage-id                     | string     | null: false       |
| collection_select_id           | string     | null: false       |
| item-scheduled-delivery-id     | string     | null: false       |
| user                           | references | foreign_key: true |

### Association

- belongs_to :user 
* has_many :order



## orders table

| Column      | Type       | Options           |
|-------------|------------|-------------------|
| item        | reference  | foreign_key: true |
| user        | references | foreign_key: true |

## Association

- belongs_to :item
- belongs_to :user
- has_one :address


## address table

| Column             | Type        | Options             |
|--------------------|-------------|---------------------|
| prefecture_id      | integer     |                     |
| postal-code        | string      |                     |
| city               | string      |                     |
| address            | string      |                     |
| house number       | string      |                     |
| building           | string      |                     |
| order              | references  | foreign_key: true   |

## Association

- belongs_to :order
