
# GEOMETRIX CITRA

Geometrix Citra atau Geometric Image Processing adalah cabang dari pengolahan citra yang berfokus pada manipulasi geometris dari gambar digital. Tujuannya adalah untuk mengubah atau memanipulasi posisi, ukuran, orientasi, dan bentuk dari objek atau gambar yang terdapat dalam citra digital. Teknik-teknik dalam geometrix citra mencakup rotasi, resize, cropping, flipping, translation. 


## Teknik-teknik dalam geometrix citra mencakup:
### 1. Rotasi Gambar
**Rotasi gambar** adalah teknik untuk mengubah orientasi atau posisi gambar dengan memutar gambar terhadap titik pusat rotasi. Rotasi bisa dilakukan dalam berbagai sudut, seperti 90 derajat searah jarum jam atau berlawanan arah jarum jam, atau sudut-sudut lainnya tergantung pada kebutuhan. Misalnya, dalam pengolahan medis, rotasi bisa digunakan untuk menyesuaikan gambar rontgen agar sesuai dengan pandangan yang diinginkan oleh dokter atau untuk memperbaiki orientasi visual dalam aplikasi desain grafis.

### 2. Resize (Perubahan Ukuran)
**Resize** adalah proses mengubah ukuran dimensi gambar. Ini bisa dilakukan dengan mempertahankan rasio aspek (aspect ratio) agar gambar tidak terdistorsi, atau tanpa mempertahankan rasio aspek untuk mengubah proporsi gambar secara keseluruhan. Resize sering digunakan dalam aplikasi web untuk mengatur ukuran gambar yang akan ditampilkan, dalam pemrosesan gambar medis untuk memperbesar detail tertentu, atau dalam desain grafis untuk menyesuaikan ukuran objek visual.

### 3. Cropping (Pemotongan)
**Cropping** adalah teknik untuk menghilangkan bagian tertentu dari gambar untuk mengubah komposisi atau fokus visual. Ini dilakukan dengan memilih area tertentu dari gambar dan menghapus area yang tidak diinginkan. Misalnya, dalam fotografi, cropping digunakan untuk memusatkan perhatian pada subjek utama dengan menghilangkan latar belakang yang mengganggu. Pemotongan juga digunakan dalam pengolahan citra untuk mempersiapkan gambar untuk analisis lebih lanjut atau untuk menghasilkan komposisi visual yang lebih dramatis.

### 4. Flipping (Pembalikan)
**Flipping** melibatkan pembalikan arah gambar, baik secara horizontal (flip horizontal) atau vertikal (flip vertical). Teknik ini berguna untuk menciptakan efek cermin atau untuk memperbaiki orientasi visual dari gambar. Misalnya, flip horizontal dapat digunakan untuk memperbaiki orientasi sebuah objek dalam gambar agar sesuai dengan sudut pandang yang diinginkan. Flipping juga sering digunakan dalam animasi, grafika komputer, dan desain untuk menciptakan variasi dalam tampilan visual atau untuk mencocokkan orientasi objek dengan kebutuhan desain.

### 5. Translation (Pergeseran)
**Translation** adalah teknik untuk memindahkan seluruh gambar dalam koordinat tertentu. Ini bisa dilakukan untuk mengubah posisi relatif dari objek dalam gambar atau untuk mengatur ulang komposisi visual. Misalnya, dalam aplikasi augmented reality, translation digunakan untuk menyesuaikan posisi objek virtual dengan lingkungan nyata. Teknik ini juga berguna dalam analisis citra untuk mengkoreksi pergeseran atau untuk mengatur posisi objek dalam kanvas visual.

## Tahapan Cara Menyelesaikan Projek

### 1.Pengambilan Foto 
- Ambil foto diri dari jarak minimal 1 meter.
- Simpan gambar dalam format yang sesuai, misalnya JPEG atau PNG.

### 2. Implementasi Code untuk Geometrix Citra
#### Mengimport Library

``` 
import cv2

import matplotlib.pyplot as plt

import numpy as np 
```
**Penjelasan:**
- **import cv2:** Ini mengimpor pustaka OpenCV (cv2) yang digunakan untuk pengolahan gambar dan video. OpenCV adalah pustaka open-source yang umum digunakan untuk aplikasi pengolahan gambar komputer dan penglihatan komputer.

- **import matplotlib.pyplot as plt:** Ini mengimpor modul pyplot dari pustaka Matplotlib. Matplotlib adalah pustaka visualisasi data yang kuat di Python. Modul pyplot menyediakan fungsi-fungsi untuk membuat plot dan visualisasi data dengan cara yang mirip dengan MATLAB.

