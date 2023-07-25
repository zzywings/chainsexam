cd /usr/local/
wget https://nodejs.org/dist/v8.11.4/node-v8.11.4-linux-x64.tar.xz
tar xvf node-v8.11.4-linux-x64.tar.xz
mv node-v8.11.4-linux-x64 nodejs
ln -s /usr/local/nodejs/bin/node /usr/bin/node
ln -s /usr/local/nodejs/bin/npm /usr/bin/npm
npm config set registry http://registry.npm.taobao.org
apt install node-gyp
apt install docker-ce

git clone git://github.com/caohuilong/Hyperledger-caliper
cd Hyperledger-caliper
npm install 
sudo npm install fabric-ca-client@1.1.0 fabric-client@1.1.0
sudo npm install grpc@1.10.1

node ./benchmark/simple/main.js

「已修改
vim ./src/fabric/e2eUtils.js (修改12000为48000) (修改60000为300000)

vim ./node_modules/fabric-client/config/default.json(45000改为120000)

node ./benchmark/simple/main.js

sudo apt-get install -y apt-transport-https ca-certificates curl software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg |sudo apt-key add -
sudo apt-key fingerprint )EBFCD88
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
sudo apt-get update
sudo apt-get install -y docker-ce
systemctl start docker
sudo apt-get install python-pip
sudo pip install docker-compose
』

















