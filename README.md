# en_populer_youtube_video_kategorileri
2005–2025 yılları arasındaki popüler YouTube video kategorileri
# YouTube Video Kategori Analizi (2005-2025)

Bu proje, 2005-2025 yılları arasında YouTube'da en popüler video kategorilerini analiz etmektedir. Veri seti, Kaggle'dan alınan **"Most Popular 1000 YouTube Videos"** verilerine dayanmaktadır.

## 📊 Kullanılan Kütüphaneler

- pandas
- matplotlib
- seaborn
- datetime

## 🔍 Veri Hazırlığı

Aşağıdaki kodlarla veri seti yüklenmiş, tarih sütunu işlenmiş ve izlenme sayısı sayısal formata dönüştürülmüştür:

```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
import datetime

# CSV dosyasını oku
df = pd.read_csv('Most_popular_1000_Youtube_videos.csv')

# Yayınlanma tarihini datetime formatına çevir
df['published'] = pd.to_datetime(df['published'], errors='coerce')

# Yıl bilgisini çıkart
df['year'] = df['published'].dt.year

# İzlenme sayısını sayısal formata çevir (virgülleri kaldırarak)
df['Video views'] = df['Video views'].replace(',', '', regex=True).astype(float)

# Temizlenmiş veriyi kaydet
df.to_csv("cl_youtube_data.csv", index=False)
