ÇCSAL E-SPOR — ÜCRETSİZ YAYINLAMA SÜRÜMÜ

İÇİNDEKİLER
- Flask web sitesi
- Yerelde SQLite, çevrim içi PostgreSQL desteği
- Render için gunicorn başlangıç dosyası
- Supabase PostgreSQL bağlantısı için DATABASE_URL desteği

ÖNEMLİ
- Bu paket, yerel demo paketinden farklı olarak DATABASE_URL ortam değişkeni verilirse PostgreSQL kullanır.
- İnternete açmadan önce ADMIN_KEY ve SECRET_KEY ortam değişkenlerini mutlaka ayarlayın.
- Yönetim paneli adresi: /yonetim?key=ADMIN_KEY_DEĞERİNİZ
- Bu temel sürüm, tam kullanıcı hesabı sistemi değildir. Yönetici anahtarı URL'de kullanıldığından halka açık turnuvada ileride güvenli oturum tabanlı yönetici girişi eklenmesi önerilir.
- Öğrenci iletişim bilgilerini herkese açık sayfalarda göstermeyin.
- Bu site Riot Games tarafından resmî olarak desteklenmez.

YEREL ÇALIŞTIRMA
py -m pip install -r requirements.txt
py app.py
http://127.0.0.1:5000

ÜCRETSİZ YAYINLAMA GENEL ADIMLARI
1. Supabase'de bir proje oluşturun.
2. Supabase Dashboard -> Connect bölümünden PostgreSQL bağlantı URI'sini alın. Mümkünse dış bağlantılar için gösterilen session pooler bağlantısını kullanın. URI'deki parolayı gizli tutun.
3. Render'a GitHub üzerinden bağlanmak için bu klasörü GitHub deposuna yükleyin.
4. Render -> New -> Web Service -> GitHub deponuzu seçin.
5. Build Command: pip install -r requirements.txt
6. Start Command: gunicorn app:app
7. Render Environment Variables bölümüne şunları ekleyin:
   DATABASE_URL = Supabase PostgreSQL URI
   SECRET_KEY = uzun ve rastgele gizli değer
   ADMIN_KEY = uzun ve rastgele yönetici anahtarı
8. Deploy tamamlanınca Render'ın verdiği HTTPS adresini açın.
9. Yönetim panelini şu biçimde açın:
   https://SİTE-ADRESİNİZ/yonetim?key=ADMIN_KEY_DEĞERİNİZ

ÜCRETSİZ PLAN SINIRLARI
- Render ücretsiz web hizmetleri 15 dakika trafik yoksa uykuya geçebilir ve ilk istekte yaklaşık 1 dakika içinde uyanabilir.
- Render'ın ücretsiz web servisindeki yerel dosyalar kalıcı değildir; bu nedenle SQLite dosyası yerine Supabase PostgreSQL kullanılmalıdır.
- Supabase ücretsiz projeler, bir hafta yetersiz etkinlikte duraklatılabilir; ücretsiz veritabanı kotası sınırlıdır. Düzenli dışa aktarma/yedekleme yapın.
- Ücretsiz planlar kesintisiz çalışma garantisi vermez.

GİZLİLİK VE GÜVENLİK
- Gerçek öğrenci isimleri ve iletişim bilgileri toplanacaksa okul yönetiminin iznini alın ve hangi verinin neden toplandığını açıklayın.
- Parolaları ve veritabanı bağlantı adresini sohbetlerde, GitHub'a açık dosyalarda veya herkese açık sayfalarda paylaşmayın.
- Bu başlangıç sürümü internet yayını için temel altyapı sağlar; geniş kullanıma açmadan önce rate limiting, CAPTCHA/spam koruması, güvenli yönetici oturumu ve yedekleme süreci eklenmelidir.
