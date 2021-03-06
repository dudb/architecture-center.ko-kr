---
title: 'CAF: 클라우드 변환과 연관된 비즈니스 위험'
description: 클라우드 변환과 연관된 비즈니스 위험에 대해 설명합니다.
author: BrianBlanchard
ms.date: 10/10/2018
ms.openlocfilehash: bfd91da42d20a85004debc6b767a1482ba3e158d
ms.sourcegitcommit: 273e690c0cfabbc3822089c7d8bc743ef41d2b6e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55902080"
---
# <a name="evaluating-risk-tolerance"></a>위험 허용 범위 평가

업무상 결정을 내릴 때는 항상 새로운 위험이 발생합니다. 예를 들어 투자를 할 때는 항상 손해 위험이 발생하며, 새 제품이나 서비스를 개발할 때는 판매량 저조 위험이 발생합니다. 현재 제품이나 서비스를 변경하는 경우에는 시장 점유율이 감소될 위험이 있습니다. 클라우드 변환에서는 일상적으로 발생하는 이러한 모든 비즈니스 위험을 해결할 수 있는 솔루션을 제공하지 않습니다. 연결된 솔루션(클라우드 또는 온-프레미스)을 사용하는 경우에는 새로운 위험이 발생하게 됩니다. 그리고 네트워크에 연결된 시설에 자산을 배포하면 훨씬 더 광범위한 전 세계 지역에 보안 약점이 노출되므로 잠재적 위협 프로필이 더욱 확장됩니다. 다행히도 클라우드 공급자는 위험의 변화, 증가 및 추가적인 발생을 모두 인지하고 있으며 고객을 대신하여 이러한 위험을 완화하기 위해 막대한 투자를 하고 있습니다.

이 문서에서는 클라우드 위험에 대해 중점적으로 설명하지는 않으며, 다양한 형태의 클라우드 변환과 연관된 비즈니스 위험에 대해 설명합니다. 그리고 이 문서 뒷부분에서는 기업의 위험 허용 범위를 파악할 수 있는 방법에 대해 주로 설명합니다.

<!-- markdownlint-disable MD026 -->

## <a name="what-business-risks-are-associated-with-a-cloud-transformation"></a>클라우드 변환과 연관된 비즈니스 위험

안타깝게도 실제 비즈니스 위험은 특정 변환의 대상과 방식에 따라 다르게 발생합니다. 하지만 매우 흔히 발생하는 몇 가지 위험과 관련된 논의부터 시작하여 개인별로 발생하는 구체적인 위험을 파악할 수 있습니다.

** 아래 내용을 확인하기 전에 이러한 각 위험은 수정할 수 있다는 점을 기억하세요. 이 문서는 독자가 위험을 완화하는 과정에서 완화 관련 논의를 더 효율적으로 진행하기 위한 준비를 돕고 유용한 정보를 제공하기 위한 용도로 작성되었습니다. **

