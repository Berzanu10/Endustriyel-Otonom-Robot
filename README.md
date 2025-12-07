# 🤖 Autonomous Rescue & Inspection Robot (Otonom Arama Kurtarma ve Denetim Robotu)

![ROS2](https://img.shields.io/badge/ROS2-Humble-blue) ![Gazebo](https://img.shields.io/badge/Gazebo-Classic-orange) ![Python](https://img.shields.io/badge/Language-Python3-yellow) ![Status](https://img.shields.io/badge/Status-Completed-success)

Bu proje, **ROS 2 Humble** ve **Gazebo** simülasyon ortamı kullanılarak geliştirilmiş, **TurtleBot3 Waffle Pi** tabanlı otonom bir mobil robot sistemidir. Robot; afet bölgeleri, hastaneler ve endüstriyel tesisler gibi riskli alanlarda otonom navigasyon, haritalama ve görüntü işleme ile hedef tespiti görevlerini icra eder.

---

## 🌍 Proje Senaryoları ve Çözümler

Proje, insan hayatını riske atmadan aşağıdaki üç kritik senaryoda görev yapmak üzere tasarlanmıştır:

### 1. 🆘 Afet Sonrası Arama Kurtarma (Deprem)
* **Problem:** Deprem sonrası yıkılma riski taşıyan veya insanların giremeyeceği kadar dar alanlarda durum tespiti yapılamamaktadır.
* **Çözüm:** Robot, enkaz altındaki dar koridorlardan geçerek canlı yaşam belirtilerini (görsel hedef) tespit eder ve konumunu ekiplere bildirir.

### 2. 🏥 Sağlık Lojistiği (Karantina)
* **Problem:** Bulaşıcı hastalık durumlarında sağlık personelinin enfekte hastalarla teması yüksek risk oluşturur.
* **Çözüm:** İlaç ve tıbbi malzemelerin, karantina odalarına insan teması olmadan otonom bir şekilde ulaştırılmasını sağlar.

### 3. 🏭 Endüstriyel Güvenlik (Sızıntı Denetimi)
* **Problem:** Kimyasal fabrikaların tehlikeli boru hatlarında oluşan sızıntıların tespiti insanlar için ölümcüldür.
* **Çözüm:** Robot, tesisin dijital ikizi (haritası) üzerinde devriye gezerek sızıntıları (renk tabanlı anomali) tespit eder.

---

## 🛠️ Kurulum ve Gereksinimler

Projeyi çalıştırmak için **Ubuntu 22.04 LTS** ve **ROS 2 Humble** gereklidir. Aşağıdaki komutlarla tüm bağımlılıkları kurabilirsiniz.

### 1. ROS 2 ve Gazebo Paketlerinin Kurulumu
```bash
sudo apt update && sudo apt upgrade -y
sudo apt install ros-humble-desktop -y
sudo apt install ros-humble-gazebo-ros-pkgs -y
sudo apt install ros-humble-cartographer ros-humble-cartographer-ros -y
sudo apt install ros-humble-navigation2 ros-humble-nav2-bringup -y

Aşağıdaki kodları sırasıyla terminallerde açarak robotu çalıştırabilirsiniz.

sudo apt install ros-humble-turtlebot3* -y

echo 'export TURTLEBOT3_MODEL=waffle_pi' >> ~/.bashrc
source ~/.bashrc

export TURTLEBOT3_MODEL=waffle_pi
ros2 launch gazebo_ros gazebo.launch.py world:=$HOME/Hackathon/sonharita.world

ros2 launch robot_fix.launch.py

export TURTLEBOT3_MODEL=waffle_pi
ros2 launch turtlebot3_navigation2 navigation2.launch.py use_sim_time:=True map:=$HOME/Hackathon/final_map.yaml

# Örnek (Parkur sonundaki hedef):
python3 akilli_navigasyon.py -8.5 4.1



