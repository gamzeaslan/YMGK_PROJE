# YMGK_PROJE
# AR Uçak Bahçesi – Çocuklar İçin Artırılmış Gerçeklik Oyunu

## 📖 Proje Hakkında

AR Uçak Bahçesi, 5-12 yaş arası çocuklar için tasarlanmış bir mobil artırılmış gerçeklik (AR) oyunudur.  
Çocuklar, sabit bir uçak kabini ortamında sanal olarak çiçek dikerek doğayı tanır ve çevresel farkındalık kazanır.  
Gerçek dünya taraması yapılmaz, sabit ve sade bir sahne içerisinde etkileşim sunar.

---

## 🎯 Özellikler

- Sabit uçak kabini ortamında AR deneyimi  
- Dokunmatik ekranla çiçek dikme  
- Renkli, sade, çocuk dostu tasarım  
- Android cihazlarda sorunsuz çalışır  
- İnternet, reklam, üyelik, veri toplama içermez  

---

## 👥 Hedef Kitle

- 5–12 yaş aralığındaki çocuklar  
- Eğitimde teknoloji kullanan öğretmenler ve ebeveynler  
- Eğlenceli ama güvenli dijital içerik arayan herkes

---

## 📲 Kurulum ve Kullanım

1. APK dosyasını indir (aşağıda)  
2. Android cihazına yükle  
3. “Bilinmeyen kaynaklara izin ver” seçeneğini aktif et  
4. Uygulamayı aç ve ekrana dokunarak çiçek dikmeye başla  
5. Uygulama tamamen çevrimdışıdır

---

## 📦 APK Dosyası

Uygulamayı test etmek isterseniz aşağıdaki bağlantıdan indirip Android cihazınıza kurabilirsiniz:

👉 **[AR Uçak Bahçesi APK'sını Buradan İndirin](https://drive.google.com/drive/folders/1_0MsRg7OLET1hZLb7BtQCeWBhKAFATiH?usp=drive_link)**



---

## 🛠️ Kullanılan Teknolojiler

- Unity 2021.3.x LTS  
- AR Foundation & XR Plugin Management  
- C# dili  
- Android platformu

---

## 🗂️ Proje Yapısı

Assets/ ├── Scenes/ │ └── MainScene.unity ├── Models/ │ └── a_detail_airplane_cabin.glb ├── Prefabs/ │ └── flowerPrefab ├── Scripts/ │ └── FlowerPlacer.cs



## 🗂️ Proje Kodu

---
### 📄 Ana Kod – FlowerPlacer.cs

```csharp
using UnityEngine;

public class cicek_ekle : MonoBehaviour
{
    public GameObject flowerPrefab;
    public Camera arCamera;

    void Update()
    {
#if UNITY_EDITOR
        // Editörde test için: Mouse tıklaması
        if (Input.GetMouseButtonDown(0))
        {
            Ray ray = arCamera.ScreenPointToRay(Input.mousePosition);
            RaycastHit hit;

            if (Physics.Raycast(ray, out hit))
            {
                Instantiate(flowerPrefab, hit.point, Quaternion.identity);
            }
        }
#else
        // Gerçek cihazda dokunma için
        if (Input.touchCount > 0 && Input.GetTouch(0).phase == TouchPhase.Began)
        {
            Ray ray = arCamera.ScreenPointToRay(Input.GetTouch(0).position);
            RaycastHit hit;

            if (Physics.Raycast(ray, out hit))
            {
                Instantiate(flowerPrefab, hit.point, Quaternion.identity);
            }
        }
#endif
    }
}

```


##  Kod Aciklamasi

- flowerPrefab: Unity sahnesine eklenecek 3D çiçek modeli

- plantPoint: Sabit konumda sahnede yer alan boş GameObject

- Kullanıcı her dokunduğunda yeni bir çiçek oluşturulur

## Proje Durumu

- Bu proje halen geliştirilmektedir ve test aşamasındadır.
- İlerleyen sürümlerde kullanıcıya tür seçimi, renk seçimi, skor tablosu gibi yeni özellikler sunulması hedeflenmektedir.

## Geliştirici
- Gamze Aslan
- Fırat Üniversitesi – Yazılım Mühendisliği
- GitHub: github.com/kullaniciadi

## Lisans
- Bu proje bireysel bir eğitim projesidir.
- Ticari kullanım için uygun değildir.
- Akademik sunum, test ve eğitim amaçlı kullanım serbesttir.
