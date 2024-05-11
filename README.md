# PCD_UTS_202231003_2024_ITPLN

**Nama : Farrel Alfared Carasiola**


**NIM : 202231003** 


**Matakuliah : Pengolahan Citra Digital - A**<hr>


Sebelum melakukan pengolahan citra harus mempunyai file foto yang akan diproses, disini saya memberi nama file foto "namaku.jpg" yang telah diupload di folder PCD_UTS_202231003_2024_ITPLN<br>

Pengolahan citra adalah proses memanipulasi dan menganalisis gambar digital untuk meningkatkan kualitasnya, mengekstraksi informasi yang berguna, atau menghasilkan representasi visual baru dari data citra. Ini melibatkan serangkaian langkah atau teknik yang digunakan untuk memproses dan menganalisis gambar digital.

Berikut adalah beberapa tahapan dalam pengolahan citra pada laporan UTS:


1. Mempersiapkan Citra/Gambar<br>
Tahap mempersiapkan citra atau gambar adalah langkah awal dalam pemrosesan citra yang melibatkan pengambilan atau pemuatan citra ke dalam program, serta melakukan prapemrosesan awal yang diperlukan sebelum analisis atau manipulasi lebih lanjut.<br>
2. Memisahkan Warna (Warna Merah, Hijau, Biru)<br>
Memisahkan warna dalam sebuah gambar adalah proses untuk mendapatkan saluran warna individu, seperti merah, hijau, dan biru, dari gambar berwarna. Dalam gambar berwarna, setiap piksel direpresentasikan oleh kombinasi intensitas dari tiga saluran warna utama: merah, hijau, dan biru (RGB). <br> Dalam konteks ini, kita menggunakan operasi slicing pada array gambar untuk mendapatkan setiap saluran warna. Misalnya, jika kita memiliki gambar berwarna dalam format BGR (Blue-Green-Red), maka saluran warna merah akan berada di saluran indeks ke-2, saluran warna hijau akan berada di saluran indeks ke-1, dan saluran warna biru akan berada di saluran indeks ke-0.<br>
3. Analisi Hasil Histogram<br>
Analisis hasil histogram merupakan proses penting dalam pemrosesan gambar yang membantu dalam pemahaman distribusi intensitas piksel di dalam gambar. Tahap ini melibatkan peningkatan kualitas citra dengan cara meningkatkan kontras, pencahayaan, atau ketajaman. Teknik yang digunakan termasuk histogram equalization, sharpening, atau filter spesifik seperti filter Gauss untuk mengurangi noise.<br>
4. Proses Menemukan Nilai Batas Ambang<br>
Proses menemukan nilai batas ambang (thresholding) merupakan tahap dalam pengolahan citra di mana kita menentukan ambang batas tertentu untuk memisahkan piksel menjadi dua kelas berdasarkan intensitasnya. Tujuan dari thresholding adalah untuk memperoleh segmentasi citra yang memungkinkan untuk mengekstraksi fitur atau objek yang spesifik.<br>

- Penjelasan teori yang mendukung pada tahap mempersiapkan citra:<br>
  -> Contoh sederhana script mempersiapkan citra
  ```python
  import cv2
  import matplotlib.pyplot as plt

  color_image = img.imread('namaku.jpg')
  plt.imshow(color_image)
  ```
  ->Membaca Citra: Tahap pertama adalah membaca citra dari penyimpanan atau sumber lainnya. Citra dapat berasal dari berbagai sumber, seperti file gambar yang tersimpan di sistem file atau aliran video yang sedang direkam oleh kamera.<br>
  ->Format Citra: Citra dapat memiliki berbagai format file, seperti JPEG, PNG, atau TIFF. Setiap format memiliki struktur data yang berbeda dan dapat memengaruhi cara citra tersebut dibaca dan diinterpretasikan.<br>
