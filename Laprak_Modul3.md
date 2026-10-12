# <h1 align="center">Laporan Praktikum Modul 1 - Codeblocks IDE & Pengenalan Bahas C++ (Bagian Pertama)</h1>
<p align="center">Muhammad Azhar nur Hafizh - 109082500049</p>

## Dasar Teori
Bahasa pemrograman C++ yang dikembangkan oleh Bjarne Stroustrup menyediakan fondasi kuat untuk pemrograman modular melalui penerapannya pada Abstract Data Type (ADT). Pada praktikum Struktur Data Modul 3 ini, C++ digunakan untuk mengimplementasikan pemisahan antarmuka dan realisasi program, pengelolaan entitas data menggunakan struct, penyimpanan koleksi data pada array 1D/2D, serta manipulasi alamat memori menggunakan pointer dan reference.

### A. Struktur Program dan Identifier<br/>
Array merupakan struktur data yang menampung sekumpulan elemen bertipe data sama pada lokasi memori yang berurutan.Array 1 Dimensi: Pada program pencatatan data mahasiswa, array 1D ber tipe Mahasiswa digunakan untuk menampung hingga 10 objek mahasiswa secara linier.   Array 2 Dimensi (Matriks): Menggunakan dua indeks [baris][kolom] (seperti matriks $3 \times 3$), yang dimanfaatkan untuk menyimpan elemen integer serta melakukan operasi penukaran nilai elemen pada koordinat tertentu.
  
### B. Pointer dan Reference<br/>
Pengelolaan lokasi memori secara langsung menjadi komponen krusial pada ADT dan manipulasi data.Pointer (*): Variabel yang menyimpan alamat memori dari variabel lain. Pada fungsi penukaran nilai pointer, operator & digunakan untuk mengambil alamat memori dan operator dereferensi * digunakan untuk mengubah nilai variabel aslinya.   Reference (&): Berfungsi sebagai alias dari variabel yang sudah ada. Digunakan pada prosedur inputMhs(mahasiswa &m) agar perubahan data mahasiswa yang diinputkan di dalam prosedur secara langsung memperbarui variabel asli pada calle

### C. Input dan Output<br/>
Output dengan cout: Digunakan untuk menampilkan data hasil perhitungan nilai akhir, data mata pelajaran, maupun mencetak elemen matriks 2D menggunakan operator <<.   Input dengan cin: Mengambil masukan data dari pengguna melalui keyboard, seperti input data NIM, nilai UTS, UAS, Tugas, serta batas jumlah mahasiswa.   Escape Sequence: Penggunaan karakter \t (tabulasi) digunakan untuk merapikan tampilan keluaran matriks $3 \times 3$ agar tercetak sejajar dalam bentuk kolom, serta \n atau endl untuk pemisah baris

### D. Operator<br/>
Operator Aritmatika: Penjumlahan (+) dan perkalian (*) digunakan dalam kalkulasi rumus nilai akhir mahasiswa ($0.3 \times \text{uts} + 0.4 \times \text{uas} + 0.3 \times \text{tugas}$) serta perhitungan rata-rata.   Operator Relasi: Operator pembanding seperti > digunakan untuk memvalidasi agar batas input jumlah mahasiswa tidak melebihi kapasitas maksimum array (10 entri).   Operator Increment (++): Digunakan dalam perulangan for untuk menaikkan indeks penelusuran array 1D mahasiswa maupun iterasi baris dan kolom matriks 2D.
ondisional, Perulangan, Pointer, dan ReferencePercabangan if: Digunakan untuk mengevaluasi dan membatasi input jumlah data mahasiswa agar tidak melebihi alokasi memori array.   Perulangan (for): Menelusuri setiap elemen array 1D mahasiswa untuk proses input/output data, serta perulangan bersarang (nested loop) untuk mengiterasi indeks [i][j] pada matriks $3 \times 3$.   Pointer (*) dan Reference (&): Reference (&) diterapkan pada prosedur ADT untuk pengubahan nilai variabel (pass-by-reference), sedangkan pointer (*) diterapkan pada prosedur tukarPointer untuk menukar isi dua variabel integer melalui alamat memorinya.   Fungsi dan Prosedur (ADT Primitif): Fungsi mengembalikan nilai balik (return value) seperti pada hitungNilaiAkhir() dan konstruktor create_pelajaran(), sedangkan prosedur (void) digunakan untuk instruksi tanpa nilai balik seperti inputMhs(), tampil_pelajaran(), dan tampilArray2D()

## Unguided 
Pisahkan contoh program coba_ADT ke dalam 3 buah file terpisah sesuai kaidah ADT, yaitu file header spesifikasi type (mahasiswa.h), file body realisasi primitif (mahasiswa.cpp), dan file program utama driver (main.cpp).

### 1. mahasiswa.h<br/>
```C++
#ifndef MAHASISWA_H_INCLUDED
#define MAHASISWA_H_INCLUDED
#include <iostream>
#include <string>
using namespace std;

struct Mahasiswa {
    string nama, nim;
    float uts, uas, tugas, nilai_akhir;
};

float hitungNilaiAkhir(Mahasiswa m);
void inputMahasiswa(Mahasiswa &m);
void tampilMahasiswa(Mahasiswa m);

#endif
```

