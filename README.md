# BTC/THB 1-Minute OHLCV Data (Bitkub)

ข้อมูล OHLCV รายนาที (1m) ของ BTC/THB จาก Bitkub Exchange 
สำหรับใช้ทำ backtest กลยุทธ์การเทรด

## 📊 ข้อมูลที่มี

| ปี | จำนวนแท่ง | ขนาด | ช่วงเวลา |
|---|---|---|---|
| 2018 | 66,487 | 1.0 MB | 2018-05-18 → 2018-12-31 |
| 2019 | 165,233 | 2.6 MB | 2019-01-01 → 2019-12-31 |
| 2020 | 347,683 | 6.0 MB | 2020-01-01 → 2020-12-31 |
| 2021 | 513,673 | 10.6 MB | 2021-01-01 → 2021-12-31 |
| 2022 | 481,786 | 10.0 MB | 2022-01-01 → 2022-12-31 |
| 2023 | 429,231 | 8.4 MB | 2023-01-01 → 2023-12-31 |
| 2024 | 452,601 | 9.3 MB | 2024-01-01 → 2024-12-31 |
| 2025 | 485,905 | 10.0 MB | 2025-01-01 → 2025-12-31 |
| 2026 | 224,886 | 4.7 MB | 2026-01-01 → 2026-06-16 |

## 📁 รูปแบบไฟล์

แต่ละไฟล์เป็น CSV บีบอัด gzip (`.csv.gz`) มี columns:

- `timestamp` — Unix timestamp
- `datetime` — เวลา (UTC)
- `open`, `high`, `low`, `close` — ราคา BTC/THB
- `volume` — ปริมาณการเทรด

## 🐍 วิธีโหลดข้อมูล (Python)

```python
import pandas as pd

# อ่านไฟล์เดียว (gzip อ่านได้เลย ไม่ต้องแตกไฟล์)
df = pd.read_csv('data/btc_thb_1m_2024.csv.gz')

# รวมหลายปี
import glob
files = sorted(glob.glob('data/*.csv.gz'))
df = pd.concat([pd.read_csv(f) for f in files], ignore_index=True)
```

## ⚠️ Disclaimer

- ข้อมูลดึงจาก Bitkub public API เพื่อการศึกษา/วิจัยเท่านั้น
- ข้อมูลไม่มีการรับประกันความถูกต้อง ใช้ด้วยความระมัดระวัง
- ช่วงที่ volume = 0 หรือไม่มีการเทรด อาจมี gap ของข้อมูล
- Data sourced from Bitkub. Not affiliated with or endorsed by Bitkub.
