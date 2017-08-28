# Docker

Criação dos conteiners Couchpotato, Sickrage, Transmission

docker create \
	--name=couchpotato \
	-v /mnt/container_conf/couchpotato/config:/config \
	-v /mnt/torrent/movies:/downloads \
	-v /mnt/torrent/movies:/movies \
	-e PGID=0 -e PUID=0  \
    -e TZ=America/Sao_Paulo \
    -e UMAS_SET=022 \
	-p 5050:5050 \
    --restart unless-stopped \
	linuxserver/couchpotato

docker create --name=sickrage \
-v /mnt/container_conf/sickrage/config:/config \
-v /mnt/downloads:/downloads \
-v /mnt/torrent/seriados:/tv \
-e PGID=0 -e PUID=0 \
-e TZ=America/Sao_Paulo \
-p 8081:8081 \
linuxserver/sickrage


docker create --name=transmission \
-v /mnt/vms/container_conf/transmission:/config \
-v /mnt/vms/torrent:/downloads \
-v /mnt/vms/downloads:/watch \
-v /mnt/vms/torrent/movie:/movie \
-e PGID=0 -e PUID=0 \
-e TZ=America/Sao_Paulo \
-p 9091:9091 -p 51413:51413 -p 51413:51413/udp \
--restart unless-stopped \
linuxserver/transmission
