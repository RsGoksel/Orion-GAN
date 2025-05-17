

# Orion Twin GenAI - Gerçekçi İnsan Modeli ve Poz Manipülasyonu

![Project Banner](https://github.com/username/orion-twin-genai/raw/main/docs/banner.png)

## Proje Özeti

Orion Twin GenAI, gerçekçi insan modelleri oluşturan ve bu modellerin vücut yapısını koruyarak farklı pozlarda görüntüler üretebilen bir yapay zeka sistemidir. StyleGAN-Human modelini temel alarak geliştirilen bu proje, moda ve e-ticaret sektöründe ürün fotoğrafçılığını dönüştürme potansiyeline sahiptir.

## Temel Özellikler

- **Gerçekçi İnsan Modeli Üretimi**: StyleGAN-Human kullanarak yüksek kaliteli insan figürleri oluşturma
- **Poz Manipülasyonu**: Aynı insan figürünün vücut yapısını koruyarak farklı pozlarda görüntülerini üretme
- **Kıyafet ve Stil Varyasyonları**: Üst ve alt giysi uzunluğu, stil ve açı manipülasyonları
- **Poz Transferi**: Referans bir görüntüden poz özelliklerini çıkarma ve bunları model üzerinde uygulama
- **İnterpolasyon**: İki poz arasında yumuşak geçişler oluşturarak animasyon yaratma

## Demo Görseller

Projede, giyim sektöründe ürün fotoğrafçılığı için yaklaşım sunmaktadır. Tek bir model ile farklı pozlarda ve giysi kombinasyonlarında görüntüler oluşturulabilir, müşteriler kendi özgün görselleri ile ilgili ürünü satın almadan öngösterim dahilinde deneyebilir.

### Üst Giysi Manipülasyonu Örnekleri
![Üst Giysi Manipülasyonu](https://github.com/username/orion-twin-genai/raw/main/examples/upper_length_samples.png)

### Alt Giysi Manipülasyonu Örnekleri
![Alt Giysi Manipülasyonu](https://github.com/username/orion-twin-genai/raw/main/examples/bottom_length_samples.png)

### Pozlar Arası Geçiş
![Pozlar Arası Geçiş](https://github.com/username/orion-twin-genai/raw/main/examples/pose_interpolation.gif)

## Teknolojik Altyapı

Orion Twin GenAI, aşağıdaki teknolojileri ve yöntemleri kullanmaktadır:

- **StyleGAN-Human**: Gerçekçi insan figürleri üretmek için temel GAN modeli
- **Latent Space Manipulation**: Poz ve giysi manipülasyonları için latent uzayı düzenleme
- **Style Mixing**: Farklı stil özelliklerini koruyarak görüntü sentezi
- **Pose Extraction & Transfer**: Referans görüntülerden poz özelliklerini çıkarma ve aktarma

## Kurulum ve Kullanım

### Gereksinimler

- Python 3.8+
- PyTorch 1.9+
- CUDA 11.1+
- Diğer bağımlılıklar: requirements.txt dosyasında listelenmiştir

### Kurulum

```bash
# Repo'yu klonlayın
git clone https://github.com/username/orion-twin-genai.git
cd orion-twin-genai

# Gerekli paketleri yükleyin
pip install -r requirements.txt

# Ön eğitimli modelleri indirin
python download_models.py
```

### Kullanım Örnekleri

#### Temel Kullanım - Görüntü Oluşturma

```bash
python generate.py --seeds=1000-1005 --trunc=0.7
```

#### Poz Varyasyonları Oluşturma

```bash
python edit.py --attr_name=upper_length --seeds=1000
```

#### Stil Karıştırma

```bash
python style_mixing.py --rows=1000 --cols=2000,2001,2002 --styles=4-7
```

#### İnterpolasyon Videosu Oluşturma

```bash
python interpolation.py --seeds=1000,2000
```

Geliştirilebilecek Noktalar
1. InsetGAN Entegrasyonu
InsetGAN yaklaşımı kullanılarak FFHQ veri setindeki yüzler ile StyleGAN-Human modelinin ürettiği vücut görüntüleri birleştirilebilir. Bu şekilde, daha kişiselleştirilmiş ve gerçekçi insan figürleri oluşturulabilir.
StyleGAN-Human reposunda bulunan "Demo for InsetGAN" örneği şu şekilde geliştirilebilir:
https://www.kaggle.com/datasets/arnaud58/flickrfaceshq-dataset-ffhq?select=00011.png

![ffhq-teaser](https://github.com/user-attachments/assets/f860f838-0312-4aab-9000-f7f77e5ddfcf)

Flickr Face HQ (FFHQ) veri seti kullanarak daha gerçekçi yüz detayları
Kullanıcının kendi yüz fotoğrafını yükleyerek kişiselleştirilmiş sonuçlar
Yüz ve vücut latent kodları arasında daha iyi optimizasyon teknikleri

2. Daha Kaliteli Çıktılar İçin İyileştirmeler
Eğitim Öncesi İyileştirmeler

Daha Yüksek Çözünürlüklü Veri Seti: 1024x1024 veya daha yüksek çözünürlükte eğitim verileri kullanmak
Veri Çeşitliliği: Farklı poz, giyim ve vücut tiplerini kapsayan daha zengin bir veri seti oluşturmak
Dengeli Veri Dağılımı: Nadir pozlar ve duruşlar için dengeli bir veri dağılımı sağlamak

Model İyileştirmeleri

LoRA (Low-Rank Adaptation): Mevcut StyleGAN modellerini daha az veri ve hesaplama kaynağı ile ince ayar yapmak
StyleGAN3 Kullanımı: Daha gelişmiş unsupervised çıktılar için StyleGAN3'e geçiş yapmak
Modüler Yaklaşım: Yüz, vücut ve kıyafet için ayrı modeller geliştirip bunları birleştirmek

Post-Processing İyileştirmeleri

Super Resolution: ESRGAN veya benzer süper çözünürlük modelleri ile çıktı kalitesini artırmak
Detay İyileştirme: Doku ve detayları geliştirmek için özel filtreler ve işlemler uygulamak
Renk Kalibrasyonu: Daha gerçekçi cilt tonları ve kıyafet renkleri elde etmek

3. OpenPose ile Poz Kontrolü İyileştirmeleri

Hassas Poz Transferi: OpenPose ile tespit edilen eklem noktalarını kullanarak daha doğru poz aktarımı
Özel Poz Oluşturma: Kullanıcının tanımladığı özel pozlarda görüntüler üretme
Kişiselleştirilmiş Modeller: Kullanıcının kendi görselini yükleyerek, bu görseldeki kişinin hedef kıyafeti giydiği veya farklı pozlarda durduğu görüntüler oluşturma
Dinamik Poz Kütüphanesi: Moda, spor, portre gibi farklı kategorilerde hazır poz setleri
