# 友達マッチングアプリ

## 概要

SNSで繋がりたい人同士をマッチングするカジュアルなサービス

## 使用技術

- Frontend: React
- Backend: Java (SpringBoot)
- DB: MySQL
- インフラ: Docker / AWS

## 機能一覧

### 必須機能

- ユーザー登録・ログイン
- プロフィール作成・編集
- いいね・マッチング機能
- メッセージ機能

### 追加機能

- タグ・趣味での絞り込み検索
- 通知機能

## ER図

## ER図

```mermaid
erDiagram
  users ||--|| profiles : has
  users ||--o{ likes : sends
  users ||--o{ likes : receives
  users ||--o{ matches : joins
  users ||--o{ user_tags : has
  matches ||--o{ chats : contains
  tags ||--o{ user_tags : categorizes

  users {
    bigint id PK
    string email
    string password_hash
    timestamp created_at
  }

  profiles {
    bigint id PK
    bigint user_id FK
    string name
    int age
    string bio
    string twitter_id
    string instagram_id
    timestamp updated_at
  }

  likes {
    bigint id PK
    bigint from_user_id FK
    bigint to_user_id FK
    timestamp created_at
  }

  matches {
    bigint id PK
    bigint user1_id FK
    bigint user2_id FK
    timestamp matched_at
  }

  chats {
    bigint id PK
    bigint match_id FK
    bigint sender_id FK
    text content
    timestamp sent_at
  }

  tags {
    bigint id PK
    string name
  }

  user_tags {
    bigint user_id FK
    bigint tag_id FK
  }
```

## 画面設計

（後で追加）
