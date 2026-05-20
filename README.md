# Auth CRUD API

REST API sederhana untuk autentikasi dan manajemen user menggunakan Node.js, Express, MySQL, dan JWT.

## Tech Stack

- Node.js + Express
- MySQL2
- JSON Web Token (JWT)
- bcryptjs
- dotenv

## Instalasi

```bash
npm install
```

Buat file `.env` di root project:

```env
PORT=3000
DB_HOST=localhost
DB_USER=root
DB_PASSWORD=
DB_NAME=nama_database
```

Buat tabel `users` di MySQL:

```sql
CREATE TABLE users (
  id INT AUTO_INCREMENT PRIMARY KEY,
  name VARCHAR(100),
  email VARCHAR(100) UNIQUE,
  password VARCHAR(255)
);
```

Jalankan server:

```bash
npm start
```

## API Endpoints

| Method | Endpoint | Auth | Deskripsi |
|--------|----------|------|-----------|
| POST | `/api/register` | ❌ | Register user baru |
| POST | `/api/login` | ❌ | Login dan dapat token |
| GET | `/api/users` | ✅ | Ambil semua user |
| GET | `/api/users/:id` | ✅ | Ambil user by ID |
| PUT | `/api/users/:id` | ✅ | Update nama & email |
| PUT | `/api/change-password/:id` | ✅ | Ganti password |
| DELETE | `/api/users/:id` | ✅ | Hapus user |

> Endpoint yang butuh auth, tambahkan header: `Authorization: Bearer <token>`

## Contoh Request

### Register
```json
POST /api/register
{
  "name": "John Doe",
  "email": "john@example.com",
  "password": "password123"
}
```

### Login
```json
POST /api/login
{
  "email": "john@example.com",
  "password": "password123"
}
```

### Change Password
```json
PUT /api/change-password/:id
{
  "oldPassword": "password123",
  "newPassword": "newpassword456"
}
```
