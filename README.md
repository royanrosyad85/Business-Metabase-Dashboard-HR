# Proyek Akhir: Menyelesaikan Permasalahan Perusahaan Edutech

## Business Understanding

PT Jaya Jaya Maju, sebuah entitas multinasional yang telah beroperasi sejak tahun 2000, memiliki skala organisasi yang besar dengan lebih dari 1.000 karyawan tersebar di berbagai wilayah di Indonesia. Meskipun telah mencapai pertumbuhan yang signifikan, perusahaan menghadapi tantangan substansial dalam aspek manajemen sumber daya manusia, yang salah satu manifestasi utamanya adalah tingkat *attrition rate* (rasio karyawan yang mengundurkan diri terhadap total karyawan) yang mengkhawatirkan, yakni melampaui angka 10%. Tingginya angka attrition ini bukan hanya sekadar statistik, melainkan indikasi adanya isu mendasar dalam kemampuan perusahaan mempertahankan talenta terbaiknya. Kondisi ini berpotensi menimbulkan dampak negatif berantai, mulai dari penurunan produktivitas tim, peningkatan biaya untuk rekrutmen dan pelatihan pengganti, hingga terganggunya stabilitas dan moral kerja secara keseluruhan.

Tujuan utama dari pengembangan HR Analytics Dashboard ini adalah untuk memberdayakan departemen Human Resources (HR) PT Jaya Jaya Maju dengan sebuah alat bantu analitik berbasis data. Dashboard ini dirancang untuk memfasilitasi identifikasi dan pemahaman mendalam mengenai faktor-faktor kunci yang berkontribusi terhadap tingginya tingkat attrition karyawan. Dengan visualisasi data yang interaktif dan insight yang dihasilkan, diharapkan HR dapat mengambil langkah-langkah strategis yang lebih tepat sasaran untuk menekan angka attrition dan meningkatkan retensi karyawan.

### Permasalahan Bisnis yang Akan Diatasi

Proyek dashboard ini bertujuan untuk menjawab beberapa pertanyaan dan mengatasi permasalahan bisnis krusial berikut:

1.  **Mengukur dan Memantau Tingkat Attrition:** Seberapa besar sebenarnya tingkat attrition karyawan saat ini dan bagaimana trennya dari waktu ke waktu? Dashboard akan menyediakan metrik yang jelas untuk ini.
2.  **Identifikasi Faktor Pemicu Attrition:** Faktor-faktor demografis (seperti usia, gender), profesional (seperti peran pekerjaan, departemen, lama bekerja), dan psikologis (seperti kepuasan kerja, keseimbangan kerja-hidup, tingkat pendapatan, jarak dari rumah) manakah yang paling signifikan mempengaruhi keputusan seorang karyawan untuk meninggalkan perusahaan?
3.  **Analisis Attrition Segmented:** Apakah terdapat perbedaan signifikan dalam tingkat attrition ketika dianalisis berdasarkan segmen tertentu, misalnya antar departemen atau peran pekerjaan yang berbeda? Ini akan membantu dalam menentukan area prioritas untuk intervensi.

### Cakupan Proyek

Untuk mencapai tujuan dan mengatasi permasalahan bisnis di atas, cakupan proyek ini meliputi:

1.  **Eksplorasi dan Analisis Data Karyawan:** Melakukan analisis mendalam terhadap dataset karyawan yang disediakan untuk mengidentifikasi pola, korelasi, dan variabel-variabel utama yang memiliki pengaruh kuat terhadap attrition rate.
2.  **Pengembangan Dashboard Interaktif:** Membangun sebuah *business dashboard* yang dinamis dan intuitif menggunakan Metabase. Dashboard ini akan menyajikan visualisasi data mengenai:
    *   Metrik utama attrition (KPI).
    *   Perbandingan attrition rate berdasarkan berbagai dimensi (demografi, peran, departemen, dll.).
    *   Analisis faktor-faktor potensial seperti kepuasan kerja, pendapatan, jarak dari rumah, masa kerja, dan keseimbangan kerja-hidup dalam kaitannya dengan attrition.
