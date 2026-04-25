## Performance Testing Result
### Test Plan 1: `/all-student-request`
- View Result Tree
![all-student-request_view-result-tree](assets/all-student-request/all-student-request_view-result-tree.png)
- View Results in Table
![all-student-request_view-result-in-table](assets/all-student-request/all-student-request_view-result-in-table.png)
- Summary Report
![all-student-request_summary-report](assets/all-student-request/all-student-request_summary-report.png)
- Graph Results
![all-student-request_graph-results](assets/all-student-request/all-student-request_graph-results.png)
- CLI
![all-student-request_cli](assets/all-student-request/all-student-request_cli.png)
- After Refactoring
![all-student-request-after](assets/all-student-request/all-student-request-after.png)

### Test Plan 2: `/highest-gpa`
- View Result Tree
![highest-gpa_view-result-tree](assets/highest-gpa/highest-gpa_view-result-tree.png)
- View Results in Table
![highest-gpa_view-results-in-table](assets/highest-gpa/highest-gpa_view-results-in-table.png)
- Summary Report
![highest-gpa_summary-report](assets/highest-gpa/highest-gpa_summary-report.png)
- Graph Results
![highest-gpa_graph-results](assets/highest-gpa/highest-gpa_graph-results.png)
- CLI
![highest-gpa_cli](assets/highest-gpa/highest-gpa_cli.png)
- After Refactoring
![highest-gpa-after](assets/highest-gpa/highest-gpa-after.png)

### Test Plan 3: `/all-student-name`
- View Result Tree
![all-student-name_view-result-tree](assets/all-student-name/all-student-name_view-result-tree.png)
- View Results in Table
![all-student-name_view-results-in-table](assets/all-student-name/all-student-name_view-results-in-table.png)
- Summary Report
![all-student-name_summary-report](assets/all-student-name/all-student-name_summary-report.png)
- Graph Results
![all-student-name_graph-results](assets/all-student-name/all-student-name_graph-results.png)
- CLI
![all-student-name_cli](assets/all-student-name/all-student-name_cli.png)
- After Refactoring
![all-student-name-after](assets/all-student-name/all-student-name-after.png)

Berdasarkan hasil sebelum dan setelah optimisasi, terdapat peningkatan efisiensi yang signifikan. Untuk `/all-student`, `/highest-gpa`, dan `/all-student-name`, ketiga endpoint menunjukkan penurunan sample time, latency, dan average sample time yang signifikan. Pada hasil JMeter, terlihat bahwa average sample time untuk endpoint `/all-student` sebelum optimasi adalah 9397, setelah dioptimasi menjadi 94.  Untuk endpoint `/highest-gpa`, average sample time sebelum optimasi adalah 1822207, setelah dioptimasi menjadi 6379. Untuk endpoint `/all-student-name`, average sample time sebelum optimasi adalah 184, setelah optimasi menjadi 41. Hasil ini menunjukkan bahwa optimasi berhasil mengurangi waktu eksekusi dan mempercepat performa aplikasi. 

## Profiling
1. `/all-student`
![all-student-request-improvement](assets/all-student-request/all-student-request-improvement.png)
2. `/highest-gpa`
![highest-gpa-improvement](assets/highest-gpa/highest-gpa-improvement.png)
3. `/all-student-name`
![all-student-name-improvement](assets/all-student-name/all-student-name-improvement.png)

## Reflection
1. Apa perbedaan antara pendekatan pengujian performa dengan JMeter dan profiling dengan IntelliJ Profiler dalam konteks optimasi performa aplikasi?
- JMeter berfokus pada performa dari sudut pandang eksternal atau pengguna. JMeter mengukur response time, throughput, dan error rate saat aplikasi diberi beban. JMeter memberi tahu kita apakah aplikasi lambat, tetapi tidak memberi tahu secara spesifik baris kode mana yang menyebabkannya.Sedangkan, IntelliJ Profiler berfokus pada internal aplikasi. Profiler mengukur penggunaan CPU, alokasi memori, dan durasi eksekusi tiap method. Profiler membantu kita melihat mengapa aplikasi lambat dengan menunjukkan bottleneck di level kode.

