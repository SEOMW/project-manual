# 도커 환경 구성
## 도커 서버 vagrant 구성
     Vagrant.configure("2") do |config|
        config.vm.define "dock" do |dock|
            dock.vm.hostname = "docker-registry"
            dock.vm.provider "virtualbox" do |vb|
                vb.name = "docker-registry"
                vb.cpus = 4 
                vb.memory = 6144
            end
            dock.vm.network "private_network", ip: "192.168.10.14"
        end
    end

## 도커 설치
     sudo apt-get update -y
     sudo apt-get install -y ca-certificates curl gnupg
     sudo install -m 0755 -d /etc/apt/keyrings
     curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
     sudo chmod a+r /etc/apt/keyrings/docker.gpg
     echo "deb [arch="$(dpkg --print-architecture)" signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
       "$(. /etc/os-release && echo "$VERSION_CODENAME")" stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
     sudo apt-get update -y
     sudo apt-get install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin
     sudo usermod -a -G docker vagrant
     docker login -u seomw --password-stdin < /kuber/env/docker_token

## 설치 완료후 젠킨스 메뉴얼(jenkins manual)로 이동


