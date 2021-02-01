***Commands***

**stream video to dummy web cam device**
`ffmpeg -re -i <INPUT> -f v4l2 /dev/video2`

**concatenate audio files with ffmpeg**
`ffmpeg -f concat -safe 0 -i <INPUT FILE> -c copy output.wav`
<INPUT FILE> in form of 
`file '/dir/to/file'
file '/dir/to/file'
etc.`

**Compress wave file ffmpeg**
`ffmpeg -i <input> <output>`


**start the pihole docker**
**have to disable these because they are using the DNS ports (53 and 67)**
`sudo systemctl disable systemd-resolved
sudo systemctl stop systemd-resolved
sudo systemctl restart NetworkManager
docker container start pihole`

**Open bash in docker container**
`docker exec -ti <docker name> bash`

**turn DNS service on again**
`sudo systemctl enable systemd-resolved
sudo systemctl restart NetworkManager`

**VirtualBox make drive image from hard ware device**
`sudo VBoxManage internalcommands createrawvmdk -rawdisk <disk> -filename <output>`

**VirtualBox can't see USB devices (logout and back in if not then reboot)**
`sudo adduser $USER vboxusers`

**set volume above 100%**
`pactl -- set-sink-volume 0 <percent>%`

**Wake-On-LAN for server**
`sudo etherwake -i <interface> <macaddress>`

**Link file Linux (symbolic link)**
`ln -s </full/path/to/source> <dest>`

**Add folder to $PATH on Linux**
`export PATH="/new/path:$PATH"`
*to make permanent add line above to ~/.bashrc*

**Pipe terminal output to file**
`<COMMAND> > <OUTPUTFILE>`
*Append*
`<COMMAND> >> <OUTPUTFILE>`

**CRONTAB**
`crontab -e`
https://crontab.guru/

**Speedtest CLI**
`speedtest-cli`
`--csv` divide values by `<DOWNLOAD>/1000/1000` to get mbps

**Change pihole password**
`sudo pihole -a -p`

**Configure pihole to allow switch minecraft**
`pihole -a hostrecord mco.lbsg.net <SERVER IP>`
Or got to `<IP>/admin` Local DNS records
Add new Domain: `mco.lbsg.net`
Add new Ip Address: `<SERVER IP>`

**Set timezone Linux**

`sudo timedatectl set-timezone America/New_York`

**Change hostname Linux**

`hostnamectl set-hostname <hostname>`

Edit `/etc/hosts` and replace old host name with new one

**Login without password SSH**
Generate SSH key
`ssh-keygen -t rsa -b 2048`
Copy keys to target server
`ssh-copy-id <USERNAME>@<SERVERNAME>`

**Leave command running after logout**
`screen` - opens bash terminal, leave by Ctrl+A + d
`screen -ls` show open screens
`screen -r` resume screen
`screen -r <PID>` resume screen by PID
	**tmux version**
	`tmux` - opens bash terminal, leave by Ctrl+b + d
	`tmux ls` list open tmux
	`tmux attach -t <number>` attach to tmux instance

**Add basic system startup**
Add `<servicename>.service` file to `/etc/systemd/system`
	Basic `.service` file

```
[Unit]
Description=<description>
[Service]
ExecStart=<filepathtoscript>
[Install]
WantedBy=multi-user.target
```

`sudo systemctl start <servicename>` #starts the service
`sudo systemctl enable <servicename>` #adds to startup

**Start command at bootup in a screen instance, accessible by user**
`runuser -l <USER> -c 'screen -dm -S <sessionname> <command>'`

**CUPS info**
`lpstat -t`

**Save Ping output**
use to roughly target time frame of unexpected system outages
`ping -D -i 10 192.168.0.20 >> pinghist`

**Pretty print uptime alias**
`alias uptime = 'uptime -p'`

