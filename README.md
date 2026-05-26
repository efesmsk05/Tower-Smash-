<div align="center">
  <!-- Kapak Fotoğrafı Düzeltildi -->
  <img src="https://github.com/user-attachments/assets/3e439a48-4959-49e0-974f-50b853d8a332" alt="Tower Smash Banner" width="100%">
  
  <br/>

  # 🏰 Tower Smash
  
  [![Play on CrazyGames](https://img.shields.io/badge/Play_on-CrazyGames-purple?style=for-the-badge&logo=game-controller)](https://www.crazygames.com/game/tower-smash-dan?bypassCache=7nudj)
  [![Made with Unity](https://img.shields.io/badge/Made_with-Unity-black?style=for-the-badge&logo=unity)](https://unity.com/)
</div>

> *Tower Smash*, web tarayıcılarında kesintisiz ve yüksek performanslı bir deneyim sunmak için Unity WebGL ile geliştirilmiş hiper-gündelik (hyper-casual) bir yıkım oyunudur. Sınırlı sayıda topla zorlu kuleleri yıktığımız, aralara serpiştirilmiş bonus kulelerle tatmin edici bir arcade deneyimi sunar.

## 🚀 Projenin Amacı ve "Base Launch"

Bu proje benim **ilk tam sürüm (full release)** oyunumdur ve şu anda CrazyGames üzerinde **Base Launch** aşamasındadır. Amacım, hyper-casual türündeki oyuncu elde tutma (retention) dinamiklerini gerçek bir platformda test etmek, WebGL optimizasyon süreçlerini uçtan uca tecrübe etmek ve geliştirme sürecimi portfolyomda sergilemektir.

## 🎮 Oynanış

<div align="center">
  <img width="240" height="426" alt="Tower Smash Gameplay" src="https://github.com/user-attachments/assets/6c78bf2c-4ce1-4308-a673-2eb1ff925008" />
</div>

> 💡 **Tasarım Notu:** *Oyuncuyu yormayan bir zorluk eğrisi (Pacing) tasarlandı. Zorlayıcı kulelerin ardından gelen bonus kuleler, oyuncuya 'nefes alma' ve tatmin olma fırsatı vererek oyunda kalma süresini (Playtime) artırmayı hedefler.*

## 🛠️ Kullanılan Teknolojiler

<div align="center">
  <img src="https://img.shields.io/badge/Unity-100000?style=for-the-badge&logo=unity&logoColor=white" />
  <img src="https://img.shields.io/badge/C%23-239120?style=for-the-badge&logo=c-sharp&logoColor=white" />
  <img src="https://img.shields.io/badge/WebGL-990000?style=for-the-badge&logo=webgl&logoColor=white" />
  <img src="https://img.shields.io/badge/Adobe%20Illustrator-FF9A00?style=for-the-badge&logo=adobe-illustrator&logoColor=white" />
</div>

<br/>

### Öne Çıkan Geliştirme Prensipleri
Bir WebGL oyunu geliştirirken en büyük düşmanımız bellek şişmesi (Memory Leak) ve tarayıcıyı yoran gereksiz hesaplamalardır. Bu projede performansı maksimize etmek için:
* **Garbage Collector Optimizasyonu:** Sürekli yaratılan ve yok edilen kule/yıkım objeleri için **Object Pooling (Nesne Havuzu)** tasarım kalıbı (Design Pattern) kullanıldı. Bu sayede tarayıcıda yaşanabilecek anlık takılmaların (Spike/FPS Drop) önüne geçildi.
* **Fizik ve Render Optimizasyonu:** Fizik hesaplamaları ve Particle System'ler (Parçacık Sistemleri) cihazı yormayacak şekilde, düşük poligonlu (low-poly) yapılar ve optimize edilmiş materyallerle desteklendi.
* **Akıcı Oyun Döngüsü:** Oyuncuyu sıkmayan, hızlı yeniden başlama mekanikleri ve gelecekteki ödüllü reklam (Rewarded Ads) entegrasyonlarına uygun temiz, modüler bir kod mimarisi kuruldu.

## 🌐 Hemen Oyna

Oyunun tam ve en güncel sürümünü tarayıcınızdan hiçbir şey indirmeden oynamak için aşağıdaki bağlantıya tıklayabilirsiniz:

👉 **[CrazyGames'te Tower Smash Oyna](https://www.crazygames.com/game/tower-smash-dan?bypassCache=7nudj)**

---
*Geliştirici:* **Efe Şimşek**  
*İletişim & Ağ:* [LinkedIn Profilin](LINKEDIN_LINKIN) | [Portfolyo Siten](VARSA_SITEN)