3.  **Penyediaan Insight untuk Pengambilan Keputusan:** Menerjemahkan temuan dari analisis data dan visualisasi menjadi insight yang dapat ditindaklanjuti oleh tim HR untuk merancang strategi retensi yang lebih efektif.


## Persiapan

Sebelum memulai analisis dan pengembangan dashboard, beberapa langkah persiapan perlu dilakukan agar proses berjalan lancar dan terstruktur. Dataset yang digunakan dalam proyek ini berasal dari PT Jaya Jaya Maju, sebuah perusahaan edutech multinasional di Indonesia. Data ini mencakup informasi karyawan seperti status attrition, kepuasan kerja, masa kerja, serta faktor-faktor lain yang relevan untuk menganalisis retensi tenaga kerja.

### Langkah-Langkah Persiapan

1. **Pengaturan Lingkungan Kerja**
   - Buat dan aktifkan environment Conda baru untuk proyek ini:
     ```bash
     conda create --name proyek-human-resources python==3.9.15
     ```
   - Instal library dan dependensi yang dibutuhkan menggunakan file `requirements.txt`:
     ```bash
     pip install -r requirements.txt
     ```

2. **Instalasi dan Konfigurasi Metabase**
   - Jalankan Metabase menggunakan Docker:
     ```bash
     docker pull metabase/metabase:v0.46.4
     docker run -p 3000:3000 --name metabase metabase/metabase
     ```
   - Setelah container dijalankan, akses halaman setup Metabase melalui browser:
     ```
     http://localhost:3000/setup
     ```
   - Ikuti langkah-langkah konfigurasi awal untuk menyiapkan dashboard interaktif.

