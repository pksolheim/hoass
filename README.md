1. Installere raspbian
https://www.raspberrypi.org/learning/software-guide/quickstart/

2. Sette opp diverse
https://www.bouvet.no/bouvet-deler/utbrudd/building-a-motion-activated-security-camera-with-the-raspberry-pi-zero

3. INstallere docker

4. Sette opp home assistant og zwave
https://snillevilla.se/styr-dina-z-wave-enheter-med-home-assistant-och-aeon-z-stick/

5. Installere home assistant med docker

6. Sette op zigbee etc
https://snillevilla.se/styr-ikea-tradfri-lampor-i-home-assistant-med-conbee/

9. Last inn configen fra github. 

7. Importere alle lys med riktig navn på nytt.

8. Importer alle zwave komponenter og gi de riktig navn.

9. Systemd autostart
# hoass home assistant configuration


docker run -d --name="home-assistant" -v /home/pi/ha:/config -v /etc/localtime:/etc/localtime:ro --device /dev/zwave:/dev/zwave -p 8123:8123 homeassistant/raspberrypi3-homeassistant:0.76.2

docker start home-assistant
docker stop home-assistant
docker restart home-assistant
docker logs home-assistant


Oppgradere:

docker stop home-assistant
docker rm home-assistant 
docker pull homeassistant/raspberrypi3-homeassistant:latest
docker run -d --name="home-assistant" -v /home/pi/ha:/config -v /etc/localtime:/etc/localtime:ro --device /dev/zwave:/dev/zwave -p 8123:8123 homeassistant/raspberrypi3-homeassistant


Deconz:
docker run -d --name=deconz --net=host --restart=always -v /home/pi/deconz:/root/.local/share/dresden-elektronik/deCONZ -e DECONZ_WEB_PORT=8080 -e DECONZ_WS_PORT=8443 --device=/dev/ttyUSB0 --dev=/dev/ttyUSB0  marthoc/deconz