# Analisis Kesiapan Karir Peserta VINIX7

Proyek akhir kelompok **Divisi Data Analyst · MSIB Mandiri VINIX7 Batch 5**
Studi kasus: **Konsultasi Karir · Talent & Career Readiness**

Repositori ini berisi seluruh alur kerja analisis: data mentah, cleaning, validasi, EDA, uji statistik, dashboard Looker Studio, dan materi presentasi.

---

## Ringkasan

Peserta VINIX7 mengikuti Tes Kesiapan Karir yang menghasilkan **Total Score** (jumlah 9 komponen Skor M, rentang 24–98) dan **Verdict** kesiapan. Data survei 2.975 respons dibersihkan dan dianalisis untuk menjawab empat pertanyaan bisnis.

| | |
|---|---|
| Respons survei | 2.975 |
| Peserta dianalisis (tanpa duplikat) | 2.972 |
| Peserta siap (Total Score ≥ 61) | 78,5% |
| Rata-rata Total Score | 68,0 |

**Definisi siap:** Total Score ≥ 61, yaitu Verdict *Siap Masuk Industri* atau *Sangat Siap*.

---

## Pertanyaan Bisnis dan Temuan

| # | Pertanyaan | Temuan utama | Bukti statistik |
|---|---|---|---|
| Q1 | Seberapa besar gap antara Dream Job peserta dan 13 divisi VINIX7? | 20,4% peserta memilih Dream Job di luar 13 divisi; tertinggi di prodi Kesehatan (74,4%) dan Desain & Seni (73,8%) | χ², Cramér's V = 0,528 (kuat), p < 0,001 (Holm) · n = 2.903 |
| Q2 | Variabel demografis/akademis mana yang berasosiasi dengan persentase peserta siap? | Semester paling berasosiasi: 60,3% siap di semester 1 menjadi 88,3% di semester 5. Ikut program VINIX7 dan referral tidak berasosiasi | Regresi logistik, uji LR (koreksi BH): semester, rumpun prodi, status kampus p < 0,05; R² model = 0,046 (lemah) · n = 2.928 |
| Q3 | Kampus (n ≥ 30) dan sumber referral mana yang memiliki persentase peserta siap tertinggi? | UGM tertinggi (92,9%), Unhas terendah (63,6%) dari 19 kampus. Ketiga kelompok referral setara (78–80%) | Kampus: χ² V = 0,167, p < 0,001 · Referral: χ² V = 0,012, p = 0,811 (Holm) |
| Q4 | Di antara frekuensi belajar dan level bahasa Inggris, variabel mana yang memiliki hubungan paling kuat dengan Total Score peserta? | Frekuensi belajar (ρ = 0,56) lebih kuat daripada bahasa Inggris (ρ = 0,42) | Spearman, p < 0,001 (Holm); selisih ρ = 0,145 (CI 95% 0,109–0,182, bootstrap 10.000×) |

> **Catatan interpretasi:** semua hasil adalah **asosiasi, bukan sebab-akibat**. Frekuensi belajar dan bahasa Inggris juga ikut menyusun Skor M, sehingga hubungannya dengan Total Score sebagian bersifat bawaan dari cara skor dihitung.

---

## Struktur Repositori

```
.
├── 01_Data_Mentah/
│   └── konsultasi_karir.csv                  # data survei asli, belum diubah
│
├── 02_Cleaning/
│   ├── VINIX7_DE_Finalisasi_v5_Final.ipynb   # notebook FINAL (menghasilkan data bersih)
│   ├── VINIX7_DE_Finalisasi_v4_Dreamjob_Kampus.ipynb
│   ├── VINIX7_DE_Finalisasi_v3_Dreamjob13Divisi.ipynb
│   ├── VINIX7_DE_Finalisasi_v1.ipynb
│   ├── vinix7_data_dictionary_ringkas.csv    # kamus kolom data ringkas
│   ├── vinix7_map_text_categories_final.csv  # pemetaan teks bebas ke kategori
│   ├── vinix7_tabel_revisi_kampus_v4.csv     # revisi nama dan status kampus
│   └── kampus_status_tidak_jelas_sisa_v4.csv
│
├── 03_Data_Bersih/
│   ├── vinix7_survey_clean_v1_final.csv      # 2.975 baris × 83 kolom (lengkap)
│   └── vinix7_survey_ringkas.csv             # 2.975 baris × 28 kolom (dipakai analisis)
│
├── 04_Validasi/
│   ├── sampel_validasi_dreamjob_q1_v4_ronde3.csv
│   ├── vinix7_validasi_ronde4.xlsx
│   ├── kampus_status_tidak_jelas.csv
│   └── label_peninjau/                       # label peninjau manusia ronde 1–3
│
├── 05_EDA/
│   ├── eda_vinix7_v2.py
│   └── grafik/                               # 7 grafik EDA (PNG)
│
├── 06_Uji_Statistik/
│   ├── uji_q4_spearman.py                    # Spearman + bootstrap 10.000× + Holm
│   ├── q4_spearman_hasil.csv
│   ├── build_tabel_dashboard_v2.py
│   ├── vinix7_stat_results_v2.csv            # 47 hasil uji lengkap
│   ├── uji_statistik.csv                     # 14 uji utama (Q1–Q4)
│   └── tabel_analisis_v2.xlsx                # 22 tabel hasil analisis (1 sheet per tabel)
│
├── 07_Dashboard/
│   ├── dashboard_final_vinix7.csv            # sumber utama Looker (1 baris = 1 peserta)
│   ├── dashboard_q4_tingkat.csv              # sumber chart Q4 per tingkat
│   ├── build_data_dashboard.py               # pembuat 2 CSV di atas
│   ├── Rumus_Field_Looker_VINIX7.txt         # pengaturan tiap chart di Looker
│   ├── Mockup_Dashboard_1Halaman.png
│   ├── buat_mockup_dashboard.py
│   └── Panduan_Looker_Studio_VINIX7.pdf
│
├── 08_Presentasi_Laporan/
│   ├── Review_Cleaning_EDA_Uji_VINIX7_DA.pptx
│   ├── build_slide_review.js
│   └── Logbook_Week13_Satrio.docx / .pdf
│
└── 99_Arsip_Lama/                            # versi yang tidak dipakai lagi, disimpan untuk jejak
```

