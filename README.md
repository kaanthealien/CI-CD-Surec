Jenkins Pipeline ile Nginx Deploy Süreci

CI/CD (Continuous Integration / Continuous Deployment) uygulamalarını anlatan ve Jenkins kullanarak Nginx'e deployment yapan bir pipeline kurulumunu tamamladım.
Bu pipeline, kodu otomatik olarak Github'dan alıp, derleyip test ediyor, ardından Nginx üzerine deploy ediyor ve son olarak Nginx'i yeniden başlatıyor.
Gerçek bir projede bu pipeline daha karmaşık hale gelebilir ve otomatik testler, derlemeler gibi işlemlerle zenginleştirilebilir.
