<div align="center">
  <img src="https://github.com/user-attachments/assets/3e439a48-4959-49e0-974f-50b853d8a332" alt="Tower Smash Banner" width="100%">
  
  <br/>

  # 🏰 Tower Smash
  
  [![Play on CrazyGames](https://img.shields.io/badge/Play_on-CrazyGames-purple?style=for-the-badge&logo=game-controller)](https://www.crazygames.com/game/tower-smash-dan?bypassCache=7nudj)
  [![Made with Unity](https://img.shields.io/badge/Made_with-Unity-black?style=for-the-badge&logo=unity)](https://unity.com/)
</div>

> *Tower Smash*, web tarayıcılarında kesintisiz ve yüksek performanslı bir deneyim sunmak için Unity WebGL ile geliştirilmiş hiper-gündelik (hyper-casual) bir yıkım oyunudur. Sınırlı sayıda topla zorlu kuleleri yıktığımız, aralara serpiştirilmiş bonus kulelerle tatmin edici bir arcade deneyimi sunar.

## 🚀 Projenin Amacı ve Platform Stratejisi

Bu proje benim **ilk tam sürüm (full release)** oyunumdur ve şu anda CrazyGames üzerinde **Base Launch** aşamasındadır. 

Oyunun temel mimarisi, CrazyGames platformundaki oyuncuların tüketim hızları ve davranış kalıpları analiz edilerek kurgulandı. Amacım sadece bir oyun yapmak değil; oyuncuyu sıkmayan, sürekli bir akış (flow state) içinde tutarak **oturumu terk etme oranını düşürmek** ve **oyunda kalma süresini ** maksimize etmekti.

## 🎮 Oynanış ve Zorluk Eğrisi (Pacing)

<div align="center">
  <img width="240" height="426" alt="Tower Smash Gameplay" src="https://github.com/user-attachments/assets/6c78bf2c-4ce1-4308-a673-2eb1ff925008" />
</div>

> 💡 **Tasarım Notu:** *Kasıtlı bir zorluk eğrisi  tasarlandı. Oyuncuyu zorlayan kulelerin hemen ardından gelen görsel olarak tatmin edici bonus kuleler, oyuncuya 'nefes alma' ve başarma hissi vererek oyun döngüsünün (core loop) kırılmasını engeller.*

---

## ✨ Özel Geliştirici Araçları ve Sistem Mimari (Custom Tooling & Systems)

### 1. Görsel Tabanlı Kule Üretim Aracı (Pixel-to-Tower Generator)
Bonus kulelerin tasarım sürecindeki zaman kaybını ortadan kaldırmak için özel bir sistem geliştirdim. Bu sistem, **8x8 boyutundaki 2D Pixel Art görselleri tarayarak onları anında 3D oynanabilir kulelere dönüştürüyor.** 
* **Avantajı:** Bölüm tasarım süresini dakikalardan saniyelere indirdi ve oyuna hızlıca yeni içerik eklememi sağlayan bir Pipeline oluşturdu.

<div align="center">
  <!-- BURAYA PIXEL ART KULE YAPIMI GIF'INI EKLEYECEKSIN -->
  <img src="https://via.placeholder.com/400x300.png?text=Pixel+Art+Generator+GIF" alt="Pixel to Tower System" />
</div>

<br/>

### 2. Prosedürel Modüler İnşa Sistemi
Oyunun tekrar edilebilirliğini artırmak ve bellek kullanımını optimize etmek için yüzlerce farklı kule modellemek yerine **Modüler Prosedürel Mimari** kurdum. Sistem, kuleleri tek bir bütün olarak değil; **Base (Zemin), Mid (Gövde) ve Top (Çatı)** olmak üzere 3 katmana ayırır.

**Nasıl Çalışır?**
Sistem önce bir taban boyutu (Örn: 3x2, 4x4, 7x2) belirler ve bu grid yapısına uygun modülleri rastgele üst üste dizerek (Stacking) sonsuz varyasyonda kule üretir.

```text
[ MODÜLER KULE MİMARİSİ ]

      ▲ [ TOP ]  -> Tabanla uyumlu rastgele çatı tipi seçilir.
      │
      █ [ MID ]  -> Taban boyutuna (Örn: 4x4) uyan rastgele gövde katmanı.
      │
    ▀▀▀▀ [ BASE ] -> Sistemin temelini belirleyen rastgele zemin (3x2, 4x4 vb.)
