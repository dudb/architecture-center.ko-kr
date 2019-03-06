---
title: 대기업 – 리소스 일관성 개선
titleSuffix: Microsoft Cloud Adoption Framework for Azure
ms.service: architecture-center
ms.subservice: enterprise-cloud-adoption
ms.custom: governance
ms.date: 02/11/2019
description: 대기업 – 리소스 일관성 개선
author: BrianBlanchard
ms.openlocfilehash: 9fc6ca015310c02338463d3c8aa53ddfc74699df
ms.sourcegitcommit: 273e690c0cfabbc3822089c7d8bc743ef41d2b6e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55901635"
---
# <a name="large-enterprise-resource-consistency-evolution"></a>대기업: 리소스 일관성 진화

이 문서에서는 중요 업무용 애플리케이션을 지원하기 위해 거버넌스 MVP에 리소스 일관성 컨트롤을 추가하여 이야기를 전개합니다.

## <a name="evolution-of-the-narrative"></a>설명 개선

클라우드 도입 팀은 보호된 데이터를 이동하기 위한 모든 요구 사항을 충족했습니다. 이러한 애플리케이션에서는 비즈니스에 대한 SLA 약정과 IT 운영 지원이 필요합니다. 두 개의 데이터 센터를 마이그레이션하는 팀 바로 뒤에 있는 여러 앱 개발 및 BI 팀은 새로운 솔루션을 프로덕션으로 이동하여 시작할 준비가 되었습니다. IT 운영은 클라우드 운영에 대한 새로운 생각이며 기존 운영 프로세스를 신속하게 통합하는 방법이 필요합니다.

### <a name="evolution-of-current-state"></a>현재 상태의 발전

- IT는 보호된 데이터가 있는 프로덕션 워크로드를 Azure로 적극적으로 이동시키고 있습니다. 우선 순위가 낮은 여러 워크로드가 프로덕션 트래픽을 제공하고 있습니다. IT 운영에서 워크로드 지원 준비를 승인하는 즉시 더 많은 작업을 줄일 수 있습니다.
- 애플리케이션 개발 팀은 프로덕션 트래픽을 처리할 준비가 되었습니다.
- BI 팀은 3개 사업부에 대해 운영되는 시스템에 예측과 통찰력을 통합할 수 있습니다.

### <a name="evolution-of-the-future-state"></a>향후 상태의 발전

- IT 운영은 클라우드 운영에 대한 새로운 생각이며 기존 운영 프로세스를 신속하게 통합하는 방법이 필요합니다.

현재와 미래의 상태가 변경되면 새로운 정책 설명이 요구되는 새로운 위험에 노출됩니다.

## <a name="evolution-of-tangible-risks"></a>실질적인 위험의 심화

**비즈니스 중단**: 새로운 플랫폼에 내재된 위험으로 인해 업무상 중요한 비즈니스 프로세스가 중단될 수 있습니다. IT 운영 팀과 다양한 클라우드 도입을 실행하는 팀은 클라우드 운영에 비교적 경험이 많지 않습니다. 이로 인해 중단 위험이 증가하므로 이를 완화하고 관리해야 합니다.

이 비즈니스 위험은 여러 기술 위험으로 확대될 수 있습니다.

- 조정되지 않은 운영 프로세스로 인해 신속하게 탐지 또는 수정될 수 없는 중단이 발생할 수 있습니다.
- 외부 침입 또는 서비스 거부 공격으로 인해 비즈니스가 중단될 수 있습니다.
- 업무상 중요한 자산이 제대로 검색되지 않아 제대로 작동하지 않을 수 있습니다.
- 검색되지 않거나 레이블이 잘못 지정된 자산은 기존 운영 관리 프로세스에서 지원하지 않을 수 있습니다.
- 배포된 자산의 구성이 성능 기대치를 충족하지 못할 수 있습니다.
- 로깅이 성능 문제를 해결할 수 있도록 적절하게 기록 및 중앙 집중화되지 않을 수 있습니다.
- 복구 정책이 실패하거나 예상보다 오래 걸릴 수 있습니다.
- 일관성 없는 배포 프로세스로 인해 보안 허점이 발생하여 데이터 누수가 발생하거나 중단될 수 있습니다.
- 구성 드리프트 또는 누락된 패치로 인해 의도치 않은 보안 허점이 발생하여 데이터 누수가 발생하거나 중단될 수 있습니다.
- 구성은 정의된 SLA 요구 사항 또는 커밋된 복구 요구 사항을 적용하지 않을 수 있습니다.
- 배포된 운영 체제 또는 애플리케이션은 OS 및 애플리케이션 강화 요구 사항을 충족하지 못할 수 있습니다.
- 클라우드에서 여러 팀이 작업하는 것으로 인해 불일치 위험이 있습니다.

