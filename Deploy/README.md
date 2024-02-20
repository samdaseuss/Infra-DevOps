# Deploy
## 환경분리
프로덕션에 나가기 전에 거치는 비슷한 환경의 테스트 환경
* 스테이지
* 메인
* 샌드박스
* 데브환경

### Main
* 외부 사용자에게 노출될 실제 production 환경
* main 브랜치와 연동
* 독립된 데이터베이스와 서버 호스팅

### Staging
* Production과 비슷한 테스트 환경
* staging 브랜치와 연동
* 독립된 데이터베이스와 서버 호스팅

## 배포 프로세스
1. Staging에서 테스팅
2. Main(Prod)에 배포할 준비가 되었다면, 다음을 실행한다.
* (1) Git: main 브랜치에 푸시
* (2) Amplify(예시)에 의해 배포 시작
    * 1. provision code
    * 2. build
    * 3. deploy
    * 4. verify
