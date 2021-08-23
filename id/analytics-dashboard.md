# Dasbor Analisis

{% hint style="info" %}
Kunjungi [analytics.ousd.com](https://analytics.ousd.com) untuk melihat bagaimana dana dialokasikan, melihat data kinerja historis, dan melacak keuntungan pribadi Anda.
{% endhint %}

Dasbor [](https://analytics.ousd.com/apy) terutama ditujukan untuk konsumsi oleh tim teknik kami, tetapi kami melanjutkan dan menerapkannya karena etos kami adalah "publik secara default" dan semua yang kami lakukan adalah [sumber terbuka](http://github.com/OriginProtocol). Sayangnya, hal itu sering kali berarti melakukan kesalahan di sisi transparansi dan belum tentu di sisi meluangkan waktu untuk menjelaskan hal-hal dengan jelas.

Sebelum masuk ke perhitungan hasil, penting untuk memahami cara kerja OUSD baik dalam hal [generasi hasil](https://docs.ousd.com/core-concepts/yield-generation) dan [rebasing](https://docs.ousd.com/core-concepts/elastic-supply). Anda dapat membaca semua tentang itu di [dokumen](https://docs.ousd.com/), termasuk [bagian tentang kontrak pintar yang dikeluarkan dari hasil](https://docs.ousd.com/core-concepts/elastic-supply/rebasing-and-smart-contracts).

Untuk meringkas bagaimana APY dihitung, ini adalah tingkat tahunan perubahan dalam akuntansi internal OUSD dari saldo pengguna antara dua titik waktu. Untuk memahaminya, mari kita urai kolom dalam tabel APY historis \(dalam urutan terbalik\).

**Perbandingan**

Ada dua jenis saldo OUSD: rebasing \(sebagian besar akun\) dan non-rebasing \(kontrak pintar yang tidak ikut serta\). Kontrak token OUSD mempertahankan akuntansi internal terpisah untuk setiap jenis saldo menggunakan apa yang disebut "kredit". Rasio yang ditunjukkan di sini adalah pasokan rebasing OUSD dibagi dengan kredit rebasing, yang memberi kita nilai tukar di antara keduanya.

**Kredit**

Beberapa kontrak pintar yang memegang OUSD memiliki saldo kredit unik karena status rebasingnya telah berubah di beberapa titik di masa lalu \(dengan memilih masuk atau keluar\). Di sini kami menunjukkan jumlah semua kredit rebasing dan kredit non-rebasing. Ketika dikalikan dengan rasio, itu memberikan perbedaan antara pasokan backing dan pasokan non-rebasing.

**Non-rebasing**

Ini adalah bagian dari pasokan yang disimpan dalam kontrak pintar lain yang belum memilih untuk melakukan rebasing. Ketika ditambahkan ke \(kredit \* rasio\), ini sama dengan pasokan cadangan. Perhatikan juga bahwa kolom **%** menunjukkan persentase OUSD yang non-rebasing.

**Dorongan**

APY secara efektif "didorong" untuk rebasing akun berkat fakta bahwa beberapa OUSD non-rebasing. Pikirkan tentang semua stablecoin yang digunakan sebagai jaminan untuk mencetak OUSD non-rebasing. Stablecoin itu masih menghasilkan melalui strategi pertanian hasil kami, tetapi keuntungan hanya diperoleh ke akun rebasing. Hasilnya adalah APY efektif lebih tinggi daripada tanpa mekanisme ini. Dorongan adalah ukuran dari perbedaan ini. Jika dorongan adalah 100%, maka pemegang OUSD biasa menikmati APY dua kali lipat dari yang seharusnya.

**Perhitungan APR/APY**

Membawa lingkaran penuh ini, saat ini kami mengukur hasil dengan mengukur perubahan [kredit rebasing per token](https://github.com/OriginProtocol/origin-dollar/blob/master/contracts/contracts/token/OUSD.sol#L45) antara dua titik waktu. Tetapi ada beberapa pertimbangan lain yang perlu diperhatikan. Pertama, kami harus membuat asumsi tentang berapa banyak blok Ethereum yang ditambang pada rata-rata hari. Kami menggunakan [ 6.500 yang sudah tetap](https://github.com/OriginProtocol/ousd-analytics/blob/master/eagleproject/core/views.py#L43), tetapi jumlah sebenarnya blok per hari adalah variabel. Kedua, kami membutuhkan cakrawala waktu yang masuk akal untuk mengukur. Kami fokus pada [7 hari](https://github.com/OriginProtocol/ousd-analytics/blob/master/eagleproject/core/views.py#L422), yang telah terbukti menjadi rentang waktu yang relatif konsisten di mana sampel lengkap dari aktivitas yang menghasilkan hasil telah terjadi. Ketiga, kami mengubah APR menjadi APY dengan mengasumsikan [pelipatgandaan harian konstan](https://github.com/OriginProtocol/ousd-analytics/blob/master/eagleproject/core/views.py#L449-L451). Dengan kata lain, hasil terus diinvestasikan kembali ke dalam strategi yang sama. Akhirnya, ada satu kelemahan yang perlu dipertimbangkan untuk menggunakan rasio rebase untuk mengukur hasil. Karena peristiwa rebase saat ini terjadi secara sporadis \(dan tidak terlalu sering di dunia dengan harga gas yang tinggi\), APY tidak akan mencerminkan pendapatan yang belum diterjemahkan ke saldo akun. Misalnya, mungkin ada lonjakan suku bunga di Compound atau lonjakan volume dalam strategi Curve 3pool, yang akan menyebabkan OUSD menghasilkan lebih banyak daripada rata-rata hari. Sampai [metode rebase](https://github.com/OriginProtocol/origin-dollar/blob/master/contracts/contracts/vault/VaultCore.sol#L365-L370) dipanggil, APY akan melaporkan pendapatan ini lebih rendah. Faktanya, siapa pun yang menjual OUSD selama waktu itu akan kehilangan "[rebase](https://analytics.ousd.com/)berikutnya". Kabar baiknya adalah Anda harus dapat mengamati perubahan saldo Anda selama satu minggu dan \(disetahunkan\) kira-kira sama dengan APY yang kami iklankan.
