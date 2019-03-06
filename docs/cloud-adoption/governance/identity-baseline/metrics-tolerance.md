---
title: 'CAF: ID 기준 메트릭, 지표 및 위험 허용 범위'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
ms.service: architecture-center
ms.subservice: enterprise-cloud-adoption
ms.custom: governance
ms.date: 02/11/2019
description: ID 기준 메트릭, 지표 및 위험 허용 범위
author: BrianBlanchard
ms.openlocfilehash: 4722de66308f3d18885ca930925e68e0e756ec03
ms.sourcegitcommit: 273e690c0cfabbc3822089c7d8bc743ef41d2b6e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55902064"
---
# <a name="identity-baseline-metrics-indicators-and-risk-tolerance"></a>ID 기준 메트릭, 지표 및 위험 허용 범위

이 문서에서는 ID 기준과 관련된 비즈니스 위험 허용 범위를 수치화하는 데 도움이 되는 정보를 제공합니다. 메트릭과 지표를 정의하면 ID 기준 분야를 완성하는 과정에서 투자할 때 활용할 비즈니스 사례를 작성할 수 있습니다.

## <a name="metrics"></a>메트릭

ID 기준에서는 개인, 사용자 그룹 또는 자동화된 프로세스를 식별/인증하고 권한을 부여하는 작업과, 이러한 개인/그룹/프로세스에 클라우드 배포의 리소스에 대한 적절한 액세스 권한을 제공하는 작업을 중점적으로 수행합니다. 위험 분석의 일환으로 ID 서비스 관련 데이터를 수집하여 발생한 위험의 수, 그리고 계획된 클라우드 배포에 대한 ID 기준 거버넌스 관련 투자의 중요도를 확인할 수 있습니다.

아래에는 ID 기준 분야 내에서 위험 허용 범위를 평가하하려는 경우 수집해야 하는 유용한 메트릭의 예가 나와 있습니다.

- **시스템 크기 파악**. ID 시스템을 통해 관리되는 사용자, 그룹 또는 기타 개체의 총 수를 확인합니다.
- **디렉터리 서비스 인프라의 전체 크기**. 조직에서 사용하는 디렉터리 포리스트, 도메인 및 테넌트의 수를 확인합니다.
- **레거시 또는 온-프레미스 인증 메커니즘에 대한 종속성**. 레거시 인증 메커니즘 또는 타사 MFA(Multi-Factor Authentication) 서비스를 사용하는 워크로드의 수를 확인합니다.
- **클라우드에 배포된 디렉터리 서비스의 범위**. 클라우드에 배포한 디렉터리 포리스트, 도메인 및 테넌트의 수를 확인합니다.
- **클라우드에 배포된 Active Directory**. 클라우드에 배포된 Active Directory 서버의 수를 확인합니다.
- **클라우드에 배포된 조직 구성 단위**. 클라우드에 배포된 Active Directory 조직 구성 단위의 수를 확인합니다.
- **페더레이션 범위**. 조직 시스템과 페더레이션된 ID 기준 시스템의 수를 확인합니다.  
- **권한이 상승된 사용자**. 리소스 또는 관리 도구에 대한 액세스 권한이 상승된 사용자 계정의 수를 확인합니다.
- **RBAC 사용**. RBAC(역할 기반 액세스 제어)를 통해 관리되지 않는 구독, 리소스 그룹 또는 개별 리소스의 수를 확인합니다.
- **인증 클레임**. 성공/실패한 사용자 인증 시도 수를 확인합니다.
- **권한 부여 클레임**. 사용자의 리소스 액세스 시도 성공/실패 횟수를 확인합니다.
- **손상된 계정**. 손상된 사용자 계정의 수를 확인합니다.

## <a name="risk-tolerance-indicators"></a>위험 허용 범위 지표

ID 기준 관련 위험은 대개 조직의 ID 인프라 복잡성과 관련하여 발생합니다. 단일 디렉터리 또는 클라우드 기본 ID 공급자(다른 서비스와 최소한으로 통합)를 사용하여 모든 사용자와 그룹을 관리하는 경우에는 위험 수준이 낮은 경우가 많습니다. 그러나 비즈니스 요구가 증가하면 ID 기준 시스템이 더 복잡한 시나리오(예: 내부 조직을 지원하는 여러 디렉터리, 외부 ID 공급자와의 페더레이션)를 지원해야 할 수 있습니다. 이러한 시스템이 복잡해질수록 위험도 증가합니다.

클라우드 채택의 초기 단계에서 IT 보안 팀 및 비즈니스 관련자와 협의하여 ID 관련 [비즈니스 위험](business-risks.md)을 파악한 다음 ID 위험 허용 범위의 적절한 기준을 결정합니다. CAF 지침의 이 섹션에서는 예제가 제공됩니다. 하지만 회사나 배포의 세부 위험 및 기준은 예제와 다를 수 있습니다.

