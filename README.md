# vMix-firstSteps
erste Tests - mein Einstieg in vMix
## SRT
Ich erzeuge im LAN auf einem Linux Rechner einen Teststream. Wichtig, ffmpeg ist hier im Modus "listener":  
```
targetServer="srt://0.0.0.0:9999?mode=listener&pkt_size=1316"
ffmpeg -r 30 -f lavfi -i testsrc -vf scale=1920:1080 -vcodec libx264 -profile:v baseline -pix_fmt yuv420p -f mpegts $targetServer
```
Meine Rechner, auf dem der SRT-Stream "liegt" hat die IP:
**
```
hostname -I
192.168.95.167
```
**
## vMix
VMix läuft auf einen Windows Rechner mit der **IP 192.168.95.122**.  
In vMix lege ich eine neue Quelle an. VMix ist im Modus "caller" und holt sich damit den Stream vom Linux Rechner.  

![SRT Einstellungen](https://github.com/richtertoralf/vMix-firstSteps/blob/6cc25a895d9174d04059e746f4fec6bfcfc7ae69/WhatsApp%20Image%202021-11-02%20at%2014.28.27.jpeg "SRT-settings")

>Achtung: In der Windows Firewall müssen die für SRT genutzten Ports explizit freigegeben werden. In diesem Fall der Port 9999 für UDP.

