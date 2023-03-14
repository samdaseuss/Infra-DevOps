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
