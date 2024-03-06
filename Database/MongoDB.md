# Mongo DB (몽고디비)
몽고디비 검색해서 관련 항목 보기

```
docker search mongodb
```
* 여러 이미지 중 official이 Ok 되어있는 것이 몽고디비 공식이미지임

## 이미지 사용하기

1. 이미지 다운받기
```
docker pull mongo
```

2. 다운받은 이미지를 가지고 컨테이너를 통해서 실행시키기
```
docker run --name mongo-container -p 27017:27017 mongodb:latest
```

docker run --name `컨테이너 이름` -p `인바운드 포트 번호`:`아웃바운드 포트 번호` `몽고디비`:`버전`

* --name : 컨테이너 이름 지정
* -p 옵션 : 사용할 port 번호 설정 
    * 몽고디비 기본 포트로 설정 ex. -p 27017
    * 인바운드와 아웃바인드를 동일하게 설정 ex. -p 27017:27017
* 최신 버전은 latest