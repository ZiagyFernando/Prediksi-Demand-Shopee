# 📈 Demand Forecasting Produk Fashion di Marketplace Shopee

Proyek ini bertujuan untuk memprediksi jumlah permintaan (penjualan) produk fashion di marketplace Shopee selama 14 hari ke depan menggunakan model **Facebook Prophet**, dan menyajikan hasil prediksinya dalam bentuk **visualisasi dashboard menggunakan Tableau**.

---

## 🧠 Latar Belakang

Permintaan terhadap produk fashion di platform e-commerce sangat fluktuatif. Dengan adanya prediksi permintaan yang akurat, pelaku bisnis dapat:
- Mengelola stok dengan lebih efisien
- Merencanakan strategi pemasaran
- Menghindari kelebihan atau kekurangan barang

---

## 📁 Dataset

Dataset yang digunakan diambil dari [Kaggle - Shopee Sales Dataset](https://www.kaggle.com/) (atau sebutkan sumber lain jika ada), kemudian dilakukan preprocessing agar dapat digunakan oleh model forecasting Prophet.

**Fitur utama:**
- `date`: Tanggal penjualan
- `product_name`: Nama produk fashion
- `quantity`: Jumlah produk yang terjual

---

## ⚙️ Tools & Teknologi

- **Python** (Pandas, Prophet, Matplotlib)
- **Facebook Prophet**: Library forecasting berbasis additive time series model
- **Tableau Public**: Visualisasi hasil prediksi

---

## 🔍 Langkah-langkah Proyek

### 1. Data Preparation
- Mengelompokkan data penjualan harian per kategori fashion
- Membersihkan data yang kosong/berulang
- Mengubah ke format time series

### 2. Forecasting dengan Prophet

```python
from prophet import Prophet

model = Prophet()
model.fit(daily_sales)

future = model.make_future_dataframe(periods=14)
forecast = model.predict(future)

forecast[['ds', 'yhat', 'yhat_lower', 'yhat_upper']].to_csv('forecast_fashion.csv', index=False)
