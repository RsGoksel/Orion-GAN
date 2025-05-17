

# Orion Twin GenAI - Gerçekçi İnsan Modeli ve Poz Manipülasyonu

![2b0f542e-8f44-4cc6-a334-71bcc23cc70c](https://github.com/user-attachments/assets/541318a3-fe85-4d49-8afa-e7eb38f88f7c)

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

### Pozlar Arası Geçiş

![latent_space_traversal (5)](https://github.com/user-attachments/assets/2237e9a7-2042-47fe-9556-a38eec5363f1)

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


## Proje dahilinde kullanılabilecek örnek veri setleri 

Link: https://renderpeople.com/
Dataset: RenderPeople - Fotogerçekçi 3D taranmış insanları içeren en yaygın kullanılan ticari veri setlerinden biri. 5.000'den fazla farklı poz ve kıyafet stiline sahip yüksek kaliteli model sunuyorlar. Modelleri arasında poz verilmiş insanlar, riglenmiş insanlar, animasyonlu insanlar ve 4D insanlar (hacimsel olarak yakalanmış) bulunmaktadır.

Link: https://humandataset.com/
Dataset: HumanDataset - 35.000'den fazla tarama ve 5.500 rafine edilmiş 3D model içeren büyük bir ticari koleksiyon. 330 kameralı fotogrametri kurulumu kullanılarak yakalanmış, 72 farklı ülkeden 7 ila 83 yaş aralığında gerçek taranmış insanlar sunuyorlar.

Link: https://3dpeople.com/en/
Dataset: 3DPeople - Görselleştirme ve animasyon için fotogerçekçi insan 3D modellerinin büyüyen bir koleksiyonu. "Nesil 2.0" modelleri gelişmiş pürüzlülük haritaları, PBR gölgelendirme, detaylı 50k meshler ve gerçekçi gözler içeriyor.

### Akademik temelli veri setleri
Link: https://github.com/ZhengZerong/DeepHuman/tree/master/THUmanDataset
Dataset: THUman - Yaklaşık 7.000 model içeren orijinal veri seti

Link: https://github.com/ZhengZerong/THUman4.0-Dataset
Dataset: THUman4.0 - Daha yüksek kaliteli taramalarla en son versiyon

Link: https://www.di.ens.fr/willow/research/surreal/data/
Dataset: SURREAL Veri Seti - Şekil, doku, bakış açısı ve poz varyasyonları altında fotogerçekçi renderlama ile 6 milyon sentetik insan karesi içerir. MoSh metodu ile ayarlanmış parametrelerle SMPL vücut modeli kullanır.

Link: https://synbody.github.io/
Dataset: SynBody - Katmanlı insan modelleri içeren sentetik bir veri seti: (1) çeşitli konular içeren giydirilmiş parametrik insan modelleri, (2) yüksek kaliteli 3D açıklamalar sunan katmanlı insan temsili ve (3) gerçekçi veri üretmek için ölçeklenebilir bir sistem özelliklerine sahiptir.

Link: https://bedlam.is.tue.mpg.de/
Dataset: BEDLAM (Bodies Exhibiting Detailed Lifelike Animated Motion) - SMPL-X formatında gerçek 3D vücutlar içeren monokular RGB videolardan oluşan büyük ölçekli sentetik bir veri seti. Çeşitli vücut şekilleri, hareketler, ten tonları, saç ve fizik kullanılarak simüle edilmiş gerçekçi kıyafetler içerir.

Link: https://amass.is.tue.mpg.de/
Dataset: AMASS (Archive of Motion Capture as Surface Shapes) - Farklı optik işaretleyici tabanlı hareket yakalama veri setlerini ortak bir çerçeve içinde birleştiren büyük bir veritabanı. Gerçekçi insan hareketini temsil etmek için SMPL modelini kullanır.

Link: https://github.com/EricGuo5513/HumanML3D
Dataset: HumanML3D - HumanAct12 ve AMASS veri setlerini birleştiren bir 3D insan hareketi-dil veri seti. 14.616 hareket ve 44.970 açıklama ile çeşitli insan eylemlerini kapsar.

Link: https://motion-x-dataset.github.io/
Dataset: Motion-X - SMPL-X formatını kullanarak zengin yüz ve el hareketleri içeren geniş ölçekli bir 3D ifade edici tüm vücut insan hareketi veri seti.