* 데이터 보호 위험: 모든 변환과 연관된 가장 중요한 위험은 데이터 보호입니다. 오늘날에는 사업 전반에서 디지털 기능이 활용되므로 데이터를 새로운 방식으로 활용할 수 있습니다. 즉, 데이터를 효율적으로 활용하면 매출을 늘리고, 업무를 효율적으로 처리하고, 고객 만족도를 높일 수 있습니다. 하지만 데이터가 누수되는 경우의 피해도 매우 심각합니다. 데이터가 저장, 처리 또는 사용되는 방식이 변경되면 위험이 발생합니다. 클라우드 변환에서는 데이터 관리 방식이 대폭 변경되므로 위험을 대수롭지 않게 여겨서는 안 됩니다. [보안 기준](../security-baseline/overview.md), [데이터 분류](./what-is-data-classification.md) 및 [증분 합리화](../../digital-estate/rationalize.md#incremental-rationalization)를 통해 이 위험을 완화할 수 있습니다.

* 운영 및 고객 환경 위험: 사업 운영 및 고객 환경의 효율성은 기술 운영 방식에 따라 크게 좌우됩니다. 클라우드 변환 과정에서는 TechOps(기술 운영) 방식이 변경됩니다. 이러한 변경이 소규모로만 진행되며 쉽게 조정 가능한 조직도 있지만, TechOps를 변경하려면 도구/기술을 변경하거나 새로운 지원 방식을 도입해야 하는 조직도 있습니다. 변경의 규모가 클수록 사업 운영 및 고객 환경에 줄 수 있는 영향도 커집니다. 변환 계획에 실무자가 참여하면 이 위험을 완화할 수 있습니다. 변환 프로젝트용 워크로드를 선택하는 방법에 대한 설명은 [증분 합리화](../../digital-estate/rationalize.md#incremental-rationalization) 문서의 릴리스 계획 및 첫 번째 워크로드 선택에 나와 있습니다. 해당 활동에서 실무자의 역할은 우선적으로 처리해야 하는 워크로드의 변경으로 인해 발생하는 위험을 사업 운영 팀에 알리는 것입니다. IT 팀이 운영에 더 적은 영향을 주는 워크로드를 선택할 수 있도록 하면 전반적인 위험이 감소합니다.

* 비용 위험: 클라우드에서는 비용 모델이 변경됩니다. 이러한 변경으로 인해 비용 초과 또는 COGS(매출원가)와 연관된 위험이 발생하며, 특히 직접적으로 발생하는 운영 비용과 관련한 위험이 증가할 수 있습니다. 실무자가 IT 팀과 긴밀하게 협력하면 여러 사업부, 프로그램, 프로젝트 등에서 사용하는 비용 및 서비스를 투명하게 파악할 수 있습니다. [비용 관리]에서는 이 주제와 관련하여 실무자와 IT 팀이 협력할 수 있는 방식의 예를 제공합니다.

위에 나와 있는 항목은 고객이 언급할 수 있는 가장 흔한 몇 가지 위험입니다. 워크로드가 마이그레이션되어 프로덕션 환경으로 릴리스할 준비가 되면 클라우드 거버넌스 팀과 클라우드 채택 팀은 위험 프로필 개발을 시작할 수 있습니다. 그러려면 적절한 비즈니스 결과와 변환 작업을 토대로 위험을 정의/세분화/완화하기 위한 논의 진행을 준비해야 합니다.

## <a name="understanding-risk-tolerance"></a>위험 허용 범위 파악

위험을 파악하는 작업은 매우 직접적인 프로세스입니다. 업계 전반에 적용되는 위험의 표준이 있기 때문입니다. 그러나 위험의 허용 범위는 개인별로 크게 다릅니다. 위험의 허용 범위를 파악하는 시점에서 실무자와 IT 팀의 논의가 중단되는 경우가 많습니다. 양측에서 서로 다른 허용 범위를 제시하기 때문입니다. 아래의 비교 요소와 질문을 참조하면 실무자와 IT 팀이 위험 허용 범위를 더 적절하게 파악하고 정확하게 계산하는 데 도움이 되는 논의를 시작할 수 있습니다.

## <a name="simple-use-case-for-comparison"></a>비교를 위한 간단한 사용 사례

위험 허용 범위를 쉽게 파악하려면 아래의 고객 데이터를 살펴보세요. 업계에 관계없이 어떤 회사에서든 비보안 서버에 고객 데이터를 게시하는 경우 해당 데이터가 손상되거나 도난당할 위험은 비교적 동일합니다. 그러나 데이터의 특성과 해당 위험에 대한 회사의 허용 범위는 업계별로 크게 다릅니다.

* 예를 들어 미국의 의료 업체와 금융 기관에는 엄격한 타사 규정 준수 요구 사항이 적용됩니다. PII(개인 식별이 가능한 정보) 또는 의료 관련 데이터는 1급 기밀로 간주됩니다. 그리고 이러한 유형의 업체/기관이 위에서 설명한 위험 시나리오에 연루되는 경우에는 심각한 결과가 발생합니다. 위험 허용 범위가 매우 낮기 때문입니다. 네트워크 내/외부에 게시되는 모든 고객 데이터에는 타사 규정 준수 정책이 적용됩니다.
* 고객 데이터가 사용자 이름, 게임 시간, 최고 점수로 제한되는 게임 업체의 경우 위에서 설명한 위험한 행위가 확인되더라도 그다지 심각한 결과가 발생하지는 않을 가능성이 높습니다. 비보안 데이터가 위험한 상태가 되어도 해당 위험의 영향은 크지 않기 때문입니다. 따라서 이 경우의 위험 허용 범위는 높다고 할 수 있습니다.
* 수천 명의 고객을 대상으로 양탄자 세탁 서비스를 제공하는 중견 기업의 경우 이 두 가지 극단적인 위험 허용 범위의 중간 정도에 해당된다고 할 수 있습니다. 이 기업의 고객 데이터에는 주소나 전화 번호 등의 더 구체적인 세부 정보가 포함될 수 있습니다. 이러한 정보는 모두 PII로 간주될 수 있으므로 보호해야 합니다. 그러나 데이터를 보호해야 한다는 구체적인 거버넌스 요구 사항은 없을 수도 있습니다. IT 관점에서 보자면 데이터는 당연히 보호해야 합니다. 하지만 실무자의 관점에서는 데이터 보호가 그렇게 간단하지 않을 수도 있습니다. 즉, 실무자가 이 위험의 허용 범위 수준을 결정하려면 세부 정보가 더 필요할 수도 있습니다.

다음 섹션에는 위의 사용 사례나 기타 사용 사례에 대해 위험 허용 범위 수준을 결정할 때 참조할 수 있는 몇 가지 샘플 질문이 나와 있습니다.

## <a name="risk-tolerance-questions"></a>위험 허용 범위 결정을 위한 질문

이 섹션에서는 손실의 영향, 손실 가능성, 완화 비용의 세 가지 범주에서 질문이 제기될 수 있는 논의 내용을 소개합니다. 실무자와 IT 팀이 함께 이러한 각 분야에 대한 논의를 진행하면 위험을 완화하는 방법과 특정 위험의 전반적인 허용 범위를 쉽게 결정할 수 있습니다.

**손실의 영향**: 위험의 영향을 확인하기 위한 질문입니다. 이러한 질문은 대답하기가 까다로울 수도 있고 경우에 따라서는 대답이 불가능할 수도 있습니다. 질문에 대답하려면 영향을 수치화하는 것이 가장 좋지만, 논의 과정 자체에서 허용 범위를 파악할 수 있는 경우도 있습니다. 위험의 범위를 파악해도 됩니다(특히, 해당 범위 결정의 근거가 된 가정 사항이 포함되는 경우).

* 이 위험이 타사 규정 준수 요구 사항을 위반하는가?
* 이 위험이 기업 내부 정책을 위반하는가?
* 이 위험으로 인해 고객이 감소하거나 시장 점유율이 낮아질 수 있는가? 해당 가능성이 있는 경우 영향을 수치화할 수 있는가?
* 이 위험으로 인해 고객 환경의 품질이 저하될 수 있는가? 품질이 저하된 환경이 영업 또는 매출 실현에 영향을 줄 가능성이 있는가?
* 이 위험으로 인해 새로운 법적 책임이 발생하는가? 그러한 경우 이러한 유형의 사례와 관련한 피해 보상 선례가 있는가?
* 이 위험으로 인해 사업 운영이 중지될 수 있는가? 그러한 경우 운영이 중단되는 기간은 어느 정도인가?
* 이 위험으로 인해 사업 운영 속도가 느려질 수 있는가? 그러한 경우 속도 저하 정도와 기간은 어느 정도인가?
* 변환의 이 단계에서 이 위험은 한 번만 발생하는가, 아니면 반복되는가?
* 변환이 진행되면 위험의 빈도가 증가하는가, 아니면 감소하는가?
* 변환 확률은 장기적으로 높아지는가, 아니면 낮아지는가?
* 위험이 시간별로 달라지는가? 위험이 해결하지 않으면 저절로 해결되는가, 아니면 악화되는가?

이러한 기본적인 질문에 대한 대답을 통해 더욱 많은 추가 정보를 파악할 수 있습니다. 효율적인 논의 내용을 파악한 후에는 관련 위험을 기록하고 가능하면 수치화하는 것이 좋습니다.

**완화 비용**: 위험을 완화하거나 제거하는 비용을 확인하기 위한 질문입니다. 이러한 질문은 내용이 매우 직접적일 수 있습니다(특히 범위를 질문하는 경우).

* 확실한 해결 방법이 있는가? 해결 방법의 비용은 어느 정도인가?
* 이 위험을 해결하거나 완화하기 위한 옵션이 있는가? 해당 솔루션의 비용 범위는 어느 정도인가?
* 실무자가 최적의 확실한 해결 방법을 선택하려면 필요한 사항은 무엇인가?
* 실무자가 비용의 유효성을 검사하려면 필요한 사항은 무엇인가?
* 이 위험을 완화하는 해결 방법을 통해 제공되는 다른 이점은 무엇인가?

이러한 질문에서는 위험을 완화하는 데 필요한 기술적인 해결 방법을 매우 간략하게만 파악할 수 있습니다. 그러나 이러한 질문을 통해 실무자가 결정 프로세스에 빠르게 통합할 수 있는 방식으로 해결 방법을 제시할 수 있습니다.

**손실 가능성**: 위험이 실제 문제로 발전할 가능성을 확인하기 위한 질문입니다. 수치화하기가 가장 어려운 분야이기도 합니다. 그러므로 클라우드 거버넌스 팀이 지원 데이터를 토대로 하여 해당 가능성을 전달하기 위한 범주를 만드는 것이 좋습니다. 다음 질문을 참조하여 팀에 유용한 범주를 만들 수 있습니다.

* 이 위험이 문제로 발전할 가능성과 관련한 연구가 진행되었는가?
* 공급업체가 영향 가능성에 대한 참조나 통계를 제공할 수 있는가?
* 관련 분야나 수직 시장에 이 위험이 발생한 다른 기업이 있는가?
* 또한 업계 전체에서 이 위험이 발생한 다른 기업이 있는가?
* 이 위험은 해당 업체의 잘못된 작업 방식으로 인해 발생한 것인가?

이러한 질문 및 클라우드 거버넌스 팀이 결정한 추가 질문에 대답을 하면 가능성 그룹이 확인될 가능성이 높습니다. 아래에는 그룹화를 시작할 때 참조할 수 있는 몇 가지 샘플 그룹이 나와 있습니다.

* 지표 없음: 가능성을 확인하기에 충분한 연구가 완료되지 않았습니다.
* 위험 수준 낮음: 현재 연구 결과 위험이 문제로 발전할 가능성이 없습니다.
* 향후 위험: 현재 가능성은 위험 수준 낮음이지만 클라우드를 계속 채택하면 새로운 분석이 트리거됩니다.
* 위험 수준 보통: 위험이 사업에 영향을 줄 가능성이 있습니다.
* 위험 수준 높음: 기업이 이 위험의 영향을 피할 수 있는 가능성은 장기적으로 계속 낮아집니다.
* 위험 수준 감소 중: 위험 수준이 보통~높음입니다. 그러나 IT 팀이나 실무자의 조치로 인해 영향 가능성이 감소하고 있습니다.

**허용 범위 결정:**

위의 3가지 범주에 포함되는 질문을 통해 초기 허용 범위를 결정하는 데 충분한 데이터를 수집할 수 있습니다. 위험과 가능성은 낮은데 완화 비용은 높으면 기업이 위험 수정에 투자할 가능성은 낮습니다. 반면 위험과 가능성이 높은 경우 비용이 잠재적 위험 수준을 초과하지 않는다면 기업은 투자를 고려할 가능성이 높습니다.

## <a name="next-steps"></a>다음 단계

실무자와 IT 팀은 이러한 유형의 논의를 통해 허용 범위를 더 효율적으로 평가할 수 있습니다. MVP 정책을 작성하고 증분 방식으로 정책을 검토하는 과정에서 이러한 논의를 진행할 수 있습니다.

> [!div class="nextstepaction"]
> [기업 정책 정의](./define-policy.md)
