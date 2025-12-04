# ProgramSederhana_SewaPS
# Muhamad Wafa Mufida Zulfi
# 312410334
# Teknik Informatika
# Universitas Pelita bangsa

## Pembahasan
Program penyewaan PlayStation ini dibuat menggunakan bahasa Python dan berjalan dalam mode console/terminal. Program ini dirancang untuk mempermudah proses administrasi penyewaan PS, mulai dari input data penyewa hingga penyimpanan riwayat transaksi

### 1. Bagian Penyimpanan Data

```python
# Daftar harga sewa per jam
harga_ps = {
    1: ("PS3", 7000),
    2: ("PS4", 10000),
    3: ("PS5", 15000)
```

 Ini adalah *dictionary*.
 
 Setiap angka *1,2,3* adalah pilihan menu.
 
 Setiap nilai berupa tuple:
 
 "PS3" → nama PS
 
 7000 → harga sewa per jam

### 2. Variable Riwayat
```python
# List untuk menyimpan riwayat transaksi
riwayat = []
```

Ini adalah list untuk menyimpan transaksi sebelum dikirim ke file.

### 3. Fungsi Menu Ps
```python
def menu_ps():
    print("\n=== PILIHAN JENIS PLAYSTATION ===")
    for key, value in harga_ps.items():
        print(f"{key}. {value[0]} - Rp{value[1]}/jam")
```
Menampilkan daftar PS beserta harga sewanya.

for key, value in harga_ps.items() digunakan untuk membaca dictionary.

### 4. Fungsi Sewa Ps
```python
def sewa_ps():
    print("\n=== INPUT DATA PENYEWA ===")
    nama = input("Nama penyewa: ")

    # Menampilkan menu PS
    menu_ps()
    pilihan = int(input("Pilih jenis PS (1/2/3): "))

    if pilihan not in harga_ps:
        print("Pilihan tidak valid!")
        return

    jenis_ps, harga_per_jam = harga_ps[pilihan]

    durasi = int(input("Durasi sewa (jam): "))
    total = durasi * harga_per_jam

    # Simpan transaksi
    transaksi = f"{nama} | {jenis_ps} | {durasi} jam | Total: Rp{total}"
    riwayat.append(transaksi)

    # Simpan ke file
    with open("riwayat_ps.txt", "a") as file:
        file.write(transaksi + "\n")
```

### 5. Tampilan Riwayat
```python
def tampilkan_riwayat():
    print("\n=== RIWAYAT TRANSAKSI ===")
    try:
        with open("riwayat_ps.txt", "r") as file:
            data = file.read()
            print(data if data else "Belum ada transaksi.")
    except FileNotFoundError:
        print("Belum ada riwayat.")
```
* Membaca file riwayat

* Menampilkan semua data transaksi

Jika file belum ada → akan muncul pesan Belum ada riwayat.

### 6. Program Utama (LoopMenu)
```python
while True:
    print("=== PROGRAM PENYEWAAN PLAYSTATION ===")
    print("1. Sewa PS")
    print("2. Lihat Riwayat Transaksi")
    print("3. Keluar")
```
* Menu akan terus berulang
  
* Pengguna memilih fitur
  
* Jika menekan *3*, program berhenti

## Seluruh Kodingannya
```python
# Program Sederhana Penyewaan PlayStation (PS)

# Daftar harga sewa per jam
harga_ps = {
    1: ("PS3", 7000),
    2: ("PS4", 10000),
    3: ("PS5", 15000)
}

# List untuk menyimpan riwayat transaksi
riwayat = []

def menu_ps():
    print("\n=== PILIHAN JENIS PLAYSTATION ===")
    for key, value in harga_ps.items():
        print(f"{key}. {value[0]} - Rp{value[1]}/jam")

def sewa_ps():
    print("\n=== INPUT DATA PENYEWA ===")
    nama = input("Nama penyewa: ")

    # Menampilkan menu PS
    menu_ps()
    pilihan = int(input("Pilih jenis PS (1/2/3): "))

    if pilihan not in harga_ps:
        print("Pilihan tidak valid!")
        return

    jenis_ps, harga_per_jam = harga_ps[pilihan]

    durasi = int(input("Durasi sewa (jam): "))
    total = durasi * harga_per_jam

    # Simpan transaksi
    transaksi = f"{nama} | {jenis_ps} | {durasi} jam | Total: Rp{total}"
    riwayat.append(transaksi)

    # Simpan ke file
    with open("riwayat_ps.txt", "a") as file:
        file.write(transaksi + "\n")

    print("\n=== STRUK PEMBAYARAN ===")
    print(f"Nama Penyewa : {nama}")
    print(f"Jenis PS     : {jenis_ps}")
    print(f"Durasi       : {durasi} jam")
    print(f"Total Bayar  : Rp{total}")
    print("=============================\n")

def tampilkan_riwayat():
    print("\n=== RIWAYAT TRANSAKSI ===")
    try:
        with open("riwayat_ps.txt", "r") as file:
            data = file.read()
            print(data if data else "Belum ada transaksi.")
    except FileNotFoundError:
        print("Belum ada riwayat.")

# Menu utama
while True:
    print("=== PROGRAM PENYEWAAN PLAYSTATION ===")
    print("1. Sewa PS")
    print("2. Lihat Riwayat Transaksi")
    print("3. Keluar")

    pilih = input("Pilih menu (1/2/3): ")

    if pilih == "1":
        sewa_ps()
    elif pilih == "2":
        tampilkan_riwayat()
    elif pilih == "3":
        print("Program selesai. Terima kasih!")
        break
    else:
        print("Pilihan tidak valid!")
```

✔ Program bisa menyewa PS

✔ Menghitung total biaya otomatis

✔ Menampilkan struk

✔ Menyimpan riwayat ke file

✔ Bisa dibuka kapan saja
