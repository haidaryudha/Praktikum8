# Praktikum 8

### **1. Pengantar Kode**
Kode ini adalah implementasi dari sebuah **program manajemen data mahasiswa** yang memungkinkan pengguna untuk:
- Menambah data mahasiswa baru,
- Menampilkan daftar mahasiswa yang ada,
- Menghapus data mahasiswa,
- Mengubah data mahasiswa yang sudah ada.

Program ini menggunakan kelas (class) dalam Python untuk mengelola data mahasiswa dan menyediakan antarmuka berbasis teks untuk pengguna. Setiap mahasiswa memiliki informasi berupa nama, NIM (Nomor Induk Mahasiswa), gender, dan nilai.

### **2. Kelas `DaftarNilaiMahasiswa`**

#### **2.1. Konstruktor `__init__`**
```python
def __init__(self):
    self.data_mahasiswa = []
```
- **Tujuan**: Konstruktor ini digunakan untuk menginisialisasi objek dari kelas `DaftarNilaiMahasiswa`. Setiap objek akan memiliki atribut `data_mahasiswa`, yang berupa list kosong. Atribut ini akan digunakan untuk menyimpan data mahasiswa dalam bentuk dictionary.
- **Penjelasan**: Setiap kali kita membuat objek baru dari kelas `DaftarNilaiMahasiswa`, konstruktor akan dipanggil, dan list kosong `data_mahasiswa` akan disiapkan untuk menampung data mahasiswa.

#### **2.2. Metode `tambah`**
```python
def tambah(self, nama, nim, gender, nilai):
    self.data_mahasiswa.append({'nama': nama, 'nim': nim, 'L/P?': gender, 'nilai': nilai})
    print("=" * 62)
    print(f"|    Data mahasiswa '{nama}' berhasil ditambahkan ✔️   |")
    print("=" * 62)
```
- **Tujuan**: Metode `tambah` digunakan untuk menambah data mahasiswa baru ke dalam `data_mahasiswa`.
- **Proses**:
  1. Data mahasiswa yang diberikan (nama, NIM, gender, dan nilai) dimasukkan dalam bentuk dictionary.
  2. Dictionary tersebut kemudian ditambahkan ke dalam list `data_mahasiswa` menggunakan metode `append()`.
  3. Setelah data berhasil ditambahkan, program akan menampilkan pesan yang menunjukkan bahwa data mahasiswa telah berhasil ditambahkan, beserta dengan emotikon **✔️** sebagai penanda keberhasilan.

#### **2.3. Metode `tampilkan`**
```python
def tampilkan(self):
    if not self.data_mahasiswa:
        print()
        print("=" * 37)
        print("|    Tidak ada data mahasiswa ❌    |")
        print("=" * 37)
    else:
        print("\n              Daftar Nilai Mahasiswa              ")
        print("=" * 49)
        print("| NO |       NAMA       |    NIM    |L/P| NILAI |")
        print("-" * 49)
        for i, mhs in enumerate(self.data_mahasiswa, start=1):
            print(f"|{i:3}.| {mhs['nama']:16} | {mhs['nim']:9} | {mhs['L/P?']:1} | {mhs['nilai']:6}|")
        print("=" * 49)
```
- **Tujuan**: Metode `tampilkan` digunakan untuk menampilkan daftar semua data mahasiswa yang ada dalam list `data_mahasiswa`.
- **Proses**:
  1. Program pertama-tama memeriksa apakah ada data mahasiswa dengan memeriksa apakah list `data_mahasiswa` kosong.
  2. Jika list kosong, program akan mencetak pesan yang memberitahukan bahwa tidak ada data mahasiswa (**❌**).
  3. Jika ada data mahasiswa, program akan mencetak header tabel dan kemudian menampilkan data mahasiswa satu per satu.
  4. Untuk setiap mahasiswa dalam `data_mahasiswa`, program mencetak nomor urut, nama, NIM, gender, dan nilai mahasiswa tersebut dengan format yang telah ditentukan.

