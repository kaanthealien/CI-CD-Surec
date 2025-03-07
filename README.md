# Jenkins Pipeline ile Nginx Deploy Süreci

Bu proje, **CI/CD (Continuous Integration / Continuous Deployment)** süreçlerini anlatan ve **Jenkins** kullanarak **Nginx** üzerine **deployment** yapmayı sağlayan bir pipeline kurulumunu içermektedir.

## 🚀 Proje Hakkında

Bu **Jenkins pipeline'ı**, aşağıdaki adımları otomatikleştirir:

1. **Kodun Github'dan Çekilmesi**: GitHub'dan en son değişiklikler alınır.
2. **Derleme (Build)**: Proje derlenir, böylece kod hataları varsa tespit edilir.
3. **Testler**: Kod test edilir (isteğe bağlı).
4. **Deploy**: Derlenen proje, **Nginx** üzerine otomatik olarak deploy edilir.
5. **Nginx Yeniden Başlatma**: Nginx servisi yeniden başlatılır, böylece yeni sürüm aktif olur.

**Teknolojiler**:
- **Jenkins**: CI/CD süreçlerinin yönetimi.
- **GitHub**: Kaynak kod deposu.
- **Nginx**: Uygulama sunucusu olarak hizmet eder.
- **Windows**: Bu pipeline Windows ortamında çalışacak şekilde ayarlanmıştır.

## 🛠️ Kurulum ve Kullanım

### Gereksinimler

- **Jenkins** kurulu ve çalışıyor olmalı.
- **Git** kurulu olmalı.
- **Nginx** kurulu ve doğru şekilde yapılandırılmış olmalı.
- **Windows işletim sistemi** kullanılmalıdır (ya da gerekli uyarlamalar yapılmalıdır).

### Pipeline Yapılandırması

1. **GitHub'dan Kod Çekme**: Kodunuzun GitHub'dan çekilmesi için **Jenkinsfile** kullanılır.
2. **Jenkins Pipeline Oluşturma**: GitHub reposunu Jenkins'e bağlayarak pipeline oluşturun.
3. **Nginx Konfigürasyonu**: Nginx'in doğru dizinleri ve konfigürasyonları yapılandırılmalıdır.

### Jenkinsfile Örneği

Aşağıda, **Jenkinsfile**'ın basit bir örneği yer almaktadır:

```groovy
pipeline {
    agent any

    environment {
        nginxDirectory = 'C:\\path' 
    }

    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/path'
            }
        }

        stage('Build') {
            steps {
                echo 'Building the project...'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
            }
        }

        stage('Deploy to Nginx') {
            steps {
                script {
                    bat "xcopy /Y /E index.html ${nginxDirectory}"
                }
            }
        }

        stage('Restart Nginx') {
            steps {
                script {
                    bat 'net stop nginx'
                    bat 'net start nginx'
                }
            }
        }
    }
}
```
## Adımlar:
GitHub Repo'sunu Klonlama: Jenkins, belirttiğiniz GitHub reposundan projenizi çeker.
Build (Derleme): Proje, belirtilen adımlara göre derlenir. Bu aşamada kodda herhangi bir hata varsa derleme başarısız olur.
Testler: Derleme tamamlandığında, otomatik testler çalıştırılır (bu aşama projeye dahil edilebilir).
Deploy: Derlenen ve test edilen proje, Nginx üzerine deploy edilir.
Nginx Yeniden Başlatma: Son olarak, Nginx servisi yeniden başlatılır, böylece yeni sürüm çalışmaya başlar.
## 📝 Notlar
Test Aşamaları: Bu pipeline, test aşamasını temel seviyede tutuyor. Gerçek projelerde testlerinizi entegre edebilirsiniz.
Geliştirme: Eğer pipeline'ı geliştirmek isterseniz, daha fazla aşama (örn. versiyon yönetimi, testler) ekleyebilirsiniz.
## 🔧 Geliştirme
Bu pipeline'ı daha da geliştirmek isterseniz, aşağıdaki adımları izleyebilirsiniz:

Otomatik Testler: Testler ekleyerek projenin her aşamasında kod kalitesini kontrol edebilirsiniz.
Build Süreci: Derleme adımında gerçek bir build aracı (Maven, Gradle, npm vs.) kullanabilirsiniz.
Versiyon Kontrolü: Her yeni dağıtımda versiyon numarası ekleyebilirsiniz.
