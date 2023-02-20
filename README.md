# テーブル設計

## users　テーブル

| Column             | Type   | Options                   |
| ------------------ | ------ | ------------------------- |
| name               | string | null: false               |
| email              | string | null: false, unique: true |
| encrypted_password | string | null: false               |

### Association

- has_many :diaries
- has_many :favorites

## diaries　テーブル

| Column             | Type       | Options                        |
| ------------------ | ---------- | ------------------------------ |
| title              | string     | null: false                    |
| good_thing         | text       | null: false                    |
| not_good           | text       | null: false                    |
| things_to_do       | text       | null: false                    |
| goal               | text       | null: false                    |
| image              | text       | null: false                    |
| day                | text       | null: false                    |
| genre_id           | integer    | null: false                    |

### Association

- belongs_to :user
- belongs_to :category


## favorites テーブル

| Column             | Type       | Options                        |
| ------------------ | ---------- | ------------------------------ |
| user               | references | null: false, foreign_key: true |
| dairy              | references | null: false, foreign_key: true |

### Association

- belongs_to :user
- belongs_to :diary


## categories テーブル

| Column             | Type       | Options                        |
| ------------------ | ---------- | ------------------------------ |
| dairy              | references | null: false, foreign_key: true |

### Association

- has_many :diaries
