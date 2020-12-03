# DB 設計

## users table

| Column       | Type   | Options     |
| -------------| ------ | ----------- |
| nickname     | string | null: false |
| email        | string | null: false |
| password     | string | null: false |
| name         | string | null: false |
| birthday     | string | null: false |

### Association

* has_many :messages
* has_many :address



## items table

| Column         | Type       | Options           |
|----------------|------------|-------------------|
| name           | string     | null: false       |
| price          | text       | null: false       |
| postage        | text       | null: false       |
| user           | references | foreign_key: true |

### Association

- belongs_to :user 
- has_many :address



## orders table

| Column      | Type       | Options           |
|-------------|------------|-------------------|
| text        | text       | null: false       |
| item        | reference  | foreign_key: true |
| user        | references | foreign_key: true |

## Association

- belongs_to :
- belongs_to :user
