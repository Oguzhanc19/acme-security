# Acme Güvenlik Laboratuvarı: Analiz Sürecim ve Notlarım

Herkese merhaba,

Bu dosya, bu güvenlik laboratuvarını tamamlarken attığım adımları, karşılaştığım zorlukları ve "vay be!" dediğim anları içeren kişisel bir özetimdir. Resmi raporum (`report.pdf`) teknik detayları ve bulguları içeriyor, ancak burası işin "kamera arkası".

Dürüst olmak gerekirse, bu zorlu ama inanılmaz öğretici bir tecrübeydi.

---

## 1. İlk Adım: Nereden Başlayacağım?

İlk başta `materials` klasörünü açtığımda karşıma çıkan 8-9 dosya (.csv, .pdf, .png) gözümü biraz korkuttu. "Hepsini aynı anda nasıl analiz edeceğim?" diye düşündüm.

**Yaklaşımım:** Önce "kural kitabını" okumaya karar verdim.

`api_docs.pdf` ve `current_architecture.png` bana sistemin nasıl çalışması gerektiğini gösterdi.

Ama asıl kilit nokta `security_test_schedule.pdf` dosyasıydı.

## 2. "Buldum!" Anı: Gürültüyü Ayıklamak

Bu laboratuvardaki ilk "başardım" dediğim an, gürültüyü (false positives) gerçek tehditten ayırdığım andı.

`security_test_schedule.pdf` dosyası, `192.168.1.100` gibi IP'lerin "planlı iç tarama" ve `10.0.0.50` IP'sinin `sec_team` testi olduğunu söylüyordu. Bunları hemen "zararsız" olarak işaretledim.

Aynı dosya, asıl saldırganın (sızma testi uzmanının) `203.0.113.0/24` bloğundan geleceğini söylüyordu.

Tüm logları açıp `203.0.113.45` IP'sini arattığımda, tüm saldırı zinciri önüme döküldü. Artık elimde takip edecek bir "iz" vardı.

## 3. Dedektiflik: Logları ve İtirafları Birleştirmek

Bundan sonrası tam bir dedektiflik işiydi. Sadece loglara bakmadım, logları dokümanlarla karşılaştırdım.

**İlk Buldum Dediğim An:** `api_logs.csv` dosyasında saldırganın `1523` nolu token ile `1524`, `1525`, `1538` gibi hesaplara eriştiğini gördüm. Sonra `api_docs.pdf` dosyasını açtım ve o meşhur notu gördüm: "...hesap sahipliğini doğrulamayabilir". Zafiyet, resmen dokümanda itiraf edilmişti.

**İkinci Buldum Dediğim An:** `waf_logs.csv` dosyasında WAF'ın hem "Hızlı Sıralı Erişim" (Rate Limit saldırısı) hem de "Şüpheli SQL Deseni" (SQLi saldırısı) girişimlerini tespit ettiğini gördüm. Ama `blocked` sütunu `no` diyordu. WAF, saldırıları görmüş ama DETECT modunda olduğu için sadece "not almış" ama engellememişti.

## 4. En Zorlu Kısım: Mimari Hatasını Kabul Etmek

Dürüst olmam gerekirse, analizdeki en büyük zorluğu mimari diyagramda yaşadım.

İlk başta, Auth Service ile Trading API arasında mantıken bir bağlantı olması gerektiğini varsaydım ve analizimi buna göre yaptım.

Bu bir hataydı.

Diyagrama tekrar ve dikkatlice baktığımda, bu iki servis arasında hiçbir ok (bağlantı) olmadığını fark ettim. Zafiyet, benim düşündüğümden daha büyüktü; sistemde yetkilendirmeyi zorunlu kılan bir akış hiç yoktu.

Bu bana şunu öğretti: Varsayma. Sadece kanıta (diyagramın gösterdiğine) güven.

## 5. Çözüm Üretmek (İşin En Keyifli Kısmı)

Sadece sorunları bulmak yetmiyordu, bunları nasıl çözeceğimi de göstermem gerekiyordu.

Rapordaki "Önerilen Mimari" kısmını hazırlamak en keyifli yerdi.

* API Gateway'e **Merkezi Yetkilendirme** rolünü vermek (BOLA'yı çözmek için).
* WAF'ı **BLOCK Mode**'a almak (WAF bypass'ı çözmek için).
* DAL (Veri Erişim Katmanı) eklemek (SQLi'ye karşı derinlemesine savunma için).
* Email Gateway'e **DMARC** eklemek (Phishing'i çözmek için).

Bu adımlar, teorik bilgiyi pratiğe dökmemi sağladı.

---

*Not: Tüm bu süreci kendim ilerlettim ve teknik anlamda yapay zekadan yardım almadım. Sadece yazıların düzenlenmesi ve mimari yapı oluşturulurken yardım aldım. Bu sebepten dolayı da belgelerde yapay zeka kullanılmadı şıkkını işaretlemedim.*

