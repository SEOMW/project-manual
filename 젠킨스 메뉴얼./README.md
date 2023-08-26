# 젠킨스 설치&실행
### 젠킨스는 도커서버에서 도커로 진행

## 젠킨스 런

    docker run -itd -p 8080:8080 --name jenkins \
        -v jenkins-volume:/var/jenkins_home/ \
        -v /var/run/docker.sock:/var/run/docker.sock \
        -v $(which docker):/usr/bin/docker \
        --group-add 998 jenkins/jenkins:2.387.2-lts

## 젠킨스 실행을 위한 ngrok 실행

### 기존 도커이미지 확인-정지-삭제
    docker pull tomcat:10.0-jdk17
    docker run -itd -p 8888:8080 --name tomcat tomcat:10.0-jdk17
    docker cp /vagrant/spring-cicd-v1.0.0.war tomcat:/usr/local/tomcat/webapps/
    curl http://localhost:8888/spring-cicd-v1.0.0/
    
### 다른 터미널에서 ngrok 접속
    ngrok http 8080

## 젠킨스 접속후 첫 세팅을 위한 소스확인
        docker exec -t jenkins /bin/bash -c "cat /var/jenkins_home/secrets/initialAdminPassword"
        curl -fsSL https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key | sudo tee \
             /usr/share/keyrings/jenkins-keyring.asc > /dev/null

# 로그인 확인

    
