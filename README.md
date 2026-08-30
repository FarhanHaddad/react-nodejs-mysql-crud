# User Management CRUD

Aplikasi web sederhana untuk mengelola data pengguna (*Create, Read, Update,* dan *Delete*). Pengguna dapat melihat daftar pengguna, menambah data baru, mengubah data, serta menghapus data setelah menyetujui konfirmasi penghapusan.

Frontend berjalan pada `http://localhost:3000` dan mengambil data dari REST API backend pada `http://localhost:5000`.

## Fitur

- Menampilkan daftar pengguna.
- Menambahkan pengguna baru.
- Mengubah data pengguna.
- Menghapus pengguna dengan dialog konfirmasi.
- Membatalkan pengisian form dan kembali ke daftar pengguna.

## Teknologi yang digunakan

| Bagian | Teknologi | Kegunaan |
| --- | --- | --- |
| Frontend | React | Membangun antarmuka pengguna berbasis komponen. |
| Routing | React Router DOM | Navigasi antarhalaman aplikasi. |
| HTTP client | Axios | Mengirim request dari frontend ke REST API. |
| UI | Bulma | Menyediakan class CSS untuk tata letak dan komponen. |
| Backend | Node.js dan Express | Menyediakan REST API. |
| ORM | Sequelize | Mengakses dan mengelola data MySQL dari Node.js. |
| Database | MySQL | Menyimpan data pengguna. |

## Prasyarat

Pastikan perangkat sudah memiliki:

- [Node.js](https://nodejs.org/) versi LTS (sudah termasuk npm).
- MySQL Server, misalnya melalui XAMPP atau MySQL Community Server.

## Instalasi

Clone atau salin proyek ini, lalu buka dua terminal: satu untuk backend dan satu untuk frontend.

### 1. Siapkan database

Jalankan MySQL, lalu buat database berikut melalui phpMyAdmin atau MySQL CLI:

```sql
CREATE DATABASE crud_db;
```

Backend menggunakan konfigurasi berikut di `backend/config/Database.js`:

```js
new Sequelize("crud_db", "root", "", {
  host: "localhost",
  dialect: "mysql",
});
```

Sesuaikan nama database, username, atau password pada file tersebut jika konfigurasi MySQL Anda berbeda. Tabel `users` akan disinkronkan oleh Sequelize saat backend dijalankan.

### 2. Instal dan jalankan backend

Di terminal pertama:

```bash
cd backend
npm install
node index.js
```

Jika ingin server otomatis *restart* saat kode berubah, instal dan gunakan Nodemon:

```bash
npm install --save-dev nodemon
npx nodemon index.js
```

Saat berhasil berjalan, backend tersedia pada `http://localhost:5000`.

> Pada Windows PowerShell, jika perintah `npm` ditolak karena *execution policy*, gunakan `npm.cmd` sebagai pengganti, misalnya `npm.cmd install`.

### 3. Instal dan jalankan frontend

Di terminal kedua:

```bash
cd frontend
npm install
npm start
```

Buka [http://localhost:3000](http://localhost:3000) di browser.

## Endpoint REST API

| Method | Endpoint | Keterangan |
| --- | --- | --- |
| `GET` | `/users` | Mengambil semua pengguna. |
| `GET` | `/users/:id` | Mengambil satu pengguna berdasarkan ID. |
| `POST` | `/users` | Menambah pengguna. |
| `PATCH` | `/users/:id` | Memperbarui pengguna. |
| `DELETE` | `/users/:id` | Menghapus pengguna. |

Contoh body untuk `POST` atau `PATCH`:

```json
{
  "name": "John Doe",
  "email": "john@example.com",
  "gender": "Male"
}
```

File `backend/request.rest` juga tersedia untuk mencoba endpoint melalui ekstensi REST Client di VS Code.

## Screenshot

### Daftar pengguna

![Halaman daftar pengguna](screenshot/List%20User.png)

### Form tambah pengguna

![Form tambah pengguna](screenshot/form%20add.png)

### Form edit pengguna

![Form edit pengguna](screenshot/form%20edit.png)

### Konfirmasi hapus pengguna

![Konfirmasi hapus pengguna](screenshot/aksi%20delete.png)
