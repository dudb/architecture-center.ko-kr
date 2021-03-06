---
title: 'Azure Virtual Datacenter: 네트워크 측면'
description: Azure에서 가상 데이터 센터를 구축하는 방법 알아보기
author: tracsman
manager: rossort
tags: azure-resource-manager
ms.topic: guide
ms.service: architecture-center
ms.subservice: enterprise-cloud-adoption
ms.custom: virtual-network
ms.date: 11/28/2018
ms.author: jonor
ms.openlocfilehash: 484f41f64b676b08ae8adb4ba082f9bff75a6a54
ms.sourcegitcommit: 14226018a058e199523106199be9c07f6a3f8592
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/31/2019
ms.locfileid: "55483116"
---
# <a name="azure-virtual-datacenter-a-network-perspective"></a>Azure Virtual Datacenter: 네트워크 측면

## <a name="overview"></a>개요

애플리케이션이 최소한의 변경 사항으로 마이그레이션되더라도 온-프레미스 애플리케이션을 Azure로 마이그레이션하면 조직은 안전하고 비용 효율적인 인프라의 혜택을 누릴 수 있습니다. 그러나 클라우드 컴퓨팅의 기민성을 활용하기 위해 기업은 Azure 기능을 이용하는 방식으로 아키텍처를 전환해야 합니다. 

Microsoft Azure는 대규모 서비스와 인프라, 엔터프라이즈급 기능과 안정성을 제공합니다. 이러한 서비스와 인프라는 다양한 하이브리드 연결 옵션을 제공하므로 고객은 공용 인터넷 또는 비공개 Azure ExpressRoute 연결을 통해 액세스할 수 있습니다. 또한 Microsoft 파트너는 Azure에서 실행하도록 최적화된 보안 서비스 및 가상 어플라이언스를 제공하여 향상된 기능을 지원합니다.

고객은 인터넷이나, 사설 네트워크 연결을 제공하는 Azure ExpressRoute를 통해 이러한 클라우드 서비스에 액세스할 수 있습니다. Microsoft Azure 플랫폼을 사용하면 고객은 중단 없이 인프라를 클라우드로 확장하고 다중 계층 아키텍처를 빌드할 수 있습니다. 또한 Microsoft 파트너는 Azure에서 실행하도록 최적화된 보안 서비스 및 가상 어플라이언스를 제공하여 향상된 기능을 지원합니다.

## <a name="what-is-the-virtual-datacenter"></a>가상 데이터 센터란?

클라우드는 처음에 공용 애플리케이션을 호스팅하기 위한 플랫폼으로 제작되었습니다. 기업은 클라우드의 가치를 인식하기 시작하면서 내부 LOB(기간 업무) 애플리케이션을 클라우드로 전환하기 시작했습니다. 이러한 유형의 애플리케이션은 추가 보안, 안정성, 성능, 비용 고려 사항을 제공하기 때문에 클라우드 서비스의 제공 방식에 추가적인 유연성이 요구되었습니다. 이에 따라 이러한 유연성을 제공하도록 설계된 새로운 인프라와 네트워킹 서비스뿐만 아니라 크기 조정, 재해 복구 및 기타 요구 사항을 위한 새 기능도 출시되었습니다.

## <a name="what-is-a-virtual-datacenter"></a>가상 데이터 센터란 무엇일까요?
처음에 클라우드 솔루션은 비교적 격리된 단일 애플리케이션을 공개적으로 호스트하도록 디자인되었습니다. 이 접근 방식은 몇 년 동안은 문제가 없었습니다. 클라우드 솔루션의 이점이 분명해지고, 여러 대규모 워크 로드가 클라우드에 호스트되었습니다. 클라우드 서비스 수명 주기에서 하나 이상의 Azure 지역에 배포할 때 보안, 안정성, 성능 및 비용 문제를 해결하는 것이 중요해졌습니다.

다음 클라우드 배포 다이어그램의 **빨간색 상자**는 보안 격차의 예를 보여줍니다. **노란색 상자**는 워크로드에서 최적화 네트워크 가상 어플라이언스에 대한 공간을 보여줍니다.

[![0]][0]

VDC(가상 데이터 센터)는 이와 같이 엔터프라이즈 워크로드에 맞게 규모를 조정할 필요성과 공용 클라우드에서 대규모 애플리케이션을 지원할 때 발생하는 문제점을 해결하기 위한 요구로부터 탄생되었습니다.

VDC 구현은 단순히 클라우드의 애플리케이션 워크로드를 나타내기보다 네트워크, 보안, 관리 및 인프라(예: DNS 및 디렉터리 서비스)라고 할 수 있습니다. 점점 더 많은 기업의 워크로드가 Azure로 전환되면서, 이러한 워크로드가 배치되는 지원 인프라 및 개체를 고려하는 것이 중요합니다. 리소스가 구성되는 방식을 신중하게 고민하면 독립적인 데이터 흐름, 보안 모델 및 규정 준수 과제를 토대로 따로 관리해야 하는 수많은 "워크로드 섬"이 확산되는 것을 방지할 수 있습니다.

VDC라는 개념은 관련 있는 별도의 엔터티로 이루어진 컬렉션을 공통의 지원 기능, 특성, 인프라를 사용하여 구현하는 방법에 대한 권장 사항 및 모범 사례로 구성된 세트입니다. 워크로드를 VDC의 시각으로 바라보면, 보다 쉬운 작동, 관리 및 규정 준수 감사와 더불어, 경제적인 규모 조정을 통한 비용 절감, 구성 요소 및 데이터 흐름 중앙화를 통해 최적화된 보안을 실현할 수 있습니다.

> [!NOTE]
> VDC가 별도의 Azure 제품이 **아니라** 사용자의 정확한 요구를 충족하기 위한 다양한 특성 및 기능 조합이라는 점을 이해하는 것이 중요합니다. VDC는 워크로드 및 Azure 사용 방식을 고민하면서 클라우드에서 리소스 및 기능을 극대화하는 방법입니다. Azure에서 IT 서비스를 구축하면서도 기업의 조직 역할과 책임을 고려하는 모듈식 접근법입니다.

VDC 구현은 다음과 같은 시나리오에서 기업이 워크로드 및 애플리케이션을 Azure로 가져오는 데 도움을 줄 수 있습니다.

-   여러 관련 워크로드 호스트.
-   온-프레미스 환경에서 Azure로 워크로드 마이그레이션.
-   여러 워크로드에 걸쳐 공유 또는 중앙 집중식 보안과 액세스 요구 사항 구현.
-   대기업에 적합하게 Azure DevOps 및 중앙 집중식 IT 혼합.

VDC의 장점을 활용하기 위한 핵심은 Azure 서비스 및 기능이 결합된 중앙 집중식 허브 및 스포크 네트워크 토폴로지입니다.

* [Azure Virtual Network][VNet],
* [네트워크 보안 그룹][NSG],
* [가상 네트워크 피어링][VNetPeering],
* [사용자 정의 경로(UDR)][UDR] 및
* [RBAC(역할 기반 액세스 제어)][RBAC]를 지원하는 Azure ID와 [Azure Firewall][AzFW], [Azure DNS][DNS], [Azure Front Door][AFD], [Azure Virtual WAN][vWAN](선택 사항).

## <a name="who-should-implement-a-virtual-datacenter"></a>가상 데이터 센터를 구현해야 하는 고객은 누구입니까?

클라우드를 도입하기로 결정한 모든 Azure 고객은 모든 애플리케이션에서 일반적으로 사용할 리소스 세트를 효율적으로 구성할 수 있다는 이점이 있습니다. 그 규모에 따라, 단일 애플리케이션도 VDC 구현을 구축하는 데 사용되는 패턴 및 구성 요소를 통해 이점을 얻을 수 있습니다.

조직에 중앙 집중식 IT, 네트워크, 보안 및/또는 규정 준수 팀/부서가 있을 경우 VDC를 구현하면 애플리케이션 팀에 사용자 요구에 적합한 자유와 제어를 부여하면서 정책 지점을 적용하고, 역할을 적절히 분리하고, 기본적인 공통 구성의 일관성을 보장하는 데 도움이 될 수 있습니다.

DevOps를 원하는 조직은 또한 VDC 개념을 활용하여 권한이 부여된 다양한 Azure 리소스를 제공하고 해당 그룹(구독 또는 공통된 구독에 포함된 리소스 그룹) 내에서 완전한 제어 권한을 가질 수 있지만, 네트워크 및 보안 경계는 허브 VNet 및 리소스 그룹의 중앙 집중식 정책에 따라 정의된 대로 규정 준수 상태를 유지합니다.

## <a name="considerations-for-implementing-a-virtual-datacenter"></a>가상 데이터 센터 구현 시 고려 사항

VDC 구현을 디자인할 때 다음과 같은 몇 가지 중대한 문제를 고려해야 합니다.

### <a name="identity-and-directory-service"></a>ID 및 디렉터리 서비스

