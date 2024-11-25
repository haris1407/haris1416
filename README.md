# LABPY.05/PRAKTIKUM06
# NAMA: HARIS ADRIANSYAH
# NIM: 312410286
# KELAS: TI.24.A4
## Program Pengelolaan Data Mahasiswa
![gambar](https://github.com/user-attachments/assets/442240d4-2793-4d3d-9a40-f1cf0b8a9fda)

# penjelasan programm

## Perhitungan Nilai Akhir
Nilai akhir pelajar dihitung berdasarkan bobot sebagai berikut:
* Tugas: 30%
* UTS: 35%
* UAS: 35%.

## Komponen Program

### 1.sruktur data 
Data siswa disimpan dalam daftar bernama data_list, yang berisi elemen kamus. Setiap kamus mewakili satu pelajar dengan format berikut:

```pyhton
{
    'Nama': 'Nama Mahasiswa',
    'NIM': 'NIM Mahasiswa',
    'Tugas': 80.0,  # Nilai Tugas
    'UTS': 75.0,    # Nilai UTS
    'UAS': 85.0,    # Nilai UAS
    'Nilai Akhir': 81.5  # Hasil perhitungan nilai akhir
}
````
### 2.Fungsi-Fungsi Utama
### oi_final_grade(tugas, uts, uas)

Fungsi ini menghitung nilai akhir siswa berdasarkan bobot masing-masing:
* Tugas: 30%
* UTS: 35%
* UAS: 35%.

```pyhton
def oi_final_grade(tugas, uts, uas):
    return (tugas * 0.30) + (uts * 0.35) + (uas * 0.35)
````

### lihat_data()
Fungsi ini menampilkan seluruh data siswa dalam format tabel. Jika data kosong, ditampilkan pesan "Tidak ada data!".

```pyhton
def lihat_data():
    if not data_list:
        print("\nTidak ada data!")
    else:
        print("\nDaftar Nilai")
        print("=" * 70)
        print("| NO | NIM      | NAMA       | TUGAS   | UTS     | UAS     | AKHIR   |")
        print("=" * 70)
        for idx, student in enumerate(data_list, start=1):
            print(f"| {idx:<2} | {student['NIM']:<8} | {student['Nama']:<10} | "
                  f"{student['Tugas']:<8.2f} | {student['UTS']:<8.2f} | {student['UAS']:<8.2f} | "
                  f"{student['Nilai Akhir']:<8.2f} |")
        print("=" * 70)
````
### ubah_data()
Fungsi ini memungkinkan pengguna untuk memperbarui data siswa berdasarkan nomor urut. Setelah memilih nomor data, pengguna dapat memasukkan data baru. Nilai akhir diperbarui secara otomatis.

```pyhton
def ubah_data():
    lihat_data()
    index = int(input("\nPilih nomor data yang ingin diubah: ")) - 1
    if 0 <= index < len(data_list):
        print("\nMasukkan data baru:")
        data_list[index]['NIM'] = input("NIM: ")
        data_list[index]['Nama'] = input("Nama: ")
        data_list[index]['Tugas'] = float(input("Nilai Tugas: "))
        data_list[index]['UTS'] = float(input("Nilai UTS: "))
        data_list[index]['UAS'] = float(input("Nilai UAS: "))
        data_list[index]['Nilai Akhir'] = oi_final_grade(
            data_list[index]['Tugas'],
            data_list[index]['UTS'],
            data_list[index]['UAS']
        )
        print("\nData berhasil diubah!")
    else:
        print("\nNomor data tidak ditemukan!")
````

### hapus_data()
Fungsi ini memungkinkan pengguna untuk menghapus data siswa berdasarkan nomor urut. Data akan dihapus dari daftar data_list.

```pyhton
def hapus_data():
    lihat_data()
    index = int(input("\nPilih nomor data yang ingin dihapus: ")) - 1
    if 0 <= index < len(data_list):
        data_list.pop(index)
        print("\nData berhasil dihapus!")
    else:
        print("\nNomor data tidak ditemukan!")
````

### cari_data()
Fungsi ini mencari data siswa berdasarkan Nama atau NIM. Jika ditemukan, data yang sesuai akan ditampilkan dalam tabel. Jika tidak ditemukan, ditampilkan pesan "Data tidak ditemukan!".

```pyhton
def cari_data():
    keyword = input("Masukkan NIM atau Nama yang ingin dicari: ").lower()
    found = [data for data in data_list if keyword in data['NIM'].lower() or keyword in data['Nama'].lower()]
    if found:
        print("\nHasil Pencarian:")
        print("=" * 70)
        print("| NO | NIM      | NAMA       | TUGAS   | UTS     | UAS     | AKHIR   |")
        print("=" * 70)
        for idx, student in enumerate(found, start=1):
            print(f"| {idx:<2} | {student['NIM']:<8} | {student['Nama']:<10} | "
                  f"{student['Tugas']:<8.2f} | {student['UTS']:<8.2f} | {student['UAS']:<8.2f} | "
                  f"{student['Nilai Akhir']:<8.2f} |")
        print("=" * 70)
    else:
        print("\nData tidak ditemukan!")
````

## 3.Program Utama (Menu Loop)
Menu program utama memungkinkan pengguna untuk memilih fitur melalui input:

*L: Melihat data.
*T: Menambahkan data.
*U: Mengubah data.
*H: Menghapus data.
*C: Mencari data.
*K: Keluar dari program.

Program terus berjalan hingga pengguna memilih opsi K.

```pyhton
while True:
    print("\n[L]ihat, [T]ambah, [U]bah, [H]apus, [C]ari, [K]eluar")
    pilihan = input("Pilih menu: ").lower()

    if pilihan == 'l':
        lihat_data()
    elif pilihan == 't':
        tambah_data()
    elif pilihan == 'u':
        ubah_data()
    elif pilihan == 'h':
        hapus_data()
    elif pilihan == 'c':
        cari_data()
    elif pilihan == 'k':
        print("\nProgram selesai. Sampai jumpa!")
        break
    else:
        print("\nPilihan tidak valid!")
````

## screenshout VSC
![gambar](https://github.com/user-attachments/assets/1d59a3ee-0e69-4dc2-a070-c4effd3af0fe)

## Contoh output
Berikut adalah contoh tampilan tabel data:

# DAFTAR NILAI
Daftar Nilai
======================================================================
| NO | NIM      | NAMA       | TUGAS   | UTS     | UAS     | AKHIR   |
======================================================================
| 1  | 1224     | AGUNG      | 90.00    | 80.00    | 85.00    | 88.25    |
| 2  | 5697     | AGUNG      | 90.00    | 85.00    | 80.00    | 85.95    |
| 3  | 9123     | AGUS       | 90.00    | 80.00    | 95.00    | 88.80    |
======================================================================

## screenshout output VSC
![GAMBAR](https://github.com/user-attachments/assets/4e3dee63-9c98-4f0e-ab1f-55f06de77877)

# BERIKUT DI BAWAH INI ADALAH FLOWCHART NYA :
![image](https://github.com/user-attachments/assets/49b1e0f3-f072-44cb-8e04-05f71026b610)
