# DASH-PI

Configuration files for the raspberry pi dashboards.

## Installation
### Files

packages.txt contains the installed debs (the result of `dpkg --get-selections > packages.txt`)

```
autostart		/etc/xdg/lxsession/LXDE/autostart
config.txt		/boot/config.txt
```

### Audio / Video
The Pi looks for an active connection on the HDMI connector during boot. If it finds one, it will try to set the correct video mode and switch the audio to HDMI out. When the Pi is 
connected to a HDMI-to-DVI converter the system guesses wrong. The output is hardcoded in `/boot/config.txt`.

To force the audio to the correct channel: (from http://raspberrypi.stackexchange.com/questions/44/why-is-my-audio-sound-output-not-working)

```
sudo amixer cset numid=3 <n>
```
where n is 0=auto, 1=headphones, 2=hdmi. If you are running Debian, try

```
cd /opt/vc/src/hello_pi/hello_audio
make
./hello_audio.bin
```
to test analogue output. And to test HDMI.

```
./hello_audio.bin 1
```

## TODO
 - Exchange ssh keys
 - Deploy with Chef, Puppet or Ansible 
