# DevOps
* Development + Operation의 합성어
* 소프트웨어 개발에서 배포까지
* 전달(delivery) 과정을 자동화하고 빠르게 하여 결국에는 비즈니스의 가치를 높일 수 있도록 하기 위한 개발 환경이나 문화

# AWS Amplify
모바일/웹 어플리케이션을 빠르게 구성+빌드+배포+운영까지 모든 라이프사이클을 한 곳에서 관리할 수 있도록 통합해둔 AWS의 풀스택 개발 통합 솔루션 서비스
* Admin UI 제공
* 서비스 모니터링
* 배포 모니터링

[장점]
* AWS 서비스와의 연동이 간편
* 인증(Cognito) - 로그인, 회원가입, 추가 인증 등
* 서비스 모니터링/로깅(CloudWatch)
* 데이터베이스 (DynamoDB, Aurora, GraphQL 지원)
* 앱 푸시 알림(PinPoint)
* CLI(Command Line Interface)으로 할 수 있는 것들이 매우 많다!
* 프론트엔드 초기 프로젝트 셋업(React, Vue, Angular, Next.js 등 지원)
* 백엔드 프로젝트 셋업 (node.js 지원)
* DB 스키마 설정 가능
* RESTful API 기본 코드셋도 제공
* DB와의 연동도 이미 되어있음
* 배포
* 커맨드 하나면 배포 끝!
* 웹 호스팅 추가
* 별도로 웹 서버 셋팅을 요구하지 않는다. 커맨드 하나면 호스팅 추가 가능. 뒷단의 웹 서버 관리는 AWS가 알아서 해준다.
* 서비스 배포
* 배포 모니터링, 로깅이 잘 되어있어, 배포가 실패할 경우 왜 실패했는지 디버깅 하기 용이
* 깃허브와 연동할 수 있어서 main 브랜치에 푸시 하는 것으로 배포 프로세스 시작 가능
* 프론트엔드와 백엔드 코드를 한 레포지터리 내에서 관리 가능
    * 그럼에도 벡엔드와 프론트엔드 분리 배포 가능
    * 디자인 툴 Figma와 연동하여 Figma 내 컴포넌트를 리액트 컴포넌트화 할 수 있음
* CloudFormation을 이용한 인프라 관리
* Infrastructure as code 서비스의 한 종류
* AWS resource를 관리하기 위한 template file
* 예시 template
```
{
    "Description": "DynamoDB resource",
    "AWSTemplateFormatVersion": "2010-09-09",
    "Parameters": {
        "partitionKeyName": {
            "Type": "String"
        },
        "partitionKeyType": {
            "Type": "String"
        },
        "env": {
            "Type": "String"
        },
        "tableName": {
            "Type": "String"
        }
    },
    "Resources": {
        "DynamoDBTable": {
            "Type": "AWS::DynamoDB::Table",
            "Properties": {
                "KeySchema": [
                    {
                        "AttributeName": "guid",
                        "KeyType": "HASH"
                    }
                ],
                "AttributeDefinitions": [
                    {
                        "AttributeName":"guid",
                        "AttributeType":"S"
                    }
                ],
                "GlobalSecodaryIndexes": [],
                "ProvisionedTroughput": {
                    "ReadCapacityUnits": 5,
                    "WriteCapacityUnits": 5
                },
                "StreamSpecification": {
                    "StreamViewType": "NEW_IMAGE"
                },
                "TableName": {
                    "Fn::If": [
                        "ShouldNotCreateEnvResources",
                        {
                            "Ref": "tableName"
                        },
                        {
                            "Fn::Join": [
                                "",
                                [
                                    {
                                        "Ref": "tableName"
                                    },
                                    "_",
                                    {
                                        "Ref": "env"
                                    }
                                ]
                            ]
                        }
                    ]
                }
            }
        }
    },
    "Outputs": {
        "Name": {
            "Value": {
                "Ref": "DynamoDBTable"
            }
        },
        "Arn": {
            "Value": {
                "Fn::GetAtt": [
                    "DynamoDBTable",
                    "Arn"
                ]
            }
        },
        "StreamArn": {
            "Value": {
                "Fn::DetAtt": [
                    "DynamoDBTable",
                    "StreamArn"
                ]
            }
        },
        "PartitionKeyName": {
            "Value": {
                "Ref": "partitionKeyName"
            }
        },
        "PartitionKeyType": {
            "Value": {
                "Ref": "partitionKeyType"
            }
        },
        "Region": {
            "Value": {
                "Ref": "AwS: Region"
            }
        }
    }

}

```

* 트랙킹하기 쉬운 형태

# React
* 사용자 인터페이스를 만들기 위한 JavaScript 라이브러리
* 특징
    * 선언형
        * 어플리케이션의 각 상태에 대한 뷰(view)만 설계하면 됨
        * 상태가 달라짐에 따라 React 가 알아서 필요한 컴포넌트만 업데이트하여 렌더링
    * 컴포넌트 기반
        * 스스로 상태를 관리하는 캡슐화된 컴포넌트
        * 컴포넌트를 통해 UI를 재사용 가능한 개별적인 여러 조각으로 나눔.
        * 컴포넌트 간 조합 가능 -> 복잡한 UI 도 구현 가능
        * 외부에서 주어지는 인풋인 props, 내부에서 관리하는 상태인 state로 이루어짐