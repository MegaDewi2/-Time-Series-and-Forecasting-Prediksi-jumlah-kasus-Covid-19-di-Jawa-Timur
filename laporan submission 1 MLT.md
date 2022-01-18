# Laporan Proyek Machine Learning - Mega Dewi Giridrawardani
 
## Domain Proyek
Domain: Kesehatan
 
Dalam masa pandemi seperti sekarang ini, menjaga kesehatan merupakan hal yang sangat penting. Bukan hanya kesehatan fisik, kesehatan
mental juga dijaga agar dapat bertahan pada masa pandemi. Selama masa pandemi ini, kita juga harus mentaati anjuran pemerintah untuk
mematuhi protokol kesehatan guna memutus rantai penyebaran virus corona. Kasus positif covid-19 Indonesia masih terbilang tinggi yaitu sebanyak
4.223.094 (https://covid19.go.id/)
- Masalah yang ingin saya angkat dalam domain ini adalah masalah virus corona (Covid-19). Yang ingin dibahas adalah bagaimana pertumbuhan virus corona setiap harinya. Hal ini dapat membantu pemerintah khususnya untuk menganalisis agar menemukan solusi yang cepat dan tepat dalam
menangani pandemi covid-19. Dengan adanya data masyarakat dapat melihat bagaimana perkembangan virus corona setiap harinya untuk mengetahui jumlah
kasus yang ada disekitar agar lebih berhati-hati.
- Berdasarkan survei AC Nielsen bekerjasama dengan UNICEF pada 6 kota besar di Indonesia dengan jumlah 2000 responden menggali tentang
sikap masyarakat terkait pencegahan COVID-19 pada kehidupan sehari-hari. Hasilnya,  69.6% responden di 6 kota besar di Indonesia mengaitkan
COVID-19 dengan aspek negatif seperti, berbahaya, menular, darurat, mematikan, menakutkan, khawatir, wabah, pandemi, dan penyakit. Dari survei
ini, terlihat bahwa masyarakat sadar bagaimana COVID-19. Hal ini mengarahkan perilaku positif masyarakat dalam mencegah penularan COVID-19.
(https://covid19.go.id/berita/memahami-perilaku-dan-informasi-tepat-untuk-mencegah-penularan-covid-19)
 
## Business Understanding
Masalah yang ingin diangkat adalah mengenai pandemi Covid-19. Penyebaran virus corona di Indonesia masih terbilang tinggi dilihat dari data dari https://covid19.go.id/. Pada bulan Juli 2021 Jawa Timur mengalami peningkatan hingga di angka 2500 kasus positif. Jawa Timur juga menjadi kota dengan kasus kematian tertinggi di Indonesia.
### Problem Statement
- Bagaimana perkembangan dari virus corona hingga tanggal 09 Juli 2021 di Jawa Timur menggunakan algoritma LSTM?
- Bagaimana prediksi kasus aktif virus corona pada beberapa tahun kedepan (10 Juli 2021 hingga 04 April 2024)?
 
### Goals
Memprediksi bagaimana perkembangan virus corona di Jawa Timur yang dapat menjadi pertimbangan dalam mengambil keputusan untuk menekan peningkatan kasus virus vorona.
 
### Solution Statement
- **LSTM** merupakan salah satu jenis dari Recurrent Neural Network (RNN). LSTM sendiri dapat mengingat informasi dalam jangka panjang.
LSTM dikembangankan sebagai solusi daari masalah gradien yang mengecil hingga layer terakhir membuat nilai bobot tidak berubah sehingga
tidak pernah menghasilkan hasil yang lebih baik. Masalah ini sering ditemukan di RNN Konvensional yang disebut dengan Vanishing gradient.
Dalam memproses input data, terdapat beberapa langkah dalam LSTM
- Forget gate, pada bagian ini informasi yang kurang dibutuhkan akan dihapus menggunakan fungsi sigmoid
- Input gate, pada langkah ini informasi akan diolah dimana informasi akan di pilah dan ditentukan mana yang dapat diperbarui ke cell state
menggunakan fungsi aktivasi sigmoid.
  - Cell state, informasi akan diperbarui.
  - Output gate, Dengan menjalankan fungsi sigmoid untuk menghasilkan nilai output pada hidden state dan menempatkan cell state pada tanh.
Fungsi tanh sendiri digunakan untuk mengatur nilai pada jaringan yang berada antara -1 dan 1.
 
## Data Understanding
Data yang saya gunakan merupakan data time series Covid-19 di Indonesia. Data ini terdiri dari 41 kolom dan 16.283 baris. Data dimulai
dari tanggal 1 Agustus 2020 hingga 7 September 2021. Dataset ini saya dapatkan dari Kaggle (https://www.kaggle.com/hendratno/covid19-indonesia).
 
Variabel-variabel pada Covid-19 Indonesia Time Series adalah sebagai berikut:
- **Date** : merupakan tanggal pelaporan kasus Covid-19.
- **Location ISO Code** : merupakan kode lokasi berdasarkan standar ISO
- **Location** : merupakan nama lokasi kasus Covid-19 (provinsi).
- **New Cases** : merupakan kasus positif baru Covid-19 setiap harinya
- **New Deaths** : merupakan kasus kematian pasien Covid-19 baru setiap harinya
- **New Recovered** : merupakan kesembuhan pasien Covid-19 baru setiap harinya
- **New Active Cases** : merupakan kasus baru Covid-19 yang aktif setiap harinya
- **Total Cases** : merupakan total kasus positif Covid-19 hingga tanggal terkait
- **Total Deaths** : merupakan total kasus kematian pasien Covid-19 hingga tanggal terkait
- **Total Recovered** : merupakan total kesembuhan pasien Covid-19 hingga tanggal terkait
- **Total Active Cases** : merupakan total kasus aktif Covid-19 hingga tanggal terkait
- **City or Regency** : merupakan nama kota dari lokasi
- **Province** : merupakan nama provinsi dari lokasi
- **Continent** : merupakan nama benua dari lokasi
- **Island** : merupakan nama pulau dari lokasi
- **Time Zone** : merupakan zona waktu dari lokasi
- **Special Status** : merupakan daerah khusus dari lokasi
- **Total Regencies** : merupakan jumlah kabupaten dari lokasi
- **Total Cities** : merupakan jumlah kota dari lokasi
- **Total Districts** : merupakan jumlah kecamatan dari lokasi
- **Total Urban Village** : merupakan jumlah kelurahan dari lokasi
- **Total Rural Village** : merupakan jumlah desa dari lokasi
- **Area (km2)** : merupakan luar area dari lokasi
- **Population** : merupakan jumlah populasi dari lokasi
- **Population Density** : merupakan kepadatan penduduk di lokasi (population / area)
- **Longitude** : merupakan garis bujur lokasi
- **Latitude** : merupakan garis lintang lokasi
- **New Cases Per Million** :  merupakan kasus positif Covid-19 per juta ((New cases / population) * 1.000.000)
- **Total Cases Per Million** : merupakan jumlah kasus positif Covid-19 per juta ((Total cases / population) * 1.000.000)
- **New Deaths Per Million** : merupakan  kasus kematian pasien baru Covid-19 per juta ((New deaths / population) * 1.000.000)
- **Total Deaths Per Million** : merupakan jumlah kasus kematian pasien Covid-19 per juta ((Total deaths / population) * 1.000.000)
- **Case Fatality Rate** : merupakan tingkat kasus kematian pasien Covid-19 ((Total deaths / total cases) * 100)
- **Case Recovered Rate** : merupakan tingkat kesembuhan pasien Covid-19 ((Total recovered / total cases) * 100)
- **Growth Factor of New Cases** : merupakan faktor pertumbuhan kasus baru Covid-19. Tingkat kasus kematian dibawah 1 berarti menurun, 1 berarti datar, di atas 1 berarti meningkat. (Kasus baru hari ini / Kasus baru kemarin)
- **Growth Factor of New Deaths** : merupakan faktor pertumbuhan kematian pasien Covid-19. merupakan faktor pertumbuhan kasus baru Covid-19. Tingkat kasus kematian dibawah 1 berarti menurun, 1 berarti datar, di atas 1 berarti meningkat. (Kasus kematian Hari Ini / Kasus kematian Kemarin)
 
Dalam memahami data juga saya melakukan visualisasi data yang menampilkan 5 kota dengan kasus positif, kematian, dan kesembuhan tertinggi.
 - 5 Kota dengan kasus positif tertinggi
 
    <img width="378" alt="aktif" src="https://user-images.githubusercontent.com/50202220/136475489-09cb4441-27fe-494f-a68b-68af478f3573.png">
 
 - 5 Kota dengan kasus kematian tertinggi
 
    <img width="365" alt="deaths" src="https://user-images.githubusercontent.com/50202220/136475567-414e0cbd-c4b3-4283-8356-630ca128991b.png">
 
 - 5 Kota dengan kesembuhan tertinggi
 
    <img width="382" alt="recovery" src="https://user-images.githubusercontent.com/50202220/136475598-6b08516d-ae6a-4781-8926-702370708bb0.png">
 
 
 ## Data Preparation
- Pengurangan fitur : Dataset yang digunakan terdiri dari 41 kolom atau fitur dan tidak semua fitur dibutuhkan. Saya menghapus kolom-kolom yang tidak dibutuhkan hingga tersisa 16 kolom saja dengan fungsi menggunakan fungsi drop.
- Mengganti nama kolom : Untuk mempermudah penulisan program saya mengganti nama semua kolom, dimana sebelumnya nama kolom terdapat spasi
lalu  mengganti spasi dengan simbol underscore dan mengubah huruf menjadi huruf kecil. (ex. New Cases -> new_cases)
- Mengganti tipe data : Kolom date pada dataset sebelumnya memiliki tipe data object lalu  mengubahnya menjadi bertipe data datetime.
- Scaling : menggunakan minmaxscaler  yaitu mengubah rentang dari antar 0-1. Scaling ini dilakukan untuk menyamakan rentang antar data
yang digunakan
- Karena disini saya ingin prediksi Kasus Covid-19 di Jawa Timur maka saya membuat dataframe baru dimana (Location == Jawa Timur)
- Menghapus data duplicate
 
 
## Modelling
Dalam menyelesaikan masalah ini saya menggunakan model LSTM (Long Short Term Memory). Saya menggunakan fitur 'date' sebagai nilai X dan
fitur 'New Cases' sebagai nilai y.
- Train test split : Disini saya menginisialisasi nilai X_train, X_test, y_train, dan y_test. Dimana jumlah data testing merupakan 20% dari keseluruhan data jawa timur
- Membuat fungsi baru agar data terbaca oleh model. Fungsi yang dibuat dapat menerima sebuah series/atribut kita yang telah di konversi
menjadi tipe numpy, lalu mengembalikan label dan atribut dari dataset dalam bentuk batch.
- Untuk arsitektur model saya menggunakan 2 layer LSTM dengan 60 neuron.
- Menambahkan dropout untuk menghindari overfit dengan rate 0.05 dan 0.2
- Terdapat 2 Lapisan dense pertama digunakan untuk menghasilkan prediksi dalam model dengan 30 neuron dan menggunakan fungsi aktivasi Relu
- Lapisan terakhir merupakan lapisan keluaran dengan 1 neuron.
- Optimizer yang digunakan adalah Adam dengan learning rate = 1.0000e-04. Semakin kecil learning rate maka akan semakin bagus pula hasilnya.
- Loss function yang digunakan Huber yang umum digunakan untuk data time series.
- Matriks evaluasi dari model adalah nilai MAE (Mean Absolute Error)
- Menambah fungsi callback dari keras untuk menghindari overfit juga
Hasil prediksi dengan model LSTM terbilang baik karena menghasil nilai loss dan MAE yang sangat kecil dimana nilai MAEnya kurang dari 0.1.
 
## Evaluation
Evaluasi dalam model ini adalah nilai MAE
- MAE merupakan singkatan dari Mean Absolute Error yang menunjukkan nilai kesalah rata-rata dari nilai yang sebenarnya dan nilai prediksi. Hasil yang dihasilkan dengan model LSTM terbilang sangat bagus. Nilai MAE yang dihasilkan dibawah 0.1. Dengan epochs sebanyak 50 menghasilkan nilai train MAE 0.0304 dan validation MAE 0.0950.
 
- Dalam program kita dapat mengimplementasikan pada saat mengkompilasi program dengan kode sebagai berikut:
 
  ```
  optimizer = tf.keras.optimizers.Adam(lr=1.0000e-04)
  model.compile(loss=tf.keras.losses.Huber(),
                optimizer=optimizer,
                metrics=["mae"])
  ```
 
- Berikut rumus dari MAE:
 
  <img width="142" alt="rumusmae" src="https://user-images.githubusercontent.com/50202220/136475619-47ae7186-2f1e-4693-b7fd-6650264bd258.png">
 
  Dari rumus diatas terlihat bahwa nilai MAE didapatkan dari nilai prediksi dikurangi dengan nilai sebenarnya lalu dibagi dengan jumlah data.
 
 
 
 
 
 
 

