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

------------------- Some changed config values: ---------------

LIBRESPOT_BITRATE="320"

------------------- Whole config: -----------------------------
# /etc/raspotify/conf -- Arguments/configuration for librespot

# A non-exhaustive list of librespot options and flags.

# Please see https://github.com/dtcooper/raspotify/wiki &
# https://github.com/librespot-org/librespot/wiki/Options
# for configuration details and a full list of options and flags.

# You can also find a full list with `librespot -h`.

# To avoid name collisions environment variables must be prepended with
# `LIBRESPOT_`, so option/flag `foo-bar` becomes `LIBRESPOT_FOO_BAR`.

# Invalid environment variables will be ignored.

# Raspotify defaults may vary from librespot defaults.
# Commenting out the environment variable will fallback to librespot's default
# unless otherwise noted.

# Flags are either on (uncommented) or off (commented),
# their values are otherwise not evaluated (but the "=" is still needed).

# Only log warning and error messages.
LIBRESPOT_QUIET=

# Automatically play similar songs when your music ends.
LIBRESPOT_AUTOPLAY=

# Disable caching of the audio data.
# Enabling audio data caching can take up a lot of space
# if you don't limit the cache size with LIBRESPOT_CACHE_SIZE_LIMIT.
# It can also wear out your Micro SD card. You have been warned. 
LIBRESPOT_DISABLE_AUDIO_CACHE=

# Disable caching of credentials.
# Caching of credentials is not necessary so long as
# LIBRESPOT_DISABLE_DISCOVERY is not set.
LIBRESPOT_DISABLE_CREDENTIAL_CACHE=

# Play all tracks at approximately the same apparent volume.
LIBRESPOT_ENABLE_VOLUME_NORMALISATION=

# Enable verbose log output.
#LIBRESPOT_VERBOSE=

# Disable zeroconf discovery mode.
#LIBRESPOT_DISABLE_DISCOVERY=

# Options will fallback to their defaults if commented out,
# otherwise they must have a valid value.

# Device name.
# Raspotify defaults to "raspotify (*hostname)".
# Librespot defaults to "Librespot".
#LIBRESPOT_NAME="Librespot"

# Bitrate (kbps) {96|160|320}. Defaults to 160.
LIBRESPOT_BITRATE="320"

# Output format {F64|F32|S32|S24|S24_3|S16}. Defaults to S16.
#LIBRESPOT_FORMAT="S16"

# Displayed device type. Defaults to speaker.
#LIBRESPOT_DEVICE_TYPE="speaker"

# Limits the size of the cache for audio files.
# It's possible to use suffixes like K, M or G, e.g. 16G for example.
# Highly advised if audio caching isn't disabled. Otherwise the cache
# size is only limited by disk space.
#LIBRESPOT_CACHE_SIZE_LIMIT=""

# Audio backend to use, alsa, pulseaudio or pipe. Defaults to alsa.
#LIBRESPOT_BACKEND="alsa"

# Username used to sign in with.
# Credentials are not required if LIBRESPOT_DISABLE_DISCOVERY is not set.
#LIBRESPOT_USERNAME=""

# Password used to sign in with.
#LIBRESPOT_PASSWORD=""

# Audio device to use, use `librespot --device ?` to list options.
# Defaults to the system's default.
#LIBRESPOT_DEVICE="default"

# Initial volume in % from 0 - 100.
# Defaults to 50 For the alsa mixer: the current volume.
#LIBRESPOT_INITIAL_VOLUME="50"

# Volume control scale type {cubic|fixed|linear|log}.
# Defaults to log.
#LIBRESPOT_VOLUME_CTRL="log"

# Range of the volume control (dB) from 0.0 to 100.0.
# Default for softvol: 60.0.
# For the alsa mixer: what the control supports.
#LIBRESPOT_VOLUME_RANGE="60.0"

# Pregain (dB) applied by volume normalisation from -10.0 to 10.0.
# Defaults to 0.0.
#LIBRESPOT_NORMALISATION_PREGAIN="0.0"

# Threshold (dBFS) at which point the dynamic limiter engages
# to prevent clipping from 0.0 to -10.0.
# Defaults to -2.0.
#LIBRESPOT_NORMALISATION_THRESHOLD="-2.0"

# The port the internal server advertises over zeroconf 1 - 65535.
# Ports <= 1024 may require root privileges.
#LIBRESPOT_ZEROCONF_PORT=""

# HTTP proxy to use when connecting.
#LIBRESPOT_PROXY=""