ID 및 디렉터리 서비스는 온-프레미스와 클라우드의 모든 데이터 센터에서 핵심적인 요소입니다. ID는 VDC 구현 내의 서비스에 대한 액세스 및 권한 부여의 모든 측면과 관련이 있습니다. Azure는 권한 있는 사용자 및 프로세스만 Azure 계정 및 리소스에 액세스할 수 있도록 하면서 인증을 위해 몇 가지 자격 증명 유형을 사용합니다. 여기에는 암호(Azure 계정 액세스용), 암호화 키, 디지털 서명 및 인증서가 포함됩니다. [Azure MFA(Multi-factor Authentication)][MFA]는 Azure 서비스 액세스에 대한 추가적인 보안 계층입니다. Azure MFA는 전화 통화, 문자 메시지, 모바일 앱 알림 등의 여러 가지 간편한 인증 옵션을 통해 강력한 인증을 제공하므로 고객은 선호하는 방법을 선택할 수 있습니다.

모든 대기업은 VDC 내부 및 VDC 구현 간의 개별 ID, 인증, 권한 부여, 역할 및 권한의 관리를 설명하는 ID 관리 프로세스를 정의해야 합니다. 이 프로세스의 목표는 비용, 가동 중지 시간 및 반복적인 수동 작업을 줄이면서 보안 및 생산성을 높이는 것입니다.

엔터프라이즈/조직은 다양한 LOB(기간 업무)를 위한 까다로운 서비스 조합을 요구할 수 있으며, 직원들은 종종 프로젝트마다 다른 역할을 맡게 됩니다. VDC에서는 적절한 거버넌스에 따라 시스템이 실행되도록 하기 위해 구체적으로 역할이 정의된 각 팀 간에 적절한 협력이 필요합니다. 책임, 액세스 및 권한 구조가 복잡할 수 있습니다. VDC의 ID 관리는 [*Azure Active Directory*(Azure AD)][AAD] 및 RBAC(역할 기반 액세스 제어)를 통해 구현됩니다.

디렉터리 서비스는 일상적인 항목과 네트워크 리소스를 찾고, 관리하고, 운영하고, 구성하기 위한 공유 정보 인프라입니다. 이러한 리소스에는 볼륨, 폴더, 파일, 프린터, 사용자, 그룹, 디바이스 및 기타 개체가 포함될 수 있습니다. 네트워크의 각 리소스는 디렉터리 서버에서 개체로 간주됩니다. 리소스에 대한 정보는 해당 리소스 또는 개체와 연결된 특성 모음으로 저장됩니다.

모든 Microsoft Online 비즈니스 서비스는 로그온 및 기타 ID가 필요로 할 때 Azure AD(Azure Active Directory)를 사용합니다. Azure Active Directory는 핵심 디렉터리 서비스, 고급 ID 관리 및 애플리케이션 액세스 관리를 통합하는 포괄적이고 항상 사용가능한 ID 및 액세스 관리 클라우드 솔루션입니다. Azure AD는 온-프레미스 Active Directory와 통합되어 모든 클라우드 기반 및 로컬로 호스트된(온-프레미스) 애플리케이션에 대한 Single Sign-On을 허용할 수 있습니다. 온-프레미스 Active Directory의 사용자 특성은 Azure AD와 자동으로 동기화될 수 있습니다.

VDC 구현에서 모든 권한을 할당하기 위해 반드시 글로벌 관리자가 필요한 것은 아닙니다. 대신, 각 특정 부서(디렉터리 서비스의 사용자 또는 서비스 그룹)는 VDC 구현 내에서 자체 리소스를 관리하는 데 필요한 권한을 가질 수 있습니다. 사용 권한을 구성할 때는 균형을 유지해야 합니다. 너무 많은 권한을 부여하면 성능 효율성이 저하될 수 있고, 권한이 너무 적거나 느슨하면 보안 위험이 높아질 수 있습니다. Azure 역할 기반 Access Control(RBAC)은 VDC 구현의 리소스에 대한 세밀한 액세스 관리를 제공하여 이 문제를 해결하도록 도와줍니다.

#### <a name="security-infrastructure"></a>보안 인프라

보안 인프라는 VDC 구현의 특정 가상 네트워크 세그먼트에서 트래픽 분리를 가리킵니다. 이 인프라는 VDC 구현에서 수신 및 송신이 제어되는 방법을 지정합니다. Azure는 배포 간에 허가되지 않고 의도하지 않은 트래픽을 방지하는 다중 테넌트 아키텍처를 기반으로 하며, VNet(Virtual Network) 격리, ACL(액세스 제어 목록), 부하 분산 장치, IP 필터, 트래픽 흐름 정책을 사용합니다. NAT(네트워크 주소 변환)는 외부 트래픽에서 내부 네트워크 트래픽을 분리합니다.

Azure 패브릭은 인프라 리소스를 테넌트 워크로드에 할당하고 VM(가상 머신)와의 통신을 관리합니다. Azure 하이퍼바이저는 VM 간의 메모리 및 프로세스 분리를 적용하고 네트워크 트래픽을 게스트 OS 테넌트로 안전하게 라우팅합니다.

#### <a name="connectivity-to-the-cloud"></a>클라우드에 대한 연결

VDC를 구현하려면 고객, 파트너 및/또는 내부 사용자에게 서비스를 제공할 수 있도록 외부 네트워크와 연결해야 합니다. 인터넷뿐 아니라 온-프레미스 네트워크 및 데이터 센터에도 연결되어야 합니다.

고객은 [Azure Firewall][AzFW] 또는 다른 유형의 NVA(가상 네트워크 어플라이언스)를 사용하여 공용 인터넷에 액세스 가능한 서비스를 제어하고, [사용자 정의 경로][UDR]를 사용하여 사용자 지정 라우팅 정책을 제어하고, [네트워크 보안 그룹][NSG]을 사용하여 네트워크 필터링을 제어합니다. 또한 [Azure DDoS Protection Standard][DDOS]를 사용하여 모든 인터넷 연결 리소스를 보호하는 것이 좋습니다.

기업에서는 구현된 VDC를 온-프레미스 데이터 센터 또는 기타 리소스에 연결해야 할 수 있습니다. 효과적인 아키텍처를 디자인할 때 Azure와 온-프레미스 네트워크 간의 연결이 매우 중요합니다. 엔터프라이즈에서는 이러한 상호 연결을 만드는 두 가지 방법, 즉 인터넷을 통한 전송과 개인 직접 연결을 사용할 수 있습니다.

[**Azure 사이트 간 VPN**][VPN]은 안전한 암호화된 연결(IPsec/IKE 터널)을 통해 설정된 온-프레미스 네트워크와 VDC 구현 간의 인터넷 방식 상호 연결 서비스입니다. Azure 사이트 간 연결은 모든 연결이 인터넷을 통해 연결되므로 유연하고, 빠르게 만들 수 있으며 추가적인 조달이 필요하지 않습니다.

VPN 연결 수가 많은 경우 [**Azure Virtual WAN**][vWAN]은 Azure를 통해 최적화 및 자동화된 분기 간 연결을 제공하는 네트워킹 서비스입니다. Virtual WAN을 사용하여 Azure와 통신하도록 분기 디바이스를 연결 및 구성할 수 있습니다. 연결 및 구성은 수동으로 또는 Virtual WAN 파트너를 통해 선호하는 공급자 디바이스를 사용하여 수행할 수 있습니다. 선호하는 공급자 디바이스를 사용하여 사용 편의성, 연결 및 구성 관리의 간소화를 얻을 수 있습니다. Azure WAN 기본 제공 대시보드는 시간을 절약할 수 있도록 도울 수 있는 즉각적인 문제 해결 인사이트를 제공하고, 대규모 사이트 간 연결을 확인하는 간편한 방법을 제공합니다.

[**ExpressRoute**][ExR]는 VDC 구현과 온-프레미스 네트워크 간에 비공개 연결을 가능하게 해주는 Azure 연결 서비스입니다. ExpressRoute 연결은 공용 인터넷을 사용하지 않으며 일관된 대기 시간과 높은 보안, 안정성 및 속도(최대 10Gbps)를 제공합니다. ExpressRoute는 ExpressRoute 고객이 비공개 연결과 관련된 규정 준수 규칙의 이점을 활용할 수 있으므로 VDC 구현에 유용합니다. [ExpressRoute Direct][ExRD]를 사용하면 넓은 대역폭을 요구하는 고객을 위해 100Gbps 속도로 Microsoft 라우터에 직접 연결할 수 있습니다.

ExpressRoute 연결을 배포할 때 일반적으로 ExpressRoute 서비스 공급자와 연계해야 합니다. 빠르게 시작해야 하는 고객의 경우 처음에는 사이트 간 VPN을 사용하여 VDC 구현과 온-프레미스 리소스 간에 연결을 설정한 다음, 서비스 공급자와 물리적 상호 연결이 완료되면 ExpressRoute 연결로 마이그레이션하는 것이 일반적입니다.

#### <a name="connectivity-within-the-cloud"></a>*클라우드 내의 연결*

[VNet][VNet] 및 [VNet 피어링][VNetPeering]은 VDC 구현 내의 기본적인 네트워킹 연결 서비스입니다. VNet은 VDC 리소스에 대한 자연스러운 격리 경계를 보장하며 VNet 피어링을 통해 동일한 Azure 지역 내의 다양한 VNet 간에 또는 지역 간에 상호 통신이 허용됩니다. VNet 내부 및 VNet 간의 트래픽 제어는 Access Control 목록을 통해 지정된 보안 규칙 집합([네트워크 보안 그룹][NSG]), [네트워크 가상 어플라이언스][NVA] 및 UDR([사용자 지정 라우팅 테이블][UDR])에 부합되어야 합니다.