2. Bagaimana proses profiling membantu dalam mengidentifikasi dan memahami titik lemah dalam aplikasi?
- Profiling menyediakan data visual seperti Flame Graph atau Method List yang menunjukkan bagian mana CPU menghabiskan waktu paling banyak. Dengan profiling, saya bisa mengetahui bahwa beberapa method di aplikasi ini memakan waktu yang lama karena melakukan pemanggilan ke database. Tanpa profiling, akan lebih susah untuk mengetahui bagian mana yang perlu dioptimasi.

3. Apakah Anda pikir IntelliJ Profiler efektif dalam membantu menganalisis dan mengidentifikasi bottleneck dalam kode aplikasi?
- Ya, sangat efektif. Saya menjadi mengetahui bagian kode mana yang memakan waktu lama dan perlu dioptimasi, tanpa perlu menebak. Saya juga dapat membandingkan hasil profiling sebelum dan setelah optimasi untuk memvalidasi apakah perubahan kode yang dilakukan benar-benar memberikan dampak positif secara langsung pada penggunaan CPU.

4. Apa tantangan utama yang dihadapi saat melakukan pengujian performa dan profiling, dan bagaimana mengatasi tantangan tersebut?
- Tantangan utama yang dihadapi adalah hasil yang tidak konsisten karena faktor eksternal, seperti JIT compiler yang baru dijalankan atau beban CPU komputer saat pengujian. Solusinya adalah melakukan proses warm-up atau pemanggilan endpoint beberapa kali sebelum merekam, dan menjalankan pengujian dalam kondisi lingkungan yang stabil, seperti menutup aplikasi berat. 

5. Apa manfaat utama yang didapatkan dari penggunaan IntelliJ Profiler untuk melakukan profiling kode aplikasi?
- Manfaat utama dari penggunaan IntelliJ Profiler adalah akurasi dan efisiensi. Saya bisa melihat alokasi memori secara real-time dan melihat selisih performa antar commit secara detail. Ini memberikan kepercayaan diri bahwa solusi refactoring yang diberikan benar-benar optimal secara teknis, bukan sekadar asumsi.

6. Bagaimana Anda menangani situasi di mana hasil profiling dengan IntelliJ Profiler tidak sepenuhnya konsisten dengan temuan dari pengujian performa menggunakan JMeter?
- Hasil JMeter tidak selaras dengan temuan IntelliJ Profiler mungkin karena adanya faktor eksternal seperti latensi jaringan, efek cache pada database, serta siklus garbage collection. Untuk mengatasi hal tersebut, maka dapat dilakukan beberapa sesi profiling secara berulang untuk memastikan data yang diperoleh konsisten, melakukan pembersihan cache pada database di antara sesi pengujian, dan menjalankan endpoint beberapa kali sebelum mulai merekam data.

7. Strategi apa yang Anda terapkan dalam mengoptimasi kode aplikasi setelah menganalisis hasil pengujian performa dan profiling? Bagaimana cara memastikan perubahan yang dibuat tidak memengaruhi fungsionalitas aplikasi?
- Saya akan memprioritaskan perbaikan pada metode yang paling sering dipanggil atau paling lama dieksekusi. Optimasi dapat berupa efisiensi query, penggunaan struktur data yang tepat, dan meminimalisasi operasi I/O di dalam loop. Untuk memastikan perubahan yang dibuat tidak memengaruhi fungsionalitasi aplikasi, maka perlu dijalankan unit testing yang sudah ada sebelum dan sesudah optimasi. Jika hasil tes tetap passed namun waktu eksekusi lebih cepat, maka optimasi dianggap berhasil tanpa merusak fungsionalitas.