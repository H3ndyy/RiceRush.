# Rice Rush — Website + Backend

## Fitur backend
- Pendaftaran dan login menggunakan password yang di-hash dengan bcrypt.
- Sesi login memakai cookie `HttpOnly`.
- Data pengguna, pesanan, dan pesan kontak disimpan di SQLite (`rice-rush.sqlite`).
- Checkout wajib login; harga setiap menu diverifikasi di server.
- Riwayat pesanan tersedia melalui `GET /api/orders/mine`.

## Menjalankan di komputer
1. Install Node.js 18 atau lebih baru.
2. Buka terminal di folder `foodlandingpage-main`.
3. Jalankan `npm install`.
4. Salin `.env.example` menjadi `.env`, lalu ganti `SESSION_SECRET` dengan string rahasia yang panjang.
5. Jalankan `npm start`.
6. Buka `http://localhost:3000` di browser. Jangan membuka `index.html` langsung lewat `file://` karena frontend perlu mengakses API server.

## Catatan keamanan
- Ini adalah backend dasar untuk proyek belajar/lokal, bukan konfigurasi produksi yang sudah diaudit.
- Sebelum deploy, wajib mengatur `SESSION_SECRET` yang kuat, HTTPS, `NODE_ENV=production`, pembatasan percobaan login (rate limiting), perlindungan CSRF yang sesuai, backup database, dan session store persisten. `express-session` default MemoryStore tidak cocok untuk produksi.
- Pembayaran online belum terintegrasi; checkout hanya menyimpan pesanan, tidak menarik uang.
- Pesan Contact disimpan ke database. Belum ada pengiriman email atau panel admin.
- File `rice-rush.sqlite` dibuat otomatis saat server pertama kali dijalankan. Jangan menghapusnya jika ingin mempertahankan data.
