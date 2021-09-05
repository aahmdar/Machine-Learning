# Clustering

Clustering termasuk dalam unsupervised learning dimana datanya tidak memiliki label. Algoritma clustering ini bekerja dengan mengelompokkan  objek-objek berdasarkan polanya, entitasnya, kejadiannya, hasil observasinya ke dalam sebuah kelompok atau dengan kata lain melakukan pemecahan atau pemisahan data ke dalam sejumlah kelompok menurut karakter tertentu. 
Clustering bisa diterapkan di berbagai bidang contohnya pada bidang :
- marketing untuk membantu pihak pemasaran menentukan grup dan membuat program khusus grup tersebut, 
- asuransi untuk mengidentifikasi grup yang memiliki tingkat claim tinggi, pada bidang biologi untuk taksonomi makhluk hidup,
- ekonomi untuk riset pasar, dan lain sebagainya.

### Partisi : K-means, K-medoids
- K-means : setiap cluster dipresentasikan oleh pusat cluster (centroid)
- K-medoids atau PAM (Partition Around Medoids) : setiap cluster dipresentasikan oleh suatu objek dalam cluster (medoid)
- Partisi himpunan D sebanyak n ke k clusters, yang memiliki jarak terdekat (dimana  c_i adalah centroid atau medoid dari cluster C_i). Partisi kedua algoritma menggunakan metode jarak terdekat dengan menggunakan Euclidean Distance : ![Alt Text](https://drive.google.com/uc?export=download&id=1pUyKb67hRP71GZM1sJtt1_vVmPhaxMHb) 

### Algoritma K-Means
1.	Pilih jumlah cluster k. Inisiasi pusat cluster (centroid). Biasanya dilakukan random
2.	Tempatkan setiap data ke cluster terdekat. Penentuan cluster berdasarkan jarak data paling dekat ke cluster mana
3.	Hitung kembali pusat cluster. Bisa menggunakan mean dari semua anggota dalam setiap cluster
4.	Ulangi langkah 2 dan 3 memakai pusat cluster yang baru hingga tidak ada lagi perubahan cluster

### Algoritma K-Medoids
- K-means sensitive dengan data pencilan (outliers). Solusinya menggunakan k-metoids
- Langkah menentukan anggota cluster sama. Letak perbedaanya pada cluster. Pusat cluster k-medoid merupakan salah satu objek data dalam cluster yang berada di tengah.

### Hirarki : Agnes, Diana
- Menggunakan jarak matriks sebagai kriteria melakukan clustering. Tidak membutuhkan input k sebagai banyaknya cluster.Visualisasi hirarki clastering biasanya dalam bentuk pohon, biasa disebut dendogram.
- Ada dua cara untuk membentuk hirarki clustering, yaitu:
    1. Agnes (Agglomerative Nesting). Dimulai dari beberapa flat clusters; pada setiap Langkah iterasi, kita menggabungkan dua node atau clusters termirip atau kesamaan yang tinggi dengan kata lain mendefinisikan arti “kedekatan” dua clusters.
    2. Diana (Divisive Analysis), merupakan kebalikan dari Agnes, dimulai dari satu cluster (seluruh data), kemudian memecah belah cluster dengan kata lain mendefinisikan cluster mana yang harus dipecah dan bagaimana cara memecahnya.

### Density-based : DBSCAN
- 2 parameter penting, yaitu:
    1. Eps : radius maksimal untuk node tetangga
    2. MinPts : jumlah minimal tetangga yang mencapai Eps
- Langkah-langkah DBSCAN :
    1. Pilih sembarang titik p
    2. Ambil semua titik yang dapat dijangkau berdasarkan Eps dan MinPts
    3. Jika p adalah titik inti (memenuhi MinPts) maka terbentuk cluster
    4. Jika p adalah titik batas (tidak memenuhi MinPts). DBSCAN pindah ke titik p lain yang belum dikunjungi
    5. Ulangi hingga semua titik telah diproses
