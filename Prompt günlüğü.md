# YAPAY ZEKA İLE ORTAK GELİŞTİRME (VIBE CODING) PROMPT GÜNLÜĞÜ

Bu günlük, projenin veri tedariği aşamasından son tahmin modelinin kurulmasına kadar geçen süreçte yapay zeka asistanı ile yapılan teknik diyaloğu, stratejik kararları ve kronolojik adımları içermektedir.

---

## FAZ 1: VERİ ÖN İŞLEME VE ÖZELLİK MÜHENDİSLİĞİ (DATA PREPROCESSING)

### 1. Prompt: Kaggle Verisini İçeri Alma ve İlk İnceleme (Adım: Veri Yükleme)
"Kaggle'dan indirdiğim 'traffic_index.csv' dosyasını Google Colab ortamına yükledim. Bu veriyi Pandas DataFrame olarak okumak, veri boyutunu, ilk 5 satırını ve sütunların veri tiplerini incelemek istiyorum. Türkçe karakter hatası (encoding) yaşamamak için güvenli bir Python kodu yazar mısın?"

* **Açıklama:** Verinin Colab ortamına sorunsuz aktarılması ve df.shape, df.head(), df.info() komutlarıyla verinin anatomisinin (3288 satır, 4 sütun) keşfedilmesi sağlanmıştır.

### 2. Prompt: Tarih Dönüşümleri ve Zaman Özellikleri Türetme (Adım: Tip Dönüşümü)
"Elimdeki veri setinde trafficindexdate sütunu metin (object) tipinde ve içinde '+0000' gibi karmaşık zaman damgası ekleri var. Bu sütunu Pandas'ın to_datetime fonksiyonu ile gerçek bir tarih formatına çevirmek istiyorum. Ayrıca bu tarihten yil, ay, gun ve gun_adi adında 4 yeni sütun (feature) üretmek istiyorum. Gün isimlerini Türkçe yapabilir miyiz?"

* **Açıklama:** Projenin teknik gereksinimlerindeki "Tip Dönüşümleri ve Özellik Mühendisliği" maddesini karşılamak için yazılmıştır. Modelin ham metni anlayamayacağı öngörülerek takvim verileri sayısal girdilere dönüştürülmüştür.

### 3. Prompt: Veri Bütünlüğü ve Eksik Değer Kontrolü (Adım: Veri Temizleme)
"Dönüşümleri tamamlanan veri setinde herhangi bir eksik (null/NaN) değer olup olmadığını sütun bazında kontrol eden ve toplam eksik veri sayısını raporlayan kodu yazar mısın?"

* **Açıklama:** Veri temizleme adımının en kritik parçasıdır. Analiz sonrasında veri setinde hiç eksik veri olmadığı (0 değeri) bu prompt ile doğrulanmıştır.

---

## FAZ 2: İSTATİSTİKSEL ANALİZ VE AYKIRI DEĞER KONTROLÜ

### 4. Prompt: Temel Betimsel İstatistiklerin Çıkarılması (Adım: Temel İstatistikler)
"Veri setindeki sayısal sütunların (minimum, maksimum ve ortalama trafik endeksleri) ortalama, standart sapma, min, max ve çeyreklik (%25, %50, %75) değerlerini tek bir tablo halinde görmek istiyorum. Pandas ile bunu nasıl hesaplarız?"

* **Açıklama:** Verinin genel karakteristiğini anlamak için .describe() fonksiyonunu tetikleyen prompttur. İstanbul'un 9 yıllık trafik ortalamasının %27.68 olduğu bu adımda keşfedilmiştir.

### 5. Prompt: IQR Yöntemi ile Aykırı Değer Tespiti (Adım: Aykırı Değer Analizi)
"İstanbul trafik endeksi verisindeki ekstrem günleri (aykırı değerleri) matematiksel olarak bulmak istiyorum. Veri biliminde kabul gören IQR (Çeyrekler Açıklığı) yöntemini kullanarak alt ve üst sınırları belirleyen, bu sınırların dışındaki satır sayısını bulan ve bu ekstrem günlerden ilk 5 tanesini ekrana yazdıran kodu hazırlar mısın?"

* **Açıklama:** Matematiksel olarak 126 adet aykırı gün bulunmasını sağlayan prompttur. Çıkan sonuçların (Pandemi yasakları, seçim günleri gibi ekstrem durumlar) analitik dürüstlük gereği silinmeyip korunması kararı bu analiz sonrası alınmıştır.

