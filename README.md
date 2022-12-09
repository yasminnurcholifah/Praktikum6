# Praktikum6
# import tabulate
from tabulate import tabulate

dataMahasiswa = { 'No' : [], 'NIM' : [], 'Nama' :[], 'Tugas' : [], 'UTS' : [], 'UAS' : [], 'Nilai Akhir' : [] } no = 0
# fungsi untuk menampilkan data
# fungsi untuk menambahkan data
def tambah(no): # menginput data nim = int(input("Masukkan NIM : ")) nama = input("Masukkan Nama : ") tugas = int(input("Masukkan Nilai Tugas : ")) uts = int(input("Masukkan Nilai UTS : ")) uas = int(input("Masukkan Nilai UAS : ")) nilai_akhir = (tugas * 30 / 100) + (uts * 35 / 100) + (uas * 35 / 100) # menambahkan data dataMahasiswa['No'].append(no) dataMahasiswa['NIM'].append(nim) dataMahasiswa['Nama'].append(nama) dataMahasiswa['UTS'].append(uts) dataMahasiswa['Tugas'].append(tugas) dataMahasiswa['UAS'].append(uas) dataMahasiswa['Nilai Akhir'].append(nilai_akhir) print("Data berhasil di tambahkan.") # print(tabulate(dataMahasiswa, headers=[ # 'NIM', 'Nama', 'Tugas', 'UTS', 'UAS', 'Nilai Akhir'], tablefmt="fancy_grid")) def tampilkan(): print("Berikut data yang ada") print(tabulate(dataMahasiswa, headers=[ 'No', 'NIM', 'Nama', 'Tugas', 'UTS', 'UAS', 'Nilai Akhir'], tablefmt="fancy_grid"))
# fungsi untuk mengedit data
def ubah(nama):
# cek jika ada nama tersebut di dataMahasiswa
if nama in dataMahasiswa['Nama']:
    # cari posisi indexnya lalu di simpan di nimIndex
    namaindex = dataMahasiswa['Nama'].index(nama)
    print("Pilih data yang mau di edit")
    # perulangan mengedit data dalam bentuk pilihan
    while True:
        editApa = int(input(
            "(1) Nim, \n (2) Nama, \n (3) Nilai Tugas, \n (4) Nilai UTS, \n (5) Nilai UAS, \n :"))
        print("")
        break
    if editApa == 1:
            # mengubah nim
            newNim = int(input("Masukkan NIM :"))
            dataMahasiswa['NIM'][namaindex] = newNim
            print("Perubahan data berhasil di simpan")
    elif editApa == 2:
            # mengubah nama
            newNama = int(input("Masukkan Nama :"))
            dataMahasiswa['Nama'][namaindex] = newNama
            print("Perubahan data berhasil di simpan")
    elif editApa == 3:
            # mengubah nilai tugas dan nilai akhir
            newTugas = int(input("Masukkan Nilai Tugas :"))
            nilai_akhir = (newTugas * 30 / 100) + (dataMahasiswa['UTS'][namaindex] * 35 / 100) + (
            dataMahasiswa['UAS'][namaindex] * 35 / 100)
            dataMahasiswa['Tugas'][namaindex] = newTugas
            dataMahasiswa['Nilai Akhir'][namaindex] = nilai_akhir
            print("Perubahan data berhasil di simpan")
    elif editApa == 4:
            # mengubah nilai uts dan nilai akhir
            newUTS = int(input("Masukkan Nilai UTS :"))
            nilai_akhir = (dataMahasiswa['Tugas'][namaindex] * 30 / 100) + (newUTS * 35 / 100) + (
            dataMahasiswa['UAS'][namaindex] * 35 / 100)
            dataMahasiswa['UTS'][namaindex] = newUTS
            dataMahasiswa['Nilai Akhir'][namaindex] = nilai_akhir
            print("Perubahan data berhasil di simpan")
    elif editApa == 5:
            # mengubah nilai uas dan nilai akhir
            newUAS = int(input("Masukkan Nilai UAS :"))
            nilai_akhir = (dataMahasiswa['Tugas'][namaindex] * 30 / 100) + (dataMahasiswa['UTS'][namaindex] * 35 / 100) * (newUAS * 35 / 100)
            dataMahasiswa['UAS'][namaindex] = nilai_akhir
            print("Perubahan data berhasil di simpan")
else:
    print("Data tidak di temukan")
# fungsi untuk menghapus data
def hapus(nama): if nama in dataMahasiswa['Nama']: namaIndex = dataMahasiswa['Nama'].index(nama) # menghapus data berdasarkan position index pada nama del dataMahasiswa['No'][namaIndex] del dataMahasiswa['NIM'][namaIndex] del dataMahasiswa['Nama'][namaIndex] del dataMahasiswa['Tugas'][namaIndex] del dataMahasiswa['UTS'][namaIndex] del dataMahasiswa['UAS'][namaIndex] del dataMahasiswa['Nilai Akhir'][namaIndex] print("Data berhasil di hapus. ") else: print("Data tidak di temukan")
# fungsi untuk mencari data
# melakukan perulangan menggunakan while sampai user menekan huruf Q perulangan akan berhenti
while True:
# opsi input pilihan T,L,U,H,K
tanya = input (
 " (T) Menambahkan data,\n (L) Melihat semua data,\n (U) Update data,\n (H) Menghapus data,\n (K) Keluar Program :") 
if tanya == "T":
    while True:
        no += 1
        # memanggil fungsi tambah data dan memparsing data no
        tambah(no)
        tambahDataLagi = input("Tambah data lagi ? (y/n) :")
        if tambahDataLagi == 'n':
            break
elif tanya == "L":
        # menampilkan data dalam bentuk table menggunakan package tabulate
        tampilkan()
        print("")
elif tanya == "U":
        print(tabulate(dataMahasiswa, headers=[
            'No', 'NIM', 'Nama', 'Tugas', 'UTS', 'UAS', 'Nilai Akhir'], tablefmt="fancy_grid"))
        nama = input("Masukkan nama yang mau di edit : ")
        print("")
        ubah(nama)
elif tanya == "H":
        print(tabulate(dataMahasiswa, headers=['No', 'NIM', 'Nama', 'Tugas', 'UTS', 'UAS', 'Nilai Akhir'], tablefmt="fancy_gird"))
        nama = input("Masukkan nama yang mau di di hapus : ")
        print("")
        hapus(nama)
elif tanya == 'K':
        print("")
        print("Anda telah keluar dari program")
        break
            