# 프로젝트 세부 정보 및 테스트 결과 확인

모니터링하기 위해 가져온 모든 워크로드는 Kubernetes 아이콘이 표시된 프로젝트 페이지에 나타납니다.

![Kubernetes icon](../../../../.gitbook/assets/uuid-24e0b69a-01c3-9434-9dac-9b44864bd269-en.png)

워크로드 테스트 결과를 보고 작업하려면 다음과 같이 진행합니다.

* **Projects** 페이지로 이동하여 Kubernetes 프로젝트에 대해서만 필터링합니다.

![](../../../../.gitbook/assets/uuid-08d7978e-0c64-a8c2-c289-402534ebec42-en.png)

확인하려는 항목을 펼칩니다.

* 워크로드에 사용하는 개별 이미지 목록입니다.
* 각 이미지의 취약점 수를 요약합니다.

이미지 기록을 포함하여 이미지에 대한 취약점을 자세히 확인하려면 이미지 이름을 클릭합니다. 선택한 이미지에 대한 프로젝트 세부 정보 페이지가 나타납니다.

![](<../../../../.gitbook/assets/image (59) (2) (3) (3) (3) (3) (4) (5) (5) (5) (4) (1) (1) (1).png>)

* 워크로드의 구성의 보안 상태에 대한 세부 정보와 함께 워크로드의 모든 이미지에 있는 취약점의 집계 목록을 확인하려면 워크로드 링크를 클릭합니다. 프로젝트 세부 정보 페이지는 다음 예제와 비슷합니다.

![](../../../../.gitbook/assets/uuid-79e06589-b59c-4bad-30e4-56c0e15607e0-en.png)

현재 다음 속성에 대해 워크로드 구성을 테스트합니다.

| **Snyk parameter**     | **Associated Kubernetes parameters**         | **Description**                                                                                                                       |
| ---------------------- | -------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------- |
| CPU and Memory limits  | Resources.limits.memory resources.limits.cpu | 컨테이너에 사용할 수 있는 예상 CPU 및 메모리를 제한하면 작동 및 보안상의 이점이 존재합니다. 보안 측면에서는 잠재적인 서비스 거부 공격이 노드 및 잠재적으로 전체 클러스터가 아닌 애플리케이션에 미치는 영향을 제한합니다.         |
| runAsNonRoot           | securityContext.runAsNonRoot                 | 기본적으로 컨테이너는 루트 사용자로 실행할 수 있습니다. 이 속성은 컨테이너 런타임에서 이를 방지하며, 이는 공격자가 컨테이너 컨텍스트에서 명령어를 실행할 수 있는 경우에만 제한된 권한을 갖게 됩니다.                      |
| readOnlyRootFilesystem | securityContext. readOnlyFilesystem          | 기본적으로 컨테이너에 마운트된 파일 시스템은 쓰기가 가능합니다. 즉, 컨테이너를 손상시키는 공격자는 디스크에 쓰기가 가능하므로 특정 종류의 공격이 더 쉬워집니다. 컨테이너가 비저장 상태인 경우 쓰기 가능한 파일 시스템이 필요하지 않습니다. |
| Capabilities           | securityContext.capabilities                 | 낮은 수준에서 리눅스 기능은 컨테이너의 다양한 프로세스(디스크에 쓰기 가능, 네트워크를 통한 통신 가능)를 제어합니다. 모든 기능을 삭제하고 필요한 기능을 추가하는 것은 가능하지만 기능 목록을 먼저 이해해야 합니다.              |
