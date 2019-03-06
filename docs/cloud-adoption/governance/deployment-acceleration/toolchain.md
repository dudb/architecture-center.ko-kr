---
title: 'CAF: Azure의 배포 가속 도구'
description: Azure의 배포 가속 도구
titleSuffix: Microsoft Cloud Adoption Framework for Azure
ms.service: architecture-center
ms.subservice: enterprise-cloud-adoption
ms.custom: governance
ms.date: 02/11/2019
author: BrianBlanchard
ms.openlocfilehash: 8d2cae87b8a3a11bfde87aafc04d4d2ef55cbbe9
ms.sourcegitcommit: 273e690c0cfabbc3822089c7d8bc743ef41d2b6e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55901951"
---
# <a name="deployment-acceleration-tools-in-azure"></a>Azure의 배포 가속 도구

[배포 가속](overview.md)은 [5개 클라우드 거버넌스 분야](../governance-disciplines.md) 중 하나입니다. 이 분야는 자산 구성 또는 배포를 제어하는 정책을 설정하는 방법에 중점을 둡니다. 5개 클라우드 거버넌스 분야에는 배포, 구성 맞춤 및 HA/DR 전략이 포함됩니다. 여기서는 수동 작업 또는 완전히 자동화된 DevOps 작업을 통해 수행될 수 있습니다. 두 경우 모두 정책이 대체로 동일하게 유지됩니다.

거버넌스에 관심 있는 클라우드 보유자, 클라우드 보호자 및 클라우드 설계자는 각각 여러 클라우드 채택 과정에서 정책과 요구 사항을 체계화하는 배포 가속 분야에 많은 시간을 투자할 가능성이 높습니다. 이 도구 체인의 도구는 클라우드 거버넌스 팀에 중요하며 팀의 학습 경로에서 높은 우선 순위로 지정되어야 합니다.

이 거버넌스 분야를 지원하는 정책과 프로세스를 완성하는 데 도움이 되는 Azure 도구 목록은 다음과 같습니다.

|  |Azure Policy  |Azure 관리 그룹  |Azure 리소스 관리자 템플릿  |Azure Blueprints  | Azure Resource Graph | Azure Cost Management |
|---------|---------|---------|---------|---------|---------|---------|
|회사 정책 구현     |예 |아니요  |아니요  |아니요 | 아니요 |아니요 |
|구독 간 정책 적용     |필수 |예  |아니요  |아니요 | 아니요 |아니요 |
|정의된 리소스 배포     |아니요 |아니요  |예  |아니요 | 아니요 |아니요 |
|완벽하게 호환되는 환경 만들기      |필수 |필수  |필수  |예 | 아니요 |아니요 |
|정책 감사      |예 |아니요  |아니요  |아니요 | 아니요 |아니요 |
|Azure 리소스 쿼리      |아니요 |아니요  |아니요  |아니요 |예 |아니요 |
|리소스 비용 보고      |아니요 |아니요  |아니요  |아니요 |아니요 |예 |

특정 배포 가속 목표를 달성하는 데 필요할 수 있는 추가 도구는 다음과 같습니다. 이러한 도구는 거버넌스 팀 외부에서 사용되는 경우가 많지만 여전히 배포 가속 측면이 분야로 간주됩니다.

|  |Azure portal  |Azure 리소스 관리자 템플릿  |Azure Policy  | Azure DevOps | Azure Backup | Azure Site Recovery |
|---------|---------|---------|---------|---------|---------|---------|
|수동 배포(단일 자산)     | 예 | 예  | 아니요  | 효율적이지 않음 | 아니요 | 예 |
|수동 배포(전체 환경)     | 효율적이지 않음 | 예 | 아니요  | 효율적이지 않음 | 아니요 | 예 |
|자동화된 배포(전체 환경)     | 아니요  | 예  | no  | 예  | no | 예 |
|단일 자산 구성 업데이트     | 예 | 예 | 효율적이지 않음 | 효율적이지 않음 | 아니요 | 예 - 복제 중 |
|전체 환경 구성 업데이트     | 효율적이지 않음 | 예 | 예 | 예  | 아니요 | 예 - 복제 중 |
|구성 드리프트 관리     | 효율적이지 않음 | 효율적이지 않음 | 예  | 예  | 아니요 | 예 - 복제 중 |
|코드를 배포하고 자산(DevOps)을 구성하는 자동화된 파이프라인 만들기     | 아니요 | 아니요 | 아니요 | 예 | 아니요 | 아니요 |
|가동 중단 또는 SLA 위반 시 데이터 복구     | 아니요 | 아니요 | 아니요 | 예 | 예 | 예 |
|가동 중단 또는 SLA 위반 시 애플리케이션 및 데이터 복구     | 아니요 | 아니요 | 아니요 | 예 | no | 예 |

위에서 언급한 Azure 네이티브 도구 외에도, 고객이 타사 도구를 사용하여 배포 가속 및 DevOps 배포를 용이하게 하는 것이 일반적입니다.