# 🎯 Görüntü İşleme Tabanlı Otonom Lazer Takip Sistemi 

![Computer Vision](https://img.shields.io/badge/Computer_Vision-FF6F00?style=for-the-badge&logo=opencv&logoColor=white)
![Processing](https://img.shields.io/badge/Processing-0096D8?style=for-the-badge&logo=processing&logoColor=white)
![Arduino](https://img.shields.io/badge/Arduino-00979D?style=for-the-badge&logo=arduino&logoColor=white)
![IoT & Embedded](https://img.shields.io/badge/IoT_&_Embedded-333333?style=for-the-badge)

Bu proje, **Görüntü İşleme (Computer Vision)** ile donanım kontrolünü (Mikrodenetleyici) birleştiren bir kavram kanıtlama (Proof of Concept - PoC) çalışmasıdır. Sistem, kamera üzerinden aldığı anlık görüntüleri işleyerek hareketli hedefleri tespit eder ve koordinatları seri haberleşme üzerinden mekanik sisteme aktararak otonom lazer nişanlaması yapar.

## 📌 Proje Amacı ve Operasyonel Vizyon
Dışa bağımlı sensörlere (PIR vb.) güvenmek yerine, tamamen görsel veri analizine dayanan bağımsız bir karar/takip mimarisi kurmak amaçlanmıştır. Bu sistem;
- Güvenlik ve çevre gözetleme sistemlerinde,
- Otonom savunma ve kamera ile kilitlenme mekanizmalarında,
- Endüstriyel otomasyon süreçlerinde kullanılabilecek bir çekirdek altyapı sunar.

## ⚙️ Sistem Mimarisi (Yazılım ve Donanım Haberleşmesi)
Proje, bilgisayar tabanlı işlem gücü (Processing) ile sahada karar alan donanımın (Arduino) senkronize çalışmasına dayanır:
1. **Görsel Veri Toplama (Processing):** Web kamerası veya harici kamera üzerinden video akışı (frame) alınır.
2. **Görüntü İşleme ve Hedef Tespiti:** Processing dili kullanılarak ardışık kareler (frames) arasındaki piksel farklılıkları (motion tracking) analiz edilir. Tespit edilen hedefin X ve Y koordinatları hesaplanır.
3. **Seri Haberleşme (Serial Port):** Hesaplanmış koordinat verileri, bilgisayar ile Arduino arasında çok düşük gecikmeyle (low-latency) aktarılır.
4. **Mekanik Eylem (Actuation - Arduino):** Gelen koordinatları işleyen C++ tabanlı Arduino algoritması, 2 eksenli (Pan-Tilt) servo motor sistemini yönlendirerek lazeri hedefe odaklar.

## 🛠️ Kullanılan Teknolojiler ve Bileşenler
- **Yazılım Katmanı:** Processing Dili (Görüntü işleme ve koordinat hesabı)
- **Donanım Katmanı (Mikrodenetleyici):** Arduino Uno / Mega
- **Eyleyiciler (Actuators):** 2x SG90/MG996R Servo Motor
- **Modül:** 5V Lazer Diyot Modülü & Kamera (Webcam)

## 💻 Sistem Gereksinimleri ve Test
1. Processing IDE üzerinden `.pde` uzantılı görüntü işleme dosyasını çalıştırın.
2. Arduino IDE üzerinden `.ino` dosyasını karta yükleyin.
3. İki yazılımın aynı COM portu ve Baud Rate (örn: 9600) üzerinden haberleştiğinden emin olun.

> **Not:** Ticari ve güvenlik hakları sebebiyle proje kodlarının tamamı değil, sadece görüntü işleme ve haberleşme mimarisini gösteren çekirdek dosyalar paylaşılmıştır.
