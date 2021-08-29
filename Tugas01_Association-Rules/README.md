# Association Rules
Association Rules yaitu aturan yang menyajikan asosiasi atau korelasi antara kumpulan item. contoh ilustrasinya yaitu terdapat beberapa transaksi, dimana transaksinya itu mengandung beberapa item. Sebuah association rules dalam bentuk A ⇒ B, dimana A dan B adalah dua kumpulan item disjoint (saling terpisah), yang masing-masing disebut sebagai aturan lhs (left-hand side, sisi kiri) dan rhs (right-hand side, sisi kanan). Tiga ukuran yang paling banyak digunakan untuk memilih aturan (rules) menarik yaitu:


### **_Support_** 
adalah adalah ukuran atau presentasi munculnya sebuah itemset dalam sebuah transaksi. Pertimbangkan itemset1 = {Roti, Mentega} dan itemset2 = {Roti, Sampo}. Dalam hal ini transaksi yang memiliki roti dan mentega akan lebih banyak dibandingkan roti dan sampo, sehingga itemset1 umumnya memiliki support yang lebih tinggi daripada itemset2.
Nilai support sebuah item diperoleh dengan rumus berikut: 

![Alt Text](https://drive.google.com/uc?export=download&id=1e5mhxgotj8_oE6qAXSM0V1RJOsBFMUEj) 

Sedangkan nilai support dari 2 item diperoleh dari rumus berikut: 

![Alt Text](https://drive.google.com/uc?export=download&id=13FGylJLXCoVjt-OQir931Z2Eixmlcqku)

Jika sebuah itemset kebetulan memiliki support yang sangat rendah, kita tidak dapat mengambil informasi yang cukup tentang hubungan antar itemnya dan karenanya tidak ada kesimpulan yang dapat ditarik dari aturan seperti itu.


### **_Confidence_** 
adalah kuatnya hubungan antar item dalam aturan asosiasi. Dapat dikatakan sebagai nilai presentase atau ukuran kemungkinan munculnya Consecuent diantara semua grup yang berisi Antercedent. Semakin tinggi nilainya, maka semakin besar kemungkinan item Consecuent muncul jika diketahui bahwa semua item Antercedent muncul dalam itemset tersebut.
Nilai confidence dari aturan A → B diperoleh dari rumus berikut :

![Alt Text](https://drive.google.com/uc?export=download&id=19biJwdHZsvnPj4Zg7UP_KTZ1AZ0agUZm)


### **_Lift_** 
adalah suatu ukuran untuk mengetahui kekuatan aturan asosisasi (association rule) yang telah terbentuk. Nilai lift ratio biasanya digunakan sebagai penentu apakah aturan asosiasi valid atau tidak valid. Untuk menghitung lift ratio digunakam rumus sebagai berikut:

![Alt Text](https://drive.google.com/uc?export=download&id=1n-n_V757UbR17Rhq6eXXQhvRYNzerWWJ)

Untuk mendapatkan nilai benchmark confidence sendiri dapat dihitung menggunakan rumus sebagai berikut:

![Alt Text](https://drive.google.com/uc?export=download&id=1fGkxIJaCRuiA7bgW6RZILmdbb6s0luCf)

dimana :
Nc = Jumlah transaksi dengan item yang menjadi consequent
N = jumlah transaksi basis data

***

## Algoritma Apriori
Algoritma apriori adalah suatu metode untuk mencari pola hubungan antar satu atau lebih item dalam suatu dataset. Algoritma apriori banyak digunakan pada data transaksi atau biasa disebut market basket, misalnya sebuah swalayan memiliki market basket, dengan adanya algoritma apriori, pemilik swalayan dapat mengetahui pola pembelian seorang konsumen, jika seorang konsumen membeli item A , B, punya kemungkinan 50% dia akan membeli item C, pola ini sangat signifikan dengan adanya data transaksi selama ini.
Cara kerja apriori :
- Tentukan minimum support
- Iterasi 1 : hitung item-item dari support(transaksi yang memuat seluruh item) dengan men-scan database untuk 1-itemset, setelah 1-itemset didapatkan, dari 1-itemset apakah diatas minimum support, apabila telah memenuhi minimum support, 1-itemset tersebut akan menjadi pola frequent tinggi,
- Iterasi 2 : untuk mendapatkan 2-itemset, harus dilakukan kombinasi dari k-itemset sebelumnya, kemudian scan database lagi untuk hitung item-item yang memuat support. itemset yang memenuhi minimum support akan dipilih sebagai pola frequent tinggi dari kandidat
- Tetapkan nilai k-itemset dari support yang telah memenuhi minimum support dari k-itemset
- lakukan proses untuk iterasi selanjutnya hingga tidak ada lagi k-itemset yang memenuhi minimum support.


***

## FP-Growth
Menggunakan Apriori memerlukan beberapa pemindaian database untuk memeriksa jumlah dukungan setiap item dan itemset. Ketika basis datanya besar, ini akan menghabiskan banyak memori dan daya komputasi. Oleh karena itu dibuatlah algoritma FP-Growth untuk mengatasi kekurangan tersebut. Metode ini hanya memindai database dua kali dan menggunakan struktur pohon (FP-Tree) untuk menyimpan semua informasi.
Root mewakili null, setiap node mewakili item, sedangkan asosiasi node adalah itemset dengan urutan yang dipertahankan saat membentuk pohon.
Pseudocode dan Penjelasan FP-tree :
1. Deduksi item yang sering dipesan. Untuk item dengan frekuensi yang sama, urutannya diberikan menurut urutan abjad.
2. Bangun pohon FP dari data di atas
3. Dari FP-tree di atas, buatlah FP-conditional tree untuk setiap item (atau itemset).
4. Tentukan Frequent Pattern.
