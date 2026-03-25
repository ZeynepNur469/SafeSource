# 📑 PRD: SafeSource AI (Product Requirement Document)

**Proje Adı:** SafeSource  
**Versiyon:** 1.0  
**Geliştirme Süresi:** 10 Gün (MVP)  
**Hazırlayan:** Kıdemli Full Stack Developer Rehberi

---

## 1. Ürün Özeti (Executive Summary)
**SafeSource**, yoğun bilgi içeren PDF belgeleriyle etkileşime girmeyi sağlayan bir "Akıllı Asistan" uygulamasıdır. Kullanıcıların uzun metinlerde kaybolmasını önler, sorularına doğrudan cevap verir ve en önemlisi bu cevapları belgedeki **görsel kanıtlarla** destekler. "Önce Gizlilik" prensibiyle, verilerin yerel cihazda işlenmesine (Offline Mode) olanak tanır.

---

## 2. Kullanıcı Deneyimi (Kullanıcı Ne Yapar?)
1. **Güvenlik Seçimi:** Kullanıcı "Bulut Modu" (Gemini) veya "Yerel Mod" (Ollama) seçeneklerinden birini belirler.
2. **Dosya Yükleme:** Analiz etmek istediği PDF dosyasını sürükleyip bırakır.
3. **Sorgulama:** Mesaj kutusuna belgenin içeriğiyle ilgili bir soru yazar.
4. **İnceleme:** Gelen cevabı okur ve sağ panelde otomatik olarak açılan PDF sayfasındaki işaretli alanı kontrol ederek bilgiyi teyit eder.

---

## 3. Sistemin İşleyişi (AI Ne Yapar?)
* **Parçalama (Chunking):** PDF metinlerini küçük, anlamlı parçalara böler ve sayfa numaralarıyla eşleştirir.
* **Anlamlandırma (Embedding):** Metinleri matematiksel kodlara dönüştürerek konunun "neyle ilgili" olduğunu anlar.
* **Arama (Retrieval):** Soru geldiğinde, kütüphanesindeki parçalar arasından en alakalı olanları bulur.
* **Yanıtlama (Generation):** Seçilen parçaları kullanarak doğal bir dille cevap yazar ve sayfa numarasını arayüze iletir.



---

## 4. Ekran Tasarımları (Wireframe)

* **Sol Menü:** Dosya Yükle butonu, Gizlilik Modu anahtarı (Switch), Temizle butonu.
* **Orta Panel:** Chat arayüzü (Kullanıcı balonları sağda, AI balonları solda).
* **Sağ Panel:** PDF Görüntüleyici (Cevap geldiğinde ilgili sayfaya otomatik kaydırma yapar).

---

## 5. Fonksiyonel Gereksinimler
* **RAG Mimarisi:** Doküman tabanlı soru-cevap yeteneği.
* **Hibrit Model Desteği:** * *Online:* Gemini 1.5 Flash (Hızlı sonuç).
    * *Offline:* Ollama / Llama 3 (Tam gizlilik).
* **Görsel Kaynak Gösterimi:** PDF üzerinde ilgili sayfanın render edilmesi.

---

## 6. Teknik Gereksinimler (Tech Stack)
* **Programlama Dili:** Python 3.10+
* **Web Arayüzü:** Streamlit (Python tabanlı hızlı UI).
* **AI Framework:** LangChain (Bileşenleri birbirine bağlamak için).
* **PDF Kütüphanesi:** PyMuPDF (Fitz) (Sayfa yakalama ve görüntüleme için).
* **Vektör Veritabanı:** FAISS veya ChromaDB (Hızlı arama için).
* **Modeller:** Google Gemini API (Bulut) & Ollama (Yerel).

---

## 7. 10 Günlük Başarı Kriterleri ve Görevler (MVP Planı)

### **Gün 1-3: Temel Mekanizma**
- [ ] Python ortamının kurulması ve kütüphanelerin yüklenmesi.
- [ ] Gemini API ile PDF'ten metin okuma ve ilk başarılı soru-cevap testi.

### **Gün 4-6: Kanıt ve Yerel Mod**
- [ ] Gemini'den sayfa numarası bilgisini çekme (JSON formatında).
- [ ] Ollama (Yerel Model) entegrasyonu ile internet kapalıyken cevap alma.
- [ ] PyMuPDF ile seçilen sayfanın arayüzde resim olarak gösterilmesi.

### **Gün 7-9: Arayüz ve UI/UX**
- [ ] Streamlit ile üç panelli (Sol-Orta-Sağ) yerleşimin kodlanması.
- [ ] Soru önerisi butonlarının ve sohbet geçmişinin eklenmesi.

### **Gün 10: Final ve Test**
- [ ] Hataların giderilmesi (Exception Handling).
- [ ] Projenin GitHub'a yüklenmesi ve demo videosunun çekilmesi.
