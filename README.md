# Google DSC - Solution Challange Hack for Prosperity Hackathon | RescueAI

Google DSC tarafından düzenlenen Solution Challenge Hack for Prosperity Hackathon için oluşturulan RescueAI projesi. 

Amacımız, Google teknolojilerini kullanarak geliştirdiğimiz RescueAI çözümleri ile Birleşmiş Milletilerin yayınladığı [*Sürdürülebilir Kalkınma Amaçları*](https://www.tr.undp.org/content/turkey/tr/home/sustainable-development-goals.html)'na katkı sağlamaktır. Bu proje, *Sürdürülebilir Şehirler ve Topluluklar (Hedef 11)* başlığı altında yer alan *Doğal Afetlerin Olumsuz Etkilerinin Azaltılması (Hedef 11.5)* konusu ile ilgilidir. 

<p align="center">
  <img width="600" src="https://github.com/oreitor/google-hack-for-prosperity-hackathon/blob/main/RescueAI.png">
</p>

Hackathon'un bu aşamasında RescueAI için belirlenen ana hedef, yaşanan bir doğal afet sonrasında arama-kurtarma, acil müdahale süreçlerini sunduğumuz Yapay Zeka, Görüntü İşleme ve Mobil Uygulama çözümleri ile daha efektif hale getirmektir. 

#### Kullanılan Google Teknolojileri
* Tensorflow
* Flutter
* Google Cloud AutoML
* Google Cloud
* Google Maps Platform API's
* Google Earth Engine Apps

### Tensorflow ile Derin Öğrenme
Yapay zeka ve görüntü işleme yöntemleri sayesinde anlık uydu görüntüleri veya gönderilen bir drone ile afet bölgesi üzerinde otonom bir şekilde hasar tespiti, durum bilgisi veya öneriler sunulması istenmiştir. 

#### Test için Örnek Veri Seti
Şu anki aşamada ise Google Earth Engine Apps üzerinden alınan görüntü verileri ile Tensorflow derin öğrenme methotları kullanılarak evlerin hasarlı olup olmadıkları tespit edilmeye çalışılmıştır. Belirtilen duruma örnek case olarak işlemek üzere Karayipler'deki bir ada ülkesi olan Sint-Maarten'de yaşanan doğal afet seçilmiştir. Bu ada ülkesi 6 Eylül 2017'de Kategori 5 seviyesinde olan Irma Kasırgası tarafından önemli ölçüde hasar aldı ve yüzlerce ev yıkıldı. Google Earth Engine Apps'ten alınan aşağıdaki görüntülerde kasırga öncesi ve sonrası incelenen bölgenin afet durumu belirtilmiştir.

<p align="center">
  <img width="600" src="https://github.com/oreitor/google-hack-for-prosperity-hackathon/blob/main/before-disaster.jpg"><br /><span>Doğal Afet Öncesi</span>
</p>

<p align="center">
  <img width="600" src="https://github.com/oreitor/google-hack-for-prosperity-hackathon/blob/main/after-disaster.jpg"><br /><span>Doğal Afet Sonrası</span>
</p>

Örnek case modeli için bu bölge üzerinde afet sonrası hasar almış 50 farklı ev rastgele seçilmiştir. Aşağıdak örnekte olduğu gibi toplamda 100 adet olan seçilen evlerin afetten önce ve sonraki görüntüleri [test_images](https://github.com/oreitor/google-hack-for-prosperity-hackathon/tree/main/test_images) klasöründe toplanmış ve modeli test etmeye hazır hale getirilmiştir. 

<p align="center">
  <img width="200" src="https://github.com/oreitor/google-hack-for-prosperity-hackathon/blob/main/test_images/a43.png"><span> &emsp;</span>
  <img width="200" src="https://github.com/oreitor/google-hack-for-prosperity-hackathon/blob/main/test_images/b43.png">
</p>

#### Derin Öğrenme Modeli ve Parametreleri
Hackathon süresinin kısıtlı olması ve profesyonel bir derin öğrenme modeli oluşturulmak istendiği için *Fine Tuning* uygulamaları tercih edilmiştir. Literatür taraması esnasında karşılaşılan bilimsel çalışmadan alınan eğitilmiş derin öğrenme modeli ile Tensorflow üzerinden *Transfer Learning* ile süreç hızlandırılmıştır. 

*Structural Building Damage Detection with Deep Learning: Assessment of a State-of-the-Art CNN in Operational Conditions* başlıklı belirlenen bilimsel çalışma ile ilgili ayrıntılı bilgiye [buradan](https://www.mdpi.com/2072-4292/11/23/2765/htm) ulaşabilirsiniz. RescueAI yapay zeka [modeli](https://github.com/oreitor/google-hack-for-prosperity-hackathon/blob/main/uav.rar) için bu çalışmada içerisinde bulunan İnsansız Hava Aracı tarafından çekilen görüntüler ile eğitilmiş toplam 2,336,725 parametre bulunan model tercih edilmiştir. 

#### Test Sonucu
Belirtilen çalışma üzerinde modelin test doğruluğu %90.8 olmasına karşın bu projede seçilen rastgele 100 görüntünün testinin doğruluk oranı %81'dir. Aradaki farkın sebepleri ise harita üzerinden alınan görüntülerin kalitesi ve konumlandırma yöntemlerinin farklı olmasıyla ilgilidir. Aşağıda RescueAI'ın ilk model denemesindeki test sonuçları ile ilgili *Confusion Matrix* görülmektedir. F1 Score sonucu 0.8257 ile şu an için yeterli düzeydedir.

<p align="center">
  <img width="800" src="https://github.com/oreitor/google-hack-for-prosperity-hackathon/blob/main/img/cm.PNG"><br /><span>Confusion Matrix</span>
</p>

<p align="center">
  <img width="800" src="https://github.com/oreitor/google-hack-for-prosperity-hackathon/blob/main/img/cm_results.PNG"><br /><span>Confusion Matrix Sonuçları</span>
</p>

Aşağıda görüldüğü gibi derin öğrenme modeli için hazırlanan test görüntüleri içerisinden alınan rastgele sonuçlara göz atacak olursak, 100 görüntü içerisinden seçilen 11 görüntünün "Normal" veya "Hasarlı" olup olamdığı durumların tahmini belirtilmektedir. PC, Predicted Class yani tahmin edilen sınıfı ve AC, Actual Class yani gerçek sınıfı temsil etmektedir. Örneğe bakıldığında 11 görüntüden yalnızca 1 hatalı tespit durumu söz konusudur. 

<p align="center">
  <img width="500" src="https://github.com/oreitor/google-hack-for-prosperity-hackathon/blob/main/img/prediction.PNG"><br /><span>Test Sonuçları</span>
</p>

### Flutter ile Mobil Uygulama
Yapay zeka ve görüntü işleme yöntemleri sayesinde anlık uydu görüntüleri veya gönderilen bir drone ile afet bölgesi üzerinde otonom bir şekilde hasar tespiti, durum bilgisi veya öneriler sunulması istenmiştir.