---

## FAZ 3: KEŞİFSEL VERİ ANALİZİ (EDA) VE DÜRÜST GÖRSELLEŞTİRME

### 6. Prompt: Araştırma Soruları ve İlk Grafik Seti (Adım: Veri Görselleştirme)
"Tanımladığım 3 araştırma sorusuna (Günlük, aylık ve yıllık trafik değişimleri ile değişkenlerin birbiriyle ilişkisi) yanıt aramak için Seaborn ve Matplotlib kullanarak tek bir figürde 4 grafik çizmek istiyorum: Günlük Bar Plot, Aylık Line Plot, Yıllık Line Plot ve Korelasyon Heatmap. Grafikler Türkçe olmalı."

* **Açıklama:** Projeye görsel zenginlik katan ve "en az 4 farklı grafik türü" kriterini tek seferde yerine getiren ana görselleştirme promptudur.

### 7. Prompt: Grafik Manipülasyonunu Engelleme ve Ölçeklendirme (Adım: Ölçek Düzeltme)
"Çizilen çizgi grafiklerde y-ekseni (Y-axis) otomatik olarak 25 ile 31 arasında dar bir aralığa sıkışmış. Bu durum trafikteki küçük dalgalanmaları devasa uçurumlar gibi gösteriyor (grafiksel manipülasyon). Grafiklerin bilimsel olarak dürüst ve net görünmesi için eksen alt sınırını 0 yapacak şekilde (plt.ylim(0, 40)) kodu günceller misin?"

* **Açıklama:** Veri etiği ve dürüst görselleştirme üzerine kurulmuş en kritik promptlardan biridir. Grafikler bu sayede yanıltıcı olmaktan çıkarılmıştır.

### 8. Prompt: Korelasyon Düşüklüğünün Teorik Analizi (Adım: İstatistiksel Doğrulama)
"Korelasyon ısı haritasında (Heatmap) zaman değişkenleri ile trafik endeksi arasındaki doğrusal ilişki sıfıra çok yakın çıktı. İstanbul gibi yoğun bir şehirde takvim ile trafik arasında neden doğrusal korelasyon çıkmadı? Bunun bilimsel nedenlerini açıklar mısın? Raporuma nasıl yazmalıyım?"

* **Açıklama:** Çıkan teknik sonuçları ezbere kabul etmeyip sorgulayan analitik bir prompttur. Trafiğin doğrusal olmayan (non-linear) yapıda olduğu ve Anscombe Dörtlüsü felsefesiyle uyuştuğu bu süreçte rapora işlenmiştir.

---

## FAZ 4: MAKİNE ÖĞRENMESİ MODELLEMESİ VE İNTERAKTİF TEST

### 9. Prompt: Doğrusal Olmayan Veri İçin Regresyon Modeli (Adım: Makine Öğrenmesi)
"Korelasyon analizinde verinin doğrusal olmadığını gördük. Bu yüzden yil, ay, gun sütunlarını girdi alarak average_traffic_index değerini tahmin edecek, doğrusal olmayan ilişkileri de yakalayabilen bir Random Forest Regressor modeli kurmak istiyorum. Veriyi %80 eğitim, %20 test olarak ayırıp MAE ve R² skorlarını hesaplayan kodu yazar mısın?"

* **Açıklama:** Projenin yapay zeka/modelleme bacağını oluşturan, verinin yapısına en uygun algoritmanın (Rastgele Orman) seçilip eğitildiği adımdır.

### 10. Prompt: İnteraktif Tahmin Arayüzü (Adım: Model Canlı Testi)
"Eğitilen bu makine öğrenmesi modelini dinamik bir yapıya kavuşturmak ve test etmek için interaktif bir kod yazalım. Kullanıcı hücreyi çalıştırdığında input() ile bir tarih girsin (Örn: 2026-07-05), kod bu tarihi parçalayıp modele sorsun ve modelin o gün için tahmin ettiği İstanbul trafik yüzdesini ekrana şık bir şekilde bassın."

* **Açıklama:** Modeli statik bir kod olmaktan çıkarıp, sunum ve test esnasında canlı olarak gösterilebilecek interaktif bir uygulamaya dönüştüren son yazılımsal prompttur.
