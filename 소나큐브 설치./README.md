# 소나큐브 설치
### 소나큐브 도커서버에서 도커이미지로 실행

## 볼륨생성 
    docker volume create --name sonarqube_data
    docker volume create --name sonarqube_logs
    docker volume create --name sonarqube_extensions

## 소나큐브 런
    docker run --rm \
        -p 9000:9000 \
        -v sonarqube_extensions:/opt/sonarqube/extensions \
        <image_name>   

## 소나큐브 실행
        docker run --rm \
                -e SONAR_HOST_URL=$SONAR_HOST_URL \
                -e SONAR_LOGIN=$SONAR_AUTH_TOKEN \
                -e SONAR_SCANNER_OPTS='-Dsonar.projectKey=sonar -Dsonar.java.binaries=./target -Dsonar.verbose=true' \
                -v /var/lib/docker/volumes/jenkins-volume/_data/workspace/project:/usr/src \
                   sonarsource/sonar-scanner-cli
           
# 설치 완료 후 localhost:9000 접속
        https://localhost:9000
