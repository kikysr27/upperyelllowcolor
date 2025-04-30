
# Instalasi dan Pengujian ROS 2 Humble di Ubuntu 22.04.5 LTS

Dokumen ini berisi panduan lengkap untuk menginstal ROS 2 Humble di Ubuntu 22.04.5 LTS serta pengujian node talker dan listener menggunakan CLI.

Referensi tambahan: [ChatGPT ROS 2 Guide](https://chatgpt.com/share/6811bd89-12cc-800a-bb37-5e03f070e579)

## Persyaratan
- Ubuntu 22.04.5 LTS
- Python 3.10 (default di Ubuntu 22.04)
- Internet aktif
- Akses sudo

---

## Langkah 1: Konfigurasi Locale

```bash
sudo apt update && sudo apt install locales
sudo locale-gen en_US en_US.UTF-8
sudo update-locale LC_ALL=en_US.UTF-8 LANG=en_US.UTF-8
export LANG=en_US.UTF-8
```

---

## Langkah 2: Tambahkan Repositori ROS 2

```bash
sudo apt install software-properties-common
sudo add-apt-repository universe
```

Tambahkan key GPG ROS:

```bash
sudo apt update && sudo apt install curl -y
sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.asc -o /usr/share/keyrings/ros-archive-keyring.gpg
```

Tambahkan source list ROS:

```bash
echo "deb [signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(. /etc/os-release && echo $UBUNTU_CODENAME) main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null
```

---

## Langkah 3: Install ROS 2 Humble

```bash
sudo apt update
sudo apt install ros-humble-desktop
```

---

## Langkah 4: Sumberkan Environment

Tambahkan ke bashrc:

```bash
echo "source /opt/ros/humble/setup.bash" >> ~/.bashrc
source ~/.bashrc
```

Untuk setiap terminal baru:

```bash
source /opt/ros/humble/setup.bash
```

---

## Langkah 5: Cek Instalasi

```bash
ros2 --version
```

Jika berhasil, akan muncul versi ROS 2, contoh: ros2 0.16.0

---

## Langkah 6: Jalankan Contoh Node Talker dan Listener

🖥 Terminal 1:

```bash
source /opt/ros/humble/setup.bash
ros2 run demo_nodes_cpp talker
```

🖥 Terminal 2:

```bash
source /opt/ros/humble/setup.bash
ros2 run demo_nodes_cpp listener
```

Jika berhasil, listener akan mencetak:

```
[INFO] [listener]: I heard: 'Hello World: 1'
```

---

## Langkah 7: Verifikasi Node dan Topic

Cek node yang aktif:

```bash
ros2 node list
```

Output jika talker aktif:

```
/talker
```

Cek pesan yang dipublikasikan:

```bash
ros2 topic echo /chatter
```

Output:

```
data: 'Hello World: 25'
---
data: 'Hello World: 26'
---
```

---

## Langkah 8: Periksa Koneksi Jaringan

Jika tidak bisa mendeteksi node listener, periksa interface:

```bash
sudo apt install net-tools
ifconfig
```

Pastikan ada interface aktif seperti wlan0 atau wlo1 (WiFi), dan bukan hanya lo (loopback).

---

## Troubleshooting

- Jika listener tidak menerima pesan:
  - Pastikan kedua terminal telah menjalankan: source /opt/ros/humble/setup.bash
  - Jalankan node listener setelah talker
  - Pastikan tidak ada VPN atau firewall yang memblokir DDS multicast

---

## Penutup

ROS 2 Humble telah berhasil diinstal dan dijalankan di Ubuntu 22.04.5 LTS. Anda dapat mulai membuat node sendiri atau mengembangkan aplikasi berbasis ROS 2.
