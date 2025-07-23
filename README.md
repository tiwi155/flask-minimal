# flask-minimal

Sebuah proyek awal Flask minimal yang dirancang untuk membantumu dengan cepat menyiapkan aplikasi web yang bersih, sederhana, dan efisien. Proyek ini disusun agar tetap ringan dan fokus pada produktivitas, dengan seluruh kodenya berada dalam satu file (app.py), serta dilengkapi dengan template dasar dan aset statis.


## Fitur
- Single-file Flask application (`app.py`) untuk memaksimalkan produktivitas dan kesederhanaan.
- Struktur template HTML dasar dengan minimal styling dan JavaScript.
- Penyiapan proyek yang sederhana dan intuitif tanpa kompleksitas yang tidak perlu
- Mudah disesuaikan untuk pengembangan aplikasi web secara cepat.

## Persiapan
```bash
sudo apt update
sudo apt install python3 python3-venv python3-pip -y
```

## Installasi

1. Clone repository-nya:
   ```bash
   git clone https://github.com/yourusername/flask-minimal.git
   cd flask-minimal
   ```

2. Buat virtual environment (direkomendasikan):
   ```bash
   python3 -m venv venv
   source venv/bin/activate
   ```

3. Install dependesi yang diperlukan:
   ```bash
   pip install -r requirements.txt
   ```

4. Jalankan aplikasinya:
   ```bash
   python app.py
   ```

Aplikasi Flask akan berjalan, dan kita bisa melihatnya dengan membuka alamat http://localhost:5000 di browser atau jika menggunakan aws http://ippublikmu:5000.

## Cara Otomatisasi
Reboot Instancenya dan jalankan lagi instancenya menggunakan perintah seperti yang dibawah ini:

1. Clone repo sekali saja
Login ke server AWS kamu, lalu jalankan:
```bash
cd /home/ubuntu
git clone https://github.com/tiwi155/flask-minimal.git
```
2. Buat virtual environment dan install dependencies
```bash
cd flask-minimal
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
deactivate
```
3. Buat script startup (opsional, bisa langsung systemd)
```bash
#!/bin/bash
source /home/ubuntu/flask-minimal/venv/bin/activate
cd /home/ubuntu/flask-minimal
exec python app.py
```
Beri izin eksekusi:
```bash
chmod +x /home/ubuntu/flask-minimal/start.sh
```

4. Buat service systemd
Buat file ``` sudo nano /etc/systemd/system/flask-minimal.service ```

Masukkan ini Ke dalam filenya
```bash
[Unit]
Description=Flask Minimal App
After=network.target

[Service]
User=ubuntu
WorkingDirectory=/home/ubuntu/flask-minimal
ExecStart=/home/ubuntu/flask-minimal/venv/bin/python /home/ubuntu/flask-minimal/app.py
Restart=always

[Install]
WantedBy=multi-user.target
```
5. Aktifkan dan jalankan service
```bash
sudo systemctl daemon-reload
sudo systemctl enable flask-minimal.service
sudo systemctl start flask-minimal.service
```
6. Cek status dan log
```bash
sudo systemctl status flask-minimal.service
sudo journalctl -u flask-minimal.service -f
```

## Penggunaan

Setelah semua dependensi terinstal dan aplikasi Flask dijalankan, kamu dapat mulai mengembangkan aplikasi web-mu. Edit app.py untuk menambahkan route, logika, atau koneksi ke database sesuai kebutuhan. File template HTML dapat dimodifikasi di folder templates/, dan aset seperti CSS atau JavaScript dapat ditambahkan ke folder static/.

## Kustomisasi
Kita dapat dengan mudah merubah:

 - HTML struktur di `templates/index.html`
 - Style interface di `static/style.css`
 - Interactivity di `static/script.js`

Silakan ubah file app.py untuk menambahkan route atau logika tambahan lainnya sesuai kebutuhanmu.

## Lisensi
Proyek ini dilisensikan di bawah Lisensi MIT.

## Kontribusi
Silakan fork repositori ini dan buat pull request jika kamu memiliki perbaikan atau peningkatan. Jika kamu punya saran, buka issue dan kita akan mendiskusikannya!



Proyek ini dibuat dengan mengutamakan kesederhanaan dan efisiensi, sangat cocok untuk memulai aplikasi web kecil atau prototipe dengan cepat dan tanpa beban yang berlebihan.

