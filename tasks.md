# SafeSource MVP Görev Listesi

Bu görev listesi `prd.md` temel alınarak hazırlanmıştır ve uygulamayı adım adım geliştirmek için optimize edilmiştir.

## 0) Proje Kurulumu ve Planlama
- [ ] Proje klasör yapısını oluştur (`app`, `core`, `services`, `data`, `tests`).
- [ ] Python 3.10+ sanal ortamını oluştur ve aktive et.
- [ ] Temel bağımlılıkları yükle: `streamlit`, `langchain`, `pymupdf`, `faiss-cpu` veya `chromadb`, `python-dotenv`, `google-generativeai` (veya ilgili istemci), `ollama`.
- [ ] `requirements.txt` dosyasını oluştur ve sürümleri sabitle.
- [ ] `.env.example` dosyası oluştur (`GEMINI_API_KEY`, model ayarları vb.).
- [ ] Başlangıç `README.md` hazırla (kurulum + çalıştırma komutları).

## 1) PDF İşleme Altyapısı
- [ ] PDF yükleme akışını tasarla (Streamlit uploader + dosya doğrulama).
- [ ] PyMuPDF ile PDF metnini sayfa bazında çıkar.
- [ ] Sayfa numarası ve metin eşleşmesini koruyan veri yapısı oluştur.
- [ ] Boş/sorunlu PDF durumları için hata yakalama ekle.
- [ ] Örnek 2-3 PDF ile metin çıkarma doğrulaması yap.

## 2) Chunking ve Embedding Katmanı
- [ ] Metni anlamlı parçalara bölen chunking fonksiyonunu yaz.
- [ ] Her chunk için metadata tut (`page`, `chunk_id`, `source`).
- [ ] Embedding üretimi için ortak bir arayüz tanımla.
- [ ] FAISS veya ChromaDB tabanlı vektör store kur.
- [ ] Chunk’ları vektör store’a yazma/okuma fonksiyonlarını tamamla.
- [ ] İlk retrieval testi yap (sorguya en alakalı chunk’lar geliyor mu?).

## 3) Online Mod (Gemini) Entegrasyonu
- [ ] Gemini istemcisi için servis katmanı oluştur.
- [ ] RAG prompt şablonu yaz (cevap + kaynak sayfa formatı).
- [ ] Soru geldiğinde retrieval + generation zincirini çalıştır.
- [ ] Model çıktısını JSON parse ederek `answer` ve `page` bilgisini ayır.
- [ ] İlk uçtan uca test: PDF yükle -> soru sor -> cevap al.

## 4) Offline Mod (Ollama) Entegrasyonu
- [ ] Ollama bağlantı ve model kontrol mekanizması ekle.
- [ ] Gemini ile aynı sözleşmede (answer/page) cevap döndüren adapter yaz.
- [ ] Mod seçimi için tek bir yönlendirici servis geliştir (cloud/local switch).
- [ ] İnternet kapalı senaryosu için smoke test çalıştır.
- [ ] Local model başarısızsa kullanıcıya açıklayıcı hata göster.

## 5) Kanıt Gösterimi (PDF Sayfası Render)
- [ ] PyMuPDF ile seçilen sayfayı görsele dönüştürme fonksiyonu yaz.
- [ ] Cevaptan gelen `page` bilgisine göre ilgili sayfayı otomatik göster.
- [ ] Geçersiz sayfa numarası durumunda fallback davranışı ekle.
- [ ] Sağ panelde görüntü kalite/performans dengesini optimize et.

## 6) Streamlit Arayüzü (3 Panel)
- [ ] Sol panel: PDF yükleme, mod seçimi (Cloud/Local), temizle butonu.
- [ ] Orta panel: chat alanı, kullanıcı/AI mesaj balonları, giriş kutusu.
- [ ] Sağ panel: seçilen kanıt sayfası görüntüleyici.
- [ ] Session state ile sohbet geçmişini sakla.
- [ ] Sık sorulan/soru önerisi butonlarını ekle.
- [ ] Yeni cevap geldiğinde sağ panelin ilgili sayfayı güncellemesini sağla.

## 7) Dayanıklılık ve Hata Yönetimi
- [ ] Tüm kritik adımlara `try/except` ve kullanıcı dostu hata mesajları ekle.
- [ ] API timeout, boş sonuç, model yanıt formatı bozukluğu senaryolarını ele al.
- [ ] Loglama altyapısı ekle (en azından info/error seviyeleri).
- [ ] Girdi doğrulama ve temel güvenlik kontrollerini ekle.

## 8) Test ve Kalite Kontrol
- [ ] Temel birim testleri yaz (chunking, parser, page mapping).
- [ ] Entegrasyon testleri yaz (RAG akışı online/offline).
- [ ] Manuel test checklist’i oluştur:
  - [ ] PDF yükleme
  - [ ] Mod değiştirme
  - [ ] Soru-cevap doğruluğu
  - [ ] Sayfa kanıtı gösterimi
  - [ ] Hata senaryoları
- [ ] Performans ölçümü yap (ilk cevap süresi, sonraki sorgu süresi).

## 9) Yayınlama ve Teslimat
- [ ] Projeyi temizle (gereksiz dosyalar, debug çıktıları).
- [ ] `README.md`yi final hale getir (özellikler, kurulum, kullanım, sınırlamalar).
- [ ] Git deposunu başlat ve ilk sürümü etiketle (MVP v1.0).
- [ ] Demo senaryosu hazırla ve kısa demo videosu çek.
- [ ] GitHub’a yükle ve paylaşılabilir bağlantıyı doğrula.

## 10) 10 Günlük Önerilen Dağılım
- [ ] Gün 1: Kurulum + PDF metin çıkarma.
- [ ] Gün 2: Chunking + metadata + vektör store.
- [ ] Gün 3: Gemini ile ilk RAG akışı.
- [ ] Gün 4: JSON kaynak sayfası üretimi ve parse.
- [ ] Gün 5: Ollama entegrasyonu.
- [ ] Gün 6: Sayfa render ve kanıt paneli.
- [ ] Gün 7: Streamlit 3 panel temel UI.
- [ ] Gün 8: Sohbet geçmişi + öneri butonları.
- [ ] Gün 9: Hata yönetimi + testler.
- [ ] Gün 10: Son düzeltmeler + GitHub + demo.
