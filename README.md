# Tugas Mandiri 2

**Nama :** Naila Islamiyati

**NIM :** 1251170037

**Mata Kuliah :** Algoritma dan Struktur Data

   
## 1. Analisis Komponen

### Variabel dan Tipe Data

| Variabel | Tipe Data | Keterangan |
|---|---|---|
| `is_member` | Boolean | Menunjukkan status keanggotaan pelanggan. Status keanggotaan hanya memiliki dua kemungkinan, yaitu `True` atau `False`, sehingga menggunakan tipe data boolean. |
| `jumlah_buku` | Integer | Menunjukkan jumlah buku yang dibeli oleh pelanggan. Jumlah buku berupa bilangan bulat, sehingga menggunakan tipe data integer. |
| `total_awal` | Real | Menunjukkan total belanja sebelum diskon. Nilai total belanja dapat berupa angka desimal, sehingga menggunakan tipe data real. |
| `nominal_diskon` | Real | Menunjukkan hasil perhitungan jumlah nominal diskon dari `total_awal`. Hasil perhitungan persentase diskon berpotensi menghasilkan angka desimal, sehingga menggunakan tipe data real. |
| `total_bayar` | Real | Menunjukkan total harga setelah dikurangi `nominal_diskon`. Nilai tersebut berasal dari perhitungan `total_awal - nominal_diskon`, sehingga menggunakan tipe data real. |

### Jenis Struktur Kontrol yang Dipakai

| Struktur Kontrol | Keterangan |
|---|---|
| **Sekuensial** | Algoritma program berjalan berurutan baris demi baris dari atas ke bawah. |
| **Perulangan (`WHILE LOOP`)** | Sistem wajib melakukan validasi terhadap `total_awal` dan `jumlah_buku`. Loop akan berjalan ketika kondisi bernilai `True`, yaitu ketika `total_awal < 0` atau `jumlah_buku < 1`. |
| **Percabangan (`IF-THEN-ELSE`)** | Tingkat pertama mengecek `is_member`. Tingkat kedua bersarang di dalam masing-masing jalur: pada jalur member, mengecek `total_awal >= 200000` dan `jumlah_buku >= 3`, sedangkan pada jalur non-member, mengecek `total_awal >= 300000`. |
---

## 2. Penyusunan Pseudocode

```text
PROGRAM HitungTotalTransaksiDanValidasiDiTokoBukuModern

DEKLARASI:
    is_member : boolean
    jumlah_buku : integer
    total_awal : real
    nominal_diskon : real
    total_bayar : real

ALGORITMA:

    INPUT(total_awal)
    INPUT(jumlah_buku)

    WHILE (total_awal < 0) OR (jumlah_buku < 1) DO
        OUTPUT("Input tidak valid, silakan input ulang")
        INPUT(total_awal)
        INPUT(jumlah_buku)
    ENDWHILE
  UNTIL (total_awal >= 0) AND (jumlah_buku >= 1)

    INPUT(is_member)

    IF (is_member = true) THEN
        IF (total_awal >= 200000) AND (jumlah_buku >= 3) THEN
            nominal_diskon ← total_awal * 0.15
        ELSE
            nominal_diskon ← total_awal * 0.10
        ENDIF
    ELSE
        IF (total_awal >= 300000) THEN
            nominal_diskon ← total_awal * 0.05
        ELSE
            nominal_diskon ← 0
        ENDIF
    ENDIF

    total_bayar ← total_awal - nominal_diskon

    OUTPUT(nominal_diskon)
    OUTPUT(total_bayar)

END PROGRAM
```

---

## 3. Uji Logika / Trace Table

### Kasus A

| No | Langkah | `is_member` | `total_awal` | `jumlah_buku` | `nominal_diskon` | `total_bayar` |
|---:|---|---|---:|---:|---:|---:|
| 1 | Input Data | - | 250000 | 4 | - | - |
| 2 | Cek Validasi → Valid | - | 250000 | 4 | - | - |
| 3 | Input Status Member | True | 250000 | 4 | - | - |
| 4 | Cek Syarat Diskon 15% → Terpenuhi | True | 250000 | 4 | 37500 | - |
| 5 | Hitung Total Bayar | True | 250000 | 4 | 37500 | 212500 |

**Hasil:**
- Nominal diskon = **Rp37.500**
- Total bayar = **Rp212.500**

### Kasus B

| No | Langkah | `is_member` | `total_awal` | `jumlah_buku` | `nominal_diskon` | `total_bayar` |
|---:|---|---|---:|---:|---:|---:|
| 1 | Input Data | - | 350000 | 2 | - | - |
| 2 | Cek Validasi → Valid | - | 350000 | 2 | - | - |
| 3 | Input Status Member | False | 350000 | 2 | - | - |
| 4 | Cek Syarat Diskon 5% → Terpenuhi | False | 350000 | 2 | 17500 | - |
| 5 | Hitung Total Bayar | False | 350000 | 2 | 17500 | 332500 |

**Hasil:**
- Nominal diskon = **Rp17.500**
- Total bayar = **Rp332.500**

### Kasus C

**Input awal:** `total_awal = -50000` sehingga data tidak valid dan harus dikoreksi menjadi `total_awal = 100000`.

| No | Langkah | `is_member` | `total_awal` | `jumlah_buku` | `nominal_diskon` | `total_bayar` |
|---:|---|---|---:|---:|---:|---:|
| 1 | Input Data | - | -50000 | 1 | - | - |
| 2 | Cek Validasi → Tidak Valid | - | -50000 | 1 | - | - |
| 3 | Input Ulang Data → Dikoreksi | - | 100000 | 1 | - | - |
| 4 | Cek Validasi → Valid | - | 100000 | 1 | - | - |
| 5 | Input Status Member | False | 100000 | 1 | - | - |
| 6 | Cek Syarat Diskon 5% → Tidak Terpenuhi | False | 100000 | 1 | 0 | - |
| 7 | Hitung Total Bayar | False | 100000 | 1 | 0 | 100000 |

**Hasil:**
- Nominal diskon = **Rp0**
- Total bayar = **Rp100.000**
