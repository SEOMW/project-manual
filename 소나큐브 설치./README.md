/# 소나큐브 설치
### 소나큐브역시 도커서버에서 도커이미지로 실행

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
docker run -d --name sonarqube \
        -p 9000:9000 \
        -e SONAR_JDBC_URL=... \
        -e SONAR_JDBC_USERNAME=... \
        -e SONAR_JDBC_PASSWORD=... \
        -v sonarqube_data:/opt/sonarqube/data \
        -v sonarqube_extensions:/opt/sonarqube/extensions \
        -v sonarqube_logs:/opt/sonarqube/logs \
        <image_name>
