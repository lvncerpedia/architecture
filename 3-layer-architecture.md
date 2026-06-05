# 3 層アーキテクチャ

```
[ プレゼンテーション層 ]  ← Frontend / Web
        ↕
[ ビジネスロジック層　 ]  ← Backend / API
        ↕
[ データ層           ]  ← Database
```

```
┌───────────────────────────────────┐
│ Presentation Layer                │
│                                   │
│  Browser / Mobile / Desktop / CLI │ <-------->
│                                   │
│  🍪 Cookie                        │
└──────────────┬────────────────────┘

│  🌐 Webサーバー (静的配信用)             │
│    └ Nginx, Apache, Vercel, Netlify      │
│      静的ファイル(HTML/CSS/JS)を返すだけ │
               │  HTTP / REST / GraphQL
               │  gRPC / WebSocket
               │  tRPC / SOAP / JSON-RPC
               ↕
┌──────────────┴───────────────────────────┐
│         ビジネスロジック層               │
│                                         │
│  🌐 Webサーバー (リバプロ・振り分け用)   │
│    └ Nginx, Apache, Caddy               │
│      └ バックエンドへのルーティング      │
│                                         │
│  [アプリサーバー]                        │
│  ┌────────────────────────────────────┐  │
│  │ JS/TS   : Node.js, Deno, Bun       │  │
│  │ Python  : Django, FastAPI, Flask   │  │
│  │ Java    : Spring Boot, Quarkus     │  │
│  │ Go      : Gin, Echo, Fiber         │  │
│  │ Ruby    : Rails, Sinatra           │  │
│  │ PHP     : Laravel, Symfony         │  │
│  └────────────────────────────────────┘  │
│                                         │
│  📦 DTO                                 │
│  ⚡ Redis (セッション・キャッシュ)       │
└──────────────┬───────────────────────────┘
               │  SQL / ORM / API
               ↕
┌──────────────┴───────────────────────────┐
│            データ層                      │
│                                         │
│  [RDB]          [NoSQL]     [ストレージ] │
│  MySQL          MongoDB      S3          │
│  PostgreSQL     Redis ※1    GCS         │
│  SQLite         Cassandra    Azure Blob  │
│  Oracle         DynamoDB                │
│  SQL Server     Firestore               │
└──────────────────────────────────────────┘
※1 永続化目的のRedis
```

<img width="300" src="https://static.zenn.studio/user-upload/daf385691e46-20241217.png">
