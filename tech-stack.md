# 🛡️ SafeSource — Teknoloji Yığını ve Kurulum Planı

---

## 🛠️ Teknoloji Yığını (Stack)

| Bileşen | Seçilen Araç | Neden Bu Aracı Seçtik? |
|---|---|---|
| **Dil** | Python | Dünyanın en popüler yapay zeka dili. Kaynak çok, öğrenmesi kolay. |
| **Arayüz (UI)** | Streamlit | HTML/CSS bilmene gerek kalmadan, sadece Python yazarak web sitesi yapmanı sağlar. |
| **Yapay Zeka (Beyin)** | Gemini 1.5 Flash | Çok hızlıdır, ücretsiz kotası geniştir ve büyük PDF'leri okuma kapasitesi yüksektir. |
| **PDF İşleme** | PyMuPDF (fitz) | PDF içindeki metni okumak ve "Kanıt" sisteminde sayfayı resim olarak göstermek için en hızlı kütüphanedir. |

---

## 💡 Neden Bu Teknolojileri Seçiyoruz?

- **Hız:** 10 günün var. React, Django gibi karmaşık framework'leri öğrenmek haftalar sürer. Streamlit ile arayüzü **1 günde** bitirebilirsin.
- **Basitlik:** Gemini API ile ekstra bir Vektör Veritabanı kurmana gerek kalmadan, doğrudan PDF içeriğini Gemini'ye gönderip cevap alabilirsin.
- **Görsel Kanıt:** Projenin en önemli özelliği olan "Sayfayı yan tarafta gösterme" işini PyMuPDF, `sayfayı resme çevir` komutuyla basitçe halleder.

---

## 🚀 Kurulum Adımları

### Adım 1: Python ve Editör Kurulumu

1. **Python** → [python.org](https://python.org) adresinden en son sürümü indir
   > ⚠️ Kurulum sırasında **"Add Python to PATH"** seçeneğini mutlaka işaretle!

2. **VS Code** → [code.visualstudio.com](https://code.visualstudio.com) adresinden indir ve kur

---

### Adım 2: Proje Klasörü ve Kütüphaneler

Bilgisayarında `SafeSource` adında bir klasör oluştur. Terminali aç, bu klasörün içine gir ve şu komutu çalıştır:

```bash
pip install streamlit google-generativeai PyMuPDF
```

---

### Adım 3: API Anahtarını Hazırla

[aistudio.google.com](https://aistudio.google.com) adresine git:

```
"Get API Key" → "Create API Key" → Kopyala (AIza... ile başlar)
```

> 🔑 Şimdilik bir yere not et, bir sonraki adımda kullanacağız.

---

## 🧪 İlk "Merhaba Dünya" Kodu

VS Code'da `app.py` adında bir dosya oluştur ve şu kodu yapıştır:

```python
import streamlit as st
import google.generativeai as genai

# Arayüz Başlığı
st.title("🛡️ SafeSource AI")

# API Anahtarı Girişi (Güvenlik için ekranda görünecek)
api_key = st.sidebar.text_input("Gemini API Key", type="password")

if api_key:
    genai.configure(api_key=api_key)
    st.success("API Anahtarı Tanımlandı!")

    # Basit bir deneme butonu
    if st.button("Selam Ver"):
        model = genai.GenerativeModel('gemini-1.5-flash')
        response = model.generate_content("Merhaba SafeSource projesine başlıyorum, bana kısa bir başarı mesajı ver.")
        st.write(response.text)
else:
    st.warning("Lütfen sol tarafa API anahtarını girin.")
```

Kodu çalıştırmak için terminale şunu yaz:

```bash
streamlit run app.py
```

---

## ✅ Başarı Kontrolü

Terminalde bu komutu çalıştırdıktan sonra tarayıcıda otomatik olarak `http://localhost:8501` açılmalı. Sol panele API anahtarını gir, **"Selam Ver"** butonuna bas — Gemini'den bir yanıt geliyorsa her şey çalışıyor demektir! 🎉

---

## 📅 Sıradaki Adım

> **PDF Yükleme ve İçeriğini Okuma** fonksiyonunu `app.py` dosyasına ekleyeceğiz.

---

*SafeSource Kurulum Planı — Mart 2026*
