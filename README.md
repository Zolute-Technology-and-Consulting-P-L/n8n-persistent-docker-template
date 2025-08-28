# n8n-persistent-docker-template
setup n8n as persistent on docker with ssl and nginx setup


steps

1. install docker
```
sudo apt-get install -y apt-transport-https ca-certificates curl software-properties-common
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc
echo   "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
$(. /etc/os-release && echo "${UBUNTU_CODENAME:-$VERSION_CODENAME}") stable" |   sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
apt-get update
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
```

2. generate SSL for the host
```
   openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout certs/n8n.key -out certs/n8n.crt -subj "/CN=set_hostname"
```
