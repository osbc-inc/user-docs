# 초기 설정

이 모듈에서는 간단한 대표적인 Pipeline을 사용하여 Bitbucket Pipelines에서 컨테이너 이미지를 빌드하고 배포합니다. 이러한 유형의 작업은 개발 팀이 일상적인 CI/CD Pipeline에서 사용하는 몇 가지 단계와 Snyk를 사용하여 파이프라인 작업을 보강하는 방법을 에뮬레이트합니다. 워크샵의 이 부분을 위해 Bitbucket 및 AWS에서 일부 항목을 구성해야 합니다.

우리가 따르는 순서는 한 곳에서 다른 곳으로 정보를 복사해야 하기 때문에 화면 사이를 탐색해야 합니다. 필요한 정보를 식별하여 해당 프로세스를 안내해 드리겠습니다.

* AWS ECR 구성
* Bitbucket Pipeline 활성화
* 저장소 변수 추가

다음 섹션에서 각각에 대해 설명합니다.
