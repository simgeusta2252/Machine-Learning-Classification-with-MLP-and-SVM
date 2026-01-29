# Machine Learning Classification with MLP and SVM

## 🔍 Proje Özeti
Bu projede, iki farklı ikili sınıflandırma veri seti (**HIGGS** ve **RCV1**) üzerinde  
**Çok Katmanlı Algılayıcı (MLP)** ve **Destek Vektör Makineleri (SVM)** algoritmaları incelenmiştir.

Projenin temel amacı, makine öğrenmesi algoritmalarının:
- nasıl öğrendiğini,
- optimizasyon sürecinin nasıl işlediğini,
- hiperparametrelerin modele etkisini  

hazır kütüphaneler kullanmadan, **yalnızca NumPy ile sıfırdan implementasyon** yaparak anlamaktır.

---

## 📊 Kullanılan Veri Setleri

### 🔹 HIGGS Veri Seti
- 28 adet sayısal özellik
- Doğrusal olmayan ilişkiler içerir
- İkili sınıflandırma problemi

### 🔹 RCV1 Veri Seti
- 47.236 boyutlu, seyrek (sparse) özellik uzayı
- Metin tabanlı (TF-IDF) veri
- Yüksek boyutlu ikili sınıflandırma problemi

Her iki veri seti de:
- eğitim (train),
- doğrulama (validation),
- test  

kümelerine ayrılmıştır.

---

## 🧠 Yöntem
Bu projede tüm modeller:
- ileri besleme (forward propagation),
- geri yayılım (backpropagation),
- gradyan hesaplamaları,
- ağırlık güncellemeleri  

**NumPy kullanılarak sıfırdan** geliştirilmiştir.

Amaç, modelin bir *“kara kutu”* gibi değil, matematiksel olarak nasıl çalıştığını doğrudan gözlemlemektir.  
TensorFlow, PyTorch veya scikit-learn gibi hazır kütüphaneler **kullanılmamıştır**.

---

## 🤖 Kullanılan Modeller

### 🔹 Çok Katmanlı Algılayıcı (MLP)
- Tam bağlantılı (fully connected) sinir ağı
- Backpropagation ile eğitilmiştir
- Test edilen aktivasyon fonksiyonları:
  - Sigmoid
  - Tanh
  - ReLU

### 🔹 Destek Vektör Makineleri (SVM)
- Lineer SVM modeli
- **Pegasos algoritması** kullanılarak implementasyon yapılmıştır
- Yüksek boyutlu ve seyrek veri setleri için uygundur

### 🔹 Stacking (Hibrit Model)
- MLP ve SVM modellerinin çıktıları birleştirilmiştir
- Meta-model olarak Logistic Regression kullanılmıştır
- Amaç, model varyansını azaltmak ve daha stabil sonuçlar elde etmektir

---

## ⚙️ Deneysel Çalışmalar
Aşağıdaki hiperparametrelerin modele etkisi incelenmiştir:

- **Optimizasyon Algoritmaları:** SGD, Momentum, RMSprop, Adam  
- **Learning Rate Değerleri:** 0.1, 0.01, 0.001  
- **Aktivasyon Fonksiyonları:** Sigmoid, Tanh, ReLU  

Eğitim süreci boyunca **loss–epoch grafikleri** analiz edilmiştir.

---

## 📈 Sonuçlar ve Gözlemler
- Adam ve RMSprop, SGD’ye göre daha hızlı yakınsama sağlamıştır
- Sigmoid aktivasyonda **vanishing gradient** problemi gözlemlenmiştir
- Learning rate = **0.01**, en dengeli sonuçları vermiştir
- HIGGS veri setinde MLP, SVM’ye kıyasla daha iyi performans göstermiştir
- Stacking yöntemi, model performansını ve kararlılığını artırmıştır

**Değerlendirme metrikleri:**
- Accuracy
- F1-Score
- Confusion Matrix
