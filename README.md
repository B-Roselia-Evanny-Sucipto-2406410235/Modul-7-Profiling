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

Berdasarkan hasil sebelum dan setelah optimisasi, terdapat peningkatan efisiensi yang signifikan. Untuk `/all-student`, `highest-gpa`, dan `all-student-name`, ketiga endpoint menunjukkan penurunan sample time, latency, dan average sample time yang signifikan. Pada hasil JMeter, terlihat bahwa average sample time untuk endpoint `all-student` sebelum optimasi adalah 9397, setelah dioptimasi menjadi 94.  Untuk endpoint `highest-gpa`, average sample time sebelum optimasi adalah 1822207, setelah dioptimasi menjadi 6379. Untuk endpoint `all-student-name`, average sample time sebelum optimasi adalah 184, setelah optimasi menjadi 41. Hasil ini menunjukkan bahwa optimasi berhasil mengurangi waktu eksekusi dan mempercepat performa aplikasi. 

## Profiling
1. `/all-student`
![all-student-request-improvement](assets/all-student-request/all-student-request-improvement.png)
2. `/highest-gpa`
![highest-gpa-improvement](assets/highest-gpa/highest-gpa-improvement.png)
3. `/all-student-name`
![all-student-name-improvement](assets/all-student-name/all-student-name-improvement.png)