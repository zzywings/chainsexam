
cd fabric-samples/first-network
../bin/cryptogen generate --config=./crypto-config.yaml

yum install -y tree

cd crypto-config/peerOrganizations/org1.example.com/peers/peer0.org1.example.com/msp/signcerts
cat peer0.org1.example.com-cert.pem
openssl x509 -in signcerts/peer0.org1.example.com-cert.pem -text
cd ../keystore/2dbd21b8a1...

byfn.sh generate -c mychannel
byfn.sh up -c mychannel -o solo -n


docker exec cli ./script/install.sh
docker exec cli ./script/invoke.sh
docker exec cli ./script/upgrade.sh

./byfn.sh up -o solo -n
docker logs peer0.org1.example.com --tail 30
 vi ./base/peer-base.yaml
 ./byfn.sh down
 docker logs peer0.org1.example.com --tail 30



