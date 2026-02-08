# Host O/S Monitoring

- GPG key 등록
sudo rpm --import https://artifacts.elastic.co/GPG-KEY-elasticsearch

- repository 등록
cp ../setting/elastic.repo /etc/yum.repos.d/elastic.repo

-metric beat 설치
dnf install metricbeat

- 시스템 모듈 활성화
metricbeat modules enable system

- /etc/metricbeat/metricbeat.yml 등록
cp setting/os-metricbeat.yml /etc/metricbeat/metricbeat.yml

- metricbeat 서비스 시작
sudo systemctl enable metricbeat
sudo systemctl start metricbeat
sudo systemctl status metricbeat

- 대시보드 설치
- metricbeat setup --dashboards