3. **Setup Database dengan Supabase**
   - Daftar dan login ke akun Supabase melalui [https://supabase.com/dashboard/sign-in](https://supabase.com/dashboard/sign-in).
   - Buat project baru pada dashboard Supabase.
   - Salin URI database dari pengaturan database Supabase untuk menghubungkannya ke aplikasi Python.
   - Kirim dataset ke database menggunakan SQLAlchemy untuk memastikan data dapat diakses oleh dashboard:
     ```python
     from sqlalchemy import create_engine

     URL = "DATABASE_URL"

     engine = create_engine(URL)
     df.to_sql('employee_attrition', engine)
     ```

## Business Dashboard

![image](https://github.com/user-attachments/assets/730902de-39a2-4367-a0b1-e7279b14a090)

Dashboard **HR Analytics: Employee Retention & Workforce Insights** dibuat untuk mendukung tim Human Resources (HR) dalam menganalisis faktor-faktor penyebab *employee attrition* serta memberikan gambaran menyeluruh mengenai kondisi tenaga kerja di PT Jaya Jaya Maju.
Dengan visualisasi interaktif, dashboard ini memudahkan HR dalam memahami pola seperti hubungan antara gaji, kepuasan kerja, masa kerja, dan keseimbangan kerja-hidup terhadap risiko karyawan keluar.
Dashboard juga menyediakan ringkasan metrik penting seperti jumlah total karyawan (**1,058**), rata-rata usia (**37.06 tahun)**, rata-rata kepuasan kerja (**2.75 dari skala 4)**, dan masa kerja rata-rata (**7.07 tahun)**.
Fitur filter memungkinkan analisis lebih spesifik berdasarkan **departemen**, **peran pekerjaan**, **pendapatan bulanan**, atau **lokasi rumah**, sehingga HR dapat mengidentifikasi segmen karyawan yang rentan attrition dan merancang strategi retensi secara lebih tepat sasaran.

### **1. Gender vs. Attrition Rate** 
![image](https://github.com/user-attachments/assets/6281020e-1bf2-4173-b336-1f1c540694bc)

Berdasarkan grafik tersebut menunjukkan tingkat *attrition* (karyawan yang keluar) antara karyawan pria dan wanita. Data menunjukkan bahwa tingkat attrition untuk karyawan pria sedikit lebih tinggi, yaitu **17.42%**, sementara untuk karyawan wanita sebesar **16.21%**. 
Hal ini menandakan bahwa secara rata-rata, karyawan pria memiliki kecenderungan sedikit lebih tinggi untuk meninggalkan perusahaan dibandingkan karyawan wanita. Namun, kedua kelompok tetap memiliki tingkat attrition yang cukup tinggi, 
sehingga jenis kelamin bukan satu-satunya faktor utama yang memengaruhi keputusan karyawan untuk keluar

### **2. Departemen vs. Attritions**
![image](https://github.com/user-attachments/assets/f0729e19-f805-473f-88f5-571b7a1ad06e)

Chart ini menunjukkan perbandingan antara jumlah pegawai, jumlah karyawan yang keluar, dan tingkat attrition pada setiap departemen. Melalui visualisasi ini, kita dapat melihat berapa banyak pegawai yang dimiliki masing-masing departemen, berapa jumlah karyawan 
yang keluar, serta seberapa besar persentase attrition rate pada Research & Development, Sales, dan Human Resources. Grafik ini membantu mengidentifikasi departemen dengan tingkat attrition tertinggi yang perlu mendapatkan perhatian khusus dari tim HR.

### **3. Job Role vs. Attrition**
![image](https://github.com/user-attachments/assets/2860980c-503a-441a-93fe-e9a7ad950798)
Chart ini memperlihatkan perbandingan antara jumlah pegawai dan tingkat attrition pada setiap job role. Dari visualisasi ini terlihat bahwa job role dengan jumlah pegawai terbesar seperti Sales Executive dan Research Scientist memiliki tingkat attrition
yang masih moderat, sementara Laboratory Technician dan Sales Representative menunjukkan attrition rate yang lebih tinggi, bahkan Sales Representative menduduki posisi tertinggi meskipun jumlah pegawainya tidak sebanyak job role lain. Insight ini menyoroti 
perlunya perhatian khusus pada job role tertentu yang memiliki risiko keluar lebih besar, sehingga HR dapat mengambil langkah strategis untuk mengurangi attrition di posisi-posisi tersebut.

### **4. Faktor Usia terhadap Attrition**
![image](https://github.com/user-attachments/assets/4f38c127-f55d-4b9c-b989-0b70ff235596)
Chart ini menggambarkan hubungan antara kelompok usia pegawai dengan tingkat attrition. Terlihat bahwa kelompok usia termuda (15–22,5 tahun) memiliki attrition rate yang paling tinggi, mencapai 50%. Seiring bertambahnya usia, attrition rate menurun cukup signifikan
dan cenderung stabil di angka yang lebih rendah pada kelompok usia di atas 30 tahun. Hal ini menunjukkan bahwa pegawai yang lebih muda cenderung lebih banyak keluar dari perusahaan, sedangkan pegawai yang lebih tua relatif lebih stabil dan bertahan. Insight ini 
penting bagi HR untuk fokus pada strategi retensi bagi karyawan muda agar attrition dapat ditekan.

### **5. Work-Life Balance vs. Attrition**
![image](https://github.com/user-attachments/assets/5be8ecd2-0c2f-4db8-aeaf-69c94b049696)
Chart ini menunjukkan hubungan antara tingkat work-life balance dengan jumlah karyawan yang keluar dari perusahaan. Terlihat bahwa sebagian besar karyawan yang keluar memiliki tingkat work-life balance pada level 3, diikuti oleh level 2. Sementara itu, 
jumlah karyawan keluar pada level paling rendah (1) dan paling tinggi (4) jauh lebih sedikit. Insight ini mengindikasikan bahwa karyawan dengan work-life balance sedang justru lebih banyak yang keluar, sehingga perusahaan perlu melakukan evaluasi mendalam 
terkait faktor-faktor lain yang mempengaruhi keputusan resign pada kelompok ini.

### **6. Hubungan Pendapatan Bulanan dengan Attrition**
![image](https://github.com/user-attachments/assets/ee0caa43-e51a-42d9-9fb0-23e7d088a5a0)
Chart ini menunjukkan perbandingan rata-rata gaji bulanan antara karyawan yang bertahan (attrition = 0) dan yang keluar (attrition = 1). Terlihat bahwa karyawan yang keluar memiliki rata-rata gaji bulanan yang lebih rendah dibandingkan dengan karyawan yang tetap 
bertahan. Insight ini mengindikasikan bahwa tingkat pendapatan dapat menjadi salah satu faktor yang mempengaruhi keputusan karyawan untuk meninggalkan perusahaan.

### **7. Rata-rata Job Satisfaction berdasarkan Job Role**
![image](https://github.com/user-attachments/assets/fe4b6ac6-52f4-44d1-a457-0ad026ff9994)
Chart ini menunjukkan perbandingan antara jumlah karyawan yang keluar dan rata-rata kepuasan kerja pada masing-masing job role. Terlihat bahwa job role dengan jumlah keluar yang tinggi, seperti Laboratory Technician, Sales Executive, dan Research Scientist, 
cenderung memiliki rata-rata kepuasan kerja yang lebih rendah. Sebaliknya, job role dengan tingkat kepuasan kerja yang lebih tinggi, seperti Research Director dan Manager, memiliki jumlah karyawan keluar yang relatif sedikit. Insight ini mengindikasikan bahwa 
tingkat kepuasan kerja berpengaruh terhadap keputusan karyawan untuk bertahan atau keluar dari perusahaan, sehingga peningkatan kepuasan kerja pada job role tertentu dapat membantu menekan angka attrition.

### **8. Pengaruh Jarak Tempuh ke Kantor terhadap Tingkat Attrition dan Lama Masa Kerja**
![image](https://github.com/user-attachments/assets/ab822bc0-fb2a-44f2-9a0e-68898231c334)
Chart ini menunjukkan hubungan antara jarak tempuh ke kantor dengan rata-rata masa kerja karyawan dan tingkat attrition. Terlihat bahwa rata-rata masa kerja relatif stabil di kisaran 6–7 tahun di semua kelompok jarak. Namun, attrition rate cenderung meningkat
pada karyawan yang menempuh jarak lebih jauh, khususnya pada kelompok 20–25 km yang mencapai attrition rate tertinggi. Hal ini mengindikasikan bahwa semakin jauh jarak rumah ke kantor, kecenderungan karyawan untuk keluar dari perusahaan menjadi lebih tinggi, 
meskipun lama masa kerja mereka tidak jauh berbeda dengan kelompok jarak lainnya. Insight ini menunjukkan pentingnya perhatian pada kebijakan fleksibilitas lokasi kerja seperti kebijakan WFA dan Hybrid Working untuk beberapa department.

### Final Result Dashboard
[Link Dashboard](https://metabase-royanrosyad-bme9bpd9bcc9fkc4.southeastasia-01.azurewebsites.net/public/dashboard/7f54369b-8ccf-47b5-af68-020557d2820a)

![HR Analytics Dashboard_ Employee Retention   Workforce Insights_1](https://github.com/user-attachments/assets/26a3b2f5-c426-47b9-8a8a-7b33ac2a6f06)
![HR Analytics Dashboard_ Employee Retention   Workforce Insights_22](https://github.com/user-attachments/assets/c274ff19-de48-4956-b0ce-ebda18f1cdc8)

## Conclusion

Berdasarkan analisis yang telah dilakukan terhadap berbagai faktor yang mempengaruhi attrition, dapat disimpulkan bahwa tingkat keluar-masuk karyawan di perusahaan ini dipengaruhi oleh kombinasi dari berbagai aspek, mulai dari gender, departemen, job role, 
usia, work-life balance, hingga pendapatan dan jarak tempuh ke kantor. Secara umum, attrition rate pada karyawan pria sedikit lebih tinggi daripada wanita, namun perbedaannya tidak terlalu signifikan. Beberapa departemen dan job role tertentu seperti Sales, 
Laboratory Technician, dan Sales Representative terbukti memiliki tingkat attrition yang lebih tinggi, sehingga membutuhkan perhatian dan strategi retensi yang lebih intensif dari tim HR.

Selain itu, faktor usia juga sangat berpengaruh, di mana karyawan usia muda cenderung memiliki attrition rate yang lebih tinggi. Work-life balance yang sedang (level 3) justru menjadi kelompok dengan jumlah resign terbanyak, sehingga perlu dieksplorasi lebih 
lanjut terkait penyebabnya. Rata-rata pendapatan bulanan yang lebih rendah serta tingkat kepuasan kerja yang rendah juga berkontribusi terhadap keputusan karyawan untuk keluar. Menariknya, semakin jauh jarak tempuh ke kantor, kecenderungan untuk keluar semakin 
tinggi, meskipun rata-rata masa kerja relatif stabil. Berdasarkan temuan ini, perusahaan sebaiknya memberikan perhatian khusus pada faktor-faktor utama tersebut, misalnya dengan menawarkan fleksibilitas kerja, meningkatkan kepuasan kerja, serta melakukan evaluasi 
dan intervensi pada job role dan departemen dengan risiko attrition tinggi, guna menekan angka attrition dan meningkatkan retensi karyawan secara berkelanjutan.

## Recommendation Action Items

Berdasarkan hasil analisis data attrition, berikut beberapa langkah strategis yang dapat diambil perusahaan untuk menurunkan tingkat keluar masuk karyawan dan meningkatkan tingkat retensi:

1. **Prioritaskan Retensi pada Departemen dan Job Role dengan Risiko Tinggi**  
   Lakukan upaya khusus untuk menekan angka attrition di departemen seperti Sales dan Research & Development, serta pada posisi seperti Laboratory Technician dan Sales Representative. Langkah-langkah yang bisa dilakukan antara lain dengan meningkatkan keterlibatan karyawan, menyesuaikan beban kerja, serta memberikan insentif atau penghargaan bagi pegawai di posisi-posisi tersebut.

2. **Peningkatan Kepuasan Kerja dan Work-Life Balance**  
   Adakan survei kepuasan kerja secara rutin, khususnya pada job role yang memiliki tingkat kepuasan rendah dan angka keluar tinggi. Gunakan hasil survei ini sebagai dasar untuk memperbaiki lingkungan kerja, memberikan pelatihan pengembangan karier, serta memperkuat kebijakan work-life balance seperti fleksibilitas jam kerja, tambahan cuti, atau opsi kerja remote/hybrid.

3. **Evaluasi dan Penyesuaian Skema Kompensasi**  
   Tinjau kembali kebijakan gaji, terutama untuk karyawan dengan pendapatan di bawah rata-rata yang cenderung lebih mudah keluar. Lakukan penyesuaian gaji berdasarkan benchmarking industri atau pertimbangkan pemberian tunjangan tambahan agar perusahaan tetap kompetitif dalam menarik dan mempertahankan talenta.

4. **Buat strategi khusus untuk Karyawan Usia Muda**  
   Karena karyawan muda memiliki tingkat attrition tertinggi, perusahaan perlu memperkuat program onboarding, menyediakan mentoring, serta memperjelas jalur pengembangan karier agar mereka merasa dihargai dan lebih loyal terhadap perusahaan.

5. **Perhatikan Faktor Jarak Tempuh dan Dukungan Transportasi**  
   Untuk karyawan yang tinggal jauh dari kantor dan punya kecenderungan attrition lebih tinggi, perusahaan bisa menawarkan subsidi transportasi, shuttle bus, ataupun opsi kerja hybrid atau remote guna mengurangi beban perjalanan dan meningkatkan kenyamanan bekerja.

6. **Peningkatan Komunikasi dan Feedback**  
   Bangun budaya komunikasi terbuka melalui forum diskusi rutin, dan sistem feedback dua arah. Pastikan setiap karyawan merasa didengar dan dilibatkan dalam pengambilan keputusan perusahaan.

Dengan menerapkan rekomendasi di atas, diharapkan perusahaan dapat menurunkan angka attrition secara signifikan, meningkatkan kepuasan serta loyalitas karyawan, dan menciptakan lingkungan kerja yang kondusif untuk pertumbuhan jangka panjang.
