# Trafik Kazaları Can Kaybı Simülasyonu — NHTSA FARS

ABD trafik kazası can kaybını simüle eden interaktif web uygulaması. NHTSA FARS (Fatality Analysis Reporting System) 1975–2023 gerçek verilerini temel alır ve kullanıcı kontrolündeki güvenlik faktörleriyle 2024–2035 dönemi için gelecek projeksiyonları oluşturur.

**Canlı Demo:** [ustunkayaeylul72.github.io/Trafik_Kazalari](https://ustunkayaeylul72.github.io/Trafik_Kazalari/)

## Özellikler

### Zamana Bağlı Simülasyon
- GHG Simulator mantığında yıl-yıl ilerleyen simülasyon (1975 → 2035)
- Başlat / Durdur / Sıfırla kontrolleri
- 4 kademeli hız ayarı (×1, ×2, ×4, ×8)

### Kontrol Edilebilir Faktörler

| Faktör | Kaynak | 2023 Gerçek Değer |
|--------|--------|-------------------|
| Alkol Etkili Sürüş | NHTSA BAC ≥ 0.08 | %30 |
| Hız İhlali | NHTSA | %29 |
| Kemersiz Yolcu | NHTSA | %47 |
| Dikkat Dağınıklığı | NHTSA | %8 |
| Emniyet Kemeri Kullanımı | NHTSA 2024 | %91 |
| ADAS Teknoloji Penetrasyonu | IIHS | %30 |
| VMT Büyüme Hızı | FHWA | +%1.5/yıl |
| Yol İyileştirme Endeksi | Bileşik | 50/100 |

### Grafikler
- **Ana grafik:** Yıllık trafik ölümleri (FARS tarihsel + simülasyon)
- **Oran grafiği:** 100M VMT başına ölüm oranı
- **Alkol grafiği:** Alkol bağlantılı ölümler
- **Yaya grafiği:** Yaya + bisikletçi ölümleri
- **Faktör dağılımı:** Katkı faktörü çubukları

### Hazır Senaryolar
1. **2023 Taban** — NHTSA gerçek değerler
2. **Vision Zero** — Sıfır ölüm hedefi
3. **1980 Sarhoş Sürüş** — Tarihsel dönem
4. **Yüksek Teknoloji** — Gelecek projeksiyonu
5. **En Kötü Senaryo** — Maksimum risk

### Dışa Aktarım
- **CSV:** Tüm simülasyon satırları + faktör girdi değerleri — Python / R / Excel uyumlu
- **JSON:** Meta bilgi + katsayı açıklamaları + veri dizisi

## Veri Kaynakları

| Veri | Kaynak | Dönem |
|------|--------|-------|
| Yıllık ölüm sayıları | [NHTSA FARS](https://www.nhtsa.gov/data) | 1975–2023 |
| VMT (milyar mil) | FHWA Highway Statistics | 1975–2023 |
| Alkol bağlantılı ölüm payı | NHTSA BAC ≥ 0.08 | Seçili yıllar |
| Hız ilişkili ölüm payı | NHTSA | Seçili yıllar |
| Yaya + bisikletçi ölümleri | NHTSA FARS | Seçili yıllar |
| Emniyet kemeri etkinliği | NHTSA / IIHS | — |
| ADAS etki değerlendirmesi | IIHS | — |

## Simülasyon Modeli

**Tarihsel yıllar (1975–2023):** FARS gerçek verisi doğrudan gösterilir.

**Gelecek projeksiyonları (2024–2035):** 2023 taban değerleri üzerinden katsayı tabanlı hesaplama:

```
Alkol:   +%2.5 / puan sapma     Hız:       +%1.8 / puan sapma
Kemersiz: +%1.2 / puan sapma    Dikkat:    +%1.5 / puan sapma
Kemer:   -%0.9 / puan sapma     ADAS:      -%0.3 / puan sapma
Yol:     -%0.15 / birim         VMT:       orantılı büyüme
```

Tüm katsayılar NHTSA ve IIHS yayınlarından türetilmiştir.

## Teknolojiler

- **HTML5** — Tek dosya yapısı (inline CSS + JS)
- **Chart.js 4** — İnteraktif grafikler
- **IBM Plex Sans / Mono** — Tipografi
- **GitHub Pages** — Barındırma

## Lisans