Header file mahasiswa.h mengimplementasikan konsep Abstract Data Type (ADT) dengan mengombinasikan Header Guard (#ifndef, #define, #endif) untuk mencegah pendefinisian ganda, deklarasi pustaka standar (<iostream> dan <string>), serta penentuan tipe data terdefinisi struct Mahasiswa yang menampung atribut nama, nim, uts, uas, tugas, dan nilai_akhir. Selain itu, file ini mendefinisikan tiga primitif ADT, yaitu fungsi hitungNilaiAkhir(Mahasiswa m) untuk mengembalikan hasil kalkulasi nilai, prosedur inputMahasiswa(Mahasiswa &m) dengan pass-by-reference (&m) agar proses pengisian data langsung mengubah nilai variabel asli, serta prosedur tampilMahasiswa(Mahasiswa m) untuk menyajikan seluruh informasi data mahasiswa ke layar.   

### 2. Prosedur inputMahasiswa(Mahasiswa &m) untuk membaca masukan nama, NIM, serta ketiga nilai, lalu secara otomatis menghitung nilai_akhir.   

```C++
#include "mahasiswa.h"

float hitungNilaiAkhir(Mahasiswa m) {
    return 0.3 * m.uts + 0.4 * m.uas + 0.3 * m.tugas;
}

void inputMahasiswa(Mahasiswa &m) {
    cout << "Nama: "; cin >> ws; getline(cin, m.nama);
    cout << "NIM: "; cin >> m.nim;
    cout << "UTS, UAS, Tugas: "; cin >> m.uts >> m.uas >> m.tugas; //pake spasi biar bisa input
    m.nilai_akhir = hitungNilaiAkhir(m);
}

void tampilMahasiswa(Mahasiswa m) {
    cout << m.nim << " | " << m.nama << " | NA: " << m.nilai_akhir << endl;
}
```
### Output Unguided 2 :
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/1488bbae-f332-40a8-bafb-24c6317ed525" />


File mahasiswa.cpp merupakan modul realisasi (body) dari ADT Mahasiswa yang mengimplementasikan fungsi dan prosedur yang telah dideklarasikan sebelumnya pada file header (mahasiswa.h). Kode ini merealisasikan fungsi hitungNilaiAkhir(Mahasiswa m) yang mengembalikan nilai kalkulasi bobot $0.3 \times \text{uts} + 0.4 \times \text{uas} + 0.3 \times \text{tugas}$, prosedur inputMahasiswa(Mahasiswa &m) dengan mekanisme pass-by-reference (&m) serta pemanfaatan cin >> ws dan getline untuk menginputkan data nama, nim, dan nilai-nilai secara presisi sekaligus langsung menghitung nilai_akhir, serta prosedur tampilMahasiswa(Mahasiswa m) yang bertugas menyajikan ringkasan data NIM, nama, dan nilai akhir mahasiswa ke layar. 

### 3. Prosedur tampilMahasiswa(Mahasiswa m) untuk menampilkan data ringkas NIM, Nama, dan Nilai Akhir ke layar.

```C++
#include "mahasiswa.h"

int main() {
    Mahasiswa mhs[10];
    int n;
    cout << "Jumlah mhs (max 10): "; cin >> n;

    for (int i = 0; i < n && i < 10; i++) {
        cout << "\nData ke-" << i + 1 << endl;
        inputMahasiswa(mhs[i]);
    }

    cout << "\n--- Hasil Data ---\n";
    for (int i = 0; i < n && i < 10; i++) {
        tampilMahasiswa(mhs[i]);
    }
    return 0;
}
```
### Output Unguided 3 :
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/de512575-0a0a-4aa3-84f9-5f45b5c0c659" />


Program ini menggunakan array satu dimensi arrA. Terdapat fungsi cariMinimum dan cariMaksimum yang mengembalikan nilai bertipe int, serta prosedur hitungRataRata (menggunakan tipe void) untuk menampilkan hasil perhitungan rata-rata. Seluruh fungsionalitas diakses secara interaktif menggunakan kontrol menu switch-case di dalam perulangan do-while.

## Kesimpulan
Berdasarkan praktikum yang telah dilakukan pada Modul 03 mengenai Abstract Data Type (ADT), dapat ditarik beberapa kesimpulan sebagai berikut:Penerapan Modularitas Program: Konsep Abstract Data Type (ADT) mempermudah pengelolaan kode program dengan memisahkan antara definisi tipe data/prototipe primitif pada file header (.h), implementasi/realisasi fungsi dan prosedur pada file body (.cpp), serta pengujian program pada file utama driver (main.cpp).   Efisiensi Pengelolaan Memori: Penggunaan pass-by-reference (&) dan pointer (*) terbukti efektif dalam memanipulasi nilai variabel secara langsung pada alamat memorinya tanpa harus melakukan duplikasi nilai data (pass-by-value).   Pengorganisasian Data Kompleks: Pemakaian struct dan array multidimensi (1D maupun 2D matriks) memungkinkan penyimpanan sekumpulan data dengan atribut heterogen secara terstruktur dan terorganisir.   

## Referensi
[2] Modul 2 Struktur Data: Tim Dosen & Asisten Laboratorium Informatika. (2026). Modul 03 Praktikum Struktur Data: Abstract Data Type (ADT). Fakultas Informatika, Telkom University.
