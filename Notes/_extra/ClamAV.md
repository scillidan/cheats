## On Arch[^1][^2]

```sh
sudo vim /etc/clamav/freshclam.conf
```

```sh
sudo vim /etc/clamav/clamd.conf
```

```
# https://wiki.archlinux.org/title/ClamAV#Configuration

# Modify the following
ExtendedDetectionInfo yes
MaxDirectoryRecursion 20
DetectPUA yes
HeuristicAlerts yes
ScanPE yes
ScanELF yes
ScanOLE2 yes
ScanPDF yes
ScanSWF yes
ScanXMLDOCS yes
ScanHWP3 yes
ScanOneNote yes
ScanMail yes
ScanHTML yes
ScanArchive yes
Bytecode yes
AlertBrokenExecutables yes
AlertBrokenMedia yes
AlertEncrypted yes
AlertEncryptedArchive yes
AlertEncryptedDoc yes
AlertOLE2Macros yes
AlertPartitionIntersection yes

OnAccessMaxFileSize 100M
OnAccessIncludePath /home
OnAccessPrevention no
OnAccessExtraScanning yes
OnAccessExcludeUname clamav

VirusEvent /etc/clamav/virus-event.bash
```

```sh
sudo vim /etc/sudoers.d/clamav
```

```
clamav ALL = (ALL) NOPASSWD: SETENV: /usr/bin/notify-send
```

```sh
sudo vim /etc/clamav/virus-event.bash
```

```bash
# https://wiki.archlinux.org/title/ClamAV#Creating_notification_popups_for_alerts

#!/bin/bash
PATH=/usr/bin
ALERT="Signature detected by clamav: $CLAM_VIRUSEVENT_VIRUSNAME in $CLAM_VIRUSEVENT_FILENAME"

# Send an alert to all graphical users.
for ADDRESS in /run/user/*; do
	USERID=${ADDRESS#/run/user/}
	/usr/bin/sudo -u "#$USERID" DBUS_SESSION_BUS_ADDRESS="unix:path=$ADDRESS/bus" PATH=${PATH} \
		/usr/bin/notify-send -w -u critical -i dialog-warning "Virus found!" "$ALERT"
done
```

```sh
sudo vim /etc/systemd/system/clamav-clamonacc.service
```

```
# clamonacc systemd service file primarily the work of ChadDevOps & Aaron Brighton
# See: https://medium.com/@aaronbrighton/installation-configuration-of-clamav-antivirus-on-ubuntu-18-04-a6416bab3b41#a340

[Unit]
Description=ClamAV On-Access Scanner
Documentation=man:clamonacc(8) man:clamd.conf(5) https://www.clamav.net/documents
Requires=clamav-daemon.service
After=clamav-daemon.service syslog.target network.target

[Service]
Type=simple
ExecStart=
ExecStart=/usr/sbin/clamonacc -F --fdpass --log=/var/log/clamav/clamonacc.log

[Install]
WantedBy=multi-user.target
```

```sh
# sudo mkdir /etc/systemd/system/clamav-clamonacc.service.d
# sudo chown clamav:clamav /var/log/clamav/clamonacc.log
sudo systemctl daemon-reload
sudo systemctl restart clamav-daemon.service
sudo systemctl enable --now clamav-clamonacc.service
```

### freshclam

```sh
sudo freshclam
sudo systemctl enable --now clamav-freshclam.service
```

### clamav-milter

```sh
sudo vim /etc/clamav/clamav-milter.conf
```

```
# https://wiki.archlinux.org/title/ClamAV#Using_the_milter

# Modify the following
MilterSocket /tmp/clamav-milter.socket
MilterSocketMode 660
FixStaleSocket yes
User clamav
MilterSocketGroup clamav
PidFile /run/clamav/clamav-milter.pid
TemporaryDirectory /tmp
ClamdSocket unix:/run/clamav/clamd.ctl
LogSyslog yes
LogInfected Basic
```

```sh
sudo vim /etc/systemd/system/clamav-milter.service
```

```
# https://wiki.archlinux.org/title/ClamAV#Using_the_milter

[Unit]
Description='ClamAV Milter'
After=clamav-daemon.service

[Service]
Type=forking
ExecStart=/usr/bin/clamav-milter --config-file /etc/clamav/clamav-milter.conf
Restart=Always

[Install]
WantedBy=multi-user.target
```

```sh
sudo systemctl enable --now clamav-milter.service
```

### Fangfrish

```sh
sudo mkdir -m 0770 -p /var/lib/fangfrisch
sudo chgrp clamav /var/lib/fangfrisch
su root
cd /var/lib/fangfrisch
python3 -m venv venv
source venv/bin/activate
```

```sh
pip install fangfrisch
```

```sh
vim /etc/fangfrisch.conf
```

```
# Minimal example configuration, meant for testing.

[DEFAULT]
db_url = sqlite:////var/lib/fangfrisch/db.sqlite
local_directory = /var/lib/clamav

[urlhaus]
enabled = yes
```

```sh
fangfrisch --conf /etc/fangfrisch/fangfrisch.conf initdb
# su <user>
# sudo /var/lib/fangfrisch/venv/bin/fangfrisch --conf /etc/fangfrisch.conf initdb
```

## Usage

```sh
# Test
curl https://secure.eicar.org/eicar.com.txt | clamscan -
```

```sh
# Scan a directory.
clamscan -r -i <dir>
```

```sh
# Scan a file with specified limits.
clamscan -v -a --max-filesize=1000M --max-scansize=1000M --alert-exceeds-max=yes <file>
```

[^1]: [ClamAV](https://wiki.archlinux.org/title/ClamAV)
[^2]: [\[SOLVED\] clamav-clamonacc won't start (easily)](https://bbs.archlinux.org/viewtopic.php?id=267222)