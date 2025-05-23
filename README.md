# Module 10: Asynchronous Programming - Tutorial 2: Broadcast Chat

## Experiment 2.1: Original code, and how it run

Untuk menjalankan aplikasi chat ini, pertama-tama saya menjalankan server di satu terminal:
```bash
cargo run --bin server
```
Server akan menampilkan listening on port 2000.

Kemudian, saya membuka tiga terminal terpisah lainnya dan di masing-masing terminal saya menjalankan client:

```bash
cargo run --bin client
```

Masing-masing client akan menampilkan Welcome to chat! Type a message.

Setelah itu, saya mencoba mengetikkan pesan di salah satu client. Misalnya, saya mengetik Selamat pagi! di Client 1. Hasilnya adalah pesan tersebut akan broadcast ke semua client yang terhubung, dan server juga akan mencatat pesan yang diterima.

Berikut adalah screenshot yang menunjukkan server dan tiga client, dengan pesan yang sudah dikirim dan diterima oleh semua:

![alt text](ss1.png)

Penjelasan:
Aplikasi ini menunjukkan konsep broadcast chat menggunakan WebSocket. Ketika sebuah client mengirim pesan, pesan tersebut dikirim ke server melalui koneksi WebSocket. Server kemudian menerima pesan tersebut dan menyebarkannya kembali ke semua client lain yang terhubung. Ini memanfaatkan sifat asynchronous dari WebSocket di mana komunikasi dua arah (full-duplex) dapat terjadi secara real-time tanpa harus melakukan polling terus-menerus. Setiap client dan server secara asinkron menunggu dan memproses event (pesan masuk atau keluar).