## <a name="virtual-datacenter-overview"></a>가상 데이터 센터 개요

### <a name="topology"></a>토폴로지

_허브 및 스포크_는 가상 데이터 센터 구현용 네트워크 토폴로지를 설계하는 데 사용되는 모델입니다. 

[![1]][1]

허브는 여러 다른 영역, 즉 인터넷, 온-프레미스 및 스포크 간의 송신 및/또는 수신 트래픽을 제어하고 검사하는 중앙 네트워크 영역입니다. 허브 및 스포크 토폴로지는 IT 부서에 중앙의 한 위치에서 보안 정책을 적용하는 효과적인 방법을 제공합니다. 또한 구성 오류 및 노출 가능성을 줄입니다.

허브는 스포크에서 사용되는 공통 서비스 구성 요소를 포함합니다. 다음은 일반적인 중앙 서비스의 예제입니다.

-   신뢰할 수 없는 네트워크에서 액세스하는 제3자가 스포크의 워크로드에 대한 액세스 권한을 얻기 위해 사용자 인증을 받는 데 필요한 Windows Active Directory 인프라. 여기에는 관련 AD FS(Active Directory Federation Services)가 포함됩니다.
-   [Azure DNS][DNS]가 사용되지 않는 경우 온-프레미스 및 인터넷에서 리소스에 액세스하기 위해 스포크의 워크로드에 대한 이름을 확인하는 DNS 서비스.
-   워크로드에 대한 Single Sign-On을 구현하기 위한 PKI(공개 키 인프라) 인프라.
-   스포크 네트워크 영역과 인터넷 간의 TCP 및 UDP 트래픽 흐름 제어.
-   스포크와 온-프레미스 간의 흐름 제어.
-   필요한 경우 한 스포크와 또 다른 스포크 간의 흐름 제어.

VDC는 여러 스포크 간에 공유 허브 인프라를 사용하여 전체 비용을 절감합니다.

각 스포크의 역할은 서로 다른 유형의 워크로드를 호스트하는 것일 수 있습니다. 스포크는 동일한 워크로드를 반복해서 배포할 수 있는 모듈식 접근 방법도 제공합니다. 개발 및 테스트, 사용자 승인 테스트, 사전 프로덕션 및 프로덕션을 예로 들 수 있습니다. 스포크는 조직 내 여러 그룹을 분리하고 사용하도록 설정할 수도 있습니다. Azure DevOps 그룹을 예로 들 수 있습니다. 스포크 내에서 계층 간 트래픽 제어를 통해 기본 워크로드 또는 복잡한 다중 계층 워크로드를 배포할 수 있습니다.

#### <a name="subscription-limits-and-multiple-hubs"></a>구독 제한 및 다중 허브

Azure에서 모든 구성 요소는 유형에 관계없이 Azure 구독에 배포됩니다. 다른 Azure 구독에서 Azure 구성 요소를 분리하면 차별화된 액세스 및 권한 부여 수준을 설정하는 것과 같은 다양한 LOB에 대한 요구 사항을 충족할 수 있습니다.

모든 IT 시스템의 경우처럼 플랫폼 제한은 있지만, 단일 VDC 구현을 많은 수의 스포크로 확장할 수 있습니다. 허브 배포는 특정 Azure 구독에 구속되므로 제한 사항 및 한도가 적용됩니다(예를 들어 VNet 피어링의 최대 수, [Azure 구독 및 서비스 한도, 할당량 및 제약 조건][ Limits] 참조). 이러한 한도가 문제가 될 수 있는 경우 단일 허브-스포크에서 허브 및 스포크 클러스터로 모델을 확장함으로써 아키텍처를 추가적으로 확장할 수 있습니다. 하나 이상의 Azure 지역에 있는 여러 허브를 VNet 피어링, ExpressRoute, Virtual WAN 또는 사이트 간 VPN을 사용하여 상호 연결할 수 있습니다.

[![2]][2]

여러 허브를 도입하면 시스템 비용 및 관리 업무가 증가합니다. 여러 허브를 도입하는 이유는 시스템 한도 또는 중복성 같은 확장성과 최종 사용자 성능 또는 재해 복구 같은 지역 복제 때문입니다. 여러 허브가 필요한 시나리오에서는 모든 허브가 작동 편의를 위해 동일한 서비스 집합을 제공하려고 합니다.

#### <a name="interconnection-between-spokes"></a>스포크 간 상호 연결

단일 스포크 내에서는 복잡한 다중 계층 워크로드를 구현할 수 있습니다. 다중 계층 구성은 동일한 VNet의 서브넷(모든 계층에 대해 1개)을 사용하고 NSG를 사용하여 흐름을 필터링하여 구현될 수 있습니다.

설계자는 여러 가상 네트워크에 다중 계층 워크로드를 배포하려고 할 수 있습니다. 가상 네트워크 피어링을 사용하면 스포크는 동일한 허브 또는 다른 허브의 다른 스포크에 연결할 수 있습니다. 이 시나리오의 일반적인 예제는 애플리케이션 처리 서버가 한 스포크 또는 가상 네트워크에 있는 경우입니다. 데이터베이스는 다른 스포크 또는 가상 네트워크에 배포됩니다. 이 경우 가상 네트워크 피어링을 통해 스포크를 쉽게 상호 연결하여 허브를 통한 전송을 방지할 수 있습니다. 허브를 우회해도 허브에만 존재하는 중요한 보안 또는 감사 지점을 우회하지 않도록 아키텍처 및 보안을 신중하게 검토해야 합니다.

[![3]][3]

또한 스포크를 허브로 작동하는 스포크에 상호 연결할 수도 있습니다. 이 접근법은 두 수준의 계층 구조를 생성합니다. 여기서는 상위 수준(수준 0)의 스포크가 계층 구조에서 하위 스포크(수준 1)의 허브가 됩니다. VDC 구현의 스포크는 온-프레미스 네트워크 또는 공개 인터넷상의 목적지에 트래픽이 전송될 수 있도록 해 중앙 허브로 트래픽을 전달하는 데 필요합니다. 두 가지 수준의 허브를 사용하는 아키텍처에서는 라우팅이 복잡해져서 간단한 허브-스포크 관계의 이점이 사라집니다.

Azure에서는 복잡한 토폴로지를 허용하지만 VDC 개념의 핵심 원리 중 하나는 반복성과 단순성입니다. 관리 업무를 최소화할 수 있도록, VDC 참조 아키텍처로 간단한 허브-스포크 디자인을 권장합니다.

### <a name="components"></a>구성 요소

가상 데이터 센터는 **인프라**, **경계 네트워크**, **워크로드** 및 **모니터링**이라는 네 가지 기본 구성 요소 유형으로 구성됩니다.

각 구성 요소 유형은 다양한 Azure 기능 및 리소스로 구성됩니다. VDC 구현은 여러 구성 요소 유형 및 동일한 구성 요소 유형의 다양한 변형 인스턴스로 구성됩니다. 예를 들어 다른 애플리케이션을 나타내는 논리적으로 분리된 여러 다른 워크로드 인스턴스가 있을 수 있습니다. 이러한 다양한 구성 요소 형식 및 인스턴스를 사용하여 궁극적으로 VDC를 구축합니다.

[![4]][4]

앞에 나온 VDC의 대략적인 개념 아키텍처는 허브-스포크 토폴로지의 여러 영역에 사용되는 다양한 구성 요소 형식을 보여 줍니다. 이 다이어그램에서는 아키텍처의 여러 부분에 있는 인프라 구성 요소를 보여 줍니다.

일반적으로 액세스 권한 및 사용 권한을 그룹 기반으로 구성하는 것이 좋습니다. 개별 사용자가 아닌 그룹을 관리하면 팀 간에 일관적인 관리 방법을 제공하여 액세스 정책을 쉽게 유지 관리할 수 있습니다.  그리고 구성 오류를 최소화하는 데에도 도움이 됩니다. 해당 그룹에서 사용자를 할당 및 제거하여 특정 사용자의 권한을 최신 상태로 유지할 수 있습니다.

각 역할 그룹의 이름에 고유한 접두사가 있어야 합니다. 이 접두사를 보면 어떤 그룹이 어떤 워크로드와 연결되었는지 쉽게 식별할 수 있습니다. 예를 들어 인증 서비스를 호스트하는 워크로드에는 **AuthServiceNetOps**, **AuthServiceSecOps**, **AuthServiceDevOps** 및 **AuthServiceInfraOps**라는 그룹이 있을 수 있습니다. 중앙 집중식 역할 또는 특정 서비스와 관련이 없는 역할은 맨 앞에 **Corp**를 붙일 수 있습니다. **CorpNetOps**를 예로 들 수 있습니다.

대부분의 조직에서는 다음과 같은 그룹 변형을 사용하여 역할을 기본적으로 분류합니다.

