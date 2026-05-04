# Store Location Suitability Prediction

پیش‌بینی مناسب بودن یک موقعیت برای احداث فروشگاه با استفاده از دو مدل:
- **رگرسیون لجستیک** برای طبقه‌بندی خوب / بد
- **رگرسیون خطی** برای پیش‌بینی امتیاز ۰ تا ۱۰۰

## ساختار پروژه
- `dataset/store_location_dataset.csv`: مجموعه داده (۸۰۰ نمونه، ۷ ویژگی)
- `notebooks/logistic_regression.ipynb`: آموزش و ارزیابی مدل طبقه‌بندی
- `notebooks/linear_regression.ipynb`: آموزش و ارزیابی مدل رگرسیون

## پیش‌نیازها
- Python 3.8+
- کتابخانه‌ها (با دستور زیر نصب کنید):
```bash
pip install -r requirements.txt