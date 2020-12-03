# DB 設計

## users table

| Column               | Type   | Options     |
| ---------------------| ------ | ----------- |
| nickname             | string | null: false |
| email                | string | null: false |
| encrypted_password   | string | null: false |
| first_name           | string | null: false |
| first_name-kana      | string | null: false |
| last_name            | string | null: false |
| last_name-kana       | string | null: false |
| birthday             | date   | null: false |

### Association

* has_many :messages
* has_many :address
* has_many :item



## items table

| Column              | Type       | Options           |
|---------------------|------------|-------------------|
| name                | string     | null: false       |
| price               | integer    | null: false       |
| detail_item         | string     | null: false       |
| detail_value        | string     | null: false       |
| weight-bold-text    | text       | null: false       |
| item-sell           | text       | null: false       |
| postage             | text       | null: false       |
| user                | references | foreign_key: true |

### Association

- belongs_to :user 
* has_many :address
* has_many :order



## orders table

| Column      | Type       | Options           |
|-------------|------------|-------------------|
| item        | reference  | foreign_key: true |
| user        | references | foreign_key: true |

## Association

- belongs_to :item
- belongs_to :user
- belongs_to :address


## address table

| Column             | Type       | Options           |
|--------------------|------------|-------------------|
| postal-code        | reference  | foreign_key: true |
| prefecture         | reference  | foreign_key: true |
| city               | reference  | foreign_key: true |
| house number       | reference  | foreign_key: true |
| building-name      | reference  | foreign_key: true |
| order              | references | foreign_key: true |

## Association

- belongs_to :user
- belongs_to :item
- belongs_to :order