-   중앙 IT 그룹 **Corp**는 인프라 구성 요소를 제어하는 소유권 권한을 갖고 있습니다. 네트워킹 및 보안을 예로 들 수 있습니다. 그룹은 스포크에서 구독의 기여자 역할, 허브 제어, 네트워크 기여자 권한이 있어야 합니다. 대규모 조직에서는 이러한 관리 책임을 여러 팀에 분산하는 경우가 많습니다. 예를 들어 네트워크 작업 **CorpNetOps** 그룹은 네트워킹에만 집중하고, 보안 작업 **CorpSecOps** 그룹은 방화벽과 보안 정책을 담당합니다. 이러한 특정 경우 이러한 사용자 지정 역할 할당을 위해 2개의 다른 그룹을 만들어야 합니다.
-   개발 및 테스트 그룹인 **AppDevOps**는 앱 또는 서비스 워크로드를 배포하는 일을 담당합니다. 이 그룹은 IaaS 배포를 위한 가상 머신 기여자 역할 또는 하나 이상의 PaaS 기여자 역할을 담당합니다. [Azure 리소스에 대한 기본 제공 역할][Roles]을 참조하세요. 필요에 따라 개발-테스트 팀이 허브 또는 특정 스포크 내에서 보안 정책(NSG) 및 라우팅 정책(UDR)에 대한 가시성이 필요한 경우가 있습니다. 이 그룹은 워크로드에 대한 기여자 역할 외에도 네트워크 읽기 권한자 역할이 필요합니다.
-   작업 및 유지 관리 그룹인 **CorpInfraOps** 또는 **AppInfraOps**는 프로덕션 환경에서 워크로드를 관리하는 일을 담당합니다. 이 그룹은 프로덕션 구독에서 워크로드에 대해 구독 참가자여야 합니다. 일부 조직에서는 프로덕션 및 중앙 허브 구독에서 구독 기여자 역할을 갖는 추가 에스컬레이션 지원 팀 그룹이 필요한지 평가할 수도 있습니다. 추가 그룹은 프로덕션 환경의 잠재적 구성 문제를 해결합니다.

VDC는 허브를 관리하는 중앙 IT 그룹에 대해 만든 그룹이 워크로드 수준에서 유지되도록 설계되었습니다. 허브 리소스를 관리하는 것 외에도, 중앙 IT 그룹만 외부 액세스 및 구독에 대한 최상위 권한을 제어할 수 있습니다. 워크로드 그룹은 또한 중앙 IT 부서와는 별도로 해당 VNet의 리소스 및 권한을 제어할 수 있습니다.

VDC를 분할하면 여러 프로젝트를 여러 LOB(기간 업무)에 안전하게 호스트할 수 있습니다. 모든 프로젝트에는 격리된 다른 환경(개발, UAT, 프로덕션)이 필요합니다. 이러한 각 환경에 대해 별도의 Azure 구독을 유지하면 자연스럽게 격리가 이루어집니다.

[![5]][5]

위의 다이어그램은 조직의 프로젝트, 사용자, 그룹 및 Azure 구성 요소가 배포되는 환경 간의 관계를 보여줍니다.

일반적으로 IT 부서에서 환경(또는 계층)은 여러 애플리케이션이 배포되고 실행되는 시스템입니다. 대기업은 개발 환경(처음에 변경이 수행되고 테스트됨) 및 프로덕션 환경(최종 사용자가 사용)을 사용합니다. 이러한 환경은 분리되며, 각 환경 사이에는 단계별 배포(롤아웃), 테스트 및 롤백(문제가 있는 경우)을 허용하는 몇 개의 스테이징 환경이 있습니다. 배포 아키텍처는 매우 다양하지만 일반적으로 개발(DEV)에서 시작하고 프로덕션(PROD)에서 끝나는 기본적인 프로세스가 계속 유지됩니다.

이러한 종류의 다중 계층 환경에 대한 일반적인 아키텍처는 개발 및 테스트용 Azure DevOps, 준비용 UAT 및 프로덕션 환경으로 구성됩니다. 조직에서는 단일 또는 여러 Azure AD 테넌트를 사용하여 이러한 환경에 대한 액세스 및 권한을 정의할 수 있습니다. 위 다이어그램에서는 Azure DevOps 및 UAT에 사용되는 하나의 Azure AD 테넌트와 프로덕션에만 사용되는 Azure 테넌트가 있는 경우를 보여줍니다.

다른 Azure AD 테넌트가 존재하므로 환경이 격리됩니다. 중앙 IT 같은 동일한 사용자 그룹은 다른 URI로 다른 AD 테넌트에 액세스하여 프로젝트의 Azure DevOps 또는 프로덕션 환경에 대한 역할 또는 사용 권한을 수정하기 위한 인증을 받아야 합니다. 다른 환경에 액세스할 때마다 다른 사용자 인증을 사용하면 작동 중단 및 인간의 오류로 인한 기타 문제를 줄일 수 있습니다.

#### <a name="component-type-infrastructure"></a>구성 요소 유형: 인프라

이 구성 요소 유형은 대부분의 지원 인프라가 있는 위치입니다. 또한 중앙 집중식 IT, 보안 및/또는 규정 준수 팀에는 대부분의 시간을 보내는 위치이기도 합니다.

[![6]][6]

인프라 구성 요소는 VDC 구현의 다양한 구성 요소에 대한 상호 연결을 제공하며 허브 및 스포크 둘 다에 존재합니다. 인프라 구성 요소를 유지 및 관리하는 책임은 일반적으로 중앙 IT 부서 및/또는 보안 팀에게 할당됩니다.

IT 인프라 팀의 주요 작업 중 하나는 엔터프라이즈에서 IP 주소 스키마의 일관성을 보장하는 것입니다. VDC 구현에 할당된 사설 IP 주소 공간은 일관되어야 하며 온-프레미스 네트워크에 할당된 사설 IP 주소와 겹치지 않아야 합니다.

온-프레미스 Edge 라우터 또는 Azure 환경의 NAT는 IP 주소 충돌을 방지할 수 있으나 인프라 구성 요소를 더 복잡하게 만듭니다. 관리의 간편성이 VDC의 주요 목표 중 하나이므로 NAT를 사용하여 IP 문제를 처리하는 것은 권장되지 않습니다.

인프라 구성 요소는 다음과 같은 기능을 갖고 있습니다.

-   [**ID 및 디렉터리 서비스**][AAD]. Azure의 모든 리소스 종류에 대한 액세스는 디렉터리 서비스에 저장된 ID에 의해 제어됩니다. 디렉터리 서비스는 사용자 목록 뿐만 아니라 특정 Azure 구독의 리소스에 대한 액세스 권한도 저장합니다. 이러한 서비스는 클라우드 전용으로 존재하거나 Active Directory에 저장된 온-프레미스 ID와 동기화될 수 있습니다.
-   [**Virtual Network**][VPN]. Virtual Network는 VDC의 주요 구성 요소 중 하나이며 Azure 플랫폼에서 트래픽 격리 경계를 만들 수 있도록 합니다. Virtual Network는 각각이 특정 IP 네트워크 접두사(서브넷)를 갖는 단일 또는 여러 가상 네트워크 세그먼트로 구성됩니다. Virtual Network는 IaaS 가상 머신 및 PaaS 서비스가 개인 통신을 구성할 수 있는 내부 경계 영역을 정의합니다. 두 가상 네트워크를 같은 구독에서 같은 고객이 만들었다 하더라도, 한 가상 네트워크의 VM(및 PaaS 서비스)이 다른 가상 네트워크의 VM(및 PaaS 서비스)과 직접 통신할 수 없습니다. 격리는 고객 VM과 통신이 가상 네트워크 안에서 비공개 상태를 유지하는 데 있어 중요한 속성입니다.
-   [**UDR**][UDR]. Virtual Network의 트래픽은 기본적으로 시스템 라우팅 테이블을 기준으로 라우팅됩니다. 사용자 정의 경로는 네트워크 관리자가 시스템 라우팅 테이블의 동작을 덮어쓰고 가상 네트워크 내에서 통신 경로를 정의하기 위해 하나 이상의 서브넷에 연결할 수 있는 사용자 지정 라우팅 테이블입니다. UDR이 있으면 스포크의 송신 트래픽이 허브 및 스포크에 있는 특정 사용자 지정 VM 및/또는 네트워크 가상 어플라이언스와 부하 분산 장치를 통해 전송될 수 있습니다.
-   [**NSG**][NSG]. 네트워크 보안 그룹은 IP 원본, IP 대상, 프로토콜, IP 원본 포트 및 IP 대상 포트에서 트래픽 필터링 역할을 하는 보안 규칙의 목록입니다. NSG는 서브넷 또는 Azure VM에 연결된 가상 NIC 카드 또는 둘 다에 적용될 수 있습니다. NSG는 허브 및 스포크에서 올바른 흐름 제어를 구현하는 데 중요합니다. NSG에서 제공하는 보안 수준은 사용자가 열어둔 포트의 기능 및 해당 용도에 해당합니다. 고객은 IPtables 또는 Windows 방화벽 같은 호스트 기반 방화벽을 사용하여 VM 기준 필터를 추가로 적용해야 합니다.
-   [**DNS**][DNS]. VDC 구현의 VNet에 있는 리소스의 이름 확인은 DNS를 통해 제공됩니다. Azure는 [공개][DNS] 및 [비공개][PrivateDNS] 이름 확인을 위한 DNS 서비스를 제공합니다. 개인 영역은 가상 네트워크 내와 가상 네트워크 간에서 이름 확인을 제공합니다. 개인 영역은 동일한 지역의 가상 네트워크 간뿐만 아니라 지역 및 구독 간에도 걸쳐 있습니다. 공용 확인을 위해 Azure DNS는 DNS 도메인에 대한 호스팅 서비스를 제공하고 Microsoft Azure 인프라를 사용하는 이름 확인을 제공합니다. Azure에 도메인을 호스트하면 다른 Azure 서비스와 동일한 자격 증명, API, 도구 및 대금 청구를 사용하여 DNS 레코드를 관리할 수 있습니다.
-   [**구독**][SubMgmt] 및 [**리소스 그룹 관리**][RGMgmt]. 구독은 Azure에서 여러 리소스 그룹을 만들기 위한 기본 경계를 정의합니다. 구독의 리소스는 리소스 그룹이라는 논리적 컨테이너에 함께 통합됩니다. 리소스 그룹은 VDC 구현의 리소스를 구성하기 위한 논리 그룹을 나타냅니다.
-   [**RBAC**][RBAC]. RBAC를 통해 조직 역할을 특정 Azure 리소스에 액세스하기 위한 권한에 매핑하여 사용자가 일부 작업만 수행하도록 제한할 수 있습니다. RBAC를 사용하면 특정 범위 내의 사용자, 그룹 및 애플리케이션에 적절한 역할을 할당하여 액세스 권한을 부여할 수 있습니다. 역할 할당의 범위는 Azure 구독, 리소스 그룹 또는 단일 리소스일 수 있습니다. RBAC는 권한 상속을 허용합니다. 부모 범위에서 할당된 역할은 역할 내에 포함된 하위 항목에 대한 액세스를 부여합니다. RBAC를 사용하면 업무를 분리하고 사용자에게 해당 작업을 수행하는 데 필요한 만큼의 권한만 부여할 수 있습니다. 예를 들어 RBAC를 사용하여 한 명의 직원은 구독의 가상 머신을 관리하도록 하고, 다른 직원은 동일한 구독 내에서 SQL DB를 관리하도록 할 수 있습니다.
-   [**VNet 피어링**][VNetPeering]. VDC의 인프라를 만드는 데 사용되는 기본 기능은 Azure 데이터 센터 네트워크를 통해 동일한 지역에서 또는 지역 간의 Azure 전 세계 백본을 사용하여 두 VNet(가상 네트워크)을 연결하는 VNet 피어링입니다.

