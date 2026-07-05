# -Kasir-Sederhana-OOP-CPP


---

# 📌 PROGRAM KASIR SEDERHANA - C++ OOP

---

# A. SYNTAX KODE LENGKAP (main.cpp)

```cpp
/*
===================================================
PROGRAM KASIR SEDERHANA - C++ OOP
===================================================
Fungsi :
- Input nama barang, harga, jumlah
- Hitung total belanja
- Beri diskon otomatis
- Tampilkan struk belanja

Dibuat oleh : Faris
Tanggal     : 25 Juni 2026
===================================================
*/

#include <iostream>
#include <iomanip>
using namespace std;

class Kasir {
private:
    string namaBarang;
    int harga;
    int jumlah;
    int total;
    double diskon;
    double totalBayar;

public:
    Kasir() {
        namaBarang = "";
        harga = 0;
        jumlah = 0;
        total = 0;
        diskon = 0;
        totalBayar = 0;
        cout << "==========================================" << endl;
        cout << "   🧾 PROGRAM KASIR SEDERHANA v1.0       " << endl;
        cout << "==========================================\n" << endl;
    }

    void inputData() {
        cout << "📦 Masukkan Nama Barang : ";
        cin.ignore();
        getline(cin, namaBarang);

        cout << "💰 Masukkan Harga       : Rp ";
        cin >> harga;

        cout << "🔢 Masukkan Jumlah      : ";
        cin >> jumlah;

        cout << endl;
    }

    int hitungTotal() {
        total = harga * jumlah;
        return total;
    }

    double hitungDiskon() {
        if (total >= 100000) {
            diskon = total * 0.10;
            cout << "🎉 Selamat! Anda mendapat diskon 10%" << endl;
        } else if (total >= 50000) {
            diskon = total * 0.05;
            cout << "🎉 Selamat! Anda mendapat diskon 5%" << endl;
        } else {
            diskon = 0;
            cout << "😊 Belum dapat diskon. Belanja minimal Rp50.000" << endl;
        }
        return diskon;
    }

    double hitungTotalBayar() {
        totalBayar = total - diskon;
        return totalBayar;
    }

    void tampilkanStruk() {
        cout << "\n==========================================" << endl;
        cout << "            🧾 STRUK BELANJA            " << endl;
        cout << "==========================================" << endl;
        cout << "  Nama Barang  : " << namaBarang << endl;
        cout << "  Harga Satuan : Rp " << harga << endl;
        cout << "  Jumlah       : " << jumlah << " buah" << endl;
        cout << "------------------------------------------" << endl;
        cout << "  Total        : Rp " << total << endl;
        cout << "  Diskon       : Rp " << diskon << endl;
        cout << "------------------------------------------" << endl;
        cout << "  TOTAL BAYAR  : Rp " << totalBayar << endl;
        cout << "==========================================" << endl;
        cout << "  Terima kasih sudah berbelanja! 🛒   " << endl;
        cout << "==========================================\n" << endl;
    }

    void proses() {
        inputData();
        hitungTotal();
        hitungDiskon();
        hitungTotalBayar();
        tampilkanStruk();
    }
};

int main() {
    Kasir kasir1;
    kasir1.proses();
    return 0;
}
```

---

B. PENJELASAN KODE (Terpisah)

1. Header dan Library

```cpp
#include <iostream>
#include <iomanip>
using namespace std;
```

· iostream → untuk input/output (cin, cout)
· iomanip → untuk formatting tampilan (opsional, bisa dipakai kalau mau bikin tabel)
· using namespace std → biar gak perlu nulis std:: setiap kali

---

2. Class Kasir

```cpp
class Kasir {
private:
    ...
public:
    ...
};
```

· Class adalah cetakan untuk membuat objek.
· private → data/property yang hanya bisa diakses dari dalam class (encapsulation).
· public → method/fungsi yang bisa diakses dari luar class.

---

3. Atribut (Private)

```cpp
private:
    string namaBarang;
    int harga;
    int jumlah;
    int total;
    double diskon;
    double totalBayar;
```

· namaBarang → nama barang (bisa pakai spasi)
· harga → harga satuan barang
· jumlah → jumlah barang yang dibeli
· total → total harga sebelum diskon
· diskon → nilai diskon dalam rupiah
· totalBayar → total yang harus dibayar setelah diskon

---

4. Constructor

```cpp
Kasir() {
    namaBarang = "";
    harga = 0;
    jumlah = 0;
    total = 0;
    diskon = 0;
    totalBayar = 0;
    cout << "==========================================" << endl;
    cout << "   🧾 PROGRAM KASIR SEDERHANA v1.0       " << endl;
    cout << "==========================================\n" << endl;
}
```

