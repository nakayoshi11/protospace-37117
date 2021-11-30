users テーブル

| Column             | Type   | Options     |
| ------------------ | ------ | ----------- |
| email              | string | null: false | ユニーク制約
| encrypted_password | string | null: false |
| name               | string | null: false |
| profile            | text   | null: false |
| occupation         | text   | null: false |
| position           | text   | null: false |


prototypesテーブル

| Column             | Type      | Options     |
| ------------------ | ------    | ----------- |
| title              | string    | null: false |
| catch_copy         | text      | null: false |
| concept            | text      | null: false |
| user               | references| null: false | 外部キー

※imageはActiveStorageで実装するため含まない


commentsテーブル

| Column             | Type      | Options     |
| ------------------ | ------    | ----------- |
| content            | text      | null: false |
| prototype          | references| null: false | 外部キー
| user               | references| null: false | 外部キー


user 単 ー 多 prototypesテーブル
  単            単
  |             |
  多            多
  commentsテーブル


データベースを消す方法
１，ロールバックで一つづつ直していく
　rails db:migrate, rails db:migrate:status

２，データベースごと一旦削除して、直接マイグレーションファイルを消す