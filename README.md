# vMix-firstSteps
erste Tests - mein Einstieg in vMix
## SRT
Ich erzeuge im LAN auf einem Linux Rechner einen Teststream. Wichtig, ffmpeg ist hier im Modus "listener":  
```
targetServer="srt://0.0.0.0:9999?mode=listener&pkt_size=1316"
ffmpeg -r 30 -f lavfi -i testsrc -vf scale=1920:1080 -vcodec libx264 -profile:v baseline -pix_fmt yuv420p -f mpegts $targetServer
```
Meine Rechner, auf dem der SRT-Stream "liegt" hat die IP:
```
hostname -I
192.168.95.167
```
## vMix
VMix läuft auf einen Windows Rechner mit der **IP 192.168.95.122**.  
In vMix lege ich eine neue Quelle an. VMix ist im Modus "caller" und holt sich damit den Stream vom Linux Rechner.  
!(WhatsApp Image 2021-11-02 at 14.28.27.jpeg)
