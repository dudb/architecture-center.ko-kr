---
title: 'CAF: 대기업 거버넌스 설명'
titleSuffix: Microsoft Cloud Adoption Framework for Azure
ms.service: architecture-center
ms.subservice: enterprise-cloud-adoption
ms.custom: governance
ms.date: 02/11/2019
description: 대기업 거버넌스 경험에 해당하는 사용 사례를 제시하는 설명을 소개합니다.
author: BrianBlanchard
ms.openlocfilehash: 2f8e18a7a845d39fd5aa1632a9d025a502518a94
ms.sourcegitcommit: 273e690c0cfabbc3822089c7d8bc743ef41d2b6e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55902135"
---
# <a name="large-enterprise-the-narrative-behind-the-governance-strategy"></a>대기업: 거버넌스 전략의 기반이 되는 설명

아래에서는 [대기업 거버넌스 경험](./overview.md)에 해당하는 사용 사례를 제시하는 설명을 소개합니다. 해당 경험을 구현하기 전에 이 설명에 반영된 가정과 추론 방식을 파악해야 합니다. 그리고 나면 거버넌스 전략을 더 효율적으로 조직의 경험에 맞게 조정할 수 있습니다.

## <a name="back-story"></a>배경 정보

고객이 회사와의 상호 작용 시에 더 효율적인 환경을 요구하고 있습니다. 현재 환경에서 시장 잠식 현상이 발생하여, 이사회에서 CDO(Chief Digital Officer)를 채용했습니다. CDO는 영업/마케팅 팀과 함께 환경을 개선하기 위한 디지털 변환을 추진하고 있습니다. 또한 여러 사업부에서 데이터 파밍을 진행하고 학습과 예측을 통해 대다수 수동 환경을 개선하기 위해 최근 데이터 과학자를 채용했습니다. IT 팀은 가능한 부분에서 이러한 작업을 지원하고 있습니다. 그러나 필요한 거버넌스 및 보안 컨트롤의 범위에 포함되지 않는 "섀도 IT" 활동도 진행되고 있는 실정입니다.

IT 조직에도 고유한 문제가 있습니다. 재무 팀이 향후 5년 동안 IT 팀의 예산을 계속 줄일 계획이어서 올해부터 필요한 지출 중 일부가 삭감될 예정입니다. 하지만 GDPR 및 기타 데이터 권리 관련 요구 사항은 계속 준수해야 하므로 IT 팀은 더 많은 국가에서 데이터를 지역화하는 자산에 투자를 해야 합니다. 기존 데이터 센터 중 2곳의 하드웨어 교체 기간이 지나서 직원 및 고객 만족도도 낮아지고 있습니다. 3개 데이터 센터의 경우 5개년 계획을 시행하는 중에 하드웨어를 교체해야 합니다. CFO는 기업비 확보를 위해 이러한 데이터 센터 대신 클라우드를 사용하도록 CIO에 요구하고 있습니다.

CIO에게는 회사에 도움이 될 수 있는 획기적인 아이디어가 있지만 급한 업무를 처리하고 비용을 제어하느라 해당 아이디어를 추진할 시간이 없습니다. CIO는 CDO 및 사업부 책임자 중 한 명과 점심 식사를 하면서 클라우드 마이그레이션에 대해 설명했고, 그러자 동료들도 관심을 보였습니다. CIO와 CDO, 그리고 사업부 책임자는 클라우드를 사용해 업무 목표를 달성하는 과정을 서로 지원하기로 하고 클라우드 채택 단계를 파악/계획하는 과정을 시작했습니다.

## <a name="business-characteristics"></a>기업 특성

이 회사의 비즈니스 프로필은 다음과 같습니다.

- 영업/운영 팀이 여러 지역에서 운영되며 전 세계 여러 시장에서 고객에게 제품/서비스를 제공합니다.
- 인수를 통해 사업을 확장했으며 대상 고객층을 기준으로 3개 사업부가 운영됩니다. 여러 사업부와 비즈니스 기능에 걸쳐 복잡한 계산을 통해 예산이 책정됩니다.
- 대부분의 IT 업무는 자본 낭비나 비용 센터로 간주됩니다.

## <a name="current-state"></a>현재 상태

이 회사의 현재 IT 및 클라우드 운영 상태는 다음과 같습니다.

