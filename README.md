
docker start home-assistant
docker stop home-assistant
docker restart home-assistant
docker logs home-assistant


Oppgradere:

docker stop home-assistant
docker rm home-assistant 
docker pull homeassistant/raspberrypi3-homeassistant:latest
docker run -d --name="home-assistant"  --net=host -v /home/pi/ha:/config -v /etc/letsencrypt/live/solheim.duckdns.org/fullchain.pem:/etc/letsencrypt/live/<url>/fullchain.pem -v /etc/letsencrypt/live/<url>/privkey.pem:/etc/letsencrypt/live/solheim.duckdns.org/privkey.pem  -v /etc/localtime:/etc/localtime:ro --device /dev/zwave:/dev/zwave -p 8123:8123 homeassistant/raspberrypi3-homeassistant


Deconz:
docker run -d --name=deconz --net=host --restart=always -v /home/pi/deconz:/root/.local/share/dresden-elektronik/deCONZ -e DECONZ_WEB_PORT=8080 -e DECONZ_WS_PORT=8443 --device=/dev/ttyUSB0 --dev=/dev/ttyUSB0  marthoc/deconz