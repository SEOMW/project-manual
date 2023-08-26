# 도커 환경 구성
## 도커 서버
-Vagrant.configure("2") do |config|
    config.vm.define "dock" do |dock|
        dock.vm.hostname = "docker-registry"
        dock.vm.provider "virtualbox" do |vb|
            vb.name = "docker-registry"
            vb.cpus = 4 
            vb.memory = 6144
        end
        dock.vm.network "private_network", ip: "192.168.10.14"
        dock.vm.network "public_network", ip: "192.168.x.x" # 원하는 공개 네트워크 IP 주소 입력
    end
end

