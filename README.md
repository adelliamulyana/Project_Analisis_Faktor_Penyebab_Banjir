# Project_Analisis_Faktor_Penyebab_Banjir

**Latar Belakang**

Provinsi Jawa Tengah merupakan salah satu wilayah di Indonesia dengan tingkat kejadian bencana banjir yang tinggi. Proyek ini bertujuan untuk mengidentifikasi dan memodelkan faktor-faktor yang memengaruhi frekuensi kejadian banjir di kabupaten/kota se-Jawa Tengah sepanjang tahun 2024. Menggunakan data sekunder dari Badan Pusat Statistik (BPS) dan BPBD Jawa Tengah, penelitian ini menerapkan Generalized Linear Models (GLM) dengan Distribusi Poisson yang diestimasi via Maximum Likelihood Estimation (MLE).

**Target Sektor & Fokus Domain**
Target Sektor: Kebencanaan & Lingkungan Hidup, Tata Ruang Daerah, dan Kebijakan Publik / BPBD & Pemprov Jawa Tengah.

Fokus Domain: Modeling Data Cacahan (Count Data), Risk Assessment, Mitigasi Bencana Berbasis Data (Data-Driven Disaster Mitigation).

**Problem Statement & ObjectivesEvaluasi**
1. Multikolinearitas: Memastikan variabel-variabel lingkungan dan demografi bebas dari masalah multikolinearitas menggunakan Variance Inflation Factor (VIF).
2. Pemodelan Frekuensi: Membentuk model matematika terbaik menggunakan GLM Regresi Poisson untuk menduga jumlah kejadian banjir (Y).
3. Identifikasi Faktor Dominan: Menentukan variabel mana yang signifikan secara statistik antara Curah Hujan (X_1), Kepadatan Penduduk (X_2), Ketinggian Wilayah (X_3), dan Deforestasi Lahan (X_4).

**Tools**
Language: Python

Environment: VS Code

Data Processing: pandas, numpy

Statistical Modeling: statsmodels.api (GLM Poisson)

Diagnostics: Variance Inflation Factor (statsmodels.stats.outliers_influence)

Visualization: matplotlib, seaborn
**Dataset**
Data diperoleh dari Badan Pusat Statistik Jawa Tengah tahun 2024

**Project Workflow**
[ 1. Data Collection ]    ---> Secondary data from BPS & BPBD (Count data & regional metrics)
[ 2. Data Cleaning ]      ---> Data format conversion, missing values handle, data merging by Regency
[ 3. VIF Diagnosis ]      ---> Multicollinearity check (VIF < 10 target)
[ 4. GLM Modeling ]       ---> Fit Poisson Regression with Log Link Function & MLE estimation
[ 5. Hypothesis Testing ] ---> Joint significance test (Likelihood Ratio Chi-Square) & Z-test (Wald)
[ 6. Data Visualization ] ---> Pie chart contribution based on Z-Score & Summary insights

**Temuan Utama dan Penjelasan**

### 1. Uji Multikolinearitas (VIF)
Seluruh variabel independen memiliki nilai VIF **< 10**, mengindikasikan bahwa model stabil dan terbebas dari multikolinearitas:
* **Curah Hujan (X_1):** VIF = 2.70
* **Kepadatan Penduduk (X_2):** VIF = 1.42
* **Ketinggian Wilayah (X_3):** VIF = 1.67
* **Total Deforestasi (X_4):** VIF = 1.51

### 2. Persamaan Model Regresi Poisson

log⁡(μ)=1.1953-0.0015 X_1+1.105e-05X_2-0.0035X_3+8.94e-06X_4

### 3. Signifikansi Parameter (Uji Wald Z-Test)
* **Signifikan (p < 0.05):** 
  * **Ketinggian Wilayah (X_3):** β_3 = -0.0035, p = 0.000 (Kontribusi Z-Score: **54.4%**)
  * **Total Deforestasi (X_4):** β_4 = 8.94×10^(-6), p = 0.023 (Kontribusi Z-Score: **27.0%**)
* **Tidak Signifikan (p >= 0.05):** 
  * Curah Hujan (X_1,  p= 0.244) & Kepadatan Penduduk (X_2, p = 0.693).

> **Kesimpulan Statistik:** Faktor geografis (ketinggian) dan faktor kerusakan lingkungan (deforestasi) terbukti memainkan peran dominan terhadap frekuensi banjir di Jawa Tengah dibandingkan faktor sosial dan intensitas curah hujan secara makro.
