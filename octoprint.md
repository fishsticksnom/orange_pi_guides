<div align="center">
<h1>Octoprint</h1>
</div>

**Update and Upgrade**

```bash
sudo apt update
sudo apt upgrade
```

Install Packages
```bash
sudo apt install python3-pip python3-dev python3-setuptools python3-venv git libyaml-dev build-essential
```

**Create Octoprint Folder**

```bash
cd
mkdir Octoprint
cd Octoprint
```

**Setup Virtual Enviorment**

```bash
python3 -m venv venv
source venv/bin/activate
```


**Install Octoprint**

```bash
pip install pip --upgrade
pip install octoprint
```

**Add orangepi user to Serial Ports**

```bash
sudo usermod -a -G tty orangepi
sudo usermod -a -G dialout orangepi
```


**Start Octoprint at boot**


```bash
cd /etc/systemd/system/
touch octoprint.service
nano octoprint.service
```

**Add config**

```bash
[Unit]
Description=The snappy web interface for your 3D printer
After=network-online.target
Wants=network-online.target

[Service]
Environment="LC_ALL=C.UTF-8"
Environment="LANG=C.UTF-8"
Type=exec
User=orangepi
ExecStart=/home/orangepi/Octoprint/venv/bin/octoprint

[Install]
WantedBy=multi-user.target
```

**Enable octoprint**

```bash
sudo systemctl enable octoprint.service
```
Plugins

Cancel Objects
Bed Visualizer
Floating Navbar
Gcode Editor
Print Time Genius
Simple Emergency Stop
Touchtest
