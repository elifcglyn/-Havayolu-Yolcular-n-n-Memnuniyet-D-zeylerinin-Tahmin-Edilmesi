# Havayolu Yolcularının Memnuniyet Düzeylerinin Tahmin Edilmesi

Makine Öğrenmesi dersi uygulamalı proje (U08). Bir yolcunun demografik bilgileri, uçuş bilgileri ve hizmet puanlarından **memnun olup olmadığı** tahmin edilmiştir (ikili sınıflandırma). Karar Ağacı ve Rastgele Orman algoritmaları karşılaştırılmıştır.

## Dosyalar

| Dosya | İçerik |
|---|---|
| [`havayolu_memnuniyet.ipynb`](havayolu_memnuniyet.ipynb) | Tüm kodlar, açıklamalar, çıktılar ve grafikler |
| [`data/train.csv`](data/train.csv) | Eğitim verisi (103.904 yolcu) |
| [`data/test.csv`](data/test.csv) | Test verisi (25.976 yolcu) |
| [`requirements.txt`](requirements.txt) | Kullanılan Python kütüphaneleri |

## Veri seti

Kaggle – [Airline Passenger Satisfaction](https://www.kaggle.com/datasets/teejmahal20/airline-passenger-satisfaction) (TJ Klein). 22 özellik, 1 hedef değişken (`satisfaction`). Veri dengelidir: eğitim verisinde %56,7 nötr / memnun değil, %43,3 memnun.

## Adımlar

1. Veriyi yükleme ve tanıma
2. Keşifsel veri analizi
3. Ön işleme: sıra numarası sütunlarının atılması, eksik değerlerin eğitim verisinin medyanıyla doldurulması, 0/1 ve one-hot kodlama
4. Karar Ağacı (`max_depth=15`, 5 katlı çapraz doğrulama ile seçildi)
5. Rastgele Orman (`n_estimators=200`, 5 katlı çapraz doğrulama ile seçildi)
6. Modellerin karşılaştırılması
7. Özellik önemi
8. Sonuç ve değerlendirme

## Sonuçlar (test verisi)

| Metrik | Karar Ağacı | Rastgele Orman |
|---|---|---|
| Accuracy | %95,53 | **%96,25** |
| Precision | %96,04 | **%97,28** |
| Recall | %93,69 | **%94,10** |
| F1 | %94,85 | **%95,66** |

Memnuniyeti en çok belirleyen özellikler: **Online boarding**, **Inflight wifi service** ve **Type of Travel**.

## Çalıştırma

Python 3.12 ile denenmiştir.

```bash
pip install -r requirements.txt
jupyter notebook havayolu_memnuniyet.ipynb
```

Ardından menüden **Run → Run All Cells** seçilir. Çapraz doğrulama adımları birkaç dakika sürebilir.

## Yapay zekâ kullanımı

Anthropic'in Claude asistanından Python kodlarının ve açıklamaların hazırlanmasında, kavramların öğrenilmesinde ve rapor taslağının oluşturulmasında yararlanılmıştır.

## Kaynaklar

1. Klein, T. J. *Airline Passenger Satisfaction* [Veri seti]. Kaggle. https://www.kaggle.com/datasets/teejmahal20/airline-passenger-satisfaction
2. Breiman, L. (2001). Random Forests. *Machine Learning*, 45(1), 5–32. https://doi.org/10.1023/A:1010933404324
3. Breiman, L., Friedman, J. H., Olshen, R. A., & Stone, C. J. (1984). *Classification and Regression Trees*. Wadsworth. https://doi.org/10.1201/9781315139470
4. Pedregosa, F. et al. (2011). Scikit-learn: Machine Learning in Python. *Journal of Machine Learning Research*, 12, 2825–2830. https://jmlr.org/papers/v12/pedregosa11a.html
5. scikit-learn geliştiricileri. Kullanım kılavuzu: [Decision Trees](https://scikit-learn.org/stable/modules/tree.html), [Ensemble methods](https://scikit-learn.org/stable/modules/ensemble.html#forest)
