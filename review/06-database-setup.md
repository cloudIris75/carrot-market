# 06 Database Setup

## Prisma

1. Install and run _Prisma_.

```
npm i prisma -D
npx prisma init
```

2. Set the _DATABASE_URL_ in the _.env_ file.
3. Set the _provider_ of the _datasource_ block in _schema.prisma_.

```prisma
// prisma/schema.prisma
generator client {
  provider        = "prisma-client-js"
  previewFeatures = ["referentialIntegrity"]
}

datasource db {
  provider             = "mysql"
  url                  = env("DATABASE_URL")
  referentialIntegrity = "prisma"
}

model User {
  id              Int         @id @default(autoincrement())
  phone           String?     @unique
  email           String?     @unique
  name            String
  avatar          String?
  createdAt       DateTime    @default(now())
  updatedAt       DateTime    @updatedAt
  tokens          Token[]
  products        Product[]
  posts           Post[]
  answers         Answer[]
  wonderings      Wondering[]
  writtenReviews  Review[]    @relation(name: "writtenReviews")
  receivedReviews Review[]    @relation(name: "receivedReviews")
  fav             Fav[]
  sales           Sale[]
  purchases       Purchase[]
  record          Record[]
  streams         Stream[]
  messages        Message[]
}

model Token {
  id        Int      @id @default(autoincrement())
  payload   String   @unique
  user      User     @relation(fields: [userId], references: [id], onDelete: Cascade)
  userId    Int
  createdAt DateTime @default(now())
  updatedAt DateTime @updatedAt

  @@index([userId])
}
```

4. Run _prisma db pull_.

```
npx prisma db pull
```

5. Run _prisma generate_.

```
npx prisma generate
```

6. Run _Prisma Studio_.

```
npx prisma studio
```
