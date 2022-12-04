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
- has_many :orders




## itemsテーブル

| Column            | Type       | Options                        |
| ----------------- | -----------| ------------------------------ |
| name              | string     | null: false                    |
| description       | text       | null: false                    |
| category_id       | integer    | null: false                    |
| status_id         | integer    | null: false                    |
| cost_id           | integer    | null: false                    |
| area_id           | integer    | null: false                    |
| days_id           | integer    | null: false                    |
| price             | integer    | null: false                    |
| user              | references | null: false, foreign_key: true |


### Association

- belongs_to :user
- has_many :comments
- has_one :order




## ordersテーブル

| Column             | Type       | Options                        |
| ------------------ | ---------- | ------------------------------ |
| user            | references | null: false, foreign_key: true |
| item            | references | null: false, foreign_key: true |


### Association

- belongs_to :user
- belongs_to :item
- has_one :destination




## destination

| Column                | Type       | Options                        |
| --------------------- | ---------- | ------------------------------ |
| post_code             | integer    | null: false                    |
| prefecture            | string     | null: false                    |
| city                  | string     | null: false                    |
| address               | string     | null: false                    |
| building              | string     | null: false                    |


### Association

- belongs_to :order


## commentsテーブル

| Column       | Type          | Options                          |
| ------------ | ------------- | -------------------------------- |
| content      | string        |                                  |
| user_id      | references    | null: false, foreign_key: true   |
| item_id      | references    | null: false, foreign_key: true   |


### Association

- belongs_to :user
- belongs_to :item

