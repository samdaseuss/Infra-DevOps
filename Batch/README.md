# 배치 파이프라인
배치 프로그램을 머신에서 돌릴 떄 일정한 시간 주기에 따라서 동작하도록 하기 위해서 스케줄링 작업을 별도로 해줘야한다. 이에 몇 가지 방법을 제시하는 문서를 작성해본다.

## OS Scheduler
머신 내부의 OS 스케줄러를 통해 배치 프로그램을 실행하는 방법이다. 어떤 주기로 프로그램을 실행할지 OS 스케줄러에 등록하고 그 결과를 머신 내부의 log 파일로 남겨 확인할 수 있는 방법이다.
```
eg. crontab - 리눅스
```
### 장단점
#### 장점
* 개인적으로 배치 프로그램을 돌려보고 싶다면 간단하게 사용 가능하다.
#### 단점
* 하나의 머신에 종속되게 os 스케줄러를 사용하게 되면 스케줄링을 확인하기 어렵다.
* 많은 Job 들을 처리하기 힘들다. > 실무 사용 현실적으로 어려움

## Quartz Scheduler
쿼츠 스케줄러를 이용하는 방법입니다. 쿼츠 스케줄러라는 프레임워크와 스프링배치 프레임워크를 함께 사용해서 애플리케이션 개발하는 방식이랍니다. 배치 로직은 스프링 배치로 작성하고 쿼츠의 스케줄러를 통해서는 개발한 배치 로직을 트리거 하게끔 설정한다.

### 장단점
#### 장점
* 애플리케이션 내부에서 스케줄링을 하기 떄문에 배치의 실행이 빠르다.
#### 단점
* 결과를 보려면 admin을 따로 만들어줘야한다.

## Jenkins (젠킨스)
CI 프로그램인 젠킨스를 사용하는 방식입니다. 배치 프로그램을 만들고 스케줄링을 할 떄 젠킨스를 사용합니다. 현업에서 가장 많이 사용하는 방식이기도 합니다.
### 젠킨스
마스터에서 슬레이브로 명령을 전달해서 배치 프로그램을 실행시킵니다.
### 장단점
#### 장점
젠킨스 어드민에서 실행 결과 (로그)를 바로 볼 수 있기 떄문에 별도의 어드민을 만들거나 할 필요 없이 젠킨스의 기능을 사용하는 것 만으로도 충분하다.
#### 단점


## SCDF ( Spring Cloud Data Flow )