#### <a name="component-type-perimeter-networks"></a>구성 요소 유형: 경계 네트워크

[경계 네트워크][DMZ] 구성 요소를 사용하면 인터넷 연결뿐 아니라 온-프레미스 또는 물리적 데이터 센터 네트워크 사이에 네트워크 연결을 지원할 수 있습니다. 이 네트워크는 네트워크 및 보안 팀이 대부분의 시간을 보내는 위치이기도 합니다.

들어오는 패킷은 스포크의 백 엔드 서버에 도달하기 전에 허브의 보안 어플라이언스를 통과해야 합니다. 방화벽, IDS, IPS를 예로 들 수 있습니다. 워크로드의 인터넷 바인딩 패킷도 네트워크에 도착하기 전에 경계 네트워크의 보안 어플라이언스를 통과합니다. 이 흐름의 목적은 정책 적용, 검사 및 감사입니다.

경계 네트워크 구성 요소는 다음과 같은 기능을 제공합니다.

-   [가상 네트워크][VNet], [UDR][UDR] 및 [NSG][NSG]
-   [네트워크 가상 어플라이언스][NVA]
-   [Azure Load Balancer][ALB]
-   [Azure Application Gateway][AppGW] 및 [WAF(웹 애플리케이션 방화벽)][WAF]
-   [공용 IP][PIP]
-   [Azure Front Door][AFD]
-   [Azure Firewall][AzFW]

일반적으로 중앙 IT 및 보안 팀은 경계 네트워크의 요구 사항을 정의하고 작업을 수행합니다.

[![7]][7]

위의 다이어그램에는 둘 다 DMZ 및 vWAN 허브에 있으며 인터넷과 온-프레미스 네트워크에 액세스할 수 있는 두 개의 경계 네트워크 적용을 보여줍니다. DMZ 허브에서 인터넷의 경계 네트워크는 다양한 WAF(웹 애플리케이션 방화벽) 및/또는 Azure Firewalls 팜을 사용하여 많은 수의 LOB를 지원하도록 확장할 수 있습니다. vWAN 허브에서는 필요에 따라 VPN 또는 ExpressRoute를 통해 확장성이 우수한 분기 간 연결 및 분기-Azure 간 연결이 설정됩니다.

[**가상 네트워크**][VNet]. 허브는 일반적으로 여러 유형의 서비스를 호스트하기 위해 NVA, WAF 및 Azure Application Gateway 인스턴스를 통해 인터넷으로 들어오고 나가는 트래픽을 필터링하고 조사하는 여러 서브넷이 있는 가상 네트워크에 구축됩니다.

[**UDR**][UDR] UDR을 사용하여 고객은 보안 경계 정책 적용, 감사 및 검사를 위해 방화벽, IDS/IPS 및 기타 가상 어플라이언스를 배포하고 이러한 보안 어플라이언스를 통해 네트워크 트래픽을 라우팅할 수 있습니다. UDR은 VDC 구현에서 사용되는 특정 사용자 지정 VM, 네트워크 가상 어플라이언스 및 내부 부하 분산 장치를 통한 트래픽 전송을 보장하기 위해 허브 및 스포크 둘 다에서 생성될 수 있습니다. 스포크에 있는 VM에서 생성된 트래픽이 올바른 가상 어플라이언스로 전송되도록 하기 위해 UDR은 내부 부하 분산 장치의 프런트 엔드 IP 주소를 다음 홉으로 설정하여 스포크의 서브넷에 설정되어야 합니다. 내부 부하 분산 장치는 내부 트래픽을 가상 어플라이언스(부하 분산 장치 백 엔드 풀)에 배포합니다.

[**Azure Firewall**][AzFW]은 Azure Virtual Network 리소스를 보호하는 관리되는 클라우드 기반 네트워크 보안 서비스입니다. 고가용성 및 무제한 클라우드 확장성이 내장되어 있는 서비스 형태의 완전한 상태 저장 방화벽입니다. 구독 및 가상 네트워크 전반에 걸쳐 애플리케이션 및 네트워크 연결 정책을 중앙에서 만들고, 적용하고 기록할 수 있습니다. Azure Firewall은 가상 네트워크 리소스에 고정 공용 IP 주소를 사용합니다. 외부 방화벽이 사용자의 가상 네트워크에서 시작되는 트래픽을 식별할 수 있습니다. 이 서비스는 로깅 및 분석을 위해 Azure Monitor와 완전히 통합됩니다.

[**네트워크 가상 어플라이언스**][NVA]. 허브에서 인터넷에 액세스할 수 있는 경계 네트워크는 일반적으로 Azure Firewall 인스턴스 또는 방화벽이나 WAF(웹 애플리케이션 방화벽) 팜을 통해 관리됩니다.

여러 LOB는 일반적으로 여러 웹 애플리케이션을 사용합니다. 이러한 애플리케이션은 다양한 취약점 및 악용 가능성을 겪게 됩니다. 웹 애플리케이션 방화벽은 일반적인 방화벽보다는 좀 더 심도 있는 방식으로 웹 애플리케이션 HTTP/HTTPS에 대한 공격을 감지하는 데 사용되는 특수한 제품입니다. 전형적인 방화벽 기술에 비해 WAF는 위협으로부터 내부 웹 서버를 보호하기 위한 특정 기능 집합을 포함합니다.

Azure Firewall 또는 NVA 방화벽은 모두 공통 관리 평면을 사용하며, 스포크에 호스트되는 워크로드를 보호하고 온-프레미스 네트워크에 대한 액세스를 제어하는 보안 규칙 세트를 적용합니다. Azure Firewall은 확장성이 내장되어 있고, NVA 방화벽은 부하 분산 장치 뒤에서 수동으로 확장할 수 있습니다. 일반적으로 방화벽 팜은 WAF에 비해 덜 특수한 소프트웨어를 사용하지만, 송신 및 수신 중인 트래픽 유형을 필터링하고 검사하기 위한 광범위한 애플리케이션 범위를 유지합니다. NVA 접근 방식을 사용하는 경우 Azure 마켓플레이스에서 찾아서 배포할 수 있습니다.

인터넷에서 시작하는 트래픽에 하나의 Azure Firewalls 세트(또는 NVA)를 사용하고, 온-프레미스에서 시작하는 트래픽에 또 하나의 세트를 사용하세요. 방화벽 집합 하나를 두 트래픽에 모두 사용하면 두 네트워크 트래픽 집합 사이에 보안 경계가 없어지므로 보안 위험이 초래됩니다. 별도의 방화벽 레이어를 사용하면 보안 규칙을 검사하는 복잡성이 줄어들고 들어오는 네트워크 요청에 해당하는 규칙이 명확해집니다.

