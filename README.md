# ✈️ Airline Passenger Satisfaction Prediction (Kaggle)

Bu proje, Kaggle üzerindeki **Airline Passenger Satisfaction** (Havayolu Yolcu Memnuniyeti) yarışması için geliştirilmiş uçtan uca bir Makine Öğrenmesi (Machine Learning) çözümüdür.

## 🚀 Proje Özeti ve Hedefi
Müşteri memnuniyetini etkileyen faktörleri analiz etmek ve yolcuların memnuniyet durumunu (satisfied / neutral or dissatisfied) yüksek doğrulukla tahmin etmek amacıyla geliştirilmiştir. En iyi performansı elde etmek için birden fazla gelişmiş gradient boosting modeli harmanlanmıştır (Ensemble).

## 🛠️ Kullanılan Teknolojiler ve Yöntemler
* **Dil:** Python 3.x
* **Kütüphaneler:** Pandas, NumPy, Scikit-Learn, LightGBM, XGBoost, CatBoost
* **Doğrulama Stratejisi:** 5-Fold Cross-Validation (Çapraz Doğrulama)
* **Model Mimarisi (Ensemble):** LightGBM, XGBoost ve CatBoost modellerinin olasılık tahminlerinin ortalaması (Rank/Probability Blending)

## 📊 Model Performansı
* **Bireysel Model Skorları:** ~0.958 - 0.959 AUC aralığı
* **Ensemble (Birleşik) Skor:** **0.95828+ Public AUC** skoru elde edilmiştir.

## ⚙️ Kod Yapısı ve Adımlar
1. **Veri Ön İşleme ve Özellik Mühendisliği (Feature Engineering):** Eksik verilerin doldurulması, kategorik değişkenlerin dönüştürülmesi ve servis puanları üzerinden türetilmiş yeni özniteliklerin (ortalama, toplam, standart sapma vb.) eklenmesi.
2. **Model Eğitimi:** LightGBM, XGBoost ve CatBoost modellerinin 5 katlı çapraz doğrulama ile eğitilmesi.
3. **Ensemble & Submission:** Modellerin OOF (Out-of-Fold) tahminlerinin birleştirilerek Kaggle için final `submission_ensemble.csv` dosyasının üretilmesi.