## <a name="evolution-of-the-policy-statements"></a>정책 설명 개선

정책을 다음과 같이 변경하면 새로운 위험을 완화하고 구현 과정을 안내할 수 있습니다. 항목이 매우 많은 것 같지만 실제로 이러한 정책을 채택하는 과정은 보기보다 쉬울 수도 있습니다.

1. 배포된 모든 자산은 중요도 및 데이터 분류를 기준으로 범주를 지정해야 합니다. 자산을 클라우드로 배포하기 전에 클라우드 거버넌스 팀과 애플리케이션 소유자가 분류를 검토해야 합니다.
2. 중요 업무용 애플리케이션을 포함하는 서브넷은 침입을 감지하고 공격에 대응할 수 있는 방화벽 솔루션에 의해 보호되어야 합니다.
3. 거버넌스 도구는 보안 기준 팀이 정의한 네트워크 구성 요구 사항을 감사하고 적용해야 합니다.
4. 거버넌스 도구는 중요 업무용 애플리케이션 또는 보호되는 데이터와 관련된 모든 자산이 리소스 고갈 및 최적화에 대한 모니터링에 포함되는지 확인해야 합니다.
5. 거버넌스 도구는 적절한 수준의 로깅 데이터가 모든 중요 업무용 애플리케이션 또는 보호되는 데이터에 대해 수집되고 있는지 확인해야 합니다.
6. 거버넌스 프로세스는 중요 업무용 애플리케이션 및 보호되는 데이터에 대해 백업, 복구 및 SLA 준수가 올바르게 구현되었는지 확인해야 합니다.
7. 거버넌스 도구는 가상 머신 배포에 승인된 이미지만 사용하도록 제한해야 합니다.
8. 거버넌스 도구는 중요 업무용 애플리케이션을 지원하는 모든 배포된 자산에서 자동 업데이트가 **금지**되도록 해야 합니다. 위반은 운영 관리 팀에서 검토되고 작업 정책에 따라 수정돼야 합니다. 자동으로 업데이트되지 않는 자산은 IT 운영 팀이 소유한 프로세스에 포함해야 합니다.
9. 거버넌스 도구는 비용, 중요성, SLA, 애플리케이션 및 데이터 분류와 관련된 태그 지정의 유효성을 확인해야 합니다. 모든 값은 클라우드 거버넌스 팀에서 관리되는 미리 정의된 값에 맞춰 정렬되어야 합니다.
10. 모든 자산에서 일관성을 유지하려면 거버넌스 프로세스에 배포 시점의 감사 내용과 정기적인 주기로 실행되는 감사 내용이 포함되어야 합니다.
11. 보안 팀은 클라우드 배포에 영향을 줄 수 있는 추세 및 약용을 정기적으로 검토하여 클라우드에서 사용되는 보안 기준 도구에 업데이트를 제공해야 합니다.
12. 프로덕션 환경에 릴리스하기 전에 모든 중요 업무용 애플리케이션과 보호되는 데이터가 지정된 운영 모니터링 솔루션에 추가되어야 합니다. 선택한 IT 운영 도구로 검색할 수 없는 자산은 프로덕션 용도로 릴리스할 수 없습니다. 자산을 검색 가능하게 만드는 데 필요한 모든 변경 사항은 향후 배포에서 자산을 검색할 수 있도록 하는 관련 배포 프로세스에 적용되어야 합니다.
13. 검색 시, 운영 관리 팀은 자산이 성능 요구 사항을 충족하는지 확인하기 위해 자산 규모를 확인합니다.
14. 배포된 자산에 거버넌스를 지속적으로 적용하기 위해 클라우드 거버넌스 팀이 배포 도구를 승인해야 합니다.
15. 배포 스크립트는 주기적 검토 및 감사를 위해 클라우드 거버넌스 팀에서 액세스할 수 있는 중앙 리포지토리에 유지되어야 합니다.
16. 거버넌스 검토 프로세스는 배포된 자산이 SLA 및 복구 요구 사항에 맞춰 제대로 구성되어 있는지 확인해야 합니다.

