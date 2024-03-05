# Elasticsearch
아래는 로컬/원격 환경에서 엘라스틱 서치를 사용하기 위한 방법을 다뤘다.
## 엘라스틱서치 설치 하기
### 로컬에 설치하기
아래 링크에서 원하는 버전과 해당하는 운영체제를 선택해 엘라스틱 서치를 머신에 설치한다.
https://www.elastic.co/kr/downloads/elasticsearch

### 도커로 설치하기
1. 도커 이미지 다운 받기
```
docker pull docker.elastic.co/elasticsearch/elasticsearch:<도커 버전>
```
예시
버전 7.10.1
```
docker pull docker.elastic.co/elasticsearch/elasticsearch:7.10.1
```
버전 8.8.1
```
docker pull docker.elastic.co/elasticsearch/elasticsearch:8.8.1
```

2. 네트워크 설정
컨테이너들끼리의 연결을 위한 네트워크를 만드는 작업 - 네트워크의 공유를 위해 사용
```
docker network create elastic
```

3. 도커 이미지 실행
```
docker run --name elasticsearch --net elastic -p 9200:9200 -p 9300:9300 -e "discovery.type=single-node" -e xpack.security.enbled=false -it docker.elastic.co/elasticsearch/elasticsearch:8.8.1
```
