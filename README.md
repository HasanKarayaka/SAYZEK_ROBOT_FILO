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

# ROS 2 Deposu ve Anahtarını Ekleyin
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



