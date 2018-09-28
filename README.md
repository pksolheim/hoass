# hoass home assistant configuration


docker run -d --name="home-assistant" -v /home/pi/ha:/config -v /etc/localtime:/etc/localtime:ro --device /dev/zwave:/dev/zwave -p 8123:8123 homeassistant/raspberrypi3-homeassistant:0.76.2

docker start home-assistant
docker stop home-assistant
docker restart home-assistant
docker logs home-assistant


docker run -d --name=deconz --net=host --restart=always -v /home/pi/deconz:/root/.local/share/dresden-elektronik/deCONZ --device=/dev/ttyUSB0 marthoc/deconz