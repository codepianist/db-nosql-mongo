docker run --name local-mongo -v /my/own/datadir:/data/db -e MONGO_INITDB_ROOT_USERNAME=root -e MONGO_INITDB_ROOT_PASSWORD=root -d mongo


## Start mongo
mongod
2018-05-26T14:35:53.313-0300 I CONTROL  [initandlisten] MongoDB starting : pid=6216 port=27017 dbpath=/data/db 64-bit host=cesar-f5
2018-05-26T14:35:53.313-0300 I CONTROL  [initandlisten] db version v3.6.5
2018-05-26T14:35:53.313-0300 I CONTROL  [initandlisten] git version: a20ecd3e3a174162052ff99913bc2ca9a839d618
2018-05-26T14:35:53.313-0300 I CONTROL  [initandlisten] OpenSSL version: OpenSSL 1.0.2g  1 Mar 2016
2018-05-26T14:35:53.313-0300 I CONTROL  [initandlisten] allocator: tcmalloc
2018-05-26T14:35:53.313-0300 I CONTROL  [initandlisten] modules: none
2018-05-26T14:35:53.313-0300 I CONTROL  [initandlisten] build environment:
2018-05-26T14:35:53.313-0300 I CONTROL  [initandlisten]     distmod: ubuntu1604
2018-05-26T14:35:53.313-0300 I CONTROL  [initandlisten]     distarch: x86_64
2018-05-26T14:35:53.313-0300 I CONTROL  [initandlisten]     target_arch: x86_64
2018-05-26T14:35:53.313-0300 I CONTROL  [initandlisten] options: {}
2018-05-26T14:35:53.313-0300 I STORAGE  [initandlisten] exception in initAndListen: NonExistentPath: Data directory /data/db not found., terminating
2018-05-26T14:35:53.313-0300 I CONTROL  [initandlisten] now exiting
2018-05-26T14:35:53.313-0300 I CONTROL  [initandlisten] shutting down with code:100


https://www.tecmint.com/install-mongodb-ubuntu-16-04-lts/

sudo apt-key adv --keyserver hkp://keyserver.ubuntu.com:80 --recv EA312927
sudo echo "deb http://repo.mongodb.org/apt/ubuntu xenial/mongodb-org/3.3 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-3.3.list
sudo apt-get update
sudo apt-get install -y --allow-unauthenticated mongodb-org
sudo vi /etc/systemd/system/mongodb.service 
Paste
```
[Unit]
Description=High-performance, schema-free document-oriented database
After=network.target
[Service]
User=mongodb
ExecStart=/usr/bin/mongod --quiet --config /etc/mongod.conf
[Install]
WantedBy=multi-user.target
```

mkdir -p /data/db

## Start
sudo systemctl start mongodb

## Test
sudo systemctl status mongodb

## Start at boot time
sudo systemctl enable mongodb


### Show database
`db`
