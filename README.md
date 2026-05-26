<div align="center">
  <img src="https://github.com/user-attachments/assets/3e439a48-4959-49e0-974f-50b853d8a332" alt="Tower Smash Banner" width="100%">
  
  <br/>

  # 🏰 Tower Smash
  
  [![Play on CrazyGames](https://img.shields.io/badge/Play_on-CrazyGames-purple?style=for-the-badge&logo=game-controller)](https://www.crazygames.com/game/tower-smash-dan?bypassCache=7nudj)
  <!-- Tıklanabilir CrazyGames Logosu -->
  <img width="500  " height="500" alt="Play_CG_Purple" src="https://github.com/user-attachments/assets/333a32bb-1bc1-4bfc-91f9-bb270983189c" />

<a href="https://www.crazygames.com/game/tower-smash-dan?bypassCache=7nudj" target="_blank">
  <img src="<img width="3260" height="1000" alt="Play_CG_Purple" src="https://github.com/user-attachments/assets/4fc47050-de0d-4113-9514-5bcb742997e5" />
" alt="Play on CrazyGames" width="200">
</a>
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

⚙️ WebGL Optimizasyonları ve Teknik Altyapı
Bir web oyununun başarılı olması sadece mekaniklerine değil, tarayıcıda ne kadar pürüzsüz çalıştığına ve ne kadar hızlı yüklendiğine bağlıdır. Bu projede web ortamının kısıtlamalarını avantaja çevirmek için uyguladığım teknikler:

Garbage Collector (GC) Optimizasyonu: Web tarayıcılarında anlık takılmaların (FPS Drop) en büyük sebebi sürekli obje yaratıp silmektir (Instantiate/Destroy). Yıkılan kule parçaları ve fırlatılan toplar için Object Pooling (Nesne Havuzu) sistemi kuruldu. Objeler yok edilmek yerine havuzda bekletilip yeniden kullanılarak bellek şişmesinin önüne geçildi.

Draw Call Optimizasyonu (Texture Atlasing): Ekranda çizilecek her farklı materyal işlemciye bir yük (Draw Call) bindirir. Özellikle prosedürel kulelerde bu yükün artmasını engellemek için görseller Texture Atlas (Doku Atlası) haritalarında birleştirildi. Tek materyal üzerinden tüm yapılar boyanarak render performansı maksimize edildi.

Hızlı Yükleme ve Build Boyutu (Code Stripping): CrazyGames gibi platformlarda oyuncu oyunun yüklenmesini 3 saniyeden fazla beklerse sekmeyi kapatır. Build boyutunu minimize etmek için Texture Compression teknikleri ve Unity'nin Managed Code Stripping (kullanılmayan motor kodlarını silme) özelliği agresif ayarlarda kullanıldı.

Responsive UI Mimarisi (UI Scaling): Web oyunları dikey bir pencerede, tam ekranda veya farklı çözünürlüklü monitörlerde oynanabilir. Arayüzün her ekranda ve en-boy oranında (Aspect Ratio) kusursuz görünmesi ve tıklanabilir alanların bozulmaması için dinamik bir UI Scaling sistemi entegre edildi.

## ✨ Özel Geliştirici Araçları ve Sistem Mimari (Custom Tooling & Systems)

### 1. Görsel Tabanlı Kule Üretim Aracı (Pixel-to-Tower Generator)
Bonus kulelerin tasarım sürecindeki zaman kaybını ortadan kaldırmak için özel bir sistem geliştirdim. Bu sistem, **8x8 boyutundaki 2D Pixel Art görselleri tarayarak onları anında 3D oynanabilir kulelere dönüştürüyor.** 
* **Avantajı:** Bölüm tasarım süresini dakikalardan saniyelere indirdi ve oyuna hızlıca yeni içerik eklememi sağlayan bir Pipeline oluşturdu.

<div align="center">
  <!-- BURAYA PIXEL ART KULE YAPIMI GIF'INI EKLEYECEKSIN -->
  <img width="426" height="240" alt="gif" src="https://github.com/user-attachments/assets/b93771f2-df13-448f-be89-dba80d91fe92" />
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


