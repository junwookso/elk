# ELK 서버 설정

Rootful 모드로 가동

### Podman Compose 설치
sudo dnf install -y python3-pip
sudo pip3 install podman-compose


## Elasticsearch 설정

### 사용자 비번 설정
- sudo podman-compose up -d elasticsearch
- sudo podman exec -it elasticsearch bin/elasticsearch-reset-password -u elastic
- 비밀번호를 .env 파일에 기록 ( 추후 로그인에 사용 )

## Kibana 설정

##### Dev
- 암호화 key 를 세개 생성 후 각각 .env (KIBANA_ENCRYPTION_KEY,XPACK_SECURITY_KEY,XPACK_REPORT_KEY) 에  저장
openssl rand -hex 32

- kibana_system 사용자 비밀번호를 .env 에 기록
sudo podman exec -it elasticsearch bin/elasticsearch-reset-password -u kibana_system

- sudo podman-compose up -d kibana logstash
- kibana 서비스 접속 ( https://localhost:5601/ )
- superuser 로 접근 ( elastic / 복사한 비밀번호 )