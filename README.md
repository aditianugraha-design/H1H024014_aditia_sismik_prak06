# H1H024014_aditia_sismik_prak06

Pertanyaan Praktikum :
1. Sebutkan dan jelaskan keuntungan menggunakan interrupt dibanding
polling!
- Dari responnya polling tergolong lambat, sementara interrupt bisa dibilang cepat. Selanjutnya Efisiensi CPU, kalu polling bisa dibilang Boros, namun Intterput tidak boros. Lalu Konsumsu data, Polling Tinggi Karena CPU selalu aktif dan Innterrupt lebih rnedah karena memungkinkan mode sleep

2.  Mengapa timer penting dalam sistem embedded dan real-time?
   - Timer sangat penting dalam sistem embedded karena banyak aplikasi membutuhkan eksekusi tugas pada interval waktu yang tepat dan konsisten. Dalam sistem real-time, ketepatan waktu bukan hanya soal kenyamanan tetapi soal kebenaran fungsional sistem. Misalnya, sistem kontrol motor yang membaca encoder setiap 10ms, sistem sampling sensor yang harus berjalan pada frekuensi tetap, atau protokol komunikasi yang membutuhkan timing presisi.

3. Jika interrupt dan timer digabung dalam satu sistem, bagaimana alur
kerjanya?
- Dalam sistem gabungan interrupt dan timer, keduanya bekerja secara komplementer. Alur kerjanya adalah sebagai berikut: program utama berjalan dalam loop() dengan pola millis() untuk tugas periodik (misalnya membaca sensor setiap 500ms dan menampilkan data setiap 1 detik). Di sisi lain, interrupt terdaftar pada pin eksternal untuk menangani event yang tidak terprediksi (misalnya tombol darurat atau sinyal alarm sensor).
Ketika event interrupt terjadi di tengah eksekusi loop(), CPU segera menghentikan loop() dan menjalankan ISR. ISR yang singkat hanya mengubah flag atau variabel global. Setelah ISR selesai, loop() dilanjutkan dan memeriksa flag tersebut untuk melakukan tindakan yang diperlukan. Dengan cara ini, sistem dapat menangani event real-time yang tidak terduga sekaligus tetap menjalankan tugas periodik secara teratur.

4. Apa yang terjadi jika ISR terlalu panjang atau kompleks?
   - Jika ISR terlalu panjang atau kompleks, beberapa masalah serius dapat terjadi.
Pertama, interrupt lain yang terjadi selama ISR berjalan akan tertunda atau bahkan
terlewat sama sekali, menyebabkan kehilangan event penting. Kedua, fungsi-fungsi
yang bergantung pada interrupt seperti delay(), millis(), dan Serial tidak akan berfungsi
dengan benar di dalam ISR karena interrupt dinonaktifkan selama ISR berjalan.