- IT 팀은 전 세계에 분산된 20개가 넘는 사유 데이터 센터를 운영하고 있습니다.
- 각 데이터 센터가 일련의 지역 임대 회선으로 연결되어 느슨하게 결합된 전역 WAN이 구축되어 있습니다.
- IT 팀은 모든 최종 사용자 이메일 계정을 Office 365로 마이그레이션하는 방식으로 클라우드를 처음 채택했습니다. 이 마이그레이션이 완료된 지 6개월 이상이 지났습니다. 그 이후에는 IT 자산 몇 가지가 클라우드에 배포되었을 뿐입니다.
- CDO의 기본 개발 팀은 개발/테스트 환경에서 클라우드의 기본 기능을 익히고 있습니다.
- 한 사업부에서는 클라우드의 빅 데이터를 다양한 방식으로 실험해 보고 있습니다. IT 팀 내부의 BI 팀이 해당 실험에 참여하고 있습니다.
- 기존 IT 거버넌스 정책에는 회사가 직접 소유한 자산에서만 고객의 PII(개인 식별이 가능한 정보) 및 금융 데이터를 호스트해야 한다는 내용이 명시되어 있습니다. 이 정책으로 인해 중요 업무용 앱이나 보호된 데이터용으로는 클라우드를 채택할 수 없습니다.
- IT 투자는 대개 CapEx(기업비)를 통해 제어됩니다. 연 단위로 계획되는 이러한 투자에는 지속적인 유지 관리 계획뿐 아니라 설정된 교체 주기(데이터 센터에 따라 3~5년)도 포함되는 경우가 많습니다.
- 연간 계획에 포함되지 않는 대부분의 기술 투자는 섀도 IT 작업을 통해 진행됩니다. 일반적으로는 사업부에서 이러한 작업을 관리하며, 자금은 사업부의 운영 경비에서 조달됩니다.

## <a name="future-state"></a>향후 상태

이후 몇 년 동안 예상되는 변화는 다음과 같습니다.

- CIO는 향후 목표 지원을 위해 PII 및 금융 데이터 관련 정책을 현대화하는 작업을 추진하고 있습니다. IT 거버넌스 팀의 구성원 두 명이 해당 과정을 함께 확인할 예정입니다.
- 앱 개발 및 BI 팀에서 진행한 초기 실험에서 성공 지표가 확인되면 향후 24개월 내에 소규모 프로덕션 솔루션을 클라우드에 릴리스할 계획입니다.
- CIO와 CFO는 비용 분석 및 적합성 연구 자료 작성을 위해 설계자와 인프라 담당 부사장을 배정했습니다. 이러한 작업을 통해 회사가 향후 36개월 동안 자산 5,000개를 클라우드로 이동할 수 있는지/이동해야 하는지를 확인할 예정입니다. 마이그레이션이 정상적으로 완료되면 CIO는 데이터 센터 2곳을 폐쇄하여 5개년 계획 기간 동안 미화 1억 달러 이상의 비용을 줄일 수 있을 것으로 예상됩니다. 데이터 센터 3~4곳에서 비슷한 결과를 낼 수 있다면 예산이 흑자로 전환되어 CIO가 더욱 혁신적인 이니셔티브를 지원하기 위한 예산을 확보할 수 있을 것입니다.
    ![향후 5년 동안 미화 1억 달러의 비용 절감 효과를 보여 주는 온-프레미스 비용과 Azure 비용 비교 그래프](../../../_images/governance/calculator-enterprise.png)
- 이 회사는 이러한 비용 절약 계획과 함께 집행된 기업비를 IT 내의 OpEx(운영 비용)로 전환함으로써 일부 IT 투자 관리 방식을 변경할 계획입니다. 이 변경으로 인해 비용을 더욱 세부적으로 제어할 수 있으며, IT 팀은 해당 비용을 활용해 계획된 기타 작업을 신속하게 진행할 수 있게 될 것입니다.

## <a name="next-steps"></a>다음 단계

이 회사는 거버넌스 구현을 작성하기 위한 기업 정책을 개발했습니다. 이 기업 정책에 따라 대부분의 기술적 사항을 결정합니다.

> [!div class="nextstepaction"]
> [초기 기업 정책 검토](./initial-corporate-policy.md)