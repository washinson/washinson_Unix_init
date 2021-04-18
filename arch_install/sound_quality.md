Т.к. сейчас перехал на `pipewire`, то как его настраивать понятий не имею, методом тыка и поверхностного знания `pulseaudio` увеличил качество так:

```
/etc/pipewire/pipewire-pulse.conf
/etc/pipewire/media-session.d/alsa-monitor.conf
/etc/pipewire/media-session.d/bluez-monitor.conf
```
выставить 
```
resample.quality = 10
```
