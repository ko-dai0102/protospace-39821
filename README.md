# テーブル設計

## users テーブル

| Column             | Type   | Options                   |
| ------------------ | ------ | --------------------------|
| email              | string | null: false, unique: true |
| encrypted_password | string | null: false               |
| name               | string | null: false               |
| profile            | text   | null: false               |
| occupation         | text   | null: false               |
| position           | text   | null: false               |

### Association

- has_many :prototypes
- has_many :comments

## prototypes テーブル

| Column      | Type       | Options                     |
| ----------- | ---------- | ----------------------------|
| title       | string     | not null                    |
| catch_copy  | text       | not null                    |
| concept     | text       | not null                    |
| user        | references | not null, foreign_key: true |

### Association

- belongs_to :users
- has_many :comments

## comments テーブル

| Column    | Type       | Options                     |
| ----------| ---------- | ----------------------------|
| content   | text       | not null                    |
| prototype | references | not null, foreign_key: true |
| user      | references | not null, foreign_key: true |

### Association

- belongs_to :users
- belongs_to :prototypes