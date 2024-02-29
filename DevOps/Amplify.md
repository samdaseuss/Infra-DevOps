# Amplify 가이드

## CLI 설치
1. npm 이용해서 CLI를 설치한다.
```
npm install -g @aws-amplify/cli
```
2. 도움말 보는 방법
다음 명령어를 쓰면 커멘드 사용법을 볼 수 있음
```
amplify help
```

## 배포 STEP
1. Provision -- 프로비전
2. Build  -- 빌드
3. Test -- 테스팅
4. Deploy -- 디플로이
5. Verify -- 베리파이

## 주요 기능
* Stage가 몇 개 있는지 보여줌
    * production 환경 ( 메인브랜치 👀 )
    * cf. testing을 위한 환경 ( dev, sandbox 환경 )
* 가장 마지막으로 배포된 버전의 커밋 메시지 보여줌
    * Auto-build : 메인 브랜치에 커밋이 추가가 됐을 떄 자동으로 빌드를 시작
* 디버깅에 용이
* view build history

## 관련 문서
* https://docs.amplify.aws/javascript/tools/cli/