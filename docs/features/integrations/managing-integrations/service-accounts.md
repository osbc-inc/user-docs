# 서비스 계정

실제 Snyk 사용자 토큰을 사용하지 않고도 CI(지속적 통합) 및 기타 자동화 용도로 사용할 서비스 계정을 설정할 수 있습니다. 서비스 계정은 연결된 API 토큰만 있는 특수한 시스템 사용자 유형으로 표준 사용자 인증 정보를 대체합니다. 이 토큰을 사용하여 개발 도구와의 통합을 설정하고 CLI 및 API를 사용할 때 Snyk 계정에 액세스하기 위한 인증 정보를 제공합니다. API에 대한 자세한 내용은 [API 문서](../../snyk-api-info/)를 참조하십시오.

조직 또는 그룹 수준에서 단일 또는 여러 토큰을 생성하여 통합을 관리할 수 있습니다. 그룹 수준 토큰을 사용하여 그룹 내 모든 조직에 대한 그룹 API endpoint, 조직 API endpoint 및 CLI에 액세스할 수 있습니다.

각 서비스 계정에는 인식하기 쉽도록 연결된 고유한 이름이 있습니다. 이름은 조직에서 중복되어 존재할 수 없으며 재사용할 수 없습니다.

서비스 계정 토큰을 사용하여 다음 작업을 수행할 수 있습니다.

* 통합을 개별적으로 관리하기 위한 여러개의 토큰 생성
* 직원이 Role을 변경하거나 Snyk 계정을 닫는 경우에도 원활한 통합을 보장합니다.

{% hint style="info" %}
Role은 그룹 수준의 서비스 계정에만 해당되며 유료 계정에만 해당됩니다.
{% endhint %}

{% hint style="info" %}
서비스 계정은 GitHub Enterprise 통합에 사용할 수 있습니다. 팀이 GitHub에서 서비스 계정을 설정해야 하는 경우 GitHub Enterprise 통합으로 설정해야 합니다. GHE는 Snyk Enterprise 계정을 통해서만 사용할 수 있습니다.
{% endhint %}

## 서비스 계정 설정

조직 또는 그룹 수준에서 단일 또는 여러 토큰을 생성하여 통합을 관리합니다.

### 전제 조건

