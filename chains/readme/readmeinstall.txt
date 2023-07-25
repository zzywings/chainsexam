yum install git unzip yum-utils -y
#git clone https://github.com/hyperledger/fabric-samples.git
cd fabric-samples
git checkout v1.4.3

#wget http://github.com/hyperledger/fabric/releases/download/v1.4.3/hyperledger-fabric-linux-amd64-1.4.3.tar.gz
#tar -zxvf hyperledger-fabric-linux-amd64-1.4.3.tar.gz

yum-config-manager --add-repo https://mirrors.tuna.tsinghua.edu.cn/docker-ce/linux/centos/docker-ce.repo
yum install -y yum-utils docker-ce  docker-ce-cli containerd.io

vim /etc/docker/daemon.json
{
	"registry-mirrors":["http://docker.mirrors.ustc.edu.cn"]
}
systemctl start docker


mv docker-compose-linux /usr/local/bin/docker-compose

docker pull hyperledger/fabric-peer:1.4
docker pull hyperledger/fabric-orderer:1.4
docker pull hyperledger/fabric-tools:1.4
docker tag hyperledger/fabric-peer:1.4 hyperledger/fabric-peer:latest
docker tag hyperledger/fabric-orderer:1.4 hyperledger/fabric-orderer:latest
docker tag hyperledger/fabric-tools:1.4 hyperledger/fabric-tools:latest

./byfn.sh up -o solo -n 

docker ps

docker pull hyperledger/fabric-couchdb:0.4.10

docker tag hyperledger/fabric-couchdb:0.4.10 hyperledger/fabric-couchdb:latest

cd /fabric-sample/first-network

./byfn.sh up generate

docker-compose -f docker-compose-cli.yaml -f docker-compose-couch.yaml up -d 



