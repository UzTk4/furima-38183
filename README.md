# テーブル設計


## usersテーブル

| Column                | Type   | Options                    |
| --------------------- | ------ | -------------------------- |
| nickname              | string | null: false                |
| email                 | string | null: false, unique: true  |
| encrypted_password    | string | null: false                |
| last_name             | string | null: false                |
| first_name            | string | null: false                |
| last_name_kana        | string | null: false                |
| first_name_kana       | string | null: false                |
| birthday              | date   | null: false                |


### Association

- has_many :items
- has_many :comments
- has_one :order




## itemsテーブル

| Column            | Type       | Options                        |
| ----------------- | -----------| ------------------------------ |
| name              | string     | null: false                    |
| description       | text       | null: false                    |
| category          | string     | null: false, foreign_key: true |
| status            | string     | null: false, foreign_key: true |
| cost              | integer    | null: false, foreign_key: true |
| area              | string     | null: false, foreign_key: true |
| days              | string     | null: false, foreign_key: true |
| price             | integer    | null: false                    |
| commission        | integer    | null: false                    |
| profit            | integer    | null: false                    |
| user              | references | null: false, foreign_key: true |


### Association

- belongs_to :user
- has_many :comments
- has_one :order




## ordersテーブル

| Column                | Type       | Options                        |
| --------------------- | ---------- | ------------------------------ |
| card                  | integer    | null: false                    |
| expiration            | integer    | null: false, unique: true      |
| security_cord         | integer    | null: false                    |
| post_code             | integer    | null: false                    |
| prefecture            | string     | null: false                    |
| city                  | string     | null: false                    |
| address               | string     | null: false                    |
| building              | string     | null: false                    |
| user                  | references | null: false, foreign_key: true |
| item                  | references | null: false, foreign_key: true |


### Association

- belongs_to :user
- belongs_to :item




## commentsテーブル

| Column    | Type          | Options                          |
| --------- | ------------- | -------------------------------- |
| content   | string        |                                  |
| user      | references    | null: false, foreign_key: true   |
| item      | references    | null: false, foreign_key: true   |


### Association

- belongs_to :user
- belongs_to :item

