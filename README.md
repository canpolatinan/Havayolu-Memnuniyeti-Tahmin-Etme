# ✈️ Havayolu Yolcu Memnuniyeti Tahmini

Kaggle Playground Series S6E10 için ikili sınıflandırma çalışması
([yarışma](https://www.kaggle.com/competitions/playground-series-s6e10) ·
[Kaggle notebook'u]([BURAYA_NOTEBOOK_LINK](https://www.kaggle.com/code/inancanpolat/havayolu-memnuniyeti-tahmin-etme)I)).

## Problem
Yolcunun memnun olup olmadığını tahmin etmek. Metrik: ROC AUC.
Veri: ~700 bin eğitim, ~300 bin test satırı (veri repo'da yok, yarışma sayfasından indirilir).

## Yaklaşım
- Servis puanlarından 13 ek özellik (ortalama, toplam, min/max/std, gecikme farkı vb.)
- LightGBM, XGBoost, CatBoost; 5 katlı StratifiedKFold
- Üç modelin sıra (rank) ortalaması ile ensemble
- Eksik değerler (`Arrival Delay in Minutes`) modellerin kendi mekanizmasıyla işlendi

## Sonuçlar
| Model | CV AUC |
|---|---|
| LightGBM (baseline, ek özelliksiz) | 0.95879 |
| LightGBM (13 ek özellikle) | 0.95866 |
| XGBoost | 0.95856 |
| CatBoost | 0.95847 |
| Rank ensemble | 0.95885 |

Public AUC: 0.95828 (baseline ve ensemble için aynı).

## Çıkarımlar
- Ek özellikler CV'yi iyileştirmedi: ağaç tabanlı modeller bu veride servis puanlarının
  basit birleşimlerini zaten öğreniyor.
- Ensemble tek modele göre CV'de yalnızca ~0.0002 kazandırdı, public skoru değiştirmedi.
- CV ile public skorun yakın çıkması, doğrulama düzeninin güvenilir olduğunu gösteriyor.
