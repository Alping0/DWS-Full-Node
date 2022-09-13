# DWS-Full-Node

# Overview

![image](https://user-images.githubusercontent.com/105454859/189886325-61dfca5a-81f2-4565-8af7-b54bfe15b32a.png)

# Setup your environment
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


# Hardware Requirements

Here are the minimal hardware configs required for running a validator/sentry node

8GB RAM

4vCPUs

300GB Disk space

# Software Requirements

#Install deps

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

# Validator Setup Guide

# Step 1 - Run a fullnode / validator using the binaries

cd $HOME

wget https://github.com/deweb-services/deweb/releases/download/v0.3/dewebd

chmod +x dewebd

sudo mv dewebd /usr/local/bin/

# Step 2 - Setting up the connection

#Set the chain-id parameter

dewebd config chain-id deweb-testnet-2

#Create a wallet: You may create a wallet with one or more keys (addresses) using dewebd; you can choose a name of your own liking (we strongly advice you use one word)

    dewebd keys add MyFirstAddress

      name: MyFirstAddress
      
      type: local
      
      address: deweb1q6wt62l9r4zef7nj97j5xe7q553j7nsllwrmqe
      
      pubkey: '{"@type":"/cosmos.crypto.secp256k1.PubKey","key":"ArhjQuNzZ+lSpIK9RrXK2da2PKAm7A3zpxTMHQnc/v+J"}'
      
      mnemonic: ""


      **Important** write this mnemonic phrase in a safe place.
      
      It is the only way to recover your account if you ever forget your password.
      

      giant favorite breeze resemble kitten surprise palm way jelly version use lucky pony depart napkin favorite slender normal grace always swarm funny hen cage
      
#Initialize the folders: 

change Moniker by your validator name (use quotes for two or more separated words "Royal Queen Seeds")
      





