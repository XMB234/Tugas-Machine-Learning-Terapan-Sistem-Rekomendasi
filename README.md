# Sistem Rekomendasi Obat Pengganti Menggunakan Teknik Contend Based Filtering - Al Hadi Busra
## Project Overview
Obat merupakan bahan kimia selain zat gizi atau bahan makanan yang diperlukan yang bila diberikan pada makhluk hidup, dapat menimbulkan efek biologis. Obat memiliki peran yang sangat penting bagi makhluk hidup, terutama dalam menjaga kesehatan dan mengobati berbagai penyakit. Bagi manusia, obat digunakan untuk mencegah, mengobati, atau mengurangi gejala penyakit, serta membantu pemulihan setelah operasi atau cedera. Selain itu, obat juga dapat digunakan untuk mengatur kondisi tubuh yang tidak seimbang, seperti hormon atau gula darah, sehingga tubuh dapat berfungsi normal. Secara umum, obat membantu makhluk hidup untuk tetap sehat, memperbaiki kerusakan tubuh, dan meningkatkan daya tahan tubuh terhadap penyakit.Namun, meskipun obat memiliki peran yang sangat vital, masalah ketersediaan obat sering kali menjadi tantangan besar.

Kekurangan obat merupakan masalah serius dalam sistem kesehatan yang disebabkan oleh berbagai faktor, seperti gangguan produksi, kekurangan bahan baku, hingga penarikan obat dari peredaran. Di negara berpendapatan menengah ke bawah, masalah ini diperparah oleh kendala lisensi, keterbatasan produksi lokal, dan penyelundupan obat. Dampaknya bisa signifikan terhadap perawatan pasien dan kinerja layanan kesehatan. Salah satu solusi untuk mengatasi masalah ini adalah penggunaan obat pengganti, yaitu obat yang memiliki efek serupa dengan obat utama namun lebih mudah diakses atau diproduksi. Obat pengganti dapat menjadi alternatif efektif, terutama dalam situasi darurat atau wilayah dengan distribusi terbatas. Meski begitu, penting untuk memastikan kualitas dan efektivitasnya agar standar perawatan tetap terjaga.

Meskipun obat pengganti dapat menjadi solusi atas kekurangan obat, penggunaannya menghadapi tantangan, terutama dalam hal kesamaan indikasi, kandungan, dan efektivitas. Tidak semua obat pengganti memberikan efek terapeutik yang setara karena perbedaan komposisi, cara kerja, atau dosis, yang dapat memengaruhi respons tubuh, terutama pada pasien dengan kondisi medis spesifik seperti penyakit kronis atau gangguan serius. Oleh karena itu, dibutuhkan sebuah sistem yang mampu mengidentifikasi dan menganalisis persamaan antar obat secara menyeluruh. Sistem ini harus dapat mengevaluasi berbagai aspek penting dari suatu obat, seperti kandungan zat aktif, bentuk sediaan, dosis, serta indikasi penggunaannya, untuk menentukan apakah suatu obat dapat berfungsi sebagai pengganti dari obat lain. Selain itu, proses pencarian obat pengganti ini memakan banyak waktu jika dilakukan secara manual.

Dalam bidang machine learning, terdapat sebuah cabang keilmuan yang sangat relevan untuk menangani permasalahan kekurangan obat dan pemilihan alternatifnya, yaitu sistem rekomendasi (recommender system). Sistem rekomendasi merupakan teknik yang dirancang untuk menyarankan pilihan terbaik kepada pengguna berdasarkan preferensi, kebutuhan, atau kesamaan karakteristik dari item yang tersedia. Dalam konteks masalah obat, sistem rekomendasi dapat dimanfaatkan untuk memberikan saran obat pengganti yang paling sesuai ketika obat utama tidak tersedia.

Dengan menggunakan sistem rekomendasi, proses pencarian obat alternatif tidak lagi dilakukan secara manual yang memakan waktu, tetapi dapat dilakukan secara otomatis dan cepat dengan mempertimbangkan berbagai faktor penting, seperti kesamaan kandungan zat aktif, indikasi medis, kategori dan sebangainya. Pada project ini, akan dibuat sebuah sistem rekomendasi obat pengganti yang merekomendasikan obat berdasarak kemiripan fitur antar obat.

