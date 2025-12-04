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
