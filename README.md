<div align="center">
  <h1>🛡️ Acme Security Lab</h1>
  <p><i>Comprehensive Open-Source Security Incident & Simulation Lab<br>Kapsamlı Açık Kaynak Güvenlik Olayı ve Simülasyon Laboratuvarı</i></p>
  
  ![Security](https://img.shields.io/badge/Security-Critical-red?style=for-the-badge)
  ![Data](https://img.shields.io/badge/Data-Analysis-blue?style=for-the-badge)
  ![Status](https://img.shields.io/badge/Status-Active-success?style=for-the-badge)
</div>

<br>

## 🇬🇧 English

**Acme Security** is a dedicated open-source repository designed to serve as a security incident laboratory. This repository is invaluable for cybersecurity students, analysts, and engineers looking to understand how real-world cyber events unfold across different layers of an application.

### 🏗️ Architecture & Logs
The repository simulates a multi-tiered architecture (Web, API, WAF). It contains actual log files generated during security tests and incident simulations:
- **`api_logs.csv` & `web_logs.csv`**: Contains traffic data, endpoints hit, status codes, and potential injection attempts.
- **`waf_logs.csv`**: Web Application Firewall logs showing blocked requests, payload signatures, and threat detection mechanisms.
- **Architecture Diagrams**: Visual aids (`current_architecture.png`) that map out how the frontend, backend, and security layers interact.

### ✨ Key Features
- 📊 **Deep Dive Log Analysis**: Analyze raw CSV logs to track down malicious actors.
- 🗓️ **Security Scheduling**: Review `security_test_schedule.pdf` to understand how penetration tests and vulnerability assessments are planned.
- 🔍 **Incident Post-Mortems**: Trace how a threat bypasses the WAF and reaches the API by correlating different log files.

---

## 🇹🇷 Türkçe

**Acme Security**, siber güvenlik olaylarını simüle etmek, incelemek ve analiz etmek için tasarlanmış kapsamlı bir açık kaynak laboratuvar reposudur. Siber güvenlik öğrencileri, analistleri ve mühendisleri için gerçek dünyadaki siber saldırıların sistemin farklı katmanlarında nasıl iz bıraktığını anlamak adına kritik bir kaynaktır.

### 🏗️ Mimari ve Log Yapısı
Bu repo, çok katmanlı bir mimariyi (Web, API, WAF) simüle eder. Güvenlik testleri sırasında oluşturulan gerçek log dosyalarını içerir:
- **`api_logs.csv` & `web_logs.csv`**: Sistem trafiği, istek yapılan uç noktalar (endpoints), durum kodları ve potansiyel zafiyet (injection) denemelerini barındırır.
- **`waf_logs.csv`**: Web Uygulama Güvenlik Duvarı (WAF) tarafından engellenen istekleri, zararlı yük (payload) imzalarını ve tehdit algılama mekanizmalarını gösterir.
- **Mimari Diyagramları**: Sistemin ön yüz, arka uç ve güvenlik katmanlarının nasıl iletişim kurduğunu gösteren görsel haritalar (`current_architecture.png`).

### ✨ Temel Özellikler
- 📊 **Derinlemesine Log Analizi**: Saldırganların izini sürmek için ham CSV dosyalarını analiz etme imkanı.
- 🗓️ **Güvenlik Planlaması**: Sızma testlerinin (pentest) ve zafiyet taramalarının nasıl planlandığını gösteren test takvimleri.
- 🔍 **Olay Korelasyonu**: Bir tehdidin WAF'ı nasıl aşıp API'ye ulaştığını farklı log dosyalarını birleştirerek (korelasyon) tespit etme.