**기능 사용 여부**\
이 기능은 Enterprise plan에서 사용할 수 있습니다. 자세한 내용은 [pricing plans](https://snyk.io/plans/)를 참조하십시오.

그룹 서비스 계정을 만들려면 그룹 관리자여야 합니다. 조직 서비스 계정을 만들려면 조직 관리자 또는 그룹 관리자여야 합니다.

이 프로세스에서는 모든 옵션을 설명합니다.

## 서비스 계정 설정 방법

* 계정에 로그인하고 관리할 관련 그룹 및 조직으로 이동합니다.
* 기존 서비스 계정과 해당 세부 정보를 확인하려면 settings ![](../../../.gitbook/assets/cog\_icon.png) > **Service accounts**를 클릭하십시오.
* **Create a service account**를 클릭하여 새로운 계정을 생성합니다. 화면은 그룹 또는 조직 중 어느 쪽을 선택했는지에 따라 다르게 나타납니다.

![](../../../.gitbook/assets/uuid-115442e7-a8bd-44df-43f8-8867a4cdc6ba-en.png)

![](../../../.gitbook/assets/uuid-632ed37e-ed7a-519d-dade-a245a35e6ac6-en.png)

* **Service Account**에 토큰 명을 입력합니다. 토큰 명은 조직 또는 그룹별로 동일한 영역의 토큰에 한 번만 사용할 수 있습니다.

![](../../../.gitbook/assets/uuid-01c4cc98-23c9-3cb1-4972-1aa4f83ad98e-en.png)

* **Role** 목록에서 **Viewer** 또는 **Admin**을 선택하여 토큰의 범위를 구성합니다.
  * Viewer는 읽기 전용 액세스를 활성화합니다.
  * Admin은 전체 관리자 액세스를 활성화합니다.
*   **Create**를 클릭합니다. 토큰은 다음과 유사한 동일한 영역에서 생성 및 표시됩니다.

    이 토큰은 다시 볼 수 없으므로 반드시 복사하십시오. 토큰을 복사한 후 **Close 및 Hide**를 클릭할 수 있습니다. 어느 쪽이든 이 페이지에서 벗어나면 더 이상 액세스할 수 없습니다. 이는 토큰을 안전하게 보호하기 위한 보안 표준입니다. 다음 이미지와 유사한 **기존 서비스 계정** 목록에도 새로운 토큰이 추가됩니다.

![](<../../../.gitbook/assets/spaces\_-MdwVZ6HOZriajCf5nXH\_uploads\_git-blob-61a8f06ca370909c1292d121c731849f7c68b9fb\_uuid-799b88fc-d1d7-72c9-5ceb-30fb2a8d572e-en (3) (3) (3) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (12) (2) (2).png>)

* 또한 **관리자** Role로 전체 그룹에 대한 토큰을 생성한 경우 **그룹** 수준에서만 편집할 수 있지만 각 조직의 **기존 서비스 계정** 목록에도 토큰이 표시됩니다.

![](../../../.gitbook/assets/uuid-1110723e-74e7-3090-3e69-da65f93acfcc-en.png)

* 그룹에 속한 조직에서 토큰을 생성한 경우 그룹 수준의 **기존 서비스 계정** 목록에도 토큰이 나타나며 그룹 관리자가 토큰 이름을 변경하거나 삭제할 수도 있습니다.

![](../../../.gitbook/assets/uuid-50563edb-6a75-9f37-2040-cd814fdf9ead-en.png)

* 서비스 계정 토큰의 이름을 업데이트하려면 링크를 클릭합니다. 그룹 레벨의 경우 그룹 레벨의 경우에만 적용되며, 조직 레벨의 경우 관련 조직 및 그룹 레벨에 적용됩니다.

![](../../../.gitbook/assets/uuid-b34e3d10-bb0c-b608-bc08-12f2bf0a4fc0-en.png)

* 이 단계를 반복하여 동일하거나 다른 조직 또는 그룹에 대해 여러 개의 토큰을 작성합니다.

## 서비스 계정 편집 및 삭제

관리자는 토큰 이름을 변경하고 토큰을 삭제할 수 있습니다. 서비스 계정을 삭제하면 서비스 계정과 연결된 API 토큰이 즉시 무효화됩니다. 계정을 그룹으로 관리하는 경우 조직 및 그룹 관리자는 조직의 토큰을 삭제할 수 있습니다. 그룹 관리자만 그룹 수준에서 토큰을 확인하고 관리할 수 있습니다. 서비스 계정을 삭제하는 것은 API 토큰을 삭제하는 것과 같습니다.

## 서비스 계정 편집 및 삭제 방법

*   계정에 로그인하고 관리할 관련 그룹 및 조직으로 이동합니다.

    그룹 토큰의 경우 그룹 수준으로 이동합니다. 조직 토큰의 경우 그룹 관리자는 그룹 또는 관련 조직에서 삭제할 수 있습니다. 조직 관리자는 관련 조직으로 이동해야 합니다.
* settings ![](../../../.gitbook/assets/cog\_icon.png) > **Service accounts**를 클릭합니다.
* 스크롤하여 기존 서비스 계정 목록을 찾습니다.

![](<../../../.gitbook/assets/spaces\_-MdwVZ6HOZriajCf5nXH\_uploads\_git-blob-61a8f06ca370909c1292d121c731849f7c68b9fb\_uuid-799b88fc-d1d7-72c9-5ceb-30fb2a8d572e-en (3) (3) (3) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (1) (12) (2).png>)

* 기존 토큰 목록에서 다음 작업을 수행합니다.
  * 토큰을 삭제하고 즉시 무효화하려면 **Delete**를 클릭합니다. 메시지가 나타나면 **OK**를 클릭합니다.삭제 후 동일한 토큰을 다시 생성할 수 없습니다!
  * 토큰 이름을 클릭하여 토큰 이름을 변경하고 **Save**를 클릭합니다.