#### **2.4. Metode `hapus`**
```python
def hapus(self, nama):
    for mhs in self.data_mahasiswa:
        if mhs['nama'] == nama:
            self.data_mahasiswa.remove(mhs)
            print("=" * 59)
            print(f"|    Data mahasiswa '{nama}' berhasil dihapus 🗑️    |")
            print("=" * 59)
            return
    print("=" * 67)
    print(f"|   Data mahasiswa dengan nama '{nama}' tidak ditemukan 🔍    |")
    print("=" * 67)
```
- **Tujuan**: Metode `hapus` digunakan untuk menghapus data mahasiswa berdasarkan nama.
- **Proses**:
  1. Program mencari mahasiswa dengan nama yang diberikan dalam list `data_mahasiswa`.
  2. Jika ditemukan, data mahasiswa akan dihapus menggunakan metode `remove()`, dan pesan keberhasilan akan ditampilkan dengan emotikon **🗑️**.
  3. Jika nama tidak ditemukan dalam daftar, program akan menampilkan pesan kesalahan yang menunjukkan bahwa mahasiswa dengan nama tersebut tidak ada (**🔍**).

#### **2.5. Metode `ubah`**
```python
def ubah(self, nama, nim, gender, nilai_baru):
    for mhs in self.data_mahasiswa:
        if mhs['nama'] == nama:
            mhs['nim'] = nim
            mhs['L/P?'] = gender
            mhs['nilai'] = nilai_baru
            print("=" * 55)
            print(f"|   Data mahasiswa '{nama}' berhasil diubah ✏️    |")
            print("=" * 55)
            return
    print("=" * 67)
    print(f"|   Data mahasiswa dengan nama '{nama}' tidak ditemukan 🔍    |")
    print("=" * 67)
```
- **Tujuan**: Metode `ubah` digunakan untuk mengubah data mahasiswa yang sudah ada berdasarkan nama.
- **Proses**:
  1. Program mencari mahasiswa dengan nama yang diberikan dalam list `data_mahasiswa`.
  2. Jika ditemukan, data mahasiswa akan diperbarui dengan informasi baru (NIM, gender, dan nilai).
  3. Setelah berhasil mengubah data, program akan mencetak pesan yang memberitahukan bahwa data mahasiswa berhasil diubah, menggunakan emotikon **✏️**.
  4. Jika nama tidak ditemukan, program akan menampilkan pesan yang memberi tahu bahwa mahasiswa tersebut tidak ditemukan (**🔍**).

### **3. Fungsi Utama (Main Program)**

#### **3.1. Inisialisasi dan Menu Pilihan**
```python
if __name__ == "__main__":
    daftar = DaftarNilaiMahasiswa()

    while True:
        print("\n        MENU        ")
        print("=" * 20)
        print("| 1. Tambah data   |")
        print("| 2. Tampilkan data|")
        print("| 3. Hapus data    |")
        print("| 4. Ubah data     |")
        print("| 5. Keluar        |")
        print("=" * 20)

        pilihan = input("Pilih Nomor Menu (1 - 5): ")
```
- **Tujuan**: Bagian ini menjalankan loop utama program, yang memungkinkan pengguna untuk memilih berbagai operasi (tambah, tampilkan, hapus, ubah, keluar) dengan menggunakan input.
- **Penjelasan**:
  1. **`__name__ == "__main__"`** memastikan bahwa kode ini hanya dijalankan jika file ini dieksekusi langsung (bukan diimpor sebagai modul).
  2. Program membuat objek `daftar` dari kelas `DaftarNilaiMahasiswa` untuk menyimpan data mahasiswa.
  3. Program kemudian menampilkan menu yang meminta pengguna untuk memilih opsi (1-5).
  4. Pengguna diminta untuk memasukkan pilihan mereka melalui input.