· Constructor adalah method yang otomatis dijalankan saat objek dibuat.
· Digunakan untuk memberi nilai awal (inisialisasi) ke semua atribut.
· Juga menampilkan header program.

---

5. Method inputData()

```cpp
void inputData() {
    cout << "📦 Masukkan Nama Barang : ";
    cin.ignore();
    getline(cin, namaBarang);

    cout << "💰 Masukkan Harga       : Rp ";
    cin >> harga;

    cout << "🔢 Masukkan Jumlah      : ";
    cin >> jumlah;

    cout << endl;
}
```

· cin.ignore() → membersihkan buffer agar getline() bisa membaca spasi.
· getline(cin, namaBarang) → membaca teks yang mengandung spasi.
· cin >> harga dan cin >> jumlah → input angka.

---

6. Method hitungTotal()

```cpp
int hitungTotal() {
    total = harga * jumlah;
    return total;
}
```

· Menghitung total belanja dengan rumus harga * jumlah.
· Hasil disimpan di atribut total dan dikembalikan.

---

7. Method hitungDiskon()

```cpp
double hitungDiskon() {
    if (total >= 100000) {
        diskon = total * 0.10;
        cout << "🎉 Selamat! Anda mendapat diskon 10%" << endl;
    } else if (total >= 50000) {
        diskon = total * 0.05;
        cout << "🎉 Selamat! Anda mendapat diskon 5%" << endl;
    } else {
        diskon = 0;
        cout << "😊 Belum dapat diskon. Belanja minimal Rp50.000" << endl;
    }
    return diskon;
}
```

· Logika diskon:
  · Total ≥ 100.000 → diskon 10%
  · Total ≥ 50.000 → diskon 5%
  · Total < 50.000 → tidak dapat diskon

---

8. Method hitungTotalBayar()

```cpp
double hitungTotalBayar() {
    totalBayar = total - diskon;
    return totalBayar;
}
```

· Menghitung total yang harus dibayar setelah dikurangi diskon.

---

9. Method tampilkanStruk()

```cpp
void tampilkanStruk() {
    cout << "\n==========================================" << endl;
    cout << "            🧾 STRUK BELANJA            " << endl;
    // ... (cetak semua data)
}
```

· Menampilkan struk belanja yang rapi dengan semua informasi.

---

10. Method proses()

```cpp
void proses() {
    inputData();
    hitungTotal();
    hitungDiskon();
    hitungTotalBayar();
    tampilkanStruk();
}
```

· Memanggil semua method secara berurutan.
· Memudahkan di main() karena cukup panggil proses() sekali.

---

11. Fungsi main()

```cpp
int main() {
    Kasir kasir1;
    kasir1.proses();
    return 0;
}
```

· Membuat objek kasir1 dari class Kasir.
· Memanggil method proses() untuk menjalankan seluruh program.

---

C. CONTOH OUTPUT PROGRAM

Input dari User:

```
📦 Masukkan Nama Barang : Buku Tulis
💰 Masukkan Harga       : Rp 5000
🔢 Masukkan Jumlah      : 25
```

Proses Diskon:

```
🎉 Selamat! Anda mendapat diskon 5%
```

Output Struk:

```
==========================================
   🧾 PROGRAM KASIR SEDERHANA v1.0       
==========================================

📦 Masukkan Nama Barang : Buku Tulis
💰 Masukkan Harga       : Rp 5000
🔢 Masukkan Jumlah      : 25

🎉 Selamat! Anda mendapat diskon 5%

==========================================
            🧾 STRUK BELANJA            
==========================================
  Nama Barang  : Buku Tulis
  Harga Satuan : Rp 5000
  Jumlah       : 25 buah
------------------------------------------
  Total        : Rp 125000
  Diskon       : Rp 6250
------------------------------------------
  TOTAL BAYAR  : Rp 118750
==========================================
  Terima kasih sudah berbelanja! 🛒  
==========================================
```

---

D. KONSEP OOP YANG DIGUNAKAN

Konsep Penjelasan
Class class Kasir → cetakan untuk membuat objek
Object Kasir kasir1; → objek nyata dari class
Encapsulation Atribut dibuat private agar tidak bisa diakses langsung dari luar
Constructor Kasir() → otomatis jalan saat objek dibuat
Method Fungsi-fungsi di dalam class → inputData(), hitungTotal(), dll
Abstraction Method proses() menyembunyikan detail kompleksitas dari main()

