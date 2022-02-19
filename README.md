
# Python - Pandas DataFrame

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

## Mengubah Nama Kolom
 - Dengan perintah fungsi .rename()
 - Kolom/field yang digunakan sebagai pengganti indeks tidak bisa ikut diganti/diubah
 - inplace=True artinya parameter untuk menyatakan bahwa perubahan indeks tersebut langsung mengubah struktur DataFrame tersebut

 #### Perintah untuk mengubah nama kolom

 ```http
data.rename(columns = {"kode" : "ID", "produsen" : "merek", "kategori" : "series"}, inplace = True)
data
```

## Mengubah Nama Indeks
 - Dengan perintah fungsi .rename()
 - inplace=True artinya parameter untuk menyatakan bahwa perubahan indeks tersebut langsung mengubah struktur DataFrame tersebut

 #### Perintah untuk mengubah nama indeks

 ```http
data.rename(index = {3 : "AWAL", 58 : "AKHIR", 4 : 4},inplace=True) 
data
```

## Mengakses beberapa Kolom beserta datanya
 - Dengan perintah fungsi .filter()

 #### Perintah untuk mengakses beberapa kolom beserta datanya

 ```http
data = data.filter(items=["nama_kolom1", "nama_kolom2", "nama_kolom3"])
data
```

## Mengurutkan Data di Kolom tertentu
 - Dengan perintah fungsi .sort_values()
 - .astype() perintah fungsi untuk mengubah type data
 - .replace() perintah fungsi untuk mengganti kata/kalimat/huruf/angka
 - .map()
 - .zfill()
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

## Melakukan Iterasi pada DataFrame
 - Dengan perintah fungsi .iterrows()

 #### Perintah untuk melakukan iterasi pada DataFrame

 ```http
for i, baris in data.iterrows():
    print("indeks:", i, 
         "nama_kolom:", baris["nama_kolom"])
```

## Mencari Data dengan Kriteria Tertentu
 - Dengan kriteria harga diatas 4 juta tampilkan

 #### Mencari Data dengan Kriteria Tertentu

 ```http
data = data[data["harga"] > 4000000]
data
```