- **import numpy as np:** Ini mengimpor pustaka NumPy (np), yang adalah pustaka fundamental untuk komputasi numerik di Python. NumPy menyediakan struktur data array yang efisien dan operasi matematika yang kuat untuk bekerja dengan data numerik.

#### Membaca Gambar 
```
img = cv2.imread('foto.jpg')
img = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
```
**Penjelasan:**
- **cv2.imread('foto.jpg')** adalah fungsi OpenCV untuk membaca gambar dari file 'foto.jpg'. Ini menyimpan gambar dalam variabel img, dengan format standar BGR (Blue, Green, Red) yang digunakan oleh OpenCV secara default.

- **cv2.cvtColor(img, cv2.COLOR_BGR2RGB)** mengubah gambar img dari format BGR ke RGB, karena format RGB lebih umum digunakan dalam aplikasi pengolahan gambar di Python seperti Matplotlib.

#### Merotasikan Gambar
```
angle = 45
height, width = img.shape[:2]
center = (width // 2, height // 2)
rotation_matrix = cv2.getRotationMatrix2D(center, angle, 1.0)
rotated_img = cv2.warpAffine(img, rotation_matrix, (width, height))
```
**Penjelasan:**
- **angle = 45:** Variabel angle menyimpan nilai sudut rotasi yang diinginkan, dalam hal ini 45 derajat.

- **height, width =** img.shape[:2]: img.shape memberikan dimensi gambar dalam format (tinggi, lebar, jumlah saluran warna). Dengan [:2], kita mengambil hanya tinggi dan lebar gambar. Variabel height menyimpan tinggi gambar dan width menyimpan lebar gambar.