#### **3.2. Penanganan Setiap Pilihan Pengguna**
```python
if pilihan == "1":
    nama = input("Masukkan nama: ")
    nim = int(input("Masukkan nim: "))
    gender = input("Masukkan gender: ")
    nilai = float(input("Masukkan nilai: "))
    daftar.tambah(nama, nim, gender, nilai)
elif pilihan == "2":
    daftar.tampilkan()
elif pilihan == "3":
    nama = input("Masukkan nama mahasiswa yang akan dihapus: ")
    daftar.hapus(nama)
elif pilihan == "4":
    nama = input("Masukkan nama mahasiswa yang diubah: ")
    nim = int(input("Masukan nim mahasiswa yang diubah: "))
    gender = input("Masukan gender mahasiswa yang diubah: ")
    nilai_baru = float(input("Masukkan nilai baru: "))
    daftar.ubah(nama, nim, gender, nilai_baru)
elif pilihan == "5":
    print("=" * 42)
    print("|    Program selesai. Terima kasih 🙏    |")
    print("=" * 42)
    break
else:
    print("=" * 50)
    print("|    Pilihan tidak valid, silakan coba lagi ⚠️   |")
    print("=" * 50)
```
- **Tujuan**: Bagian ini menangani pilihan menu yang dipilih oleh pengguna dan memanggil metode yang sesuai dari objek `daftar` untuk menjalankan operasi yang diinginkan.
- **Penjelasan**:
  1. **Jika pengguna memilih "1"**: Program meminta input untuk menambah data mahasiswa baru, seperti nama, NIM, gender, dan nilai. Setelah data dimasukkan, metode `tambah` dipanggil untuk menyimpan data mahasiswa tersebut.
  2. **Jika pengguna memilih "2"**: Program akan menampilkan daftar data mahasiswa dengan memanggil metode `tampilkan`.
  3. **Jika pengguna memilih "3"**: Program akan meminta nama mahasiswa yang ingin dihapus dan memanggil metode `hapus` untuk menghapus data mahasiswa tersebut.
  4. **Jika pengguna memilih "4"**: Program akan meminta informasi baru untuk mahasiswa yang ingin diubah, dan kemudian memanggil metode `ubah` untuk memperbarui data mahasiswa tersebut.
  5. **Jika pengguna memilih "5"**: Program akan mencetak pesan perpisahan dan keluar dari loop utama dengan `break`.
  6. **Jika input tidak valid**: Program akan memberi tahu pengguna bahwa pilihan yang dimasukkan tidak valid dan meminta mereka untuk mencoba lagi.


### Simulasi Eksekusi Program

**1. Menjalankan Program:**
Saat pertama kali program dijalankan, tampilan menu akan muncul seperti berikut:

```
        MENU        
====================
| 1. Tambah data   |
| 2. Tampilkan data|
| 3. Hapus data    |
| 4. Ubah data     |
| 5. Keluar        |
====================
Pilih Nomor Menu (1 - 5): 
```

Pengguna diminta untuk memilih salah satu opsi yang ada.

---

**2. Pilihan 1: Menambah Data Mahasiswa**
Misalnya, pengguna memilih menu "1" untuk menambah data mahasiswa baru. Program akan meminta input untuk memasukkan nama, NIM, gender, dan nilai mahasiswa.

```
Pilih Nomor Menu (1 - 5): 1
Masukkan nama: John Doe
Masukkan nim: 123456
Masukkan gender: L
Masukkan nilai: 85.5
```

Output dari program setelah data berhasil ditambahkan:

```
==============================================================
|    Data mahasiswa 'John Doe' berhasil ditambahkan ✔️   |
==============================================================
```

**Penjelasan**:
- Program menerima data mahasiswa, lalu menambahkan data tersebut ke dalam daftar mahasiswa.
- Pesan yang menunjukkan bahwa data berhasil ditambahkan dicetak dengan emotikon **✔️** sebagai penanda keberhasilan.

---

**3. Pilihan 2: Menampilkan Data Mahasiswa**
Selanjutnya, pengguna memilih opsi "2" untuk menampilkan semua data mahasiswa yang sudah ada.

```
Pilih Nomor Menu (1 - 5): 2
```

Jika hanya ada satu mahasiswa yang ditambahkan (misalnya "John Doe"), hasil yang ditampilkan adalah:

```
              Daftar Nilai Mahasiswa              
=================================================
| NO |       NAMA       |    NIM    |L/P| NILAI |
-------------------------------------------------
|  1.| John Doe          | 123456    | L  |  85.5 |
=================================================
```

**Penjelasan**:
- Program memeriksa apakah ada data mahasiswa yang sudah dimasukkan. Karena ada satu data, maka data mahasiswa tersebut ditampilkan dengan format tabel.

---

**4. Pilihan 3: Menghapus Data Mahasiswa**
Sekarang, pengguna memilih menu "3" untuk menghapus data mahasiswa tertentu.

```
Pilih Nomor Menu (1 - 5): 3
Masukkan nama mahasiswa yang akan dihapus: John Doe
```

Output yang muncul setelah data berhasil dihapus:

```
===============================================================
|    Data mahasiswa 'John Doe' berhasil dihapus 🗑️    |
===============================================================
```

**Penjelasan**:
- Program mencari mahasiswa dengan nama "John Doe" dalam daftar. Setelah ditemukan, data tersebut dihapus.
- Pesan yang menunjukkan bahwa data berhasil dihapus dicetak dengan emotikon **🗑️** sebagai penanda penghapusan.