->Konversi Warna: Setelah membaca citra, seringkali perlu untuk mengonversi skema warna citra ke format yang sesuai untuk analisis atau pemrosesan selanjutnya. Misalnya, jika citra awalnya dalam format RGB, namun analisis yang diinginkan membutuhkan format HSV, maka perlu dilakukan konversi dari RGB ke HSV.<br>
->Prapemrosesan Awal: Beberapa prapemrosesan awal mungkin diperlukan tergantung pada kebutuhan spesifik aplikasi. Ini bisa termasuk pemotongan (cropping) citra untuk menyesuaikan bidang pandang, pengurangan noise dengan filter, penyesuaian kecerahan dan kontras, atau transformasi lainnya untuk meningkatkan kualitas citra atau membuatnya lebih sesuai untuk analisis yang diinginkan.<br>
->Penampilan Awal: Sebelum melakukan analisis atau manipulasi lanjutan, seringkali berguna untuk menampilkan citra secara sementara untuk memverifikasi bahwa citra telah dibaca dan diproses dengan benar. Hal ini memungkinkan untuk memastikan bahwa langkah-langkah pemrosesan awal telah dilakukan dengan benar sebelum melanjutkan ke tahap selanjutnya.<br>
- Penjelasan teori yang mendukung pada tahap memisahkan warna:<br>
-> Contoh sederhana script memisahkan warna
  ```python
  red = color_image[:, :, 0]
  green = color_image[:, :, 1]
  blue = color_image[:, :, 2]
  ```
  Untuk mendapatkan tiga saluran warna terpisah dari gambar yang disimpan dalam variabel color_image. Variabel red, green, dan blue masing-masing berisi saluran warna merah, hijau, dan biru dari gambar. Dengan memisahkan saluran warna ini, kita dapat menganalisis atau memanipulasi setiap komponen warna secara terpisah, misalnya untuk deteksi warna tertentu atau untuk memperbaiki gambar.<br>

- Penjelasan teori yang mendukung pada tahap analisis histogram: <br>
  -> Contoh sederhana script analisis histogram
  ```python
  import cv2
  import numpy as np
  import matplotlib.pyplot as plt

  # Membaca gambar
  img = cv2.imread('gambar.jpg', cv2.IMREAD_GRAYSCALE)

  # Menghitung histogram
  histogram = cv2.calcHist([img], [0], None, [256], [0, 256])

  # Menampilkan histogram
  plt.plot(histogram, color='black')
  plt.title('Histogram Grayscale')
  plt.xlabel('Intensitas Piksel')
  plt.ylabel('Jumlah Piksel')
  plt.show()
  ```
-> Identifikasi distribusi intensitas adalah histogram menunjukkan sebaran intensitas piksel dalam gambar. Pada sumbu x, nilai intensitas piksel (dalam skala 0-255) diwakili, sedangkan pada sumbu y, jumlah piksel dengan intensitas tersebut ditampilkan. Dengan melihat histogram, kita dapat mengidentifikasi apakah gambar memiliki distribusi intensitas yang merata atau terkonsentrasi di area tertentu.<br>
-> Kontrast adalah histogram dapat membantu dalam mengevaluasi tingkat kontras dalam gambar. Kontras yang tinggi akan menghasilkan histogram yang tersebar luas di seluruh rentang intensitas, sementara kontras yang rendah akan menghasilkan histogram yang terkonsentrasi di area tertentu.<br>
-> Kompresi atau ekspansi dinamis adalah histogram juga dapat membantu dalam menentukan apakah gambar memanfaatkan seluruh rentang intensitas yang tersedia. Jika histogram tidak mencapai nilai maksimum dan minimum (0 dan 255), itu mungkin menunjukkan bahwa gambar perlu mengalami proses normalisasi untuk memanfaatkan seluruh rentang dinamis.<br>
-> Deteksi kecerahan dan ketidakseimbangan warna adalah dengan melihat distribusi intensitas di berbagai saluran warna (misalnya, merah, hijau, dan biru), kita dapat mengidentifikasi kecerahan relatif di setiap saluran. Hal ini dapat membantu dalam mendeteksi ketidakseimbangan warna atau kecenderungan warna tertentu dalam gambar.<br>
-> Deteksi kebisingan adalah histogram yang menunjukkan puncak kecil di luar kisaran intensitas utama dapat menunjukkan keberadaan kebisingan dalam gambar. Hal ini dapat membantu dalam menentukan apakah gambar memerlukan proses penghalusan atau pengurangan kebisingan.<br>

- Penjelasan teori yang mendukung pada tahap proses menemukan nilai batas ambang:<br>
  -> Contoh sederhana script mencari ambang batas
  ```python
  import cv2
  import matplotlib.pyplot as plt

  # Baca citra grayscale
  image = cv2.imread('gambar.jpg', cv2.IMREAD_GRAYSCALE)
  
  # Metode thresholding Otsu
  _, thresh = cv2.threshold(image, 0, 255, cv2.THRESH_BINARY + cv2.THRESH_OTSU)

  # Menampilkan citra asli dan hasil thresholding
  plt.figure(figsize=(10, 5))
  plt.subplot(1, 2, 1)
  plt.imshow(image, cmap='gray')
  plt.title('Citra Asli')
  plt.axis('off')
  
  plt.subplot(1, 2, 2)
  plt.imshow(thresh, cmap='gray')
  plt.title('Hasil Thresholding')
  plt.axis('off')

  plt.show()
  ```
