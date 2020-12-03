# DB 設計

## users table

| Column               | Type   | Options     |
| ---------------------| ------ | ----------- |
| nickname             | string | null: false |
| email                | string | null: false |
| password             | string | null: false |
| encrypted_password   | string | null: false |
| first_name           | string | null: false |
| last_name            | string | null: false |
| birthday             | date   | null: false |

### Association

* has_many :messages
* has_many :address



## items table

| Column         | Type       | Options           |
|----------------|------------|-------------------|
| name           | string     | null: false       |
| price          | integer    | null: false       |
| detail-item    | string     | null: false       |
| detail-value   | string     | null: false       |
| weight-bold    | text       | null: false       |
| sell           | text       | null: false       |
| postage        | text       | null: false       |
| user           | references | foreign_key: true |

### Association

- belongs_to :user 
- has_many :address



## orders table

| Column      | Type       | Options           |
|-------------|------------|-------------------|
| item        | reference  | foreign_key: true |
| user        | references | foreign_key: true |

## Association

- belongs_to :item
- belongs_to :user


## address table

| Column             | Type       | Options           |
|--------------------|------------|-------------------|
| postal-code        | reference  | foreign_key: true |
| prefecture         | reference  | foreign_key: true |
| city               | reference  | foreign_key: true |
| house number       | reference  | foreign_key: true |
| building-name      | reference  | foreign_key: true |
| user               | references | foreign_key: true |

## Association

- belongs_to :user
- belongs_to :item
- belongs_to :order
