# Snyk Container 작동 방식

## 컨테이너 이미지란 무엇인가?

컨테이너 이미지는 OCI([Open Container Initiative](https://opencontainers.org)) 사양에 정의된 계층화된 파일 시스템 및 관련 메타데이터로 구성됩니다.

컨테이너 이미지는 종종 다음과 같은 타사 소프트웨어가 포함된 여러 레이어를 포함합니다.

* Debian, Ubuntu 또는 CentOS와 같은 운영체제 배포판
* npm, pip 및 RubyGems와 같은 애플리케이션 패키지 매니저

## Snyk Container가 감지하는 것

Snyk Container가 이미지를 스캔할 때 먼저 다음을 포함하여 이미지에 설치된 소프트웨어를 찾습니다.

* dpkg, rpm 및 apk 운영체제 패키지
* 관리되지 않는 일반적인 소프트웨어(패키지 매니저 외부에 설치됨)
* 매니페스트 파일의 존재를 기반으로 하는 애플리케이션 패키지

**Note:** Snyk이 파일 시스템에서 정보를 읽을 때 컨테이너를 실행할 필요가 없으므로, 성공적으로 스캔하기 위해 컨테이너나 외부 코드를 실행할 필요가 없습니다.

설치된 소프트웨어 목록을 확보한 후, 공용 소스 및 독점 연구를 결합한 취약점 데이터베이스와 대조하여 찾습니다.

## 지원하는 운영체제

다음을 기반으로 이미지의 취약점을 감지합니다.

* Alpine
* Debian
* Ubuntu
* CentOS
* UBI(Universal Base Image)를 포함한 RHEL(Red Hat Enterprise Linux)
* Amazon Linux
* Oracle Linux
* SUSE Linux Enterprise Server

특정 버전 지원은 [운영 체제 지원](https://docs.snyk.io/products/snyk-container/snyk-container-security-basics/supported-operating-system-distributions) 페이지를 확인하고, 모든 최신 업데이트에 대해서는 [업데이트](https://updates.snyk.io) 페이지를 확인하십시오.

{% hint style="info" %}
**Note:** Snyk은 Distroless 이미지와 같은 관련 패키지 매니저 없이 해당 배포판의 패키지를 사용하는 이미지도 지원합니다.
{% endhint %}

## 관리되지 않는 소프트웨어

업스트림 공급자의 일부 소프트웨어 구성 요소는 패키지 매니저를 사용하여 설치되지 않고 타사 실행 파일로 다운로드 됩니다. Snyk은 file fingerprinting을 사용하여 다음 구성 요소 버전을 탐지합니다.

* Node.js
* OpenJDK

## 반복 스캔

새로운 취약점이 지속적으로 공개되고 있습니다. 설치된 이미지 소프트웨어가 변경되지 않은 경우에도 Snyk은 이미지의 새로운 취약점에 대해 경고할 수 있습니다.

Snyk 서비스에 설치된 소프트웨어의 스냅샷을 저장하는 통합을 사용하여 이미지가 변경되지 않은 경우, Snyk Container는 이미지에 액세스하지 않고 자동으로 다시 스캔하여 새로운 취약점을 더 빨리 알려줍니다. 그러나 이미지가 변경된 경우 Snyk은 이미지에 액세스하여 이미지를 다시 스캔하기 전에 이미지를 pull 합니다.

{% hint style="info" %}
반복 스캔은 애플리케이션의 디펜던시에 대한 업데이트를 감지하지 못합니다. 반복 스캔은 애플리케이션을 가져올 때 애플리케이션 디펜던시의 스냅샷을 사용하여 새로운 취약점을 테스트하기만 합니다.\
\
업데이트된 디펜던시와 같은 애플리케이션의 변경 사항을 감지하려면 Snyk에서 컨테이너 이미지를 다시 가져오십시오.

다음은 이미지를 가져오는 방법에 대해서 [Snyk Container 시작하기](../getting-started-snyk-container.md)를 참조하십시오.
{% endhint %}

[container security](https://snyk.io/learn/container-security/)를 통해 자세한 내용을 확인할 수 있습니다.
