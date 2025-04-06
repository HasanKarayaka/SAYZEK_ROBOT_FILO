# SAYZEK_ROBOT_FILO

### Ubuntu 22.04 ve GitHub Kurulumu

Bu rehber, Ubuntu 22.04 işletim sisteminin ve GitHub araçlarının kurulumuna ilişkin adımları içermektedir.

### Neden Ubuntu 22.04?

Ubuntu 22.04, uzun süreli destek (LTS) sunan, kararlı ve güvenilir bir Linux dağıtımıdır. Şu anda daha stabil çalıştığı için tercih edilmiştir.

### Ubuntu 22.04 Kurulumu

1. Ubuntu 22.04 kurulum dosyasını indirin: [Ubuntu Resmi Web Sitesi](https://ubuntu.com/download/desktop).
2.  İSO dosyasını indirdikten sonra USB belleğinize iso dosyasını yazdırın (örneğin [Rufus](https://rufus.ie)) kullanın.
3. Bilgisayarınızı yeniden başlatarak bios'u açarak USB ubuntu seçeneğini seçin.
4. Ekrandaki kurulum talimatlarını takip ederek Ubuntu 22.04'ü yükleyin.

Daha ayrıntılı kurulum rehberi için şu bağlantıya göz atabilirsiniz: [Ubuntu 22.04 Kurulum Rehberi](https://ubuntu.com/tutorials/install-ubuntu-desktop).

### ROS 2 Humble Kurulumu (Ubuntu 22.04)

Aşağıdaki tek komut bloğunu terminale sırasıyla girerek ROS 2 Humble kurulumunu gerçekleştirebilirsiniz:


### Locale Ayarlarını Yapılandırma
locale  # check for UTF-8

sudo apt update && sudo apt install locales -y
sudo locale-gen en_US en_US.UTF-8
sudo update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8
export LANG=en_US.UTF-8

locale  # verify settings

### Gerekli Depoları ve Araçları Kurma
sudo apt install software-properties-common -y
sudo add-apt-repository universe

### ROS 2 Deposu ve Anahtarını Ekleyin
sudo apt update && sudo apt install curl -y
sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key -o /usr/share/keyrings/ros-archive-keyring.gpg

echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(. /etc/os-release && echo $UBUNTU_CODENAME) main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null

### ROS 2 Humble'ı Kurma
sudo apt update
sudo apt upgrade -y
sudo apt install ros-humble-desktop -y
sudo apt install ros-humble-ros-base -y
sudo apt install ros-dev-tools -y

### ROS Ortamını Kaynaklama
source /opt/ros/humble/setup.bash

### Kurulumun Doğrulanması
ros2 run demo_nodes_cpp talker  # Başka bir terminalde çalıştırılacak listener için bekleyin
ros2 run demo_nodes_py listener

## Open RMF
(Open Robotics Middleware Framework), ROS 2 ekosisteminin bir parçası olarak geliştirilmiş açık kaynaklı bir çerçevedir. Amacı, çoklu robot sistemlerinin ve altyapının bir arada çalışmasını sağlamak, yani farklı türdeki robotların ve cihazların koordinasyonunu yönetmektir.

### Open RMF'nin Temel Özellikleri
Çoklu Robot Koordinasyonu: Farklı üreticilerin robotlarını aynı ortamda çakışmadan çalıştırır.

Görev Yönetimi: Robotların görev dağılımını ve optimizasyonunu sağlar (örn. teslimat, temizlik görevleri).

Ortak Altyapı Kullanımı: Asansörler, kapılar veya şarj istasyonları gibi altyapı unsurlarının robotlar tarafından paylaşılmasını koordine eder.

Simülasyon ve Test: Çeşitli robotların aynı senaryoda çalışmasını simüle ederek test eder.

### Kullanım Alanları
Endüstriyel Otomasyon: Depo ve lojistikte farklı robotların bir arada çalışması.

Akıllı Binalar: Robotların bina altyapısını ortak kullanımı (örn. asansör entegrasyonu).

Hizmet Robotları: Çok robotlu sistemlerin koordinasyonu (örn. oteller, hastaneler).

Open RMF, farklı robot sistemlerini ve altyapıyı kolayca entegre ederek karmaşık ortamlarda verimli ve organize bir çalışma ortamı sunar.

### OpenRMF (Open Robotics Middleware Framework) Nedir ve Neden Tercih Edilir?
OpenRMF, robot filo sistemlerini yönetmek için geliştirilmiş bir yazılım altyapısıdır. Özellikle birden fazla robotun bir arada çalıştığı sistemlerde, farklı markalardaki veya türlerdeki robotların uyumlu bir şekilde iş birliği yapmasını sağlar. Aşağıda, OpenRMF’nin neden tercih edildiği detaylı bir şekilde açıklanmıştır:

### 1. Farklı Robot Sistemlerini Destekler
OpenRMF, farklı üreticilere veya teknolojilere ait robotların bir arada çalışabilmesini sağlar. Bu, karmaşık ve çeşitlilik içeren robot filoları için büyük bir avantajdır.

### 2. Görev Yönetimi ve Planlama
OpenRMF, robotlara görevleri dinamik olarak atayabilir ve bu görevleri önceliklendirebilir. Bu sayede robotların verimli çalışması sağlanır ve zaman kaybı en aza indirilir.

### 3. Modüler ve Esnek Tasarım
Sistem modüler bir yapıya sahiptir ve kolayca özelleştirilebilir. Kullanıcılar, ihtiyaçlarına göre yeni özellikler ekleyerek sistemi geliştirebilir.

### 4. ROS 2 Entegrasyonu
OpenRMF, robot teknolojilerinde yaygın olarak kullanılan ROS 2 (Robot Operating System 2) üzerine inşa edilmiştir. Bu sayede gerçek zamanlı iletişim, güvenlik ve yüksek performans sunar.

### 5. Simülasyon ve Test İmkânı
Sistemi gerçek ortamda kullanmadan önce, Gazebo gibi simülasyon araçları ile test etmek mümkündür. Bu, maliyetleri düşürürken aynı zamanda geliştirme sürecinde güvenilirliği artırır.

### 6. Açık Kaynak ve Topluluk Desteği
OpenRMF, açık kaynaklı bir projedir. Bu, kullanıcıların projeyi ücretsiz olarak kullanabilmesini ve geliştirebilmesini sağlar. Ayrıca dünya çapında geniş bir kullanıcı topluluğundan destek alınabilir.

### 7. Altyapı ve Kaynak Yönetimi
OpenRMF, robotların haritalama, asansör kontrolü, kapı erişimi gibi altyapı elemanlarıyla iletişim kurmasını sağlar. Aynı zamanda tüm bu kaynakları merkezi bir şekilde yönetme imkânı sunar.

### 8. Engel Algılama ve Güvenlik
Sistem, gerçek zamanlı olarak engelleri algılayabilir ve robotların rotasını otomatik olarak yeniden planlayarak güvenli bir çalışma ortamı oluşturur.

### 9. Karmaşık Alan Yönetimi
Depolar, fabrikalar veya çok katmanlı binalar gibi karmaşık alanların yönetimini kolaylaştırır. Robotlar, bu alanlar içinde etkin bir şekilde hareket edebilir ve görevlerini tamamlayabilir.

### 10. Kapsamlı Dokümantasyon ve Kolay Kullanım
OpenRMF, detaylı dokümantasyonu ve kullanıcı dostu yapısı sayesinde, hem yeni başlayanlar hem de deneyimli kullanıcılar için kolay bir deneyim sunar.

### OpenRMF’yi indirmek ve kurulumunu gerçekleştirmek için aşağıdaki bağlantıda yer alan GitHub reposundaki talimatları takip etmeniz gerekmektedir:
https://github.com/open-rmf/rmf

Bu bağlantıda, OpenRMF’nin nasıl indirileceği, gerekli bağımlılıkların nasıl yükleneceği ve çalıştırılacağı adım adım açıklanmaktadır. Burdaki önemli husus kullanmış olduğunuz ROS sürümünü seçmeniz ve sürüme ait kurulum adımlarını takip etmeniz.


## Nav2
ROS 2'nin Nav2 (Navigation2) paketi, mobil robotların otonom bir şekilde belirli bir başlangıç noktasından hedefe ulaşmasını sağlamak için kullanılır. Bu paket, robotun çevresel algılama, hedef planlama ve hareket kontrolü gibi temel navigasyon görevlerini yerine getirir.


### Nav2'nin Temel Görevleri
Haritalama ve Yerelleştirme: Robot, çevresini haritalandırır ve harita üzerinde kendi konumunu belirler. (Örn: SLAM ve Monte Carlo Localization)

Yol Planlama: Robot, engelleri aşarak hedefe en uygun yolu belirler. (Global: A*; Yerel: Dynamic Window Approach)

Hareket Kontrolü: Robotun hız ve yönünü kontrol ederek planlanan yolu takip etmesini sağlar.

Engelden Kaçınma: Statik ve dinamik engelleri algılayarak çarpışmaları önler.

### Kullanım Alanları
Otonom Robotlar: Depo robotları, hizmet robotları.

Araştırma ve Eğitim: Algoritma geliştirme.

Savunma: Tehlikeli bölgelerde keşif.

Nav2, modüler yapısı ve ROS 2'nin avantajları sayesinde robotların çevresinde güvenli ve etkili bir şekilde hareket etmesine olanak tanır.

### NAV2' nin Github repositoriesi adresteki linktedir,  ros sürümünüze göre uygun olan kurulum talimatlarını takip ederek kurabilirsiniz.
https://github.com/ros-navigation/navigation2.git



## Multiple turtlebot3 usage

Gazebo ortamında filo simülasyonu gerçekleştirmek için birden fazla mobil robot kullanımı gereklidir. Bu amaç doğrultusunda, TurtleBot3 robotları tercih edilmekte olup, söz konusu robotların kullanımını sağlayan birden fazla robotlu simülasyonlar için https://github.com/arshadlab/turtlebot3_multi_robot GitHub deposu örnek teşkil etmektedir.

Bu depoda, birden fazla TurtleBot3 robotunu simüle etmek için gerekli yapılandırma ve kodlar sunulmaktadır. Projede, birden fazla robotun başlatılması ve yönetilmesi, özellikle launch dosyalarının özelleştirilmesi ile mümkün kılınmaktadır.

### Temel Amaç
Projenin temel hedefi, var olan launch dosyasını ihtiyaçlara göre düzenleyerek istenilen sayıda TurtleBot3 robotunun simülasyon ortamında başlatılmasını sağlamaktır. Bu süreçte, robotların isimlendirilmesi, farklı namespace tanımları yapılması ve Gazebo ortamında çakışma olmaksızın tüm robotların düzgün bir şekilde entegre edilmesi gereklidir.

### Sonuç
Bu yöntem, çok robotlu sistemlerin koordinasyonu, filo yönetimi algoritmalarının geliştirilmesi ve çeşitli otonom navigasyon uygulamalarının test edilmesi gibi çalışmalar için güçlü bir altyapı sunmaktadır. Projenin akademik ve endüstriyel araştırmalarda geniş bir kullanım alanı bulunmaktadır.

# UYGULAMA
### Terminal Ekranına Sırayla
### Install Gazebo
- sudo apt install ros-humble-gazebo-*

### Install Cartographer
- sudo apt install ros-humble-cartographer
- sudo apt install ros-humble-cartographer-ros

### Install Navigation2
- sudo apt install ros-humble-navigation2
- sudo apt install ros-humble-nav2-bringup

### Install the required TurtleBot3 Packages.
- mkdir -p ~/turtlebot3_ws/src
- cd ~/turtlebot3_ws/src/
- git clone -b humble https://github.com/ROBOTIS-GIT/DynamixelSDK.git
- git clone -b humble https://github.com/ROBOTIS-GIT/turtlebot3_msgs.git
- git clone -b humble https://github.com/ROBOTIS-GIT/turtlebot3.git
- sudo apt install python3-colcon-common-extensions

- cd ~/turtlebot3_ws
- colcon build --symlink-install
- echo 'source ~/turtlebot3_ws/install/setup.bash' >> ~/.bashrc
- source ~/.bashrc

### Setup your ROS environment for the Remote PC.
- echo 'export ROS_DOMAIN_ID=30 #TURTLEBOT3' >> ~/.bashrc
- echo 'source /usr/share/gazebo/setup.sh' >> ~/.bashrc
- source ~/.bashrc

### paketleri başarılı bir şekilde kurduktan sonra gazebo ortamında simülasyon için haritamızı oluşturuyoruz.
### gazebo uygulamasını çatığımızda sol üste build editör kısmından kendi haritamızı oluşturabiliriz.
![gazebo_build_editor](https://github.com/user-attachments/assets/e8f8d882-7dab-4121-94e1-f404a489ae73)

### ctrl+s ile haritamızı kaydetmeliyiz.

![model_ctrl_s](https://github.com/user-attachments/assets/ea43a488-f740-472a-b224-335e2d004860)

### haritayı kaydettikten sonra editör kısmından çıkış yapmalıyız, sol üsteki sekmeden çıkış yapabilirsiniz.
### çizmiş olduğumuz haritayı insert kısmından hangi isim ile kaydetmişseniz o ismli uzantıdan ekleyebilirsiniz.

![model_insert](https://github.com/user-attachments/assets/952f5d91-11a7-4005-a7fd-3e0d48afcb93)

### 1 herşeyi kapatın ve terminale sırayla

- cd turtlebot3_ws/
- source install/setup.bash 
- export TURTLEBOT3_MODEL=burger
- ros2 launch turtlebot3_gazebo empty_world.launch.py

### turtlebot3  robotunuz boş haritada geldiyse insert kısmından haritanızı ekleyebilirsiniz.
### 2. termianl açınız ve 

- cd turtlebot3_ws/
- source install/setup.bash 
- ros2 run turtlebot3_teleop teleop_keyboard

### komutu ile robotu haraket ettirebilirsiniz.
### 3. bir termianl açın ve şu komutları giriniz
- cd turtlebot3_ws/
- source install/setup.bash 
- export TURTLEBOT3_MODEL=burger
- ros2 launch turtlebot3_cartographer cartographer.launch.py use_sim_time:=True
" klavye ile robotunuzu gezdirin tüm haritayı taradıktan sonra rvizde haritayı görebilirsiniz"

### artık rviz açılmış olması lazım ve haritanın lidar tarafından algılanan yerlerini görüyor olmanız gerekiyor.

![nav2](https://github.com/user-attachments/assets/aeb22b7b-6c78-4753-8bde-075346bcc75e)

### tüm haritayı tarattıktan sonra artık map'i kaydetmeliyiz.

- ros2 run nav2_map_server map_saver_cli -f ~/map

### bu kodu 4. termianlde çalıştırın, terminalın bulunduğu konuma resmi kaydedecektir buna dikkat ediniz.
### artık nav2 paketini kullanmaya hazırız tüm terminalleri kapatabilirsiniz.
### şimdi tekrar 1. termianl
- cd turtlebot3_ws/
- source install/setup.bash 
- export TURTLEBOT3_MODEL=burger
- ros2 launch turtlebot3_gazebo empty_world.launch.py

### 2. terminal
- export TURTLEBOT3_MODEL=burger
- ros2 launch turtlebot3_navigation2 navigation2.launch.py use_sim_time:=True map:=$HOME/map.yaml

![nav2](https://github.com/user-attachments/assets/74336632-95d0-4320-8d75-b7dd25ff5ee1)


### haritanın neresindeyse robot orasına Pose Estimation ataması yapmalısın robotun yönü buradakı ok yönü ile aynı olması gerekmektedir.
![Screenshot from 2025-01-29 21-07-54](https://github.com/user-attachments/assets/170a8e3b-cc9a-4554-9434-f028fd46702f)

### robotun yönünü belirledikten sonra artık robotun nereye gitmesini istiyorsanız oraya nav2 goal atamalısınız

![nav2_gitmesi](https://github.com/user-attachments/assets/ca358b5a-0905-485b-ac6b-7a90e281a004)

https://github.com/user-attachments/assets/73829583-634e-4d49-97fc-b2254f80ad1f


# **Free Fleet** 

## **Free Fleet Nedir?**   
**Free Fleet**, **Open-RMF (Open Robotics Middleware Framework)** ekosistemi içinde bulunan açık kaynaklı bir filo yönetim sistemidir. Robot filolarını merkezi bir sistem üzerinden yönetmek, görevleri koordine etmek ve farklı üreticilere ait robotları birlikte çalıştırmak için kullanılır.  

## **Free Fleet’in Temel Özellikleri**  
1. **Çoklu Robot Yönetimi**  
   - Aynı anda birden fazla robotun görev almasını ve yönetilmesini sağlar.  

2. **Bağımsız Robot Entegrasyonu**   
   - Farklı üreticilere ait robotların tek bir çatı altında çalışmasını sağlar.  

3. **Açık Kaynak ve Modüler Yapı**  
   - Open-RMF’nin modüler mimarisine uygun şekilde geliştirilmiştir.  
   - Kullanıcılar ihtiyaçlarına göre özelleştirebilir.  

4. **REST API & ROS 2 Uyumluluğu**   
   - Free Fleet, REST API ile uzaktan kontrol edilebilir.  
   - ROS 2 desteklidir, böylece Open-RMF ile sorunsuz çalışır.  

5. **Görev Yönetimi**   
   - Robotlara belirlenen görevleri dinamik olarak atayabilir.  
   - Görev ilerlemelerini takip edebilir.  

6. **Özel Protokoller ve Haberleşme**   
   - WebSocket, MQTT gibi haberleşme yöntemlerini destekleyebilir.  

## Server - Client Yapısı

Free Fleet, klasik bir **Server - Client** mimarisi ile çalışır:

### Server (`free_fleet_server`)
- Merkezi filo yöneticisidir.
- Robotlara hangi görevleri ne zaman yapacaklarını belirler.
- Kullanıcıdan gelen görevleri (örneğin, "robot A’yı noktadan noktaya gönder") robotlara iletir.
- ROS 2 üzerinden görevleri yayınlar (`/destination_requests` gibi).
- Genellikle güçlü bir makinede, merkezi sunucuda çalışır.

### Client (`free_fleet_client`)
- Robot üzerinde çalışır.
- Free Fleet Server’dan gelen görevleri alır.
- Robotun iç kontrol sistemine bu görevleri iletir (örneğin `nav2`, `slam_toolbox` gibi sistemlerle entegre olabilir).
- Robotun anlık konumu ve durumu gibi verileri Server'a geri yollar.
- ROS 1 veya ROS 2 ile uyumlu çalışabilir.


linketi adrese giderek kurulum yapabilirsiniz
- https://github.com/open-rmf/free_fleet/tree/legacy?tab=readme-ov-file


- ros2 humble için kurulum yapıcaksanız dikkat etmeniz gerekenler;

- git clone https://github.com/open-rmf/free_fleet -b legacy
 
- git clone https://github.com/open-rmf/rmf_internal_msgs -b humble

**burdaki iki kodu şu şekilde yazmanı gerekmtedir.**

- rosdep install --from-paths src --ignore-src --rosdistro humble -yr

bu komutu çalıştırdığınızda eğer ros1 ile ilgili hatalar alıyorsanız, ros1 ile ilgili klasörleri silebilir ve tekrar deneyebilirsiniz veya kurulum esnasında gösterlien şu adımı uygulayabilirsiniz

#### Optionally use the command below to only build the relevant packages, başlığı altındaki kodu uygulayabilirsiniz.

Derleme ve kurulum başarılı olduktan sonra;
#### 1. terminalde
- export TURTLEBOT3_MODEL=burger; ros2 launch ff_examples_ros2 turtlebot3_world_ff.launch.xml
- gazebo ve rviz dünyasını başlatıyoruz.

#### 2. terminalde
- ros2 launch ff_examples_ros2 turtlebot3_world_ff_server.launch.xml

görevlerin robota iletileceği bir server oluşturuyoruz

![Screenshot from 2025-02-11 21-18-40](https://github.com/user-attachments/assets/1315ced0-3aba-43bb-85e0-a3d43f16c7ba)
- new robot: [ros2_tb3_0]  / fleet name: turtlebot3

robotun isim tanımlamalarını görev vermek için kullancağız bu yüzden burdaki tanımları bilmeniz gerekiyor

#### 3. terminalde görev vermeye artık hazırız

- ros2 run ff_examples_ros2 send_destination_request.py -f turtlebot3 -r ros2_tb3_0 -x 1.725 -y -0.39 --yaw 0.0 -i deneme

**kodu dikatli incelediğinizde new robot ile fleet name isimlendirmelerinin nasıl atandığını fark ediyorsunnuz, deneme yazan yer kefi olarak yazılabilir. 
Artık bu komutu da çalıştırdığınızda robotun rviz ve gazeboda istediğiniz konuma otonom haraketini izleyebilirsiniz.**
https://github.com/user-attachments/assets/4c6fb214-0b3c-453f-825a-ac24dc604d3b
![Screenshot from 2025-03-20 11-36-08](https://github.com/user-attachments/assets/6be087e8-aaa3-4173-8f0e-a35b9b7fd043)



# Traffic Editor   

## **Traffic Editor Nedir?**  
**Traffic Editor**, **Open-RMF (Open Robotics Middleware Framework)** ekosistemi içinde kullanılan bir araçtır. Bina içi haritaları ve robot trafiğini yönetmek için geliştirilmiştir. Kullanıcıların robotların hareket edebileceği haritaları oluşturmalarına, düzenlemelerine ve simülasyonlara entegre etmelerine olanak tanır.  

## **Özellikler**   

- **Harita ve Kat Planı Düzenleme**   
  - Robotların hareket edebileceği alanları belirlemek için bina haritaları oluşturur.  
  - Kat planlarını düzenleyerek geçiş yolları, engeller ve odalar eklenebilir.  

- **Şeritler ve Geçiş Noktaları** 
  - Robotların takip etmesi gereken yolları (lane) belirler.  
  - Kavşaklar ve yön değişim noktaları tanımlanabilir.  

- **Filo Trafik Yönetimi**  
  - Çoklu robot sistemlerinde trafik yönetimini sağlar.  
  - Çakışmaları önlemek için şeritler arasında önceliklendirme yapar.  

- **Simülasyon ve Open-RMF Uyumluluğu**   
  - Open-RMF ile entegre çalışarak gerçek robot sistemleriyle uyumlu senaryolar oluşturur.  
  - Robotların hareketlerini simüle etmek ve test etmek için kullanılabilir.  

- **Kolay Kullanım ve Açık Kaynak**  
  - Kullanıcı dostu arayüzü ile harita düzenlemeyi kolaylaştırır.  
  - Açık kaynak olduğu için geliştiriciler tarafından özelleştirilebilir.  

## **Çalışma Mantığı**   
- **Traffic Editor**, haritaları düzenlemek ve robotların kullanacağı yolları belirlemek için kullanılır.  
- **Şeritler (lanes)** ve **düğümler (nodes)** eklenerek robotların izlemesi gereken yollar tanımlanır.  
- Harita **Open-RMF’ye aktarılır** ve filo yönetim sistemi tarafından kullanılır.  

## **Kullanım Senaryoları**   
✅ Kapalı alanlarda robotların takip edeceği yolları belirlemek.  
✅ Çoklu robot sistemlerinde çarpışmaları önlemek ve trafiği yönetmek.  
✅ Open-RMF tabanlı filo yönetimi sistemlerinde bina içi haritaları oluşturmak.  
## traffic-editor uygulamasını indiriyoruz ve https://www.youtube.com/watch?v=V-pzesxVJoA eğitim videosuna göre oluşturduğumuz haritayı uygulamada açıyoruz
- haritayı png formatına açabilirsiniz ros2 ile kaydettiğiniz mapin formatı png formatında olmayabilir!
- haritayı açtıktan sonra video eğitim ile haritanızın trafik yönetimi oluşturun
- haritayı kaydettikten sonra .buildin.yaml dosyanın içerisinde png nin konumuna dikkat edin yaml ile aynı konumda olması gerkiyor

# ÇOKLU ROBOTLARA MANUAL GÖREV ATAMA(Free Fleet algoritmasını kullanmadan NAV2 ile göreve gönderme)

https://github.com/user-attachments/assets/73829583-634e-4d49-97fc-b2254f80ad1f







