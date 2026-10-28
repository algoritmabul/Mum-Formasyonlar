# 🕯️ Candlestick Pattern Detection — ASELS.IS

**Python · TA-Lib · yfinance · Matplotlib · mplfinance**

ASELSAN (BIST: ASELS) hisse senedinin tarihsel fiyat verileri üzerinde **61 farklı Japon mum formasyonunu** tespit eden ve sonuçlarını grafiklerle görselleştiren Python projesi.

Bu çalışma, [Entreprenerdly — Automating 61 Candlestick Trading Patterns in Python](https://entreprenerdly.com/automating-61-candlestick-trading-patterns-in-python/) başlıklı makalede yayımlanan Python kodlarının bir araya getirilmesi ve ASELSAN hissesi üzerinde uygulanmasıyla hazırlanmıştır.

## 📌 Project Overview

Japon mum formasyonları, fiyat hareketlerini teknik analiz perspektifinden incelemek için kullanılan yaygın araçlardan biridir. Bu proje, TA-Lib kütüphanesinin mum formasyonu fonksiyonlarını kullanarak ASELSAN'ın tarihsel OHLC fiyat verilerini analiz eder.

Tespit edilen formasyonlar, hisse fiyatı grafiği üzerinde işaretlenir. Ayrıca her formasyonun görüldüğü tarihler çevresindeki mum grafikleri ayrı panellerde gösterilerek fiyat hareketlerinin daha yakından incelenmesi sağlanır.

### ✨ Features

- **61 candlestick patterns:** TA-Lib üzerinden farklı mum formasyonlarının taranması.
- **Historical market data:** Yahoo Finance üzerinden ASELSAN fiyat verilerinin alınması.
- **Pattern detection:** Formasyonların oluştuğu tarihlerin otomatik belirlenmesi.
- **Price chart visualization:** Formasyon tarihlerinin kapanış fiyatı grafiğinde işaretlenmesi.
- **Candlestick inspection:** Tespit edilen son beş formasyon örneğinin yakın plan mum grafiklerinin oluşturulması.
- **Date annotations:** Formasyon tarihlerinin grafik üzerinde gösterilmesi.
- **Automated plotting:** Her formasyon türü için ayrı analiz grafiği oluşturulması.

## 📊 Data & Configuration

| Parameter | Value |
|---|---|
| Stock | ASELSAN |
| BIST Ticker | `ASELS.IS` |
| Data Source | Yahoo Finance |
| Start Date | 2020-01-01 |
| End Date | 2024-02-16 |
| Data Frequency | Daily |
| Pattern Library | TA-Lib |
| Visualization | Matplotlib, mplfinance |

> Not: `yfinance` tarih aralığında bitiş tarihi genellikle hariç tutulur. Bu nedenle 16 Şubat 2024 tarihinin veriye dahil olup olmadığı ayrıca kontrol edilmelidir.

## 🧠 How It Works

### 1. Download historical data

ASELSAN'ın günlük Open, High, Low ve Close (OHLC) fiyat verileri Yahoo Finance üzerinden alınır.

### 2. Detect candlestick patterns

TA-Lib'in `CDL` fonksiyonları kullanılarak her formasyon için ayrı bir sinyal sütunu oluşturulur.

TA-Lib fonksiyonları genel olarak şu değerleri döndürür:

- `100` veya pozitif değerler: Formasyonun boğa yönlü sınıflandırılması.
- `-100` veya negatif değerler: Formasyonun ayı yönlü sınıflandırılması.
- `0`: İlgili mumda formasyon tespit edilmemesi.

Dönen değerlerin tam anlamı ilgili TA-Lib fonksiyonuna göre değişebilir.

### 3. Mark detected patterns

Formasyonun tespit edildiği tarihler, kapanış fiyatı grafiğinde dikey çizgiler ve tarih etiketleriyle gösterilir.

### 4. Visualize individual occurrences

Her formasyonun son beş tespitinden mevcut olanlar için, formasyon tarihinin yaklaşık beş takvim günü öncesi ve sonrası incelenir. Bu aralıkta işlem günü bulunmaması veya hafta sonları nedeniyle gerçek örnek sayısı değişebilir.

### 5. Generate charts

Her formasyon türü için ayrı bir grafik oluşturulur. Böylece farklı mum formasyonlarının ASELSAN fiyat geçmişindeki dağılımı görsel olarak incelenebilir.

## 🕯️ Candlestick Patterns

Kodda yer alan formasyonlar arasında şunlar bulunur:

| Category | Examples |
|---|---|
| Reversal patterns | Hammer, Hanging Man, Shooting Star, Morning Star, Evening Star |
| Engulfing patterns | Bullish/Bearish Engulfing |
| Doji patterns | Doji, Dragonfly Doji, Gravestone Doji, Morning Doji Star |
| Three-candle patterns | Three Black Crows, Three White Soldiers, Three Inside Up/Down |
| Continuation patterns | Rising/Falling Three Methods, Mat Hold, Tasuki Gap |
| Other patterns | Harami, Piercing Pattern, Dark Cloud Cover, Kicking, Hikkake |

Liste, kodda tanımlanan 61 formasyon fonksiyonunun tamamını kapsayan bir katalog değil, öne çıkan örneklerin özetidir.

## 🛠️ Installation

Python ortamını oluşturduktan sonra gerekli kütüphaneleri yükle:

```bash
pip install yfinance pandas matplotlib mplfinance
pip install TA-Lib
```

TA-Lib kurulumu kullanılan işletim sistemi ve Python sürümüne bağlı olarak ek sistem bağımlılıkları gerektirebilir. Kurulum sonrasında aşağıdaki komutla kontrol edebilirsin:

```python
import talib
print(talib.__version__)
```

## ▶️ Usage

Python kodunu `candlestick_patterns.py` adıyla kaydet ve çalıştır:

```bash
python candlestick_patterns.py
```

Program, ASELSAN verilerini indirir, tanımlı formasyonları tarar ve tespit edilen formasyonlar için grafik pencereleri oluşturur.

**Requirements:** Python, internet bağlantısı ve grafik arayüzünü destekleyen bir ortam.

## ⚠️ Limitations

- Proje, formasyon tespiti ve görselleştirme amacı taşır; kendi başına bir alım-satım stratejisi değildir.
- Bir mum formasyonunun tespit edilmesi, fiyatın belirli bir yönde hareket edeceğini garanti etmez.
- İşlem maliyetleri, kayma, pozisyon büyüklüğü, stop-loss ve portföy riski hesaplanmaz.
- Kodda ileriye dönük getiri analizi, backtest veya işlem performansı ölçümü bulunmaz.
- Sonuçlar kullanılan veri kaynağına, tarih aralığına ve TA-Lib uygulamasına bağlıdır.

## 📚 Reference

Original article: [Automating 61 Candlestick Trading Patterns in Python — Entreprenerdly](https://entreprenerdly.com/automating-61-candlestick-trading-patterns-in-python/)

The code in this repository consolidates the candlestick-pattern detection and visualization approach described in the article and applies it to ASELSAN (`ASELS.IS`).

## ⚖️ Disclaimer

This project is intended for educational and technical analysis research purposes only. It does not constitute investment advice or a recommendation to buy or sell any security. Historical patterns do not guarantee future results.

## 📄 License & Attribution

The implementation is based on an approach described in the referenced article. Please review the original author's licensing and reuse terms before redistributing adapted code. A license for this repository should be specified separately if applicable.