---

**5. Pilihan 2: Menampilkan Data Setelah Penghapusan**
Sekarang, pengguna mencoba untuk menampilkan data mahasiswa lagi setelah menghapusnya.

```
Pilih Nomor Menu (1 - 5): 2
```

Karena data mahasiswa sudah dihapus, output yang muncul adalah:

```
=====================================
|    Tidak ada data mahasiswa ❌    |
=====================================
```

**Penjelasan**:
- Program memeriksa apakah ada data mahasiswa di dalam daftar.
- Karena tidak ada data yang tersisa setelah penghapusan, program memberi tahu pengguna bahwa daftar mahasiswa kosong dengan emotikon **❌**.

---

**6. Pilihan 4: Mengubah Data Mahasiswa**
Jika pengguna memilih opsi "4" untuk mengubah data mahasiswa, program akan meminta input baru.

```
Pilih Nomor Menu (1 - 5): 4
Masukkan nama mahasiswa yang diubah: John Doe
Masukan nim mahasiswa yang diubah: 654321
Masukan gender mahasiswa yang diubah: P
Masukkan nilai baru: 90.0
```

Jika mahasiswa dengan nama "John Doe" ditemukan, data mahasiswa tersebut akan diubah. Output yang ditampilkan adalah:

```
=======================================================
|   Data mahasiswa 'John Doe' berhasil diubah ✏️    |
=======================================================
```

**Penjelasan**:
- Program mencari mahasiswa dengan nama "John Doe" dalam daftar. Jika ditemukan, data seperti NIM, gender, dan nilai diperbarui.
- Pesan yang menunjukkan bahwa data berhasil diubah dicetak dengan emotikon **✏️**.

---

**7. Pilihan 5: Keluar dari Program**
Jika pengguna memilih menu "5", program akan berhenti.

```
Pilih Nomor Menu (1 - 5): 5
==========================================================
|    Program selesai. Terima kasih 🙏    |
==========================================================
```

**Penjelasan**:
- Program akan mencetak pesan perpisahan dengan emotikon **🙏**, lalu keluar dari loop utama dan menghentikan program.

---

**8. Pilihan yang Tidak Valid**
Jika pengguna memasukkan pilihan yang tidak valid, program akan menampilkan pesan kesalahan.

```
Pilih Nomor Menu (1 - 5): 10
==================================================
|    Pilihan tidak valid, silakan coba lagi ⚠️   |
==================================================
```

**Penjelasan**:
- Program memeriksa apakah input pilihan berada di antara 1 dan 5. Jika tidak, pesan yang memberi tahu pengguna tentang pilihan yang tidak valid akan ditampilkan dengan emotikon **⚠️**.

---

### **Ringkasan dan Penjelasan Hasil**
Berikut adalah gambaran dari bagaimana program ini bekerja dan hasil yang didapatkan selama eksekusi:

1. **Menambah Data**:
   - Ketika data mahasiswa baru ditambahkan, program memeriksa input dan menambahkannya ke dalam list.
   - Pesan berhasil ditambahkan akan ditampilkan dengan emotikon **✔️**.

2. **Menampilkan Data**:
   - Jika ada data mahasiswa, program akan menampilkan tabel data mahasiswa.
   - Jika tidak ada data, program akan menampilkan pesan bahwa data tidak ada, menggunakan emotikon **❌**.

3. **Menghapus Data**:
   - Program akan mencari nama mahasiswa dan menghapus data jika ditemukan.
   - Pesan sukses dihapus ditampilkan dengan emotikon **🗑️**.

4. **Mengubah Data**:
   - Program mencari mahasiswa berdasarkan nama, dan jika ditemukan, data akan diperbarui dengan input baru.
   - Pesan berhasil diubah ditampilkan dengan emotikon **✏️**.

5. **Keluar**:
   - Setelah memilih menu keluar, program memberikan ucapan terima kasih dengan emotikon **🙏** dan program berhenti.

6. **Pilihan Tidak Valid**:
   - Jika input tidak sesuai dengan pilihan menu, program memberi tahu pengguna bahwa pilihan tidak valid dengan emotikon **⚠️**.

Dengan cara ini, pengguna dapat mengelola data mahasiswa dengan cara yang sangat mudah dipahami, menggunakan antarmuka berbasis teks dengan feedback yang jelas dan emotikon yang membuat pengalaman menjadi lebih menyenangkan.
