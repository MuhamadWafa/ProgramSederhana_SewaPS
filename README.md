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

