ŞCSAL E-SPOR — KURULUM

Gereksinim: Python 3.11+
Yerel çalıştırma:
1) python -m venv .venv
2) Windows: .venv\Scripts\activate | macOS/Linux: source .venv/bin/activate
3) pip install -r requirements.txt
4) Windows PowerShell:
   $env:SECRET_KEY="uzun-rastgele-gizli-anahtar"
   $env:ADMIN_KEY="yonetim-sifresi"
   python app.py
   macOS/Linux:
   SECRET_KEY='uzun-rastgele-gizli-anahtar' ADMIN_KEY='yonetim-sifresi' python app.py
5) http://127.0.0.1:5000

Yönetici paneli: /yonetim
Render ayarları: Build Command = pip install -r requirements.txt
Start Command = gunicorn app:app
Ortam değişkenleri: SECRET_KEY, ADMIN_KEY, DATABASE_URL

ÖNEMLİ:
- Bu pakette render.yaml özellikle bulunmuyor; mevcut Render ayarlarını değiştirmeyin.
- Supabase PostgreSQL kullanıyorsanız DATABASE_URL değişkenini Render Environment bölümünde ayarlayın.
- Var olan veritabanı silinmez. Eski teams tablosuna eksik rank alanları otomatik eklenir.
- Kaptan telefon numarası ve Peak Rank bilgileri yalnızca yönetici panelinde gösterilir.
- Herkese açık sayfalarda takım numaraları gösterilir; gerçek takım adı, oyuncu bilgileri, telefon ve ranklar gösterilmez.
- Takım silinince başvuru/oyuncu bilgileri ve ilgili maç sonuçları temizlenir; boş fikstür slotları turnuva ağacının yapısını korumak için kalır.
- Rank simgeleri bu projeye özel basit SVG çizimleridir; Riot Games'in resmî görselleri değildir.