- **center = (width // 2, height // 2):** center adalah titik pusat rotasi, yang dihitung berdasarkan setengah dari lebar dan tinggi gambar. Ini penting karena rotasi akan dilakukan terhadap titik ini.

- **rotation_matrix = cv2.getRotationMatrix2D(center, angle, 1.0):** cv2.getRotationMatrix2D() mengembalikan matriks rotasi berdasarkan center, angle, dan faktor skala (dalam hal ini 1.0 yang artinya tidak ada perubahan skala).

- **rotated_img = cv2.warpAffine(img, rotation_matrix, (width, height)):** cv2.warpAffine() digunakan untuk menerapkan transformasi affin (termasuk rotasi) pada gambar menggunakan matriks rotasi yang telah diperoleh dari cv2.getRotationMatrix2D(). Hasilnya disimpan dalam variabel rotated_img.

#### Mengubah Ukuran Gambar
```
new_width = 400
new_height = 800
resized_img = cv2.resize(img, (new_width, new_height))
```
**Penjelasan:**
- **new_width = 400:** Variabel new_width menyimpan nilai lebar baru yang diinginkan untuk gambar hasil resize, dalam hal ini 400 piksel.

- **new_height = 800:** Variabel new_height menyimpan nilai tinggi baru yang diinginkan untuk gambar hasil resize, dalam hal ini 800 piksel.

- **resized_img = cv2.resize(img, (new_width, new_height)):** cv2.resize() adalah fungsi OpenCV yang digunakan untuk meresize gambar img menjadi ukuran yang baru ditentukan oleh tuple (new_width, new_height). Hasilnya disimpan dalam variabel resized_img.

#### Mengcrop Gambar
```
start_x = 0
end_x = 900
start_y = 0
end_y = 800
cropped_img = img[start_y:end_y, start_x:end_x]
```
**Penjelasan:**
- **start_x = 0:** Variabel start_x menentukan posisi awal (indeks kolom) dari mana proses pemotongan dimulai, dalam hal ini dimulai dari kolom ke-0.

- **end_x = 900:** Variabel end_x menentukan posisi akhir (indeks kolom + 1) di mana proses pemotongan berakhir, dalam hal ini sampai kolom ke-899 (karena slicing di Python berakhir sebelum indeks yang ditentukan).

- **start_y = 0:** Variabel start_y menentukan posisi awal (indeks baris) dari mana proses pemotongan dimulai, dalam hal ini dimulai dari baris ke-0.

- **end_y = 800:** Variabel end_y menentukan posisi akhir (indeks baris + 1) di mana proses pemotongan berakhir, dalam hal ini sampai baris ke-799.

- **cropped_img = img[start_y:end_y, start_x:end_x]:** Ini adalah operasi slicing pada array NumPy (gambar img), yang efektif melakukan pemotongan (cropping) pada gambar. Dengan menggunakan indeks yang ditentukan (start_y:end_y untuk baris dan start_x:end_x untuk kolom), kita memotong bagian gambar yang diinginkan dari img. Hasilnya disimpan dalam variabel cropped_img.

#### Pencerminan Gambar
```
flipped_img = cv2.flip(img, 1)
```
**Penjelasan:**
- **flipped_img = cv2.flip(img, 1)** menggunakan fungsi cv2.flip() dari OpenCV untuk melakukan flipping horizontal pada gambar img. Proses flipping ini memanipulasi gambar dengan membalikkan piksel-pikselnya secara horizontal, mirip dengan cerminan horizontal dari gambar asli. Dengan menggunakan parameter 1 pada cv2.flip(), yang menunjukkan flipping horizontal, hasilnya adalah flipped_img yang berisi gambar img yang telah dimodifikasi sesuai dengan operasi flipping yang dilakukan. 

#### Translasi Gambar
```
tx = 100
ty = 100
translation_matrix = np.float32([[1, 0, tx], [0, 1, ty]])
translated_img = cv2.warpAffine(img, translation_matrix, (width, height))
```
**Penjelasan:**
- **tx = 100:** Variabel tx menentukan jumlah pergeseran (translasi) dalam sumbu x, dalam hal ini sebesar 100 piksel.

- **ty = 100:** Variabel ty menentukan jumlah pergeseran (translasi) dalam sumbu y, dalam hal ini sebesar 100 piksel.

- translation_matrix = np.float32([[1, 0, tx], [0, 1, ty]]) menggunakan fungsi np.float32() dari NumPy untuk membuat matriks transformasi translasi 2D. Matriks ini, [[1, 0, tx], [0, 1, ty]], memiliki komponen sebagai berikut:
    - 1, 0: Menunjukkan skala untuk sumbu x, yang berarti tidak ada perubahan skala dalam arah sumbu x.
    - 0, 1: Menunjukkan skala untuk sumbu y, yang berarti tidak ada perubahan skala dalam arah sumbu y.
    - tx, ty: Menunjukkan jumlah pergeseran untuk sumbu x dan sumbu y, masing-masing.

- **translated_img = cv2.warpAffine(img, translation_matrix, (width, height))** menggunakan fungsi cv2.warpAffine() dari OpenCV untuk menerapkan transformasi translasi pada gambar img. Transformasi translasi ini didasarkan pada matriks translation_matrix, yang telah didefinisikan sebelumnya menggunakan np.float32() dari NumPy. Matriks ini, [[1, 0, tx], [0, 1, ty]], menentukan jumlah pergeseran untuk sumbu x (tx) dan sumbu y (ty). Hasil dari operasi cv2.warpAffine() adalah translated_img, yang merupakan gambar img yang telah dipindahkan sesuai dengan nilai tx dan ty. Ukuran gambar hasil setelah translasi, (width, height), diambil dari dimensi gambar asli menggunakan img.shape[:2].

#### Menampilkan Output
```
fig, axs = plt.subplots(2, 3, figsize=(12, 8))
axs = axs.ravel()

axs[0].imshow(img)
axs[0].set_title('Citra Asli')

axs[1].imshow(rotated_img)
axs[1].set_title('After Rotated')

axs[2].imshow(resized_img)
axs[2].set_title('After Resized')

axs[3].imshow(cropped_img)
axs[3].set_title('After Cropped')

axs[4].imshow(flipped_img)
axs[4].set_title('After Flipped')

axs[5].imshow(translated_img)
axs[5].set_title('After Translated')

plt.tight_layout()
plt.show()

```
**Penjelasan:**

- **Membuat Subplot: plt.subplots(2, 3, figsize=(12, 8))** menghasilkan sebuah figur (fig) yang terdiri dari 2 baris dan 3 kolom subplot. figsize=(12, 8) menentukan ukuran figur dalam inci (lebar x tinggi).

- **Mengatur Plotting Area: axs = axs.ravel()** mengubah array 2D axs menjadi array 1D, memudahkan untuk mengakses setiap subplot secara langsung.

- *Menampilkan Gambar:** Setiap subplot ditetapkan untuk menampilkan hasil dari transformasi gambar:

     - **axs[0].imshow(img):** Menampilkan gambar asli.
     - **axs[1].imshow(rotated_img):** Menampilkan gambar setelah rotasi.
     - **axs[2].imshow(resized_img):** Menampilkan gambar setelah diresize.
     - **axs[3].imshow(cropped_img):** Menampilkan gambar setelah dipotong.
     - **axs[4].imshow(flipped_img):** Menampilkan gambar setelah diflip.
     - **axs[5].imshow(translated_img):** Menampilkan gambar setelah translasi.
- **Judul Subplot:** Setiap subplot diberi judul yang sesuai menggunakan set_title().

- **Penyesuaian Layout: plt.tight_layout()** mengatur penempatan subplot secara otomatis agar lebih rapi.

- **Menampilkan Plot: plt.show()** menampilkan figur dengan semua subplot yang telah disiapkan.