---

## Alur Data

```
konsultasi_karir.csv (mentah)
        │
        ▼  02_Cleaning/VINIX7_DE_Finalisasi_v5_Final.ipynb
vinix7_survey_clean_v1_final.csv  +  vinix7_survey_ringkas.csv
        │
        ▼  buang flag_duplikat = 1  →  2.972 peserta
EDA (05) dan uji statistik (06)
        │
        ▼  07_Dashboard/build_data_dashboard.py
dashboard_final_vinix7.csv  +  dashboard_q4_tingkat.csv
        │
        ▼
Dashboard Looker Studio (1 halaman, dengan filter)
```

---

## Metode

### Cleaning
- Standardisasi nama kampus dan status kampus (Negeri/Swasta) dengan revisi manual.
- Pengelompokan program studi ke rumpun prodi.
- Pemetaan teks bebas Dream Job ke 13 divisi VINIX7: Data Analyst, Cybersec, SDM, Project Management, Digital Forensic, Public Relations, Banking & Finance, Web Dev, Bisnis Digital, Python Data Science, Business Administration, Python ML, Ethical Hacker.
- Perbaikan kode referral yang salah ketik, lalu dikelompokkan menjadi DS26, DA4, dan Tanpa referral.
- Penandaan duplikat (`flag_duplikat`).

### Validasi pengodean Dream Job
Hasil pemetaan otomatis dibandingkan dengan label peninjau manusia dalam beberapa ronde. Kecocokan naik dari **72,5% → 78,9% → 85,5%** (ronde 1–3). Ronde 4 dipakai untuk memutuskan pedoman kasus ambigu sebelum notebook final v5 dibuat.

### Uji statistik
| Pertanyaan | Uji | Koreksi uji berganda |
|---|---|---|
| Q1 | Chi-square, Cramér's V | Holm |
| Q2 | Regresi logistik (Model A), uji likelihood ratio, ΔR² | Benjamini-Hochberg |
| Q3 | Chi-square, Kruskal-Wallis | Holm |
| Q4 | Korelasi Spearman, bootstrap 10.000× untuk selisih ρ | Holm |

Tingkat signifikansi α = 0,05. Analisis kampus hanya memakai kampus dengan n ≥ 30 (19 kampus).

### Variabel yang tidak dianalisis
- **Tempat/status magang**: tidak dipakai atas masukan mentor (dokumentasi pertanyaan awal tidak tersedia, sehingga jawaban bisa berarti tempat magang impian).
- **Skor M, Total Score, Archetype** tidak dipakai sebagai prediktor Q2 karena Verdict diturunkan langsung dari Total Score.

---

## Dashboard

Dashboard Looker Studio 1 halaman dengan 3 filter (rumpun prodi, semester, status kampus) dan 4 kartu jawaban: Minat Dream Job, Kesiapan Peserta, Kampus dan Referral, Frekuensi Belajar vs Bahasa Inggris.

🔗 **Link dashboard:** [--]

![Mockup dashboard](07_Dashboard/Mockup_Dashboard_1Halaman.png)

---

## Cara Menjalankan

**Kebutuhan:** Python 3.10+, `pandas`, `numpy`, `scipy`, `statsmodels`, `matplotlib`, `openpyxl`, Jupyter atau Google Colab.

```bash
pip install pandas numpy scipy statsmodels matplotlib openpyxl
```

1. Jalankan `02_Cleaning/VINIX7_DE_Finalisasi_v5_Final.ipynb` untuk menghasilkan data bersih.
2. Jalankan `05_EDA/eda_vinix7_v2.py` untuk grafik EDA.
3. Jalankan `06_Uji_Statistik/uji_q4_spearman.py` dan `build_tabel_dashboard_v2.py` untuk hasil uji dan tabel.
4. Jalankan `07_Dashboard/build_data_dashboard.py` untuk membuat CSV sumber dashboard.

> ⚠️ Skrip `.py` masih memakai path `/mnt/user-data/outputs/`. Ganti path ke folder lokal Anda sebelum dijalankan.

---

## Keterbatasan

- Responden survei bukan sampel acak, jadi hasil berlaku untuk peserta VINIX7 ini dan tidak bisa digeneralisasi ke populasi mahasiswa.
- Pengodean Dream Job memiliki kecocokan 85,5% dengan peninjau manusia pada ronde terakhir yang diukur; angka Q1 sebaiknya dibaca sebagai perkiraan.
- R² model Q2 hanya 0,046: variabel demografis dan akademis menjelaskan sebagian kecil variasi kesiapan.
- Kampus dengan n mendekati 30 memiliki interval kepercayaan lebar, sehingga urutan antarkampus yang berdekatan belum tentu stabil.

---

*Data survei bersifat anonim dan disediakan oleh PT. untuk keperluan proyek akhir.*
