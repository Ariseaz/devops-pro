# TO INSTALL JENKINS DOCKER ON UBUNTU INSTANCE/VM

To install jenkins docker on ubuntu VM

## Install docker

```
sudo apt install apt-transport-https ca-certificates curl software-properties-common -y
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
apt-get update
apt list --upgradable
sudo apt-get install -y docker-ce
usermod -aG docker ubuntu
systemctl restart docker
```