인터넷에서 시작되는 트래픽에 하나의 Azure Firewall 인스턴스 또는 NVA 집합을 사용하고, 온-프레미스에서 시작되는 트래픽에는 또 다른 집합을 사용하는 것이 좋습니다. 방화벽 집합 하나를 두 트래픽에 모두 사용하면 두 네트워크 트래픽 집합 사이에 보안 경계가 없어지므로 보안 위험이 초래됩니다. 별도의 방화벽 레이어를 사용하면 보안 규칙을 검사하는 복잡성이 줄어들고 들어오는 네트워크 요청에 해당하는 규칙이 명확해집니다.

[**Azure Load Balancer**][ALB]는 고가용성 계층 4(TCP, UDP) 서비스를 제공하여 들어오는 트래픽을 부하 분산 집합에 정의된 서비스 인스턴스 간에 분산할 수 있도록 합니다. 프런트 엔드 엔드포인트(공용 IP 엔드포인트 또는 개인 IP 엔드포인트)에서 부하 분산 장치로 전송된 트래픽은 주소 변환과 관계없이 백 엔드 IP 주소 풀 집합(예: 네트워크 가상 어플라이언스 또는 VM)으로 다시 배포될 수 있습니다.

또한 Azure Load Balancer는 다양한 서버 인스턴스의 상태를 검사할 수 있으며, 프로브가 응답하지 않을 경우 부하 분산 장치는 비정상 인스턴스로의 트래픽 전송을 중지합니다. VDC에서는 외부 부하 분산 장치가 허브 및 스포크에 배포됩니다. 허브에서는 부하 분산 장치가 스포크의 서비스에 트래픽을 효율적으로 라우팅하는 데 사용되며, 스포크에서는 애플리케이션 트래픽을 관리하는 데 사용됩니다.

[**AFD(Azure Front Door)**][AFD]는 가용성과 확장성이 우수한 Microsoft의 웹 애플리케이션 가속 플랫폼, 글로벌 HTTP 부하 분산 장치, 애플리케이션 보호 및 Content Delivery Network입니다. Microsoft 글로벌 네트워크 Edge의 100개가 넘는 위치에서 실행되는 AFD를 사용하면 동적 웹 애플리케이션 및 정적 콘텐츠를 빌드, 운영 및 규모 확장할 수 있습니다. AFD는 애플리케이션에 세계적 수준의 최종 사용자 성능, 통합된 지역/스탬프 유지 관리 자동화, BCDR 자동화, 통합 클라이언트/사용자 정보, 캐싱 및 서비스 인사이트를 제공합니다. 이 플랫폼은 기본적으로 Azure에서 개발, 운영 및 지원되는 성능, 안정성 및 지원 SLA, 규정 준수 인증, 감사 가능한 보안 사례를 제공합니다.

[**Application Gateway**][AppGW] Microsoft Azure Application Gateway는 전용 가상 어플라이언스이며 ADC(애플리케이션 배달 컨트롤러)를 서비스로 제공하여 다양한 계층 7 부하 분산 기능을 제공합니다. 따라서 사용자는 Application Gateway에 CPU 집약적인 SSL 종료를 오프로드하여 웹 팜 생산성을 최적화할 수 있습니다. 또한 들어오는 트래픽의 라운드 로빈 배포, 쿠키 기반 세션 선호도, URL 경로 기반 라우팅 및 단일 Application Gateway의 여러 웹 사이트를 호스트할 수 있는 능력을 비롯한 다른 계층 7 라우팅 기능이 제공됩니다. WAF(웹 애플리케이션 방화벽) 또한 Application Gateway WAF SKU의 일부로 제공됩니다. 이 SKU 기능은 일반적인 웹 취약점 및 악용으로부터 웹 애플리케이션을 보호합니다. Application Gateway는 인터넷 연결 게이트웨이, 내부 전용 게이트웨이 또는 둘의 조합으로 구성할 수 있습니다. 

[**공용 IP**][PIP]. 일부 Azure 기능을 사용하면 서비스 엔드포인트를 공용 IP 주소에 연결할 수 있으므로 인터넷에서 리소스에 액세스할 수 있습니다. 엔드포인트에서는 NAT(Network Address Translation)를 사용하여 트래픽을 Azure Virtual Network상의 내부 주소와 포트로 라우팅합니다. 이 경로가 외부 트래픽을 가상 네트워크 내부로 전달하는 기본 방법입니다. 공용 IP 주소를 구성하여 어떤 트래픽을 안으로 들일 것인지, 가상 네트워크의 어느 부분에서 어떻게 전환할 것인지 결정할 수 있습니다.

[**Azure DDoS Protection Standard**][DDOS]는 [기본 서비스][DDOS] 계층에 대해 Azure Virtual Network 리소스에 맞게 특별히 조정된 추가적인 완화 기능을 제공합니다. DDoS Protection 표준은 간단히 사용하도록 설정할 수 있고 애플리케이션을 변경할 필요가 없습니다. 보호 정책은 전용 트래픽 모니터링 및 기계 학습 알고리즘을 통해 조정됩니다. 정책은 가상 네트워크에 배포된 리소스와 연결된 공용 IP 주소에 적용됩니다. Azure Load Balancer, Azure Application Gateway 및 Azure Service Fabric 인스턴스를 예로 들 수 있습니다. 공격을 받고 있을 때 기록을 위해 Azure Monitor 뷰를 통해 실시간 원격 분석을 사용할 수 있습니다. Azure Application Gateway 웹 애플리케이션 방화벽을 통해 애플리케이션 레이어 보호를 추가할 수 있습니다. IPv4 Azure 공용 IP 주소에 대한 보호가 제공됩니다.

#### <a name="component-type-monitoring"></a>구성 요소 유형: 모니터링

모니터링 구성 요소는 다른 모든 구성 요소 유형의 가시성 및 경고를 제공합니다. 모든 팀은 액세스 권한이 있는 구성 요소 및 서비스에 대한 모니터링에 액세스할 수 있습니다. 중앙 지원 센터 또는 작업 팀이 있는 경우 이러한 구성 요소에서 제공하는 데이터에 대한 통합된 액세스 권한이 필요합니다.

Azure는 Azure 호스팅 리소스의 동작을 추적하기 위한 다양한 유형의 로깅 및 모니터링 서비스를 제공합니다. Azure의 워크로드 거버넌스 및 제어는 로그 데이터 수집뿐 아니라 보고된 특정 이벤트를 기준으로 작업을 트리거하는 기능을 토대로 제공됩니다.

[**Azure Monitor**][Monitor]. Azure에는 모니터링 공간에서 특정 역할이나 태스크를 개별적으로 수행하는 여러 서비스가 포함됩니다. 이러한 서비스는 애플리케이션 및 애플리케이션을 지원하는 Azure 리소스로부터 원격 분석데이터를 수집하고 분석하고 조치를 취하는 포괄적인 솔루션을 제공합니다. 이러한 서비스가 하이브리드 모니터링 환경을 제공하기 위해 중요한 온-프레미스 리소스를 모니터링하기 위해 작동할 수도 있습니다. 사용 가능한 도구와 데이터를 이해하는 것이 애플리케이션에 대한 전체 모니터링 전략을 개발하는 첫 번째 단계입니다.

Azure에는 다음과 같은 2가지 주요 로그 유형이 있습니다.

-   이전에는 **작업 로그**라고 불렀던 [Azure 활동 로그][ActLog]는 Azure 구독에 있는 리소스에서 수행된 작업에 대한 정보를 제공합니다. 이러한 로그는 구독에 대한 제어 평면 이벤트를 보고합니다. 모든 Azure 리소스는 감사 로그를 생성합니다.

-   [Azure Monitor 진단 로그][DiagLog]는 해당 리소스의 작업에 대한 풍부하고 빈번한 데이터를 제공하는 리소스에서 생성된 로그입니다. 이러한 로그의 내용은 리소스 유형에 따라 달라집니다.

[![9]][9]

NSG 로그, 특히 다음 정보를 추적하는 것이 중요합니다.

-   [이벤트 로그][NSGLog]는 VM 및 MAC 주소 기반 인스턴스 역할에 적용된 NSG 규칙에 대한 정보를 제공합니다.
-   [카운터 로그][NSGLog]는 트래픽을 허용하거나 거부하기 위해 각 NSG 규칙이 실행된 횟수를 추적합니다.

모든 로그는 감사, 정적 분석 또는 백업 목적으로 Azure 스토리지 계정에 저장할 수 있습니다. 로그를 Azure 스토리지 계정에 저장하면 고객은 다양한 유형의 프레임워크를 사용하여 이 데이터를 검색, 준비, 분석, 시각화한 후 클라우드 리소스의 상태를 보고할 수 있습니다. 