기준을 결정한 후에는 확인된 위험의 허용 불가능한 증가를 나타내는 최소 벤치마크를 설정합니다. 이러한 벤치마크는 해당 위험을 완화하기 위한 조치를 취해야 할 때 트리거로 사용됩니다. 아래에는 위에서 설명한 것과 같은 ID 관련 메트릭의 수치가 ID 기준 분야의 투자를 늘려야 하는 수준에 해당되는 몇 가지 예가 나와 있습니다.

- **사용자 계정 수 트리거**. ID 시스템에서 관리되는 사용자, 그룹 또는 기타 개체의 수가 X개보다 많은 회사의 경우 대량의 계정에서 거버넌스를 효율적으로 적용하기 위해 ID 기준 분야에 투자를 하면 효율적일 수 있습니다.
- **온-프레미스 ID 종속성 트리거**. 레거시 인증 기능이나 타사 MFA가 필요한 워크로드를 클라우드로 마이그레이션하려는 회사의 경우 리팩터링 또는 추가 클라우드 인프라 배포 관련 위험을 줄이기 위해 ID 기준 분야에 투자를 해야 합니다.
- **디렉터리 서비스 복잡성 트리거**. 유지 관리하는 개별 포리스트, 도메인 또는 디렉터리 테넌트의 수가 X개보다 많은 회사의 경우 여러 시스템에 분산되어 있는 다수의 사용자 자격 증명과 관련된 효율성 문제 및 계정 관리 관련 위험을 줄이기 위해 ID 기준 분야에 투자를 해야 합니다.
- **클라우드에서 호스트되는 디렉터리 서비스 트리거**. 클라우드에서 호스트되는 Active Directory 서버 VM(가상 머신) X대를 호스트하거나 이러한 클라우드 기반 서버에서 X개의 조직 구성 단위를 관리하는 회사의 경우 온-프레미스 또는 기타 외부 ID 서비스와의 통합을 최적화하기 위해 ID 기준 분야에 투자를 하면 효율적일 수 있습니다.
- **페더레이션 트리거**. 외부 ID 기준 시스템 X대와의 ID 페더레이션을 구현하는 회사는 모든 페더레이션 멤버에 일관된 조직 정책을 적용하기 위해 ID 기준 분야에 투자를 하면 효율적일 수 있습니다.
- **상승된 액세스 권한 트리거**. 관리 도구 및 리소스에 대한 관리자 권한을 보유한 사용자 수가 X%를 초과하는 회사는 사용자에게 액세스 권한을 부적절하게 초과 프로비전할 위험을 최소화할 수 있도록 ID 기준 분야 투자를 고려해야 합니다.
- **RBAC 트리거**. 역할 기반 액세스 제어 방법을 사용하는 리소스의 비율이 X% 미만인 회사는 리소스 액세스 권한을 사용자에게 할당하는 최적화된 방식을 파악하기 위해 ID 기준 분야 투자를 고려해야 합니다.
- **인증 실패 트리거**. 인증 실패 비율이 인증 시도 중 X%를 초과하는 회사는 인증 방법이 외부 공격을 받지 않도록 하고 사용자가 인증 방법을 올바르게 사용하도록 하기 위해 ID 기준 분야에 투자를 해야 합니다.
- **권한 부여 실패 트리거**. 액세스 시도가 거부된 시간이 X%를 초과하는 회사는 액세스 제어 적용과 업데이트를 개선하고 악의적일 수 있는 액세스 시도를 식별하기 위해 ID 기준 분야에 투자를 해야 합니다.
- **손상된 계정 트리거**. 손상된 계정 수가 X개보다 많은 회사는 인증 메커니즘의 강도와 보안을 개선하고 손상된 계정 관련 위험을 완화하는 메커니즘을 향상시키기 위해 ID 기준 분야에 투자를 해야 합니다.

위험 허용 범위를 측정하는 데 사용하는 정확한 메트릭/트리거와 ID 기준 분야의 투자 수준은 조직에 따라 달라지지만 위의 예제는 클라우드 거버넌스 팀 내에서 논의를 진행하는 데 유용한 기준이 됩니다.

## <a name="next-steps"></a>다음 단계

[클라우드 관리 템플릿](./template.md)을 사용하여 현재 클라우드 채택 계획에 적합한 메트릭과 허용 범위 지표를 문서로 작성합니다.

이러한 위험 및 허용 범위에 따라 ID 기준 정책 준수를 제어하고 관련 정보를 전달하는 프로세스를 설정합니다.

> [!div class="nextstepaction"]
> [정책 준수 프로세스 설정](compliance-processes.md)