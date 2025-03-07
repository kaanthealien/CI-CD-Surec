Jenkins Pipeline ile Nginx Deploy Süreci
Bu proje, CI/CD (Continuous Integration / Continuous Deployment) süreçlerini anlatan ve Jenkins kullanarak Nginx üzerine deployment yapmayı sağlayan bir pipeline kurulumunu içermektedir.

🚀 Proje Hakkında
Bu Jenkins pipeline'ı, aşağıdaki adımları otomatikleştirir:

Kodun Github'dan Çekilmesi: GitHub'dan en son değişiklikler alınır.
Derleme (Build): Proje derlenir, böylece kod hataları varsa tespit edilir.
Testler: Kod test edilir (isteğe bağlı).
Deploy: Derlenen proje, Nginx üzerine otomatik olarak deploy edilir.
Nginx Yeniden Başlatma: Nginx servisi yeniden başlatılır, böylece yeni sürüm aktif olur.
Teknolojiler:

Jenkins: CI/CD süreçlerinin yönetimi.
GitHub: Kaynak kod deposu.
Nginx: Uygulama sunucusu olarak hizmet eder.
Windows: Bu pipeline Windows ortamında çalışacak şekilde ayarlanmıştır.
🛠️ Kurulum ve Kullanım
Gereksinimler
Jenkins kurulu ve çalışıyor olmalı.
Git kurulu olmalı.
Nginx kurulu ve doğru şekilde yapılandırılmış olmalı.
Windows işletim sistemi kullanılmalıdır (ya da gerekli uyarlamalar yapılmalıdır).
Pipeline Yapılandırması
GitHub'dan Kod Çekme: Kodunuzun GitHub'dan çekilmesi için Jenkinsfile kullanılır.
Jenkins Pipeline Oluşturma: GitHub reposunu Jenkins'e bağlayarak pipeline oluşturun.
Nginx Konfigürasyonu: Nginx'in doğru dizinleri ve konfigürasyonları yapılandırılmalıdır.

📝 Notlar
Test Aşamaları: Bu pipeline, test aşamasını temel seviyede tutuyor. Gerçek projelerde testlerinizi entegre edebilirsiniz.
Geliştirme: Eğer pipeline'ı geliştirmek isterseniz, daha fazla aşama (örn. versiyon yönetimi, testler) ekleyebilirsiniz.
🔧 Geliştirme
Bu pipeline'ı daha da geliştirmek isterseniz, aşağıdaki adımları izleyebilirsiniz:

Otomatik Testler: Testler ekleyerek projenin her aşamasında kod kalitesini kontrol edebilirsiniz.
Build Süreci: Derleme adımında gerçek bir build aracı (Maven, Gradle, npm vs.) kullanabilirsiniz.
Versiyon Kontrolü: Her yeni dağıtımda versiyon numarası ekleyebilirsiniz.
