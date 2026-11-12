# Cross-Asset Financial Market EDA — Final

پروژه پایان دوره Data Analyst با موضوع بررسی رابطه بین **S&P 500، Gold، WTI Oil، DXY و VIX**.

## چرا این نسخه اصلاح شد؟
فایل خام S&P ساختار چندبلوک دارد: 503 ticker برای هر یک از `Close / High / Low / Open / Volume`. در نسخه نهایی، فقط بلوک `Close` برای محاسبه بازده استفاده می‌شود تا متغیرهای مختلف با هم قاطی نشوند.

## ساختار
- `notebooks/01_Prepare_SP500.ipynb`: استخراج، پاک‌سازی، کنترل کیفیت و ساخت proxy از دیتاست اصلی.
- `notebooks/02_Cross_Asset_EDA.ipynb`: ادغام S&P با Gold/Oil/DXY/VIX و EDA کامل.
- `data/sp500_market_proxy.csv`: خروجی سبک و آماده برای Notebook دوم.
- `data/sp500_quality_report.csv`: خلاصه کنترل کیفیت دیتاست اصلی.

## کنترل واقعی دیتاست ارسالی
- Raw shape: 4,236 × 2,516
- 503 ticker برای هر یک از 5 متغیر OHLCV
- بازه زمانی: 2010-01-04 تا 2026-10-30
- 445 ticker حداقل 80٪ پوشش داده دارند.
- تاریخ تکراری و Close غیرمثبت در بررسی اولیه مشاهده نشد.

## داده‌های cross-asset
Notebook دوم هنگام اجرا Gold (`GC=F`)، WTI (`CL=F`)، DXY (`DX-Y.NYB`)، VIX (`^VIX`) و S&P رسمی (`^GSPC`) را با `yfinance` می‌گیرد. بنابراین اعداد cross-asset به تاریخ اجرای Notebook وابسته‌اند و نباید بدون اجرای دوباره، نتیجه عددی ثابت ادعا شود.

## نصب
```bash
pip install -r requirements.txt
jupyter notebook notebooks/01_Prepare_SP500.ipynb
jupyter notebook notebooks/02_Cross_Asset_EDA.ipynb
```

## GitHub
فایل خام 162MB است و بهتر است مستقیماً در Git معمولی commit نشود؛ اگر لازم است در repository نگه داشته شود از Git LFS استفاده کنید.
