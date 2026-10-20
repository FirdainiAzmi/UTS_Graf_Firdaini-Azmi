# UTS_Graf_Firdaini-Azmi

**Mata kuliah:** Graf Sains Data
**Nama:** Firdaini Azmi
**NIM:** 23031554071

## Deskripsi

Project ini membangun graf interaksi e-commerce di Neo4j dari dataset RetailRocket, menghitung kemiripan antar item dengan cosine similarity, lalu memakainya untuk merekomendasikan item ke seorang user dengan pendekatan KNN berbasis item (k = 5). Kualitas rekomendasi dievaluasi dengan Hit@5 dan NDCG@5.

## Dataset

- **Sumber:** RetailRocket e-commerce dataset (Roman Zykov, Kaggle), berkas `events.csv`.
- **Fitur:** `timestamp`, `visitorid`, `event` (`view`, `addtocart`, `transaction`), `itemid`, `transactionid`.
- **Pembagian periode (filter pada `timestamp`):**
  - P1 (train): 11 Juni - 11 Juli 2015 
  - P2 (test): 11 Agustus - 21 Agustus 2015

## Struktur Repository

```
├── graf_uts.ipynb
├── requirements.txt   
├── data_filtered/
│   ├── events_P1_train.csv   
│   └── events_P2_test.csv
└── README.md
```

## Hasil untuk user 144241:

| Keterangan | Nilai |
|---|---|
| Jumlah kandidat | 20 |
| Top-5 rekomendasi | 67787, 100589, 133700, 140360, 225706 |
| 3 item iklan | 67787, 100589, 133700 |
| Hit@5 | 0 |
| NDCG@5 | 0 |

## Analisis Singkat
- Kelima rekomendasi teratas memiliki skor identik (0,2041) dan hanya didukung satu visitor bersama, sehingga urutannya tidak informatif. Ini menunjukkan data interaksi yang sangat jarang (sparse).
- Skor cosine relatif kecil karena item acuan sangat populer dan data sparse, sehingga skor lebih tepat dibaca sebagai peringkat relatif.
- Hit@5 dan NDCG@5 bernilai 0 untuk user terpilih. Hasil ini wajar pada dataset sparse: jumlah item sangat banyak, perilaku user dapat berubah antar periode. Evaluasi pada satu user belum cukup untuk menilai kualitas sistem secara keseluruhan.
