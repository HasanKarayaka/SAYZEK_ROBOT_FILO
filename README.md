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

#UYGULAMA

###Install Gazebo
sudo apt install ros-humble-gazebo-*

###Install Cartographer
sudo apt install ros-humble-cartographer
sudo apt install ros-humble-cartographer-ros

###Install Navigation2
sudo apt install ros-humble-navigation2
sudo apt install ros-humble-nav2-bringup

###Install the required TurtleBot3 Packages.
$ mkdir -p ~/turtlebot3_ws/src
$ cd ~/turtlebot3_ws/src/
$ git clone -b humble https://github.com/ROBOTIS-GIT/DynamixelSDK.git
$ git clone -b humble https://github.com/ROBOTIS-GIT/turtlebot3_msgs.git
$ git clone -b humble https://github.com/ROBOTIS-GIT/turtlebot3.git
$ sudo apt install python3-colcon-common-extensions
$ cd ~/turtlebot3_ws
$ colcon build --symlink-install
$ echo 'source ~/turtlebot3_ws/install/setup.bash' >> ~/.bashrc
$ source ~/.bashrc

###Setup your ROS environment for the Remote PC.
$ echo 'export ROS_DOMAIN_ID=30 #TURTLEBOT3' >> ~/.bashrc
$ echo 'source /usr/share/gazebo/setup.sh' >> ~/.bashrc
$ source ~/.bashrc

###paketleri başarılı bir şekilde kurduktan sonra gazebo ortamında simülasyon için haritamızı oluşturuyoruz.
![gazebo_build_editor](https://github.com/user-attachments/assets/e8f8d882-7dab-4121-94e1-f404a489ae73)



