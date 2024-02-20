# Infra-DevOps 레포지토리
Source > Build > Test > Production

DevOps Engineer ( 데브옵스 엔지니어 )
- CI/CD 소개
* Continuous Integration/ Continuous Delivery(Deployment)의 약자
    * 지속적 통합 - 메인 브랜치에 여러 작은 변화들을 자주 merging 하는 것
    * 지속적 배포 - 언제든지 빠르고 자주 안정적인 소프트웨어가 배포될 수 있는 환경
        * 배포 파이프라인
            * 플래닝
            * 코드 pull
            * 빌드
            * 테스트
            * 배포
            * 플래닝
        * 프로덕션에 서비스를 안정적으로 빠르게 배포하기 위해 거쳐야 할 단계들, 프로세스을 자동화 한 것
- CI/CD 자동화
- CI/CD Pipeline
    - Commit change ( 커밋 변경 사항 발행 )
    - Trigger build ( 빌드 트리거 )
    - Build ( 빌드 )
    - Notify of build outcome ( 빌드 결과 알림 )
    - Run test  ( 테스트 실행 )
    - Notify of test outcome ( 테스크 결과 알림 )
    - Deliver build to staging ( 빌드된 것을 스테이징에 전달 )
    - Deploy to production ( 프로덕션에 배포 )

Tools
1. Docker
2. Framework
3. Batch Pipeline
4. Setting Files