## <a name="evolution-of-the-best-practices"></a>모범 사례 개선

이 문서 섹션에서는 Azure Cost Management 구현 및 새로운 Azure 정책을 포함하도록 거버넌스 MVP 디자인을 개선합니다. 이 두 가지 디자인 변경을 통해 새 기업 정책 설명을 충족하게 됩니다.

이 가상의 예제를 경험한 후에는 보호되는 데이터 진화가 이미 발생했다고 가정합니다. 이러한 모범 사례를 바탕으로 다음은 운영 모니터링 요구 사항을 추가하여 중요 업무용 애플리케이션에 대한 구독을 준비합니다.

**회사 IT 구독**: 허브 역할을 하는 회사 IT 구독에 다음을 추가합니다.

1. 외부 종속성으로 클라우드 운영 팀은 운영 모니터링 도구, BCDR(비즈니스 연속성/재해 복구) 도구 및 자동화된 수정 도구를 정의해야 합니다. 그러면 클라우드 거버넌스 팀에서 필요한 검색 프로세스를 지원할 수 있습니다.
    1. 이 사용 사례에서 클라우드 운영 팀은 중요 업무용 애플리케이션을 모니터링하기 위한 기본 도구로 Azure Monitor를 선택했습니다.
    2. 또한 기본 BCDR 도구로는 Azure Site Recovery를 선택했습니다.
2. Azure Site Recovery 구현
    1. 백업 및 복구 프로세스를 위한 Azure Vault 정의 및 배포
    2. 각 구독에 자격 증명 모음을 만드는 Azure Resource Management 템플릿 만들기
3. Azure Monitor 구현
    1. 중요 업무용 구독을 식별한 후에는 PowerShell을 사용하여 Log Analytics 작업 영역을 만들 수 있습니다. 배포 전 프로세스입니다.

**개별 클라우드 도입 구독**: 다음은 각 구독을 모니터링 솔루션으로 검색 가능하고 BCDR 사례에 포함할 수 있는지 확인합니다.

1. 중요 업무용 노드에 대한 Azure Policy
    1. 표준 역할 사용을 감사하고 해당 역할만 사용하도록 하는 정책을 적용합니다.
    2. 모든 스토리지 계정에 대한 암호화 적용을 감사하고 적용합니다.
    3. 네트워크 인터페이스별 승인된 네트워크 서브넷 및 VNet 사용을 감사하고 적용합니다.
    4. 사용자 정의 라우팅 테이블의 제한을 감사하고 적용합니다.
    5. Windows 및 Linux 가상 머신용 Log Analytics 에이전트의 배포를 감사하고 적용합니다.
2. Azure blueprint
    1. `mission-critical-workloads-and-protected-data`라는 청사진을 만듭니다. 이 청사진은 보호되는 데이터 청사진 이외의 자산을 적용합니다.
    2. 새 Azure 정책을 청사진에 추가합니다.
    3. 중요 업무용 애플리케이션을 호스트할 것으로 예상되는 모든 구독에 청사진을 적용합니다.

## <a name="conclusion"></a>결론

이러한 프로세스와 변경 내용을 거버넌스 MVP에 적용하면 리소스 거버넌스와 연관된 대부분의 위험을 완화할 수 있습니다. 또한 클라우드 인식 작업을 강화하는 데 복구, 크기 조정 및 모니터링 컨트롤을 추가합니다.

## <a name="next-steps"></a>다음 단계

클라우드 채택 과정이 계속 개선되어 비즈니스 가치를 추가적으로 제공하는 과정에서 위험 및 클라우드 거버넌스 요구도 발전합니다. 이 과정에 있는 가상의 회사에서 다음 트리거는 배포 규모가 클라우드에 대해 1,000개 자산을 초과하거나 월간 지출이 월간 10,000달러를 초과하는 경우입니다. 지금은 클라우드 거버넌스 팀에서 Cost Management 컨트롤을 추가하고 있습니다.

> [!div class="nextstepaction"]
> [Cost Management 진화](./cost-management-evolution.md)