# 🗺️ SafeSource: Kullanıcı Akış Şeması (User Flow)

Bu belge, bir kullanıcının uygulamayı açtığı andan itibaren yaşadığı deneyimi ve sistemin arka plandaki tepkilerini adım adım özetler.

---

### 🟢 1. Adım: Başlangıç ve Güvenlik Yapılandırması
Uygulama açıldığında kullanıcıyı sade bir "Hoş Geldiniz" ekranı ve güvenlik tercihleri karşılar.
* **Kullanıcı Ne Yapar?** Ekrandaki "Gizlilik Modu" anahtarını (toggle) kullanarak **Bulut Modu** (Hızlı/Gemini) veya **Yerel Mod** (Tam Gizli/Ollama) arasında seçim yapar.
* **AI/Sistem Ne Yapar?** Seçilen moda göre gerekli motoru (LLM) arka planda hazır hale getirir.

---

### 📥 2. Adım: Veri Kaynağını Tanımlama (PDF Yükleme)
Kullanıcı, analiz edilmesini istediği dökümanı sisteme yükler.
* **Kullanıcı Ne Yapar?** PDF dosyasını sürükleyip bırakır veya dosya seçiciyi kullanır.
* **AI/Sistem Ne Yapar?** PDF'i okur, metinleri sayfa numaralarıyla eşleştirerek parçalara (chunks) ayırır ve hızlı arama için indeksler.

---

### 🔍 3. Adım: Akıllı Yönlendirme ve Sorgulama
Sistem, kullanıcının dökümanı anlamasını kolaylaştırmak için inisiyatif alır.
* **Kullanıcı Ne Yapar?** Kendi sorusunu yazar veya sistemin sunduğu **"Otomatik Soru Önerileri"** butonlarından birine tıklar.
* **AI/Sistem Ne Yapar?** PDF'in genelini saniyeler içinde analiz ederek en mantıklı 3 soruyu kullanıcıya sunar.

---

### ⚙️ 4. Adım: İşleme ve Yanıtlama
Sorulan soru, seçilen gizlilik protokolüne göre işlenir.
* **Kullanıcı Ne Yapar?** Soruyu gönderir ve "Analiz Ediliyor..." animasyonunu izler.
* **AI/Sistem Ne Yapar?** İndekslediği parçalar arasından en alakalı olanları bulur, bunları sentezleyerek doğal dilde bir cevap üretir.

---

### 📍 5. Adım: Kanıt Sunumu ve Doğrulama (Final)
Uygulamanın en ayırt edici "Vay be!" anıdır.
* **Kullanıcı Ne Yapar?** Sohbet ekranındaki cevabı okurken, sağ panelde beliren PDF sayfasını inceler.
* **AI/Sistem Ne Yapar?** Cevabın alındığı orijinal PDF sayfasını anında sağ panelde açar ve ilgili paragrafın üzerini fosforlu kalemle çizilmiş gibi (Highlight) vurgular.
* **Sonuç:** Kullanıcı, verisinin güvende olduğundan ve cevabın doğruluğundan %100 emin olarak işlemi tamamlar.