<br>
-> Pemilihan Metode Thresholding adalah ada berbagai metode thresholding yang dapat dipilih tergantung pada sifat citra dan karakteristik objek yang ingin diekstraksi. Beberapa metode yang umum digunakan antara lain adalah: <br>
Threshold Global: Ambang batas dihitung secara global untuk seluruh citra; Threshold Otsu: Metode yang digunakan untuk menentukan ambang batas secara otomatis berdasarkan analisis histogram citra; Threshold Adaptif: Ambang batas yang berbeda-beda digunakan pada bagian-bagian citra yang berbeda untuk menangani variasi intensitas pencahayaan.<br>
-> Perhitungan Ambang Batas adalah ambang batas dapat dihitung secara manual atau otomatis. Dalam thresholding global, ambang batas sering kali ditentukan secara manual berdasarkan analisis histogram citra. Sementara dalam thresholding adaptif, ambang batas dapat disesuaikan secara dinamis tergantung pada konten lokal dari citra.<br>
-> Segmentasi Citra: Setelah nilai ambang batas ditentukan, proses thresholding membagi piksel citra menjadi dua kelas: piksel yang bernilai di atas ambang batas (objek) dan piksel yang bernilai di bawah ambang batas (latar belakang). Hasilnya adalah citra biner di mana objek atau fitur yang diminati dihighlight sebagai putih, sementara latar belakang menjadi hitam.<br>
-> Evaluasi dan Pemrosesan Lanjutan: Hasil dari thresholding sering kali memerlukan evaluasi lebih lanjut atau pemrosesan lanjutan, seperti operasi morfologi untuk membersihkan dan meningkatkan segmentasi, atau ekstraksi fitur untuk mengidentifikasi objek yang relevan. <br>

- Penjelasan teori yang mendukung pada tahap proses citra kontras,:<br>
 -> Contoh sederhana script proses citra kontras
  ```python
  import cv2
  import matplotlib.pyplot as plt

  # Membaca gambar
  img = cv2.imread('contoh.jpg')

  # Konversi warna BGR ke RGB (karena OpenCV membaca gambar dalam format BGR)
  img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

  # Menambahkan kontras
  alpha = 1.5  # Faktor penambahan kontras
  adjusted_img = cv2.convertScaleAbs(img, alpha=alpha, beta=0)

  # Menampilkan hasil
  plt.figure(figsize=(10, 6))

  plt.subplot(1, 2, 1)
  plt.imshow(img_rgb)
  plt.title('Gambar Asli')
  plt.axis('off')

  plt.subplot(1, 2, 2)
  plt.imshow(adjusted_img)
  plt.title('Gambar dengan Kontras Ditambahkan')
  plt.axis('off')

  plt.show()
  ```
 -> Membaca Gambar adalah langkah pertama adalah membaca gambar yang akan diproses. Gambar ini dapat diambil dari berbagai sumber, seperti file lokal atau sumber online.<br>
 -> Konversi Warna adalah pada saat setelah gambar dibaca, langkah selanjutnya adalah mengonversinya ke ruang warna yang sesuai. Dalam contoh ini, gambar dibaca dalam format BGR (Blue-Green-Red), tetapi untuk keperluan pemrosesan lebih lanjut, kita perlu mengonversinya ke ruang warna lain, seperti RGB (Red-Green-Blue) atau HSV (Hue-Saturation-Value). Konversi warna ini dapat dilakukan menggunakan fungsi cv2.cvtColor().<br>
 -> Penambahan Kontras adalah proses penambahan kontras dilakukan setelah konversi warna. Hal ini dapat dicapai dengan berbagai metode, salah satunya adalah dengan meningkatkan perbedaan antara intensitas piksel yang ada. Metode yang paling sederhana adalah dengan mengalikan setiap nilai piksel dengan skalar tertentu. Namun, ada juga metode lain yang lebih kompleks dan dapat memberikan hasil yang lebih baik, seperti transformasi histogram atau teknik pemetaan logaritmik.<br>
 -> Menampilkan Hasil adalah setelah proses penambahan kontras selesai, hasilnya kemudian ditampilkan kembali menggunakan fungsi plt.imshow(). Ini memungkinkan kita untuk melihat efek dari proses penambahan kontras pada gambar.
