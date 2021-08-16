# Panduan Integrasi Untuk Pertukaran

Pertukaran terpusat akan memainkan peran penting dalam membantu kami mencapai tujuan kami untuk membuat OUSD ada di mana-mana. Kami dengan senang hati membantu pertukaran apa pun yang ingin membuat OUSD tersedia bagi penggunanya. Kami percaya OUSD akan menjadi tambahan yang bagus untuk pertukaran apa pun yang ingin menawarkan stablecoin superior dan peluang hasil tinggi baru bagi penggunanya.

Dokumen ini adalah titik awal yang bagus untuk memahami cara kerja OUSD. Berikut adalah beberapa pertanyaan penting untuk pertukaran yang ingin mengintegrasikan OUSD untuk dipertimbangkan:

**Apakah Anda ingin berpartisipasi dalam hasil yang dihasilkan?**

Kami berasumsi bahwa jawabannya adalah ya dan kami juga sangat menganjurkan hal ini! Namun, mungkin ada beberapa contoh di mana Anda lebih memilih untuk bergerak cepat dan mendaftar OUSD tanpa berpartisipasi dalam sifat [rebasing dari OUSD](../core-concepts/elastic-supply/rebasing-and-smart-contracts.md) karena ini adalah integrasi tercepat dan paling sederhana. Untuk pertukaran yang ingin mencantumkan OUSD, tetapi kekurangan sumber daya teknik, Anda mungkin ingin meluncurkan versi non-rebasing terlebih dahulu sementara teknisi Anda membuat perubahan apa pun yang diperlukan. Untuk membuat OUSD non-rebasing, Anda dapat memanggil `rebaseOptOut()` dari setiap dompet EOA yang menyimpan OUSD, atau tidak melakukan apa pun jika Anda menyimpan OUSD pada kontrak pintar. OUSD non-rebasing berperilaku seperti token ERC-20 lainnya.

**Apakah Anda menyimpan saldo pelanggan pada kontrak pintar \(mis. multi-tanda\) atau dompet EOA?**

Kontrak cerdas apa pun yang memegang OUSD perlu memilih secara manual untuk menerima hasil dengan memanggil `rebaseOptIn()`. Hal ini disebabkan oleh pasokan elastis [](../core-concepts/elastic-supply/) dan sifat [rebasing dari OUSD](../core-concepts/elastic-supply/rebasing-and-smart-contracts.md). Banyak pertukaran menyapu dana pelanggan ke dompet multi-tanda untuk penyimpanan dingin. Jika Anda melakukan ini, Anda pasti ingin memastikan bahwa Anda memilih untuk melakukan rebasing sehingga Anda selalu menghasilkan.

**Apakah Anda melakukan caching saldo pengguna?**

OUSD secara dinamis memperbarui nilai yang dikembalikan oleh fungsi `balanceOf()` pada kontrak ERC20 kami. Saldo pengguna akan diperbarui beberapa kali sehari karena hasil baru dihasilkan oleh protokol. Selama Anda tidak menyimpan nilai ini dalam cache, pengguna akan selalu melihat jumlah OUSD yang benar yang mereka pegang.

**Apakah Anda mencampur dana pengguna?**

Jika Anda mengumpulkan dana, Anda pasti ingin memastikan bahwa setiap pengguna mendapatkan jumlah pro-rata dari hasil yang dihasilkan oleh protokol. Mungkin cara termudah untuk melakukannya adalah dengan melacak saldo setiap pengguna sebagai persentase dari kumpulan, bukan sebagai jumlah tetap.

**Apa rencana Anda untuk likuiditas?**

OUSD dapat dicetak atau ditebus kapan saja menggunakan [Origin Dollar DApp](https://www.ousd.com), atau langsung dari kontrak pintar kami. Jika Anda berencana untuk menyediakan likuiditas sendiri, Anda harus menyadari bahwa jumlah pasti OUSD yang akan Anda terima sebagai ganti USDT, USDC, atau DAI Anda bergantung pada nilai tukar saat ini sebagaimana ditentukan oleh [oracle](../smart-contracts/api/oracle.md). Jika Anda berencana menebus OUSD untuk stablecoin yang mendasarinya, Anda harus tahu bahwa ada biaya keluar 0,5% dan OUSD akan mengembalikan sekeranjang stablecoin sebanding dengan stablecoin pendukung di pool. Kami mendorong bursa untuk memanfaatkan kumpulan likuiditas lainnya, seperti di Uniswap, untuk menghindari biaya tersebut. Jika memungkinkan, permen atau penebusan harus dilakukan dalam jumlah besar untuk efisiensi maksimum. 



