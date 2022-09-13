# DWS-Full-Node
Running a Full-Node and Validator Setup Guide
System Requirements
![image](https://user-images.githubusercontent.com/105454859/189886325-61dfca5a-81f2-4565-8af7-b54bfe15b32a.png)

1. Setup your environment
# Update the system
sudo apt update
sudo apt upgrade

# Install git, gcc and make
sudo apt install git build-essential ufw curl jq snapd --yes

# Install Go with Snap
sudo snap install go --classic

# Export environment variables
echo 'export GOPATH="$HOME/go"' >> ~/.profile
echo 'export GOBIN="$GOPATH/bin"' >> ~/.profile
echo 'export PATH="$GOBIN:$PATH"' >> ~/.profile
source ~/.profile

Step 0A - Run a fullnode / validator using the binaries
cd $HOME
wget https://github.com/deweb-services/deweb/releases/download/v0.3/dewebd
chmod +x dewebd
sudo mv dewebd /usr/local/bin/

Hardware Requirements
Here are the minimal hardware configs required for running a validator/sentry node

8GB RAM
4vCPUs
300GB Disk space

Software Requirements
Install deps
sudo apt-get install build-essential jq

Compile instructions: install GoLang

#First remove any existing old Go installation as root
sudo rm -rf /usr/local/go
#Download the software:
curl https://dl.google.com/go/go1.19.linux-amd64.tar.gz | sudo tar -C/usr/local -zxvf -
#Update environment variables to include go (copy everything and paste)
cat <<'EOF' >>$HOME/.profile
export GOROOT=/usr/local/go
export GOPATH=$HOME/go
export GO111MODULE=on
export GOBIN=$HOME/go/bin
export PATH=$PATH:/usr/local/go/bin:$GOBIN
EOF
source $HOME/.profile
#To verify that Go is installed:
go version

Compile dewebd source code by yourself
git clone https://github.com/deweb-services/deweb.git
cd deweb
git checkout v0.3
make build   #it build the binary in build/ folder
#To know the version:
build/dewebd version
#The output must be 0.3

#Is the version match, now you have two options
Move the binary to the /usr/local/bin path with: sudo mv build/dewebd /usr/local/bin/
Compile and install the binary in the $GOPATH path: make install




