# Heart Failure Prediction - POINTER 2026 Mini Project
Repository ini berisi seluruh berkas proyek kelompok kami untuk **Mini Project Workshop Traditional Machine Learning POINTER 2026**. Proyek ini berfokus pada pembangunan model klasifikasi untuk memprediksi indikasi penyakit jantung berdasarkan 11 fitur klinis pasien, dikombinasikan dengan sistem penalaran medis berbasis LLM (*Large Language Model*).

---

## 📁 Struktur Repositori

Berikut adalah daftar berkas yang tersedia di dalam repositori ini beserta fungsinya:

| Nama Berkas | Deskripsi | Keterangan |
| :--- | :--- | :--- |
| train.csv | Dataset training klinis. | Memiliki 11 fitur + target label HeartDisease. |
| test.csv | Dataset testing klinis. | Digunakan untuk prediksi akhir (tanpa label HeartDisease). |
| notebook.ipynb | Jupyter Notebook utama proyek. | Berisi end-to-end pipeline data science dan kode LLM. |
| submission.csv | Hasil prediksi model pada test.csv. | Format biner (0/1) yang siap dievaluasi sistem otomatis. |
| reasoning.pdf | Dokumen analisis & sample reasoning LLM. | Dokumen pendukung klinis untuk tahap penentu (tie-breaker). |

---

## 📊 Ringkasan Dataset & Alur Fitur

Model kami mengevaluasi 11 fitur klinis dari pasien untuk memprediksi target biner pada kolom `HeartDisease`:
* **0**: Normal (Tidak ada indikasi penyakit jantung).
* **1**: Terdeteksi (Terindikasi penyakit jantung).

### Fitur yang Digunakan:
* **Demografi & Fisik:** `Age` (Usia), `Sex` (M/F), `RestingBP` (Tekanan darah istirahat), `Cholesterol` (Kolesterol serum).
* **Gejala & Klinis:** `ChestPainType` (TA/ATA/NAP/ASY), `FastingBS` (Gula darah puasa > 120 mg/dl), `MaxHR` (Detak jantung maks).
* **Hasil Pemeriksaan EKG & Exercise:** `RestingECG` (Normal/ST/LVH), `ExerciseAngina` (Y/N), `Oldpeak` (Depresi ST), `ST_Slope` (Up/Flat/Down).
* **LLM:** Qwen/Qwen2.5-3B-Instruct

---

## 🛠️ Alur Kerja Proyek (`notebook.ipynb`)

Notebook utama kami diimplementasikan secara runtut dan seluruh *cells* telah dieksekusi agar visualisasinya langsung terlihat:

1. **Exploratory Data Analysis (EDA):** Analisis distribusi fitur klinis dan korelasi antar variabel terhadap target penyakit jantung.
2. **Data Preprocessing & Cleaning:** Penanganan *missing values*, mitigasi data pencilan (*outlier handling*), dan imputasi data yang konsisten.
3. **Feature Engineering:** Transformasi data kategorikal (*encoding* seperti *One-Hot/Label Encoding*) dan pemilihan fitur berbasis urgensi klinis.
4. **Model Training & Tuning:** Eksperimen minimal pada 2 model *Machine Learning* tradisional (misal: *Random Forest*, *XGBoost*), termasuk *hyperparameter tuning* untuk optimasi metrik.
5. **Evaluasi Model:** Analisis performa menggunakan *Confusion Matrix*, *Accuracy*, dan fokus utama pada **F1-Score (macro)** untuk mengatasi kondisi data yang *imbalanced*.
6. **Integrasi LLM (Tie-Breaker):** Implementasi inferensi lokal menggunakan model bahasa (seperti Qwen 0.5B) untuk menghasilkan narasi penalaran klinis otomatis dari hasil prediksi model.

---

## 🤖 Sistem Penalaran Medis LLM (`reasoning.pdf`)

Sebagai pemenuhan syarat tahap seleksi ke-2 (*Tie-Breaker*), kami menyertakan 5 sampel penalaran medis yang diproduksi oleh LLM. Evaluasi dokumen ini dinilai oleh panitia berdasarkan:
* **Relevansi Klinis (35%)**: Keselarasan narasi LLM dengan ilmu kedokteran jantung.
* **Kedalaman Analisis Fitur (35%)**: Penjelasan kontribusi fitur krusial (seperti *ST_Slope*, *Oldpeak*, atau *ChestPainType*).
* **Kejelasan Narasi (30%)**: Penyajian terstruktur dan mudah dipahami.

> **Contoh Pola Output Reasoning:**
> * Pasien ID: #XXX -> Prediksi Model: [0/1] -> Confidence Score: XX%
> * Analisis Kombinasi Fitur Risiko (e.g., Dampak *ST_Slope Flat* atau *ChestPainType ASY* terhadap hasil prediksi).

---

## 👥 Anggota Kelompok
* 2410511077 - Najwa Azahra Putri (Ketua)
* 2410511076 - Nisrina Nafisah Ghaniz (Anggota)
* 2410511093 - Nasywa Febriani (Anggota)
* 2410501050 - Faizatul Husna (Anggota)