대기업은 아마도 온-프레미스 시스템을 모니터링하기 위한 표준 프레임워크를 이미 갖추고 있을 것입니다. 클라우드 배포에서 생성된 로그를 통합하도록 이러한 프레임워크를 확장할 수 있습니다. [Azure Log Analytics](/azure/log-analytics/log-analytics-queries)를 사용하면 조직은 클라우드의 모든 로깅을 유지할 수 있습니다. Log Analytics는 클라우드 기반 서비스로 구현됩니다. 따라서 최소의 인프라 서비스 투자로 신속하게 작동할 수 있습니다. 또한 Log Analytics는 System Center Operations Manger와 같은 System Center 구성 요소와 통합하여 기존 관리 투자를 클라우드로 확장할 수 있습니다. 

Log Analytics는 운영 체제, 애플리케이션, 인프라 클라우드 구성 요소에서 생성된 로그 및 성능 데이터를 수집하고, 상호 연관 짓고, 검색하고, 실행하는 데 도움이 되는Azure의 서비스입니다. 이 기능은 통합된 검색 및 사용자 지정 대시보드를 사용하여 VDC 구현의 모든 작업과 관련된 모든 레코드를 분석함으로써 실시간으로 전반적인 작업을 이해할 수 있도록 합니다.

[Azure Network Watcher][NetWatch]는 Azure 가상 네트워크의 리소스를 모니터링 및 진단하고 메트릭을 보고 그에 대한 로그를 활성화 또는 비활성화하는 도구를 제공합니다. 다음과 같은 기능을 허용하는 다면적 서비스입니다.
-    가상 머신과 엔드포인트 간의 통신 모니터링.
-    가상 네트워크의 리소스와 해당 리소스의 관계 보기.
-    VM에 대한 네트워크 트래픽 필터링 문제 진단.
-    VM에서 네트워크 경로 설정 문제 진단.
-    VM에서 아웃바운드 연결 진단.
-    VM에 대한 패킷 캡처.
-    Azure 가상 네트워크 게이트웨이 및 연결에 대한 문제 진단.
-    Azure 지역과 인터넷 서비스 공급자 간의 상대 대기 시간 결정.
-    네트워크 인터페이스에 대한 보안 규칙 보기.
-    네트워크 메트릭 보기.
-    네트워크 보안 그룹에 대한 트래픽 분석.
-    네트워크 리소스에 대한 진단 로그 보기.

Operations Management Suite의 [네트워크 성능 모니터][NPM] 솔루션은 자세한 네트워크 정보를 종합적으로 제공할 수 있습니다. 이 정보에는 Azure 네트워크 및 온-프레미스 네트워크의 단일 뷰가 포함됩니다. 이 솔루션은 ExpressRoute 및 공용 서비스에 대한 특정 모니터를 사용합니다.

#### <a name="component-type-workloads"></a>구성 요소 유형: 워크로드

워크로드 구성 요소는 실제 애플리케이션 및 서비스가 있는 위치입니다. 애플리케이션 개발 팀이 대부분의 시간을 보내는 위치이기도 합니다.

워크로드 가능성은 무궁무진합니다. 다음은 몇 가지 가능한 워크로드 유형입니다.

**내부 LOB 애플리케이션**: LOB(기간 업무) 애플리케이션은 엔터프라이즈의 진행 중인 작업에 중요한 컴퓨터 애플리케이션입니다. LOB 애플리케이션은 다음과 같은 몇 가지 공통된 특성을 갖습니다.

-   기본적으로 **대화형**. 데이터가 입력되면 결과 또는 보고서가 반환됩니다.
-   **데이터 중심**&mdash;데이터 집약적이어서 데이터베이스 또는 다른 스토리지에 자주 액세스합니다.
-   **통합적**&mdash;조직 내부 또는 외부의 다른 시스템과 통합됩니다.

**고객 관련 웹 사이트(인터넷 또는 내부 연결)**: 인터넷과 상호 작용하는 대부분의 애플리케이션은 웹 사이트입니다. Azure에서는 IaaS VM 또는 [Azure Web Apps][WebApps] 사이트(PaaS)에서 웹 사이트를 실행하는 기능을 제공합니다. Azure Web Apps는 VNet과의 통합을 지원하여 스포크 네트워크 영역에서 웹앱의 배포를 허용합니다. 내부용 웹 사이트의 경우에는 비공개 VNet의 비공개 비인터넷 라우팅 가능 주소를 통해 리소스에 액세스할 수 있으므로 공개 인터넷 엔드포인트를 공개할 필요가 없습니다.

**빅 데이터/분석**: 데이터를 큰 볼륨으로 확장해야 하는 경우 데이터베이스가 제대로 확장되지 않을 수 있습니다. Hadoop 기술은 많은 수의 노드에서 동시에 분산 쿼리를 실행하는 시스템을 제공합니다. 고객은 IaaS VM 또는 PaaS([HDInsight][HDI]) 중 하나에서 데이터 작업을 실행할 수 있습니다. HDInsight는 위치 기반 VNet으로의 배포를 지원하며, VDC의 스포크에 있는 클러스터에 배포할 수 있습니다.

**이벤트 및 메시징**: [Azure Event Hubs][EventHubs]는 수백만 개의 이벤트를 수집, 변환 및 저장하는 하이퍼스케일(hyper-scale) 원격 분석 수집 서비스입니다. 분산 스트리밍 플랫폼으로서 Azure Event Hubs는 짧은 대기 시간과 구성 가능한 시간 보존을 제공하여 엄청난 양의 원격 분석을 Azure로 수집하고 여러 애플리케이션에서 데이터를 읽을 수 있게 해줍니다. Event Hubs를 통해 단일 스트림은 실시간 및 일괄 처리 기반 파이프라인을 모두 지원할 수 있습니다.

[Azure Service Bus][ServiceBus]를 통해 애플리케이션과 서비스 간에 매우 안정적인 클라우드 메시지 서비스를 구현할 수 있습니다. 클라이언트와 서버 간의 비동기 조정된 메시징, 구조적 FIFO(선입 선출) 메시지 및 게시/구독 기능을 제공합니다.

[![10]][10]

### <a name="making-the-vdc-highly-available-multiple-vdcs"></a>고가용성 VDC 구현: 여러 개의 VDC

지금까지 이 문서에서는 단일 VDC의 디자인을 집중적으로 살펴보고 복원력에 기여하는 기본 구성 요소와 아키텍처를 설명했습니다. Azure Load Balancer, NVA, 가용성 집합, 확장 집합과 같은 Azure 기능과 기타 메커니즘은 프로덕션 서비스에 견고한 SLA 수준을 구축할 수 있는 시스템을 구현하도록 합니다.

그러나 단일 VDC는 일반적으로 단일 지역 내에 구현되므로 전체 지역에 영향을 주는 주요 중단에 취약할 수 있습니다. 높은 SLA가 필요한 고객은 동일한 프로젝트를 다른 지역에 있는 두 개 이상의 VDC 구현으로 배포하여 서비스를 보호해야 합니다.

SLA 문제 외에도, 여러 VDC 구현을 배포하는 것이 적절한 일반적인 몇 가지 시나리오가 있습니다.

-   지역 또는 글로벌 서비스.
-   재해 복구
-   데이터 센터 간에 트래픽을 전환하는 메커니즘.

#### <a name="regionalglobal-presence"></a>지역/글로벌 서비스

Azure 데이터 센터는 전 세계 여러 지역에 있습니다. 고객은 여러 Azure 데이터 센터를 선택할 경우 상호 관련된 2가지 요인인 지리적 거리와 대기 시간을 고려해야 합니다. 최상의 사용자 환경을 제공하려면 각 VDC 구현 간의 지리적 거리와 각 VDC 구현 및 최종 사용자 간의 거리를 평가하세요.

VDC 구현이 호스트되는 지역은 조직이 운영되는 모든 법적 관할권에 의해 설정된 규정 요구 사항을 준수해야 합니다.

#### <a name="disaster-recovery"></a>재해 복구

재해 복구 계획의 디자인은 워크로드 유형과 여러 VDC 구현 간에 워크로드의 상태를 동기화하는 기능에 따라 달라집니다. 대부분의 고객이 바라는 이상적인 메커니즘은 빠른 장애 조치(failover) 메커니즘이며, 이를 위해서는 여러 VDC 구현을 실행하는 배포 사이에 애플리케이션 데이터 동기화가 필요할 수 있습니다. 그러자 재해 복구 계획을 설계할 때는 대부분의 애플리케이션이 이러한 데이터 동기화로 인해 발생할 수 있는 대기 시간에 민감하다는 사실을 감안하는 것이 중요합니다.

여러 VDC 구현에 있는 애플리케이션의 동기화 및 하트비트 모니터링을 위해서는 이러한 VDC 구현이 네트워크를 통해 통신할 수 있어야 합니다. 서로 다른 지역의 두 VDC 구현을 다음을 통해 연결할 수 있습니다.

-   VNet 피어링 - VNet 피어링은 여러 지역의 허브를 연결할 수 있습니다
-   각 VDC 구현의 VDC 허브가 동일한 ExpressRoute 회로에 연결되는 경우 ExpressRoute 전용 피어링
-   회사 백본을 통해 연결된 여러 ExpressRoute 회로 및 ExpressRoute 회로로 연결된 여러 VDC 구현
-   각 Azure 지역에 있는 VDC 구현의 허브 영역 사이의 사이트 간 VPN 연결