## Business Understanding
### Problem Statements
Untuk membuat sistem rekomendasi yang dapat mencarai pengganti obat, terdapat beberapa dua permasalahan utama, yaitu:
* Bagaimana cara membuat sistem rekomendasi pengganti obat berdasarkan kemiripan fitur antar obat
### Goals
Untuk menyelesaikan permasalahan tersebut, akan dibuat sebuah sistem rekomendasi yang terfokus pada tujuan berikut:
* Sistem yang dapat memberikan rekomendasi obat pengganti yang tepat berdasarkan kesaaman fitur antar obat.
### Solutions Statements
Untuk mencapai tujuan tersebut, maka akan digunakan:
* Teknik _content based filtering_. Ini merupakan salah satu teknik yang digunakan dalam sistem rekomendasi untuk menyarankan item kepada pengguna berdasarkan kesamaan atribut atau fitur yang ada pada item tersebut. Teknik ini cocok digunakan untuk kasus sistem rekomendasi pengganti obat.  Teknik ini bekerja dengan menganalisis karakteristik atau atribut dari obat utama, seperti kandungan zat aktif, indikasi,kategori dan lain-lain. Kemudian mencocokkannya dengan obat lain yang memiliki kesamaan fitur. Dengan cara ini, sistem dapat memberikan rekomendasi obat pengganti yang relevan dan sesuai dengan kebutuhan. Dengan penerapan teknik ini dalam sistem informasi rekomendasi, proses pencarian obat pengganti menjadi lebih cepat, tepat, dan berbasis data, sehingga dapat membantu mengurangi risiko kesalahan pengobatan akibat kekeliruan dalam memilih alternatif obat.

