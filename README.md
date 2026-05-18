# Predict-Customer-Churn

# 📌 Deskripsi
Proyek ini bertujuan untuk memprediksi Customer Churn (kemungkinan pelanggan berhenti berlangganan) menggunakan dataset profil pelanggan. Dengan memprediksi churn secara akurat, perusahaan dapat mengambil langkah proaktif (seperti pemberian promo atau peningkatan layanan) untuk mempertahankan pelanggan yang berisiko tinggi akan pergi.

# 🎯 Tujuan
1. Mengidentifikasi faktor kunci yang menyebabkan pelanggan churn.<br>
2. Membangun model prediktif dengan performa tinggi menggunakan teknik Ensemble Learning.<br>
3. Memberikan segmentasi risiko pelanggan untuk tindakan bisnis yang tepat sasaran.<br>

# 📊 Analisis Data
Berdasarkan eksplorasi data, ditemukan beberapa insight kunci:
1. **Churn Rate**: Rata-rata churn berada di angka 22.52%.<br>
2. **Faktor Kontrak**: Pelanggan dengan kontrak Month-to-month memiliki tingkat churn yang sangat tinggi (~42.1%) dibandingkan pelanggan kontrak 2 tahun (~1.0%).
3. **Korelasi**: Fitur seperti MonthlyCharges dan tenure memiliki pengaruh signifikan terhadap keputusan pelanggan.

# 🛠️ Metodologi & Modeling
Proyek ini menggunakan pendekatan Out-of-Fold (OOF) Predictions dengan Stratified 5-Fold Cross-Validation untuk memastikan stabilitas model.<br>
**Model yang digunakan**:<br>
1. **LightGBM**: Efisien dan cepat dalam menangani dataset besar.<br>
2. **XGBoost**: Memberikan performa yang tangguh dengan regularisasi yang ketat.<br>
3. **CatBoost**: Sangat baik dalam menangani fitur kategorikal secara otomatis.<br>
4. **Ensemble** (Weighted Average): Menggabungkan ketiga model di atas untuk meminimalkan error dan meningkatkan skor AUC.

**Strategi Preprocessing**:
* Missing value handling menggunakan median (numerik) dan modus (kategorik).
* Label Encoding untuk fitur kategorikal.
* Threshold Optimization menggunakan F1-Score untuk menentukan titik potong probabilitas yang paling optimal.

# 📈 Performa Model
Model Ensemble berhasil memberikan performa terbaik dibandingkan model tunggal lainnya:<br>
<img width="789" height="390" alt="image" src="https://github.com/user-attachments/assets/1380d65e-9c84-4996-bf20-ff9826c3c867" />

# 💡 Implementasi Bisnis
Hasil akhir dari proyek ini bukan sekadar prediksi "Ya/Tidak", melainkan Segmentasi Risiko:
* 🟢 **Low Risk** (Probabilitas < 0.3): Pelanggan loyal.
* 🟡 **Medium Risk** (Probabilitas 0.3 - 0.6): Perlu dipantau (Nurturing).
* 🔴 **High Risk** (Probabilitas > 0.6): Membutuhkan intervensi segera (Retention Program).