일반적으로 VNet 피어링 또는 ExpressRoute 연결은 Microsoft 백본을 통해 전송할 경우 대역폭이 더 높아지고 대기 시간이 일관되게 유지되므로 선호되는 네트워크 연결 유형입니다.

고객은 네트워크 검증 테스트를 실행하여 연결의 대기 시간 및 대역폭을 확인하고, 테스트 결과를 바탕으로 동기 또는 비동기 데이터 복제가 적절한지 여부를 확인하는 것이 좋습니다. 또한 최적의 복구 시간 목표(RTO) 관점에서 이러한 결과를 저울질하는 것이 중요합니다.

#### <a name="disaster-recovery-diverting-traffic-from-one-region-to-another"></a>재해 복구: 다른 지역으로 트래픽 우회

[Azure Traffic Manager][TM]는 여러 다른 VDC 구현의 공용 엔드포인트에 대한 서비스 상태를 주기적으로 확인하고, 이러한 엔드포인트에 장애가 발생할 경우 자동으로 DNS(Domain Name System)를 사용하여 보조 VDC로 라우팅합니다. 

Traffic Manager는 DNS를 사용하므로 Azure 공용 엔드포인트 전용입니다.  서비스는 일반적으로 VDC 구현의 정상 인스턴스에서 Azure VM 및 Web Apps에 대한 트래픽을 제어하거나 우회하는 데 사용됩니다. Traffic Manager는 전체 Azure 지역에 장애가 발생하더라도 복원되며, 몇 가지 조건에 따라 여러 다른 VDC에 있는 서비스 엔드포인트에 대한 사용자 트래픽 분산을 제어할 수 있습니다. 예: 특정 VDC 구현의 서비스 장애 또는 네트워크 대기 시간이 가장 낮은 VDC 구현 선택.

### <a name="summary"></a>요약

가상 데이터 센터는 데이터 센터 마이그레이션의 한 방법으로, Azure에서 클라우드 리소스 사용을 극대화하고, 비용을 절감하고, 시스템 거버넌스를 간소화하는 확장 가능한 아키텍처를 만듭니다. VDC는 허브 및 스포크 네트워크 토폴로지를 기준으로 하며 허브에 일반적인 공유 서비스를 제공하고 스포크에서 특정 애플리케이션/워크로드를 허용합니다. 또한 VDC는 여러 부서(예: 중앙 IT, DevOps, 운영 및 유지 관리)가 특정한 역할을 수행하면서 서로 함께 협력하는 회사 역할 구조와 일치합니다. VDC는 "리프트 및 시프트" 마이그레이션에 대한 요구 사항을 충족할 뿐만 아니라 네이티브 클라우드 배포에도 많은 이점을 제공합니다.

## <a name="references"></a>참조

이 문서에서는 다음 기능에 대해 살펴보았습니다. 자세한 내용을 보려면 링크를 따라가세요.

| | | |
|-|-|-|
|네트워크 기능|부하 분산|연결|
|[Azure Virtual Networks][VNet]</br>[네트워크 보안 그룹][NSG]</br>[NSG 로그][NSGLog]</br>[사용자 정의 라우팅][UDR].</br>[네트워크 가상 어플라이언스][NVA]</br>[공용 IP 주소][PIP]</br>[Azure DDOS][DDOS]</br>[Azure Firewall][AzFW]</br>[Azure DNS][DNS]|[Azure Front Door][AFD]</br>[Azure Load Balancer(L3)][ALB]</br>[Application Gateway(L7)][AppGW]</br>[웹 응용 프로그램 방화벽][WAF]</br>[Azure Traffic Manager][TM]</br></br></br></br></br> |[VNet 피어링][VNetPeering]</br>[가상 사설망][VPN]</br>[Virtual WAN][vWAN]</br>[ExpressRoute][ExR]</br>[ExpressRoute Direct][ExRD]</br></br></br></br></br>
|ID</br>|모니터링</br>|모범 사례</br>|
|[Azure Active Directory][AAD]</br>[Multi-Factor Authentication][MFA]</br>[역할 기반 Access Control][RBAC]</br>[기본 Azure AD 역할][Roles]</br></br></br> |[Network Watcher][NetWatch]</br>[Azure Monitor][Monitor]</br>[활동 로그][ActLog]</br>[진단 로그][DiagLog]</br>[Microsoft Operations Management Suite][OMS]</br>[네트워크 성능 모니터][NPM]|[경계 네트워크 모범 사례][DMZ]</br>[구독 관리][SubMgmt]</br>[리소스 그룹 관리][RGMgmt]</br>[Azure 구독 제한][Limits] </br></br></br>|
|기타 Azure 서비스|
|[Azure Web Apps][WebApps]</br>[HDInsights(Hadoop)][HDI]</br>[Event Hubs][EventHubs]</br>[Service Bus][ServiceBus]|

## <a name="next-steps"></a>다음 단계

 - VDC 허브 및 스포크 디자인에 대한 기본 기술인 [VNet 피어링][VNetPeering] 알아보기
 - [Azure AD][AAD]를 구현하여 [RBAC][RBAC] 탐색 시작
 - 조직의 구조, 요구 사항 및 정책을 충족하도록 구독 및 리소스 관리 모델과 RBAC 모델을 개발하세요. 가장 중요한 작업은 계획입니다. 재구성, 합병, 신제품 라인 등에 대한 실제 계획도 중요합니다.

<!--Image References-->
[0]: ./images/networking-redundant-equipment.png "구성 요소 중복 예제" 
[1]: ./images/networking-vdc-high-level.png "고급 수준의 허브 및 스포크 VDC 예제"
[2]: ./images/networking-hub-spokes-cluster.png "허브 및 스포크 클러스터"
[3]: ./images/networking-spoke-to-spoke.png "스포크-스포크"
[4]: ./images/networking-vdc-block-level-diagram.png "VDC의 블록 수준 다이어그램"
[5]: ./images/networking-users-groups-subsciptions.png "사용자, 그룹, 구독 및 프로젝트"
[6]: ./images/networking-infrastructure-high-level.png "고급 수준의 인프라 다이어그램"
[7]: ./images/networking-highlevel-perimeter-networks.png "고급 수준의 인프라 다이어그램"
[8]: ./images/networking-vnet-peering-perimeter-neworks.png "VNet 피어링 및 경계 네트워크"
[9]: ./images/networking-high-level-diagram-monitoring.png "모니터링에 대한 높은 수준의 다이어그램"
[10]: ./images/networking-high-level-workloads.png "워크로드에 대한 높은 수준의 다이어그램"

<!--Link References-->
[Limits]: /azure/azure-subscription-service-limits
[Roles]: /azure/role-based-access-control/built-in-roles
[VNet]: /azure/virtual-network/virtual-networks-overview
[NSG]: /azure/virtual-network/virtual-networks-nsg
[DNS]: /azure/dns/dns-overview
[PrivateDNS]: /azure/dns/private-dns-overview
[VNetPeering]: /azure/virtual-network/virtual-network-peering-overview 
[UDR]: /azure/virtual-network/virtual-networks-udr-overview 
[RBAC]: /azure/role-based-access-control/overview
[MFA]: /azure/multi-factor-authentication/multi-factor-authentication
[AAD]: /azure/active-directory/active-directory-whatis
[VPN]: /azure/vpn-gateway/vpn-gateway-about-vpngateways 
[ExR]: /azure/expressroute/expressroute-introduction
[ExRD]: /azure/expressroute/expressroute-erdirect-about
[vWAN]: /azure/virtual-wan/virtual-wan-about
[NVA]: /azure/architecture/reference-architectures/dmz/nva-ha
[AzFW]: /azure/firewall/overview
[SubMgmt]: /azure/architecture/cloud-adoption/appendix/azure-scaffold 
[RGMgmt]: /azure/azure-resource-manager/resource-group-overview
[DMZ]: /azure/best-practices-network-security
[ALB]: /azure/load-balancer/load-balancer-overview
[DDOS]: /azure/virtual-network/ddos-protection-overview
[PIP]: /azure/virtual-network/resource-groups-networking#public-ip-address
[AFD]: /azure/frontdoor/front-door-overview
[AppGW]: /azure/application-gateway/application-gateway-introduction
[WAF]: /azure/application-gateway/application-gateway-web-application-firewall-overview
[Monitor]: /azure/monitoring-and-diagnostics/
[ActLog]: /azure/monitoring-and-diagnostics/monitoring-overview-activity-logs 
[DiagLog]: /azure/monitoring-and-diagnostics/monitoring-overview-of-diagnostic-logs
[NSGLog]: /azure/virtual-network/virtual-network-nsg-manage-log
[OMS]: /azure/operations-management-suite/operations-management-suite-overview
[NPM]: /azure/log-analytics/log-analytics-network-performance-monitor
[NetWatch]: /azure/network-watcher/network-watcher-monitoring-overview
[WebApps]: /azure/app-service/
[HDI]: /azure/hdinsight/hdinsight-hadoop-introduction
[EventHubs]: /azure/event-hubs/event-hubs-what-is-event-hubs 
[ServiceBus]: /azure/service-bus-messaging/service-bus-messaging-overview
[TM]: /azure/traffic-manager/traffic-manager-overview