## Data Understanding
Dataset obat yang digunakan diambil dari situs Kaggle dengan nama [Indian Medicine Data](https://www.kaggle.com/datasets/mohneesh7/indian-medicine-data). Dataset terdiri dari :
* **sub\_category**: merujuk pada kategori medis spesifik yang menentukan bidang aplikasi obat tersebut.
* **product\_name**: nama produk seperti yang terdaftar di pasar India.
* **salt\_composition**: komposisi kimia dari obat tersebut.
* **product\_price**: harga sebelumnya dari produk. Harap pertimbangkan ini sebagai referensi, karena harganya cenderung sangat fluktuatif terkait dengan pasar kesehatan.
* **product\_manufactured**: Perusahaan farmasi yang bertanggung jawab dalam memproduksi obat/obat tersebut.
* **medicine\_desc**: Gambaran menyeluruh dan deskripsi rinci tentang produk spesifik ini.
* **side\_effects**: Potensi efek samping yang dapat terjadi terkait dengan obat/obat ini.
* **drug\_interactions**: Interaksi dan efek yang terjadi ketika mengkombinasikan obat ini dengan obat lainnya.

Berikut tabel sturuktur dataset Indian medicine dataset

| No | Column               | Non-Null Count | Dtype  |
|----|----------------------|----------------|--------|
| 1  | sub_category         | 195605 non-null | object |
| 2  | product_name         | 195605 non-null | object |
| 3  | salt_composition     | 195605 non-null | object |
| 4  | product_price        | 176169 non-null | object |
| 5  | product_manufactured | 195605 non-null | object |
| 6  | medicine_desc        | 195605 non-null | object |
| 7  | side_effects         | 195605 non-null | object |
| 8  | drug_interactions    | 195605 non-null | object |


Dari tebel diatas dapat dilihat bahwa dataset memiliki 8 kolom dengan tipe object. Dataset terdiri  195605 baris yang menandakan bahwa terdapat 195605 data obat pada dataset. Selanjutnya pemeriksaan nilai unik masing-masing fitur. Berikut tabel dari nilai unik masing-masing fitur pada dataset.

| Kategori                | Jumlah Nilai Uniq |
|-------------------------|-------------------|
| Sub Kategori            | 252               |
| Produk Name             | 7469              |
| Komposisi Obat          | 2663              |
| Product Price           | 3782              |
| Medicine Desc           | 7469              |
| Side Effect             | 1184              |
| Drug Interactions       | 179               |

Pada tabel, dapat dilihat bahwan fitur-fitur dataset memiliki nilai yang beragam. Ini menandakan bahwa ada kesamaan nilai pada fitur-fitur antar obat. Hal ini mengindikasikan ada kesamaan ciri-ciri antar obat pada dataset sehingga data cocok digunakan untuk project sistem rekomendasi pengganti obat.

Selanjutnya kita akan mengecek missing value pada data. Berikut tabel yang menunjukan miisng value pada masing masing fitur.


| Kolom                  | Jumlah Nilai Kosong |
|------------------------|----------------------|
| sub_category           | 0                    |
| product_name           | 0                    |
| salt_composition       | 0                    |
| product_price          | 19436                |
| product_manufactured   | 0                    |
| medicine_desc          | 0                    |
| side_effects           | 0                    |
| drug_interactions      | 0                    |

Dari tabel dapat dilihat bahwa terdapat satu fitur yang memiliki _missing value_ yaitu _product price_. Tapi untuk project kita kali ini kita tidak akan menggunakan fitur _product price_, sehingga ini dapat dihapus pada dataset nantinya. 

Pada project ini kita berfokus menggunakan 2 fitur pada data yaitu _sub category_ dan _salt composition_, sehingga fitur seperti _product price, product_manufactured, medicine desc, dan drug interactions_ kan dihapus pada dataset. Karena kita menggunaka fitur sub kategori dan salt composition pada project ini, maka kita perlu memahami lebih lanjut terkait fitur-fitur ini.

| No | Description            | Count  |
|----|------------------------|--------|
| 1  | Subkategori            | 252    |
| 2  | Komposisi Obat         | 2663   |

Berdasarkan tabel diatas, dapat dilihat bahwa terdapat 252 jenis _sub category_ pada data dan 2663 jenis _salt compotition_ pada dataset yang menandakan data data pada dataset sangat beragam. Selanjutnya kita akan meliaht distribusi jumalah fitur terhadap jumlah data pada fitur.
Berikut histogram distribusi Jumlah kategori per jumlah data pada fitur sub kategori.

![Histogram Distribusi Jumlah Kategori per Jumlah Data](https://raw.githubusercontent.com/XMB234/Tugas-Machine-Learning-Terapan-Sistem-Rekomendasi/a0b1c7f224d354f17d1156a4c535fe056bd98707/Jumlah%20Ketegori%20per%20Jumlah%20Data.png)

Dari histogram dapat dilihat bahwa terdapat 25 jenis _sub category_ yang memiliki 80 data dan ini merupakan jumlah data yang memiliki sub kategori terbanyak pada histogram. Selain itu, terdapat 25 jenis _sub category_ yang memiliki jumlah data dibawah 5 serta beberapa jenis sub kategori yang memiliki jumlah data mencapai ribuan.

Selanjutnya, memahami distribusi jumlah jenis _salt compositon_ per jumlah data pada fitur _salt composition_.

![Histogram Distribusi Jumlah Salt Commposition per Jumlah Data](https://raw.githubusercontent.com/XMB234/Tugas-Machine-Learning-Terapan-Sistem-Rekomendasi/55c7f8ba0317f3c3794ef76dec88de32fc238fa9/Jumlah%20Salt%20Compositon%20per%20Jumlah%20Data.png)

Dari histogram dapat dilihat bahwa terdapat 242 jenis _salt composition_ yang memiliki 1 data dan ini merupakan jumlah data yang memiliki jenis _salt composition_ terbanyak pada histogram. Selain itu, terdapat beberapa jenis _salt composition_ yang memiliki jumlah data mencapai ribuan.

Kemudian, dilakukan pengecekan duplikat pada data yang memiliki product name, sub kategori, dan salt composition yang memiliki nilai yang sama. Hal ini dikarenakan terdapat kesamaan _product name, sub category, dan salt composition_ pada obat yang diproduksi pada beberapa manufaktur seperti pada tabel dibawah

Berikut tabel jumlah data duplikat dan jenis data duplikat berdasarkan kombinasi fitur _sub category, salt composition, dan product name_.

| No | Description                    | Count   |
|----|--------------------------------|---------|
| 1  | Jumlah Jenis Kombinasi Duplikat      | 6248    |
| 2  | Jumlah Data dengan Kombinasi Duplikat | 194376 |

Berdasarkan tabel , dapat dilihat bahwa terdapat 194376 data duplikat berdasarkan kombinasi fitur sebelumnya. Hal ini menunjukkan adanya sejumlah besar produk dengan informasi yang sangat mirip atau identik, yang berpotensi mengganggu akurasi dan keandalan dalam memberikan rekomendasi obat yang tepat pada model nantinya. Sehingga, data duplikat ini akan dihapus nantinya pada prose data preparation.

## Data Preparation
* Mengahapus fitur-fitur yang tidak diperlukan pada dataset. Untuk meningkatkan kinerja dan efisiensi sistem rekomendasi obat pengganti, beberapa fitur yang tidak relevan akan dihapus dari dataset. Fitur-fitur seperti _product price, product_manufactured, medicine description, dan drug interactions_ akan dikeluarkan karena tidak berkontribusi langsung dalam proses pencocokan obat. Fokus utama dari sistem ini adalah merekomendasikan obat pengganti berdasarkan kesamaan _sub category dan salt composition_. Dengan menghapus data yang tidak diperlukan, sistem dapat lebih cepat dan tepat dalam memberikan rekomendasi yang sesuai dengan kebutuhan pengguna.
* Menghapus Data Duplikat. Data yang dihapus merupkan data yang memiliki nilai sama pada fitur _product name, sub category, dan salt composition_. Duplikasi data dapat menyebabkan sistem rekomendasi menjadi bias dan tidak efisien. Dengan menghapus data ganda, kita memastikan bahwa model hanya belajar dari informasi yang unik dan relevan, sehingga meningkatkan akurasi rekomendasi.
* Menyaring _Sub Category_ dengan Jumlah Data < 5. Sub kategori yang memilki data dibawah 5 akan dihapus. Jumlah data yang terlalu sedikit pada suatu kategori membuat model sulit belajar pola yang kuat. Hal ini bisa menyebabkan overfitting atau hasil rekomendasi yang tidak akurat karena minimnya representasi data
* Normalisasi Data pada Fitur _Sub Category_ dan _Salt Composition_. Normalsisai dilakukan dengan cara Mengubah huruf menjadi huruf kecil (_lowercase_) dan menghapus karakter khusus seperti tanda baca atau simbol. Normalisasi membantu menyamakan format penulisan sehingga data yang secara semantik sama tapi tertulis berbeda dapat dikenali sebagai satu entitas. Contohnya: "Paracetamol" dan "paracetamol" akan dianggap sama. Ini penting agar proses pencocokan dan analisis teks lebih akurat.
* Menggabungkan Fitur _Sub Category_ dan _Salt Composition_ menjadi Fitur Baru. Sebelum modelling , akan dibuat fitur baru yang merupakan gabungan dari _sub category_ dan _salt composition_ yang telah dinormalisasi. Menggabungkan dua fitur ini membantu membentuk representasi yang lebih lengkap dari setiap obat. Fitur gabungan ini akan menjadi dasar dalam teknik _content-based filtering_, di mana sistem akan mencari obat pengganti berdasarkan kemiripan konten medis dan komposisi zat aktifnya.

## Modeling
Obat obat yang telah dipilih akan menjadi dataset dari pembuatan model sistem rekomendasi. Dalam membuat model sistem rekomendasi, akan digunakan teknik _content based filtering_ dalam membuat model sistem rekomendasi.
### Content-based filtering
_Content-based filtering_ adalah salah satu teknik yang digunakan dalam sistem rekomendasi. Sistem rekomendasi dengan metode content-based filtering memberikan saran item yang serupa dengan item yang sebelumnya disukai atau dipilih oleh pengguna. Kemiripan antar item dihitung berdasarkan fitur-fitur yang terdapat pada item yang dibandingkan. Dalam pendekatan ini, rekomendasi diberikan berdasarkan karakteristik atau konten dari item yang sudah dipilih oleh pengguna sebelumnya.
#### Kelebihan
* **Personalisasi Tinggi**: Memberikan rekomendasi yang sesuai dengan preferensi pengguna.
* **Independen dari Pengguna Lain**: Tidak bergantung pada data pengguna lain.
* **Objektif**: Rekomendasi didasarkan pada fitur item yang jelas dan terukur.
* **Kontrol Pengguna**: Pengguna dapat menyesuaikan rekomendasi sesuai preferensi.

#### Kelemahan 
* **Keterbatasan Keberagaman**: Rekomendasi cenderung terbatas pada kategori yang sudah dipilih.
* **Kesulitan Menangkap Preferensi Kompleks**: Sulit memahami kombinasi preferensi yang lebih kompleks.
* **Masalah Cold Start**: Sulit memberikan rekomendasi untuk pengguna atau item baru.
* **Ketergantungan pada Kualitas Fitur**: Kualitas rekomendasi bergantung pada kualitas fitur yang digunakan

Pada proyek ini, penerapan _content based filtering_ akan menggunakan fungsi _tfidfvectorizer_ dari library sklearn. Dengan melakukan fit dan transform dari fungsi tersebut, maka akan diidentifikasi fitur-fitur penting dari setiap obat. Setelah ditemukan fitur-fitur penting, maka akan dibentuk vektor tfidf dalam bentuk matriks menggunakan fungsi todense(). Vektor tfidf berfungsi untuk mengidentifikasi korelasi antara nama obat dengan fitur-fitur penting yang telah di peroleh. Selanjutnya adalah langkah mencari korelasi antar obat menggunakan _cosine similarity_, dengan memasukkan vektor tfidf kedalam _cosine similarity_ maka akan didapat larik yang berisi hubungan antar obat.

Dapat dilihat pada tabel diatas bahwa terdapat nilai 0.0 dan 1.0, nilai ini menunjukkan korelasi antar 2 buku. Korelasi dengan nilai 1.0 menunjukkan bahwa kedua buku tersebut memiliki korelasi yang tinggi, sedangkan nilai 0.0 menunjukkan bahwa kedua buku tidak memiliki korelasi. Contoh pada tabel diatas dapat dilihat bahwa Obat dengan nama ... memiliki korelasi dengan ..... Dengan menggunakan nilai korelasi inilah sistem rekomendasi akan dibuat.

Selanjutnya dibuatlah sebuah fungsi dengan parameter nama obat, dataframe korelasi antar buku, dan dataframe antara judul buku dan penulis buku. Fungsi ini akan mengembalikan 5 rekomendasi sesuai dengan obat yang menjadi parameter berdasarkan sub ketegori dan komposisinya.

Untuk melihat apakah penerapan teknik _content based filtering_ berjalan dengan baik, maka dilakukan uji coba dengan memasukkan  "Alrista Plus Tablet SR" sebagai parameter pada fungsi yang telah dibuat. Berikut hasil kembalian dari fungsi tersebut

Dari tabel diatas dapat dilihat bahwa penerapan content based filtering dapat memberikan rekomendasi yang memiliki kesamaan sub kategori dan salt composition dengan obat yang ingin diganti.

## Evaluation
Pada model _content based filtering_, matrix evaluasi yang digunakan adalah _content based filtering precision_. Presisi adalah  metrik yang digunakan untuk mengukur sejauh mana model berhasil dalam mengklasifikasikan positif dengan benar di antara semua prediksi positif yang dihasilkan oleh model. Dalam konteks sistem rekomendasi, presisi mengukur sejauh mana item yang direkomendasikan relevan dengan preferensi atau kebutuhan pengguna. Presisi pada _content based filtering_, dihitung dengan membandingkan jumlah item yang relevan yang direkomendasikan dengan total jumlah item yang direkomendasikan. Dalam hal ini, item relevan adalah item yang benar-benar disukai atau diinginkan oleh pengguna. Metrik ini penting karena memberikan gambaran tentang kualitas rekomendasi yang diberikan oleh sistem, memastikan bahwa item yang dipilih tidak hanya banyak, tetapi juga relevan dengan pengguna. Presisi sangat berguna ketika fokus utama adalah memberikan rekomendasi yang akurat dan sesuai harapan. 

![Presisi](https://raw.githubusercontent.com/XMB234/Tugas-Machine-Learning-Terapan-Sistem-Rekomendasi/69af212be3660b8863f22bd176711f568bca5c64/Presisi.jpg)

Pada tabel hasil penerapan teknik _content based filtering_ dapat dilihat bahwa seluruhnya merupakan obat pada sub kategori dan komposisi yang sama. Hal ini memberikan arti bahwa nilai presisi dari rekomendasi dengan teknik _content based filtering_ adalah 100%.

Pada tabel hasil penerapan teknik _content based filtering_, dapat dilihat bahwa seluruh rekomendasi obat yang diberikan sistem berasal dari sub kategori dan komposisi yang sama dengan obat yang akan diganti. Artinya, sistem berhasil menyarankan obat-obat yang memiliki kesamaan karakteristik dengan obat yang dicari. Dalam hal ini, nilai presisi dari rekomendasi yang dihasilkan menggunakan teknik _content based filtering_ mencapai angka 100%, yang menunjukkan bahwa seluruh rekomendasi yang diberikan relevan dan sesuai dengan kebutuhan pengguna. Performa model ini terhadap Business Understanding sangat signifikan. Sistem yang dapat memberikan rekomendasi obat pengganti yang tepat merupakan hal yang sangat penting dalam konteks bidang kesehatan. Dengan tingkat presisi yang sangat tinggi, pengguna dapat merasa yakin bahwa obat yang direkomendasikan benar-benar sesuai dengan yang mereka butuhkan, baik dari segi sub kategori maupun komposisi obat tersebut. Hal ini berpotensi meningkatkan kepuasan pengguna dan mengurangi kebingungannya dalam memilih obat pengganti yang tepat.

Selain itu, tingkat presisi yang tinggi juga memberikan dampak positif pada kepercayaan pengguna terhadap sistem, yang pada gilirannya bisa meningkatkan loyalitas dan penggunaan sistem lebih lanjut. Dalam konteks bisnis, hal ini sangat penting untuk membangun hubungan jangka panjang dengan pelanggan dan meningkatkan efektivitas operasional, karena pengguna dapat dengan mudah mendapatkan obat yang tepat tanpa perlu mencari atau membandingkan secara manual. Dengan demikian, sistem rekomendasi ini tidak hanya mempermudah proses pemilihan obat bagi pengguna, tetapi juga meningkatkan efisiensi dan kepuasan yang berdampak positif pada keberhasilan bisnis.


## Kesimpulan
Dengan menggunakan metode _content based filtering_, karakteristik kebutuhan pasien atau pengguna dapat diidentifikasi dengan baik melalui informasi obat yang pernah digunakan, seperti komposisi zat aktif (salt composition) dan kategori terapi (sub_category) dari obat tersebut. Berdasarkan informasi ini, sistem dapat merekomendasikan obat pengganti yang memiliki karakteristik serupa, baik dari segi kandungan maupun kategorinya. Rekomendasi yang sesuai tentu akan lebih relevan dan dipercaya oleh tenaga medis maupun pasien, sehingga diharapkan dapat meningkatkan kecepatan dan ketepatan dalam pengambilan keputusan pengobatan, terutama saat terjadi kekurangan obat utama. Dengan begitu, sistem ini tidak hanya membantu dalam menjaga kontinuitas pengobatan, tetapi juga meningkatkan kepercayaan dan kepuasan pengguna terhadap layanan kesehatan.

## References
1. Aryanto, A. D., Santoso, J., & Purwanto, D. D. (2022). SISTEM REKOMENDASI OBAT PENGGANTI MENGGUNAKAN METODE CNN. Jurnal Sistem Cerdas Dan Rekayasa (JSCR), 3(1), 25–36.
2. Hariri, F. R., & Rochim, L. W. (2022). Sistem Rekomendasi Produk Aplikasi Marketplace Berdasarkan Karakteristik Pembeli Menggunakan Metode User Based Collaborative Filtering. Teknika, 11(3), 208–217. https://doi.org/10.34148/teknika.v11i3.5383. 
3. Havilah Mondi, R., Wijayanto, A., & Winarno, W. (2019). RECOMMENDATION SYSTEM WITH CONTENT-BASED FILTERING METHOD FOR CULINARY TOURISM IN MANGAN APPLICATION. ITSMART: Jurnal Teknologi Dan Informasi, 8, 65–72.
4. Ritter, J. M., Flower, R. J., Henderson, G., Loke, Y. K., MacEwan, D., Robinson, E., & Fullerton, J. (2023). What is pharmacology? In Rang & Dale’s Pharmacology (10th ed.). Elsevier.
5. Shukar, S., Zahoor, F., Hayat, K., Saeed, A., Gillani, A. H., Omer, S., Hu, S., Babar, Z.-U.-D., Fang, Y., & Yang, C. (2021). Drug Shortage: Causes, Impact, and Mitigation Strategies. Frontiers in Pharmacology, 12. https://doi.org/10.3389/fphar.2021.693426
 
