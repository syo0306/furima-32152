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

| Column                  | Type       | Options           |
|-------------------------|------------|-------------------|
| name                    | string     | null: false       |
| price                   | integer    | null: false       |
| detail_item             | text       | null: false       |
| detail_value            | string     | null: false       |
| weight-bold-text        | text       | null: false       |
| item-sell               | text       | null: false       |
| postage                 | text       | null: false       |
| collection_select       | text       | null: false       |
| item-scheduled-delivery | text       | null: false       |
| user                    | references | foreign_key: true |

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

| Column             | Type       | Options           |
|--------------------|------------|-------------------|
| prefecture_id      | integer    |                   |
| postal-code_id     | string     |                   |
| city_id            | string     |                   |
| address_id         | string     |                   |
| house number_id    | string     |                   |
| building_id        | string     |                   |
| order              | string     |                   |

## Association

- belongs_to :order
