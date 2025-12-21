🚀 Setup Backend TodoList (Node.js + Prisma)

1️⃣ Cài dependency
npm install

2️⃣ Cài & khởi tạo Prisma
npx prisma init

👉 Lệnh này sẽ tạo:

prisma/
└─ schema.prisma

👉 Đồng thời sinh file .env với nội dung dạng:

DATABASE_URL="mysql://user:pass@localhost:3306/todolist"

⚠️ Nhớ sửa user, pass, todolist cho đúng DB của bạn

3️⃣ Tạo schema Todo (QUAN TRỌNG)

Mở file:

prisma/schema.prisma

Ví dụ:

model Todo {
id Int @id @default(autoincrement())
title String
completed Boolean @default(false)
createdAt DateTime @default(now())
}

4️⃣ Migrate database & generate Prisma Client
npx prisma migrate dev --name init
npx prisma generate

👉 Kết quả:

Database được tạo bảng Todo

Prisma Client sẵn sàng dùng trong code

✅ Kiểm tra database (tuỳ chọn)
npx prisma studio

Mở browser để xem & sửa dữ liệu trực tiếp.

📌 Done!
Giờ bạn có thể:

Viết API CRUD Todo
