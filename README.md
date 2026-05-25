# Praktikum Kecerdasan Buatan - Pertemuan 9: Algoritma Genetika

Repository ini berisi implementasi **Algoritma Genetika (Genetic Algorithm - GA)** untuk memecahkan permasalahan **Knapsack Problem** biner (0/1). Proyek ini disusun untuk memenuhi tugas praktikum Kecerdasan Buatan.

---

## Identitas Mahasiswa

*   **Nama:** Muhammad Fathan Ramdani
*   **NIM:** H1D024026
*   **Kelas:** Praktikum Kecerdasan Buatan (A)
*   **Instansi:** Universitas Jenderal Soedirman

---

## Deskripsi Masalah (Knapsack Problem)

Knapsack Problem adalah masalah optimasi di mana kita harus memilih kombinasi barang yang akan dimasukkan ke dalam wadah (tas/knapsack) dengan kapasitas maksimal tertentu. Setiap barang memiliki nilai (*value/price*) dan berat (*weight*). Tujuannya adalah untuk **memaksimalkan total nilai barang** yang dibawa tanpa melebihi **kapasitas maksimum tas**.

Pada praktikum ini, permasalahan diselesaikan menggunakan **Algoritma Genetika (GA)** dengan tahapan-tahapan sebagai berikut:
1.  **Inisialisasi Populasi:** Membangkitkan sejumlah individu (kromosom biner) secara acak.
2.  **Evaluasi Fitness:** Menghitung total nilai barang dari kromosom yang terpilih. Jika total berat melebihi kapasitas tas, individu tersebut mendapatkan penalti dengan nilai *fitness* = 0.
3.  **Seleksi Orang Tua:** Menggunakan *Roulette Wheel Selection* dan *Tournament Selection* untuk memilih individu terbaik yang akan bereproduksi.
4.  **Crossover (Penyilangan):** Mengkombinasikan dua orang tua menggunakan *One-Point*, *Two-Point*, atau *Uniform Crossover* untuk menghasilkan anak (*offspring*).
5.  **Mutasi:** Memberikan variasi genetik acak menggunakan *Swap Mutation*, *Inversion Mutation*, atau *Uniform Mutation*.
6.  **Pengulangan Generasi:** Mengulangi siklus di atas hingga jumlah generasi tertentu tercapai.

---

## Struktur Proyek

Seluruh kode program diletakkan dalam direktori [`Algoritma Genetika/`](./Algoritma%20Genetika) yang terdiri dari modul-modul berikut:

| Nama File | Deskripsi |
| :--- | :--- |
| 📄 [`inisiasipopulasi.py`](./Algoritma%20Genetika/inisiasipopulasi.py) | Berisi fungsi `inisialisasi_populasi` untuk membangkitkan populasi awal yang berisi kromosom biner acak. |
| 📄 [`EvaluasiFitness.py`](./Algoritma%20Genetika/EvaluasiFitness.py) | Berisi fungsi `hitung_fitness` untuk mengevaluasi kelayakan dan total nilai dari suatu kromosom berdasarkan kapasitas tas. |
| 📄 [`selection.py`](./Algoritma%20Genetika/selection.py) | Implementasi metode seleksi: **Roulette Wheel Selection** dan **Tournament Selection**. |
| 📄 [`crossover.py`](./Algoritma%20Genetika/crossover.py) | Implementasi metode crossover: **One-Point Crossover**, **Two-Point Crossover**, dan **Uniform Crossover**. |
| 📄 [`mutation.py`](./Algoritma%20Genetika/mutation.py) | Implementasi metode mutasi: **Swap Mutation**, **Inversion Mutation**, dan **Uniform Mutation**. |
| 📄 [`main.py`](./Algoritma%20Genetika/main.py) | Berisi logika utama evolusi algoritma genetika, visualisasi grafik perkembangan nilai fitness menggunakan `matplotlib`, dan menampilkan barang terbaik yang terpilih. |

---

## Parameter Algoritma Genetika (`main.py`)

Simulasi pada `main.py` menggunakan konfigurasi parameter default sebagai berikut:
*   **Jumlah Generasi:** 50
*   **Jumlah Populasi:** 20
*   **Probabilitas Crossover:** 0.5 (50%)
*   **Probabilitas Mutasi:** 0.1 (10%)
*   **Kapasitas Tas:** 50 kg / unit berat

### Data Barang yang Digunakan:
| Nama Barang | Nilai (Fitness) | Berat |
| :--- | :---: | :---: |
| Barang1 | 60 | 10 |
| Barang2 | 100 | 20 |
| Barang3 | 120 | 30 |
| Barang4 | 90 | 25 |
| Barang5 | 69 | 11 |
| Barang6 | 70 | 9 |
| Barang7 | 80 | 15 |
| Barang8 | 90 | 10 |
| Barang9 | 25 | 3 |

---

## Cara Menjalankan Kode

1.  Pastikan Anda telah menginstal pustaka yang diperlukan (`matplotlib` dan `numpy`):
    ```bash
    pip install matplotlib numpy
    ```
2.  Masuk ke direktori `Algoritma Genetika/`:
    ```bash
    cd "Algoritma Genetika"
    ```
3.  Jalankan file `main.py` untuk melihat proses evolusi dan grafik perkembangan nilai fitness:
    ```bash
    python main.py
    ```

---

## Output Grafik & Hasil Evolusi

Setelah program `main.py` selesai dijalankan:
1.  Akan muncul jendela grafik interaktif `matplotlib` yang menunjukkan:
    *   **Garis Biru:** Perkembangan *Fitness* Tertinggi (Terbaik) di setiap generasi.
    *   **Garis Kuning:** Perkembangan *Fitness* Terendah di setiap generasi.
    *   **Garis Merah:** Perkembangan *Fitness* Rata-rata populasi.
    *   **Titik Abu-abu:** Nilai *fitness* dari seluruh individu dalam populasi.
2.  Di terminal akan tercetak kombinasi barang terbaik yang berhasil dipilih oleh Algoritma Genetika beserta nilai fitness terbaik dan total beratnya.
