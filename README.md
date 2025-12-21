# 🚀 Setup Backend TodoList (Node.js + Prisma + PostgreSQL + Docker)

## 0️⃣ Yêu cầu

- Node.js >= 18
- Docker & Docker Compose
- npm

## 1️⃣ Khởi động Database bằng Docker

### Chạy database

```bash
docker compose up -d
```

### Kiểm tra container

```bash
docker ps
```

## 2️⃣ Cài dependency

```bash
npm install
```

## 3️⃣ Cài & khởi tạo Prisma

```bash
npx prisma init
```

👉 Lệnh này sẽ tạo:

```
prisma/
└─ schema.prisma
```

👉 Đồng thời sinh file `.env`

### Sửa .env cho đúng PostgreSQL (QUAN TRỌNG)

```env
DATABASE_URL="postgresql://todolist_user:todolist_pass@localhost:5432/todolist_db"
```

⚠️ KHÔNG dùng mysql URL vì project đang chạy Postgres bằng Docker.

## 4️⃣ Tạo schema Todo (QUAN TRỌNG)

### Mở file: `prisma/schema.prisma`

Ví dụ:

```prisma
model Todo {
    id        Int      @id @default(autoincrement())
    title     String
    completed Boolean  @default(false)
    createdAt DateTime @default(now())
    updatedAt DateTime @updatedAt
}
```

## 5️⃣ Migrate database & generate Prisma Client

```bash
npx prisma migrate dev --name init
npx prisma generate
```

👉 Kết quả:
- Database tạo bảng Todo
- Prisma Client sẵn sàng dùng trong code

## 6️⃣ Kiểm tra database (tuỳ chọn)

```bash
npx prisma studio
```

👉 Mở browser để xem & chỉnh sửa dữ liệu trực tiếp.

## 7️⃣ Chạy backend

```bash
npm run dev
```

Server mặc định: `http://localhost:3000`

## 📌 Done!

Giờ bạn có thể:

- ✅ Viết API CRUD Todo
- 🔗 Kết nối Flutter / React frontend
- 🔐 Mở rộng User + JWT Auth
- 📦 Docker hoá luôn backend
