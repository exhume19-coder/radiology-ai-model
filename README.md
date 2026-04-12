# 🫁 Radiology AI: Chest X-Ray Pneumonia Classification

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![TensorFlow/Keras](https://img.shields.io/badge/TensorFlow-CNN-orange)
![Google Colab](https://img.shields.io/badge/Google%20Colab-Environment-yellow)
![Status](https://img.shields.io/badge/Status-In%20Progress-brightgreen)

## 📌 Project Overview
This project focuses on building a Convolutional Neural Network (CNN) to classify Chest X-Ray images into two categories: **Normal** and **Pneumonia**. 

The goal of this project is not just to train a model, but to understand the end-to-end pipeline of medical imagery classification, identify real-world clinical biases, and iteratively improve a## 🧑‍⚕️ Klinik Yapay Zeka Denetimi (The Doctor's Audit)
Bu proje, standart bir mühendislik yaklaşımının ötesine geçerek, bir **Tıp Doktorunun (MD)** doğrudan denetimiyle şekillendirilmiştir. Yapay zekanın "kara kutu" (black box) doğası, klinik tecrübe ile sorgulanmış ve şu keşifler yapılmıştır:

### 1. Veri Setindeki "Gizli Gürültü" (Label Noise)
100 adet akciğer grafisi üzerinde yapılan manuel klinik denetim sonucunda:
- **Hatalı Normal Etiketleri:** "Normal" denilen vakaların yaklaşık %15'inde (Vaka 4, 10, 27, 86 vb.) aslında belirgin **bilateral intersisyel/peribronşial paternler** saptanmıştır.
- **Hatalı Pnömoni Etiketleri:** "Pnömoni" denilen vakaların %20'sinde (Vaka 14, 15, 18, 19, 94, 100 vb.) ise **pozitif radyolojik bulguya rastlanmamıştır.**

**Sonuç:** Yapay zekanın %100 başarıya ulaşamamasının sebebi, "yanlış etiketlenmiş" verilerle (klinik tanı var ama radyoloji temiz) eğitilmeye çalışılmasıdır.

### 2. Çift Doğrulama (Dual-Validation) Doktrini
Hekim denetimi sonucunda projemize şu altın kural getirilmiştir: *"Güvenilir bir AI için veri setleri sadece klinik tanıdan değil, **klinik tanı ile teyit edilmiş ve radyolojik bulgu ile desteklenmiş** görüntülerden seçilmelidir."*

---

## 🚀 Model v2.0: Klinik Vizyonun Gücü
Hekim denetimi sonrası geliştirilen yeni modelimiz şu iyileştirmeleri içermektedir:

*   **Net Görüş (256x256 Resolution):** Pikselleşmeyi önleyerek, doktorun işaret ettiği o ince infiltrasyon detaylarını modelin de görebilmesi sağlandı.
*   **Önyargı Filtresi (Class Weights):** Veri setindeki Pnömoni çokluğuna rağmen, modelin "Normal" (Sağlıklı) vakaları kaçırmaması için matematiksel bir "dengeleme" uygulandı.
*   **Klinik Başarı:** v2.0 modelimiz, saptanan %17'lik veri hatalarına rağmen **%91 Doğruluk (Accuracy)** ve **%95 Duyarlılık (Recall)** seviyesine ulaşarak rüştünü ispatlamıştır.

---

## ⚠️ Kritik Değerlendirme ve Kısıtlamalar (Limitations)
Her başarılı yapay zeka projesi gibi, bu çalışma da belirli kısıtlamalar altında yürütülmüştür:
1. **Örneklem Boyutu:** Klinik denetim (audit) 100 vaka ile sınırlıdır; veri setinin tamamındaki gürültü oranını %100 temsil etmeyebilir.
2. **Tek Merkez Bağımlılığı:** Verilerin tek bir coğrafi bölgeden (Guangzhou) gelmesi, modelin evrensel genellenebilirliğini kısıtlayabilir.
3. **Binary Basitlik:** Model şimdilik sadece "Normal/Pnömoni" ayrımı yapmaktadır; diğer akciğer patolojilerini (ateletazi, efüzyon vb.) ayırt etme kapasitesi henüz test edilmemiştir.

## 🏁 Sonuç ve Vizyon: "Hekim Odaklı AI"
Bu çalışma, mevcut tüm kısıtlamalara rağmen şu gerçeği sarsılmaz bir şekilde ortaya koymaktadır: **Tıbbi vizyona sahip uzmanların elinde, uzun soluklu bir süreçte, doğru verilerle ve bu kısıtlamalar göz önüne alınarak kurgulanan yapay zeka modellemeleri, standart mühendislik yaklaşımlarından çok daha verimli ve güvenilir sonuçlar üretmektedir.** Bu proje, "Klinik Denetimli Yapay Zeka" (Expert-in-the-Loop) yaklaşımının radyoloji dünyasındaki en somut örneklerinden biridir.

## 👨‍💻 How to Run
The entire workflow is contained within a Jupyter Notebook.
1. Open the `case.ipynb` notebook in Google Colab or your local Jupyter environment.
2. Upload the respective dataset.
3. Run all cells sequentially to train and evaluate the model.
