# AWS Amplify 가이드

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

3. 리소스 유무 확인
인프라 관련 측면에서 `git diff` 버전이라고 보면 됨
```
amplify status
```
* `Current Environment`: staging, main 등

4. 환경 추가
```
amplify env add main
```

5. amplify env checkout staging
현재 바라보고 있는 환경을 스테이징으로 바꾸는 명령어로 git checkout으로 브랜치를 바꾸는 것과 비슷
```
amplify env checkout staging
```

6. amplify push
백엔드 리소스를 모두 빌드한 다음에 리모트에 푸쉬 -- Build all your local backend resources and provision it in the cloud.
```
amplify push
```

7. amplify publish
백엔드 & 프론트엔드 리소스 모두 배포
```
amplify publish
```


## 배포 환경 구축
### 로컬(콘솔) 배포
dev(데브) 환경의 리소스에 대해서는 콘솔에서 배포하도록 설정하는 것이 유용할 수 있다.

1. 루트 디렉토리로 이동 후 초기화
```
amplify init
```

2. 엡 Pull 받기
```
amplify pull --appId 앱 아이디
```
로컬에 있는 프로젝트를 리모트와 연동 -- 이미 있는 프로젝트이므로 로컬에 pull을 받으면 됨
* General에 앱에 대한 정보 들어있음
    * 앱 ARN : 아마존 리소스의 고유 번호 (아이디 값)

3. 로컬에서 pull을 받기 위한 access token 생성 (IAM 생성)
* 리소스가 있는 지역과 IAM 의 지역은 같야아함
```
amplify configure
```

4. 프로젝트 루트 폴더에서 다음 명령을 실행해 Amplify CLI를 사용하여 앱을 이 백엔드 환경에 연결
```
amplify pull --appId 앱 아이디 --envName staging
```

※ 만약 에러가 난다면, amplify 관련 디렉터리 지우기
```
rm -rf amplify/
```

4. api 추가하기
```
amplify add api
```

5. 배포
```
amplify push

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

## 폴더 구조
### 📁 amplify
#### 📄 .config
#### 📄 


## 관련 문서
* https://docs.amplify.aws/javascript/tools/cli/
* [Set up Amplify CLI](https://docs.amplify.aws/javascript/tools/cli/start/set-up-cli/#configure-the-amplify-cli)
* Amplify CLI를 이용한 벡엔드 골격 생성