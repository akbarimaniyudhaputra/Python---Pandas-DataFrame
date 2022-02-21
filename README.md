
# Python - Pandas - DataFrame

## Mengambil Data di File Excel
 - Dengan library Pandas
 - bentuk file : .xlsx ataupun .xls
 
#### Perintah untuk mengambil data di file Excel

```http
import pandas as pd
from pandas import ExcelFile

FileExcel = "E:\dataset\smartphone.xlsx"
data = pd.read_excel(FileExcel, sheet_name="Sheet1")

print(data)
```
![1](https://user-images.githubusercontent.com/86678205/154907651-c562a62b-2d20-4ff0-a55f-bc99a073706e.PNG)
###
![1 lebih rapi](https://user-images.githubusercontent.com/86678205/154907725-3174a4dc-3a93-4c18-9022-278d3763f169.PNG)


## Cara Melebarkan Tampilan Notebook Jupyter 
 - https://qastack.id/programming/21971449/how-do-i-increase-the-cell-width-of-the-jupyter-ipython-notebook-in-my-browser


## Mengubah Indeks
 - Dengan perintah fungsi .set_index()
 - Kita bisa menjadikan field/kolom yang mempunyai nilai unik
 - Seperti field/kolom Nomor Induk Pegawai, Nomor Induk Mahasiswa, Kode Barang, dll.
 - inplace=True artinya parameter untuk menyatakan bahwa perubahan indeks tersebut langsung mengubah struktur DataFrame tersebut
 
 #### Perintah untuk mengubah indeks

```http
data.set_index("nama_kolom", inplace=True)
data
```
![2](https://user-images.githubusercontent.com/86678205/154907928-51d7fe66-4ffc-4c68-a3d8-774185617d10.PNG)

## Menambah Kolom
 - Dengan membuat list
 - Kemudian list dimasukkan ke DataFrame
 - Anda membuat/menambahkan data list dari kiri ke kanan, tetapi tampilan indeks dimulai dari atas ke bawah

 #### Perintah untuk menambah kolom

```http
listKeterangan = ["Tingkatkan", "Evaluasi", "Tingkatkan", "Evaluasi"]
data["nama_kolom_baru"] = listKeterangan
data
```
![3](https://user-images.githubusercontent.com/86678205/154908069-6f5f32f7-21c5-4c46-9af4-d92395b323cb.PNG)

## Menghapus Data Baris 
 - Dengan perintah fungsi .drop()
 - axis=0 artinya parameter untuk menunjukkan bahwa penghapusan dilakukan pada baris
 - inplace=True artinya parameter untuk menyatakan bahwa perubahan indeks tersebut langsung mengubah struktur DataFrame tersebut
 - Hapus sesuai nama indeksnya

 #### Perintah untuk menghapus data baris

```http
data.drop([indeksnya], axis=0, inplace=True)
data
```
![4](https://user-images.githubusercontent.com/86678205/154908126-6802eded-c5b1-4acf-a6e8-f7e919ea963e.PNG)

## Menghapus Data Kolom
 - Dengan perintah fungsi .drop()
 - axis=1 artinya parameter untuk menunjukkan bahwa penghapusan dilakukan pada kolom
 - inplace=True artinya parameter untuk menyatakan bahwa perubahan indeks tersebut langsung mengubah struktur DataFrame tersebut
 - Hapus sesuai nama kolom

 #### Perintah untuk menghapus Kolom

 ```http
data.drop(["nama_kolom"], axis=1, inplace=True)
data
```
![5](https://user-images.githubusercontent.com/86678205/154908167-871f1cc8-1c2a-4dcb-8e43-02742882ca90.PNG)

## Mengubah Nama Kolom
 - Dengan perintah fungsi .rename()
 - Kolom/field yang digunakan sebagai pengganti indeks tidak bisa ikut diganti/diubah
 - inplace=True artinya parameter untuk menyatakan bahwa perubahan indeks tersebut langsung mengubah struktur DataFrame tersebut

 #### Perintah untuk mengubah nama kolom

 ```http
data.rename(columns = {"nama_kolom_lama" : "nama_kolom_baru", "nama_kolom_lama" : "nama_kolom_baru", "nama_kolom_lama" : "nama_kolom_baru"}, inplace = True)
data
```
![6](https://user-images.githubusercontent.com/86678205/154908252-598160e7-79cb-4221-ab12-2c2823be3942.PNG)

## Mengubah Nama Indeks
 - Dengan perintah fungsi .rename()
 - inplace=True artinya parameter untuk menyatakan bahwa perubahan indeks tersebut langsung mengubah struktur DataFrame tersebut

 #### Perintah untuk mengubah nama indeks

 ```http
data.rename(index = {3 : "AWAL", 58 : "AKHIR", 4 : 4},inplace=True) 
data
```
![7](https://user-images.githubusercontent.com/86678205/154908278-28c415c6-ec48-4519-9fce-85d2056c5940.PNG)

## Mengakses beberapa Kolom beserta datanya
 - Dengan perintah fungsi .filter()

 #### Perintah untuk mengakses beberapa kolom beserta datanya

 ```http
data = data.filter(items=["nama_kolom1", "nama_kolom2", "nama_kolom3"])
data
```
![8](https://user-images.githubusercontent.com/86678205/154908302-7363e3f9-98e1-42d6-b939-82b3e3df4c5e.PNG)

## Mengurutkan Data di Kolom tertentu
 - Dengan perintah fungsi .sort_values()
 - .astype() perintah fungsi untuk mengubah type data
 - .replace() perintah fungsi untuk mengganti kata/kalimat/huruf/angka
 - fungsi lambda dengan fungsi .map() untuk menerapkan fungsi ke semua nilai 
 - .zfill() perintah fungsi untuk menentukan panjang nilai X
 - axis=0 artinya parameter untuk menunjukkan bahwa penghapusan dilakukan pada baris
 - inplace=True artinya parameter untuk menyatakan bahwa perubahan indeks tersebut langsung mengubah struktur DataFrame tersebut
 - ascending=False, Ascending adalah pengurutan dari yang terkecil ke yang terbesar tetapi disini perintahnya False jadi besar ke kecil

 #### Perintah untuk mengurutkan Data di Kolom tertentu

 ```http
data["ram"] = data["ram"].astype(str) #ubah type data
data["ram"] = [x.replace("gb","") for x in data["ram"]] #menghilangkan kata gb
data["ram"] = data["ram"].map(lambda x: x.zfill(2)) #2 digit angka
data.sort_values("ram", axis=0, ascending=False, inplace=True)
data
```
![9](https://user-images.githubusercontent.com/86678205/154908331-78e4cffb-dbc1-48e1-abea-622105dd4448.PNG)

## Mengurutkan Data Berdasarkan Indeks
 - Dengan perintah fungsi .sort_values()
 - axis=0 artinya parameter untuk menunjukkan bahwa penghapusan dilakukan pada baris
 - inplace=True artinya parameter untuk menyatakan bahwa perubahan indeks tersebut langsung mengubah struktur DataFrame tersebut
 - ascending=False, Ascending adalah pengurutan dari yang terkecil ke yang terbesar tetapi disini perintahnya False jadi besar ke kecil
 
 #### Perintah untuk mengurutkan data berdasarkan Indeks

 ```http
data.sort_index(axis=0, ascending=False, inplace=True)
data
```
![12](https://user-images.githubusercontent.com/86678205/154908358-31cb0b29-c0f2-4248-acb5-1ec4b9a16ffa.PNG)

## Menghapus Nilai yang Hilang
 - Dengan perintah fungsi .dropna()
 - axis=0 artinya parameter untuk menunjukkan bahwa penghapusan dilakukan pada baris
 - inplace=True artinya parameter untuk menyatakan bahwa perubahan indeks tersebut langsung mengubah struktur DataFrame tersebut
 - parameter how=”any” menunjukkan bahwa penghapusan pada suatu baris dilakukan jika pada baris terdapat satu atau beberapa nilai NaN pada kolomnya
 
 #### Perintah untuk menghapus nilai yang hilang

 ```http
data.dropna(axis=0, how="any", inplace=True)
data
```
![14](https://user-images.githubusercontent.com/86678205/154908379-1f5ab4cf-51c7-49b9-a1fb-3bce77ee7442.PNG)

## Melakukan Iterasi pada DataFrame
 - Dengan perintah fungsi .iterrows()

 #### Perintah untuk melakukan iterasi pada DataFrame

 ```http
for i, baris in data.iterrows():
    print("indeks:", i, 
         "nama_kolom:", baris["nama_kolom"])
```
![15](https://user-images.githubusercontent.com/86678205/154908405-a38f89e3-dec8-4547-af5f-ddf1956f98f2.PNG)

## Mencari Data dengan Kriteria Tertentu
 - Dengan kriteria harga diatas 4 juta tampilkan

 #### Mencari Data dengan Kriteria Tertentu

 ```http
data = data[data["harga"] > 4000000]
data
```
![16](https://user-images.githubusercontent.com/86678205/154908422-5a09d746-a26d-42cc-a318-3ad45b7ccd8d.PNG)
