# Raspberry Pi Spotify Connect - my setup
Raspberry Pi Spotify Connect with Cambridge Audio Azur 651A amplifier 

Follow this [nice tutorial](https://pimylifeup.com/raspberry-pi-spotify/) to install Raspotify (Librespot wrapper) on Raspberry PI.

sudo nano /etc/asound.conf

defaults.ctl.card 1
defaults.pcm.card 1
defaults.pcm.dmix.rate 48000
defaults.pcm.dmix.format S16_LE


speaker-test -c2 -l1

aplay -Dhw:1 --dump-hw-params /usr/share/sounds/alsa/Front_Right.wav

sudo systemctl restart raspotify
tail -f /var/log/syslog

aplay -l

sudo nano /etc/raspotify/conf
