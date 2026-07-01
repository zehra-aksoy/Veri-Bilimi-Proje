# Veri-Bilimi-Proje
# 🚗 İstanbul Trafik Yoğunluğu Analizi ve Tahmin Projesi

Bu proje, İstanbul'un son 9 yıllık (2015-2024) günlük trafik yoğunluğu endeksini inceleyen, Keşifsel Veri Analizi (EDA) ile trafik örüntülerini ortaya çıkaran ve makine öğrenmesi (Random Forest) ile gelecek günlerin trafik yoğunluğunu tahmin eden uçtan uca bir veri bilimi projesidir.

---

## 👥 Proje Ekibi Bilgileri
* **Öğrenci Numarası:** 1306230032
* **Adı Soyadı:** Zehra Aksoy

---

## 🚀 Projeyi Çalıştırma Talimatları

Proje tamamen bulut tabanlı bir geliştirme ortamı olan **Google Colab** üzerinde hazırlanmıştır. Bilgisayarınıza herhangi bir Python ortamı (Anaconda, PyCharm vb.) kurmanıza gerek yoktur. Projeyi çalıştırmak için aşağıdaki adımları sırasıyla takip ediniz:

1. Projenin GitHub deposunda bulunan `Istanbul_Trafik_Analizi.ipynb` dosyasına tıklayın ve sağ üstteki **"Open in Colab"** butonuna basarak projeyi Google Colab üzerinde açın.
2. Projede kullanılan veri setini indirmek için Kaggle üzerindeki [Istanbul Traffic Index](https://www.kaggle.com/datasets/fatihardazengin/istanbul-traffic-index) sayfasına gidin ve sağ üstteki **Download** butonuna basarak `traffic_index.csv` dosyasını bilgisayarınıza indirin.
3. Google Colab ekranının sol tarafında bulunan **"Dosyalar" (Klasör simgesi)** sekmesine tıklayın ve indirdiğiniz `traffic_index.csv` dosyasını bu alana sürükleyip bırakarak yükleyin.
4. Menüde bulunan **Çalışma Zamanı (Runtime) -> Tümünü Çalıştır (Run all)** seçeneğine tıklayın.
5. Kodlar sırasıyla çalışacak; veri temizleme, istatistiksel analizler ve grafikler ekrana gelecektir.
6. En alttaki **"Canlı Test Alanı"** hücresine geldiğinizde, Colab sizden bir tarih girdisi isteyecektir. Oraya `YYYY-AA-GG` formatında (Örn: `2026-07-05`) bir tarih yazıp **Enter** tuşuna basarak modelin canlı tahmin üretmesini sağlayabilirsiniz.

---

## 📦 Kullanılan Kütüphaneler

Projede veri analizi, görselleştirme ve makine öğrenmesi süreçleri için aşağıdaki standart Python kütüphaneleri kullanılmıştır:
* **Pandas:** Veri manipülasyonu, yükleme ve temizleme işlemleri için.
* **NumPy:** Matematiksel ve istatistiksel hesaplamalar için.
* **Matplotlib & Seaborn:** Veri setinin dağılımını gösteren dürüst, manipülasyondan uzak grafiklerin (Bar Plot, Line Plot, Heatmap) çizilmesi için.
* **Scikit-Learn:** Verinin eğitim/test olarak bölünmesi, Random Forest Regressor modelinin kurulması ve MAE, R² metriklerinin hesaplanması için.

---

## 📊 Veri Kaynağı ve Lisans Bilgileri

* **Veri Kaynağının Adı:** İstanbul Büyükşehir Belediyesi (İBB) Açık Veri Portalı - Trafik Yoğunluk İndeksi Verisi (Kaggle üzerinden `fatihardazengin/istanbul-traffic-index` reposundan temin edilmiştir).
* **Veri Seti Lisansı:** **Open Data Commons Attribution License (ODC-By)**
  * *Lisans Açıklaması:* Bu lisans, kullanıcıların veri setini serbestçe paylaşmasına, değiştirmesine ve kullanmasına izin verir. Tek şart, verinin asıl kaynağına (İstanbul Büyükşehir Belediyesi Açık Veri Portalı) uygun şekilde atıfta bulunulmasıdır. Projemizde bu kurala tam anlamıyla riayet edilmiştir.

---
