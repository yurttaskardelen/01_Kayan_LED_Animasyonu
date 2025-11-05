# STM32F407 ile Kayan LED Animasyonu (v1 - Temel Yöntem)

Bu proje, **STM32F407-Discovery** kartı üzerinde 4 adet LED kullanarak klasik **Kara Şimşek (Knight Rider)** benzeri bir ileri-geri kayan ışık animasyonu gerçekleştirir.

Proje, STM32CubeIDE ve HAL kütüphanesi kullanılarak geliştirilmiştir. Bu versiyon, her bir LED'in ayrı komutlarla (`HAL_GPIO_WritePin`, `HAL_Delay`) kontrol edildiği, konunun **en temel ve açık** halini gösteren bir uygulamadır.

> **💡 İyileştirilmiş Versiyon (Refactor Edilmiş Kod)**
>
> Bu projenin, kod tekrarını önleyen (DRY Prensibi), diziler (`array`) ve `for` döngüleri kullanılarak yazılmış **daha kısa ve profesyonel** bir versiyonu da mevcuttur.
>
> ➡️ **[02_Kayan_LED_Animasyonu_Kisa_Kod](https://github.com/yurttaskardelen/02_Kayan_LED_Animasyonu_Kisa_Kod)** deposuna göz atabilirsiniz.

---

### 🎯 Proje Senaryosu

Animasyon, 4 LED üzerinde sıralı bir hareketle çalışır:
1.  LED'ler `PA1`'den `PA4`'e doğru sırayla yanar (Sağa hareket).
2.  LED'ler `PA4`'den `PA1`'ye doğru sırayla yanar (Sola hareket).
3.  Döngü başa döner.

**Zamanlama:**
* **LED Yanma Süresi:** 200 ms
* **LED Sönme Süresi:** 100 ms (Bir sonraki LED'e geçmeden önce)

---

### 🛠️ Gerekli Donanım

* **1x** STM32F407-Discovery Geliştirme Kartı
* **4x** Tercih edilen renkte LED
* **4x** 220 Ohm Direnç (LED'ler için ön direnç)
* Breadboard ve Jumper kablolar

---

### 🔌 Devre Şeması

LED'lerin anot (uzun) bacakları STM32 pinlerine, katot (kısa) bacakları ise direnç üzerinden GND hattına bağlanmalıdır.

| LED | Direnç | STM32 Pini |
| :--- | :--- | :--- |
| LED 1 | 220 Ohm | `PA1` |
| LED 2 | 220 Ohm | `PA2` |
| LED 3 | 220 Ohm | `PA3` |
| LED 4 | 220 Ohm | `PA4` |
| (Tümü) | - | `GND` |

<img width="473" height="404" alt="Pin_Baglantilari" src="https://github.com/user-attachments/assets/7103876f-9e8b-4da0-b089-e8e4b43abb4a" />


### Kod Bloğu

<img width="662" height="793" alt="Kod_Blogu" src="https://github.com/user-attachments/assets/d375b92d-ba41-46d8-8b72-448fcf781fcc" />

---

### 🚀 Nasıl Kullanılır?

1.  Bu depoyu klonlayın (`git clone ...`).
2.  STM32CubeIDE yazılımını açın.
3.  `File > Open Projects from File System...` seçeneği ile proje klasörünü seçin.
4.  Proje içindeki `.ioc` dosyasını açarak pin yapılandırmasını inceleyebilirsiniz.
5.  Derleyin (Build) ve ST-Link V2 üzerinden kartınıza yükleyin (Run).
