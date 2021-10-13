before start container:

sysctl -w vm.max_map_count=262144

start container

cd ./docker

docker-compose up -d --build --force-recreate