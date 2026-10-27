ŞCSAL E-SPOR — KURULUM

Gereksinim: Python 3.11+
Yerel çalıştırma:
1) python -m venv .venv
2) Windows: .venv\Scripts\activate  | macOS/Linux: source .venv/bin/activate
3) pip install -r requirements.txt
4) Windows PowerShell: $env:SECRET_KEY="uzun-gizli-anahtar"; $env:ADMIN_KEY="yonetim-sifresi"; python app.py
   macOS/Linux: SECRET_KEY='uzun-gizli-anahtar' ADMIN_KEY='yonetim-sifresi' python app.py
5) http://127.0.0.1:5000

Render: Build Command `pip install -r requirements.txt`; Start Command `gunicorn app:app`. Ortam değişkenleri: SECRET_KEY ve ADMIN_KEY. Kalıcı PostgreSQL için DATABASE_URL ekleyin.
Yönetim paneli: /yonetim

Güvenlik/veri: Var olan SQLite veritabanı silinmez. Eski veritabanına team_number sütunu otomatik ve veri kaybetmeden eklenir. Başvuru telefonları ve gerçek takım adları herkese açık sayfada gösterilmez. Yönetici 1-8 arasında herkese açık takım numarası atar.
