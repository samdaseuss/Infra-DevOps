# application.yml
스프링부트 프로젝트 작성 시 사용하기 편리하게 다양한 yml 애플리케이션 설정파일의 예시를 구성해놓은 리드미 문서입니다.
## batch job ( 배치 잡 )
```
spring:
    profiles:
        active: local
    batch:
        job:
            names: ${job.name:NONE}
```
* 로컬 프로파일을 기본적으로 액티브
* 배치 잡의 names를 지정하지 않으면 배치 프로그램에 있는 모든 배치 잡들이 실행됨
* NONE으로 설정하면 내가 파라미터로 준 배치 잡들만 실행

```
spring:
    config:
        activate:
            on-profile: local
    datasource:
        url: jdbc:mysql://127.0.0.1:3306/marketprice
        driver-class-name: com.mysql.cj.jdnc.driver
        username: root
        password:
    jpa:
        show-sql: true
        generate-ddl: false
        hibernate:
            ddl-auto: none
    batch:
        jdbc:
            initialize-schema: ALWAYS
```
* 로컬 프로파일이 active 되었을 떄 로컬을 사용
* 데이터소스 설정
* JPA 설정 ORM으로 JPA 사용
* 스프링 배치의 스키마를 초기화
    ** [참고] springboot batch 동작을 하기 위해선 `@EnableBatchProcessing` 어노테이션 필요