---
title: 'Azure 도입: 중간'
description: 엔터프라이즈가 Azure를 채택하기 위해 필요한 중간 지식 수준 설명
author: petertay
ms.openlocfilehash: 227d9558647ed8076b2832d95e192f2f0c43b9db
ms.sourcegitcommit: 26b04f138a860979aea5d253ba7fecffc654841e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36206364"
---
# <a name="azure-cloud-adoption-guide-intermediate-overview"></a><span data-ttu-id="0d8a3-103">Azure 클라우드 도입 가이드: 중간 개요</span><span class="sxs-lookup"><span data-stu-id="0d8a3-103">Azure Cloud Adoption Guide: Intermediate Overview</span></span>

<span data-ttu-id="0d8a3-104">기본 도입 단계에서는 Azure 리소스 거버넌스의 기본 개념을 도입했습니다.</span><span class="sxs-lookup"><span data-stu-id="0d8a3-104">In the foundational adoption stage, you were introduced to the basic concepts of Azure resource governance.</span></span> <span data-ttu-id="0d8a3-105">기본 단계는 Azure 도입을 시작하기 위해 디자인되었으며 단일 소규모 팀을 사용하여 단순 워크로드를 배포하는 방법을 설명했습니다.</span><span class="sxs-lookup"><span data-stu-id="0d8a3-105">The foundational stage was designed to get you started with your Azure adoption journey, and it walked you through how to deploy a simple workload with a single small team.</span></span> <span data-ttu-id="0d8a3-106">실제로 대부분의 대규모 조직에는 동시에 많은 다른 워크로드에서 작업하는 많은 팀이 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d8a3-106">In reality, most large organizations have many teams that are working on many different workloads at the same time.</span></span> <span data-ttu-id="0d8a3-107">예상하는 것처럼 단순한 거버넌스 모델은 복잡한 조직 및 개발 시나리오를 관리하기에 충분하지 않습니다.</span><span class="sxs-lookup"><span data-stu-id="0d8a3-107">As you would expect, a simple governance model is not sufficient to manage more complex organizational and development scenarios.</span></span>

<span data-ttu-id="0d8a3-108">Azure 도입의 중간 단계의 중점은 새로운 여러 Azure 개발 워크로드에서 작업하는 여러 팀에 대한 거버넌스 모델을 디자인하는 것에 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d8a3-108">The focus of the intermediate stage of Azure adoption is designing your governance model for multiple teams working on multiple new Azure development workloads.</span></span>  

<span data-ttu-id="0d8a3-109">가이드의 이 단계에 대한 대상은 다음과 같은 조직 내의 가상 사용자입니다.</span><span class="sxs-lookup"><span data-stu-id="0d8a3-109">The audience for this stage of the guide is the following personas within your organization:</span></span>
- <span data-ttu-id="0d8a3-110">*재무:* Azure에 대한 재무 약정의 소유자로서 청구 및 차지백을 포함한 리소스 소비 비용을 추적하기 위한 절차 및 정책 개발을 담당합니다.</span><span class="sxs-lookup"><span data-stu-id="0d8a3-110">*Finance:* owner of the financial commitment to Azure, responsible for developing policies and procedures for tracking resource consumption costs including billing and chargeback.</span></span>
- <span data-ttu-id="0d8a3-111">*중앙 IT:* 리소스 관리 및 액세스, 워크로드 상태 및 모니터링을 포함한 조직의 클라우드 리소스 관리를 담당합니다.</span><span class="sxs-lookup"><span data-stu-id="0d8a3-111">*Central IT:* responsible for governing your organization's cloud resources including resource management and access, as well as workload health and monitoring.</span></span>
- <span data-ttu-id="0d8a3-112">*공유 인프라 소유자*: 온-프레미스에서 클라우드까지 네트워크 연결을 담당하는 기술 역할입니다.</span><span class="sxs-lookup"><span data-stu-id="0d8a3-112">*Shared infrastructure owner*: technical roles responsible for network connectivity from on-premises to cloud.</span></span>
- <span data-ttu-id="0d8a3-113">*보안 작업*: Azure를 포함하기 위해 온-프레미스 보안 경계를 확장하는 데 필요한 보안 정책의 구현을 담당합니다.</span><span class="sxs-lookup"><span data-stu-id="0d8a3-113">*Security operations*: responsible for implementing security policy necessary to extend on-premises security boundary to include Azure.</span></span> <span data-ttu-id="0d8a3-114">비밀 저장을 위해 Azure에서 고유 보안 인프라를 소유할 수도 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d8a3-114">May also own security infrastructure in Azure for storing secrets.</span></span>
- <span data-ttu-id="0d8a3-115">*워크로드 소유자:* Azure에 워크로드 게시를 담당합니다.</span><span class="sxs-lookup"><span data-stu-id="0d8a3-115">*Workload owner:* responsible for publishing a workload to Azure.</span></span> <span data-ttu-id="0d8a3-116">조직의 개발 팀의 구조에 따라 개발 책임자, 프로그램 관리 책임자 또는 빌드 엔지니어링 책임자일 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d8a3-116">Depending on the structure of your organization's development teams, this could be a development lead, a program management lead, or build engineering lead.</span></span> <span data-ttu-id="0d8a3-117">게시 프로세스의 일부에는 Azure에 대한 리소스 배포가 포함될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d8a3-117">Part of the publishing process may include the deployment of resources to Azure.</span></span>
  - <span data-ttu-id="0d8a3-118">*워크로드 기여자:* Azure에 워크로드를 게시하는 데 기여하는 일을 담당합니다.</span><span class="sxs-lookup"><span data-stu-id="0d8a3-118">*Workload contributor:* responsible for contributing to the publishing of a workload to Azure.</span></span> <span data-ttu-id="0d8a3-119">성능 모니터링 또는 튜닝을 위해 Azure 리소스에 대한 읽기 권한이 필요할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d8a3-119">May require read access to Azure resources for performance monitoring or tuning.</span></span> <span data-ttu-id="0d8a3-120">리소스를 만들고 업데이트하고 또는 삭제하는 권한이 필요 없습니다.</span><span class="sxs-lookup"><span data-stu-id="0d8a3-120">Does not require permission to create, update, or delete resources.</span></span>

## <a name="section-1-azure-concepts-for-multiple-workloads-and-multiple-teams"></a><span data-ttu-id="0d8a3-121">섹션 1: 여러 워크로드 및 여러 팀에 대한 Azure 개념</span><span class="sxs-lookup"><span data-stu-id="0d8a3-121">Section 1: Azure concepts for multiple workloads and multiple teams</span></span>

<span data-ttu-id="0d8a3-122">기본 도입 단계에서는 Azure 내부 구조에 대한 몇 가지 기본 사항 및 리소스를 생성하고 읽고 업데이트하고 삭제하는 방법을 알아봤습니다.</span><span class="sxs-lookup"><span data-stu-id="0d8a3-122">In the foundational adoption stage, you learned some basics about Azure internals and how resources are created, read, updated, and deleted.</span></span> <span data-ttu-id="0d8a3-123">또한 Azure는 해당 리소스에 액세스해야 하는 사용자를 인증하고 권한을 부여하려면 Azure AD(Active Directory)만 신뢰한다는 것과 ID에 대해 알아봤습니다.</span><span class="sxs-lookup"><span data-stu-id="0d8a3-123">You also learned about identity and that Azure only trusts Azure Active Directory (AD) to authenticate and authorize users who need access to those resources.</span></span>

<span data-ttu-id="0d8a3-124">또한 조직의 Azure 리소스 사용을 관리하기 위한 Azure 거버넌스 도구 구성 방법에 대한 학습을 시작했습니다.</span><span class="sxs-lookup"><span data-stu-id="0d8a3-124">You also started learning about how to configure Azure's governance tools to manage your organization's use of Azure resources.</span></span> <span data-ttu-id="0d8a3-125">기본 단계에서는 단순한 워크로드를 배포하는 데 필요한, 단일 팀의 리소스 액세스를 관리하는 방법을 살펴봤습니다.</span><span class="sxs-lookup"><span data-stu-id="0d8a3-125">In the foundational stage we looked at how to govern a single team's access to the resources necessary to deploy a simple workload.</span></span> <span data-ttu-id="0d8a3-126">실제로 조직은 동시에 여러 워크로드에서 작업하는 여러 팀으로 구성될 예정입니다.</span><span class="sxs-lookup"><span data-stu-id="0d8a3-126">In reality, your organization is going to be made up of multiple teams working on multiple workloads simultaneously.</span></span> 

<span data-ttu-id="0d8a3-127">시작하기 전에 **워크로드** 용어가 실제로 무엇을 의미하는지를 알아봅시다.</span><span class="sxs-lookup"><span data-stu-id="0d8a3-127">Before we begin, let's take a look at what the term **workload** actually means.</span></span> <span data-ttu-id="0d8a3-128">응용 프로그램이나 서비스 같은 임의 단위의 기능을 정의하기 위해 일반적으로 이해되는 용어입니다.</span><span class="sxs-lookup"><span data-stu-id="0d8a3-128">It's a term that is typically understood to define an arbitrary unit of functionality such as an application or service.</span></span> <span data-ttu-id="0d8a3-129">필요한 데이터베이스 등의 서버 및 다른 모든 서비스에 배포되는 코드 아티팩트를 기준으로 한 워크로드에 대해 생각합니다.</span><span class="sxs-lookup"><span data-stu-id="0d8a3-129">We think about a workload in terms of the code artifacts that are deployed to a server as well as any other services, such as a database, that are necessary.</span></span> <span data-ttu-id="0d8a3-130">이는 온-프레미스 응용 프로그램 또는 서비스에 대한 유용한 정의이지만 클라우드에서는 이를 확장해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d8a3-130">This is a useful definition for an on-premises application or service but in the cloud we need to expand on it.</span></span> 

<span data-ttu-id="0d8a3-131">클라우드에서 워크로드는 모든 아티팩트뿐만 아니라 클라우드 리소스도 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="0d8a3-131">In the cloud, a workload not only encompasses all the artifacts but also includes the cloud resources as well.</span></span> <span data-ttu-id="0d8a3-132">**코드 기반 인프라**로 알려진 개념 때문에 클라우드 리소스를 정의의 일부로 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="0d8a3-132">We include cloud resources as part of our definition because of a concept known as **infrastructure-as-code**.</span></span> <span data-ttu-id="0d8a3-133">"Azure 작동 방법" 설명에서 알아본 것처럼 오케스트레이터 서비스에서 Azure 리소스를 배포합니다.</span><span class="sxs-lookup"><span data-stu-id="0d8a3-133">As you learned in the "how does Azure work" explainer, resources in Azure are deployed by an orchestrator service.</span></span> <span data-ttu-id="0d8a3-134">오케스트레이터 서비스는 웹 API를 통해 이 기능을 공개하고 Powershell, Azure CLI(명령줄 인터페이스) 및 Azure Portal 같은 여러 도구를 사용하여 이 웹 API를 호출할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d8a3-134">The orchestrator service exposes this functionality through a web API, and this web API can be called using several tools such as Powershell, the Azure command line interface (CLI), and the Azure portal.</span></span> <span data-ttu-id="0d8a3-135">즉, 응용 프로그램과 연결된 코드 아티팩트와 함께 저장될 수 있는 컴퓨터가 읽을 수 있는 파일에서 리소스를 지정할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d8a3-135">This means that we can specify our resources in a machine-readable file that can be stored along with the code artifacts associated with our application.</span></span>

<span data-ttu-id="0d8a3-136">이렇게 함으로써 코드 아티팩트 및 필요한 클라우드 리소스를 기준으로 워크로드를 정의할 수 있으며, 또한 워크로드를 **격리**할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d8a3-136">This enables us to define a workload in terms of code artifacts and the necessary cloud resources, and this further enables us to **isolate** our workloads.</span></span> <span data-ttu-id="0d8a3-137">워크로드는 리소스가 조직되는 방법 및 네트워크 토폴로지 또는 다른 특성에 의해 격리될 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d8a3-137">Workloads may be isolated by the way resources are organized, by network topology, or by other attributes.</span></span> <span data-ttu-id="0d8a3-138">워크로드 격리의 목적은 팀이 해당 리소스의 모든 측면을 독립적으로 관리할 수 있도록 워크로드의 특정 리소스를 팀과 연결하는 데 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d8a3-138">The goal of workload isolation is to associate a workload's specific resources to a team so the team can independently manage all aspects of those resources.</span></span> <span data-ttu-id="0d8a3-139">이렇게 하면 여러 팀이 Azure에서 리소스 관리 서비스를 공유하는 반면 각자의 리소스가 의도하지 않게 삭제되거나 수정되는 것을 방지할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d8a3-139">This enables multiple teams to share resource management services in Azure while preventing the unintentional deletion or modification of each other's resources.</span></span>

<span data-ttu-id="0d8a3-140">이 격리를 통해 [DevOps](https://azure.microsoft.com/solutions/devops/)라는 다른 개념을 사용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d8a3-140">This isolation also enables another concept known as [DevOps](https://azure.microsoft.com/solutions/devops/).</span></span> <span data-ttu-id="0d8a3-141">DevOps는 소프트웨어 개발 및 IT 작업 모두를 포함하는 소프트웨어 개발 구성 요소를 포함하지만 가능한 한 많은 자동화 사용을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="0d8a3-141">DevOps includes the software development practices that include both software development and IT operations above, but adds the use of automation as much as possible.</span></span> <span data-ttu-id="0d8a3-142">DevOps의 원리 중 하나는 지속적인 통합 및 지속적인 업데이트(CI/CD) 알려져 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d8a3-142">One of the principles of DevOps is known as continuous integration and continuous delivery (CI/CD).</span></span> <span data-ttu-id="0d8a3-143">지속적인 통합은 개발자가 코드 변경에 커밋할 때마다 실행되는 자동화된 빌드 프로세스를 의미하고, 지속적인 업데이트는 테스트를 위한 **개발 환경** 또는 최종 배포를 위한 **프로덕션 환경** 같이 다양한 **환경**에 이 코드를 배포하는 자동화된 프로세스를 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="0d8a3-143">Continuous integration refers to the automated build processes that are run each time a developer commits a code change, and continuous delivery refers to the automated processes that deploy this code to various **environments** such as a **development environment** for testing or a **production environment** for final deployment.</span></span>

## <a name="section-2-governance-design-for-multiple-teams-and-multiple-workloads"></a><span data-ttu-id="0d8a3-144">섹션 2: 여러 팀 및 여러 워크로드에 대한 거버넌스 디자인</span><span class="sxs-lookup"><span data-stu-id="0d8a3-144">Section 2: Governance design for multiple teams and multiple workloads</span></span>

<span data-ttu-id="0d8a3-145">Azure 클라우드 도입 가이드의 [기본 단계](/azure/architecture/cloud-adoption-guide/adoption-intro/overview)에서 클라우드 거버넌스의 개념을 도입하였습니다.</span><span class="sxs-lookup"><span data-stu-id="0d8a3-145">In the [foundational stage](/azure/architecture/cloud-adoption-guide/adoption-intro/overview) of the Azure cloud adoption guide, you were introduced to the concept of cloud governance.</span></span> <span data-ttu-id="0d8a3-146">단일 워크로드에서 작업하는 단일 팀에 대한 단순한 거버넌스 모델을 디자인하는 방법을 알아봤습니다.</span><span class="sxs-lookup"><span data-stu-id="0d8a3-146">You learned how to design a simple governance model for a single team working on a single workload.</span></span> 

<span data-ttu-id="0d8a3-147">중간 단계에서 [거버넌스 디자인 가이드](governance-design-guide.md)는 기본 개념을 확장하여 여러 팀, 여러 워크로드 및 여러 환경을 추가합니다.</span><span class="sxs-lookup"><span data-stu-id="0d8a3-147">In the intermediate stage, the [governance design guide](governance-design-guide.md) expands on the foundational concepts to add multiple teams, multiple workloads, and multiple environments.</span></span> <span data-ttu-id="0d8a3-148">문서의 예제를 끝마치면 조직의 거버넌스 모델의 구현 및 디자인에 디자인 원칙을 적용할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d8a3-148">Once you've gone through the examples in the document you can apply the design principles to designing and implementing your organization's goverance model.</span></span>

## <a name="section-3-implementing-a-resource-management-model"></a><span data-ttu-id="0d8a3-149">섹션 3: 리소스 관리 모델 구현</span><span class="sxs-lookup"><span data-stu-id="0d8a3-149">Section 3: Implementing a resource management model</span></span>

<span data-ttu-id="0d8a3-150">조직의 클라우드 거버넌스 모델은 정의한 액세스 관리 규칙, 사람, Azure의 리소스 액세스 관리 도구 간의 교차를 나타냅니다.</span><span class="sxs-lookup"><span data-stu-id="0d8a3-150">Your organization's cloud governance model represents the intersection between Azure's resource access management tools, your people, and the access management rules you've defined.</span></span> <span data-ttu-id="0d8a3-151">거버넌스 디자인 가이드에서는 Azure 리소스에 대한 액세스를 관리하기 위해 여러 다른 모델에 대해 알아보았습니다.</span><span class="sxs-lookup"><span data-stu-id="0d8a3-151">In the goverance design guide, you learned about several different models for governing access to Azure resources.</span></span> <span data-ttu-id="0d8a3-152">디자인 가이드에서 **공유 인프라**, **프로덕션** 및 **개발** 환경 각각에 대해 구독 하나씩 사용하여 리소스 관리 모델을 구현하는 데 필요한 단계를 살펴볼 것입니다.</span><span class="sxs-lookup"><span data-stu-id="0d8a3-152">Now we'll walk through the steps necessary to implement the resource management model with one subscription for each of the **shared infrastructure**, **production**, and **development** environments from the design guide.</span></span> <span data-ttu-id="0d8a3-153">세 가지 환경 모두에 대해 한 명의 **구독 소유자**가 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d8a3-153">We'll have one **subscription owner** for all three environments.</span></span> <span data-ttu-id="0d8a3-154">각 워크로드는 **기여자** 역할과 함께 추가된 **워크로드 소유자**를 통해 **리소스 그룹**에서 격리됩니다.</span><span class="sxs-lookup"><span data-stu-id="0d8a3-154">Each workload will be isolated in a **resource group** with a **workload owner** added with the **contributor** role.</span></span>

> [!NOTE]
> <span data-ttu-id="0d8a3-155">Azure 계정 및 구독 간의 관계에 대해 자세히 알아보려면 [Azure에서 리소스 액세스 이해][understand-resource-access-in-azure]를 읽어봅니다.</span><span class="sxs-lookup"><span data-stu-id="0d8a3-155">Read [understanding resource access in Azure][understand-resource-access-in-azure] to learn more about the relationship between Azure Accounts and subscriptions.</span></span> 

<span data-ttu-id="0d8a3-156">다음 단계를 수행하세요.</span><span class="sxs-lookup"><span data-stu-id="0d8a3-156">Follow these steps:</span></span>

1. <span data-ttu-id="0d8a3-157">조직에 아직 [Azure 계정](/azure/active-directory/sign-up-organization)이 없는 경우 새로 하나 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0d8a3-157">Create an [Azure account](/azure/active-directory/sign-up-organization) if your organization doesn't already have one.</span></span> <span data-ttu-id="0d8a3-158">Azure 계정에 등록하는 사람이 Azure 계정 관리자가 되고 조직의 지도부는 이 역할을 맡을 개인을 선정해야 합니다.</span><span class="sxs-lookup"><span data-stu-id="0d8a3-158">The person who signs up for the Azure account becomes the Azure account administrator, and your organization's leadership must select an individual to assume this role.</span></span> <span data-ttu-id="0d8a3-159">이 개인은 다음을 담당하게 됩니다.</span><span class="sxs-lookup"><span data-stu-id="0d8a3-159">This individual will be responsible for:</span></span>
    * <span data-ttu-id="0d8a3-160">구독 만들기 및</span><span class="sxs-lookup"><span data-stu-id="0d8a3-160">Creating subscriptions, and</span></span>
    * <span data-ttu-id="0d8a3-161">해당 구독에 대한 사용자 ID를 저장하는 [Azure AD(Active Directory)](/azure/active-directory/active-directory-whatis) 테넌트 만들기 및 관리하기.</span><span class="sxs-lookup"><span data-stu-id="0d8a3-161">Creating and administering [Azure Active Directory (AD)](/azure/active-directory/active-directory-whatis) tenants that store user identity for those subscriptions.</span></span>    
2. <span data-ttu-id="0d8a3-162">조직의 경영진은 사람들이 담당하는 분야를 결정합니다.</span><span class="sxs-lookup"><span data-stu-id="0d8a3-162">Your organization's leadership team decides which people are responsible for:</span></span>
    * <span data-ttu-id="0d8a3-163">사용자 ID 관리, 조직의 Azure 계정을 만들 경우 기본적으로 만든 [Azure AD 테넌트](/azure/active-directory/develop/active-directory-howto-tenant) 및 기본적으로 [Azure AD 전역 관리자](/azure/active-directory/active-directory-assign-admin-roles-azure-portal#details-about-the-global-administrator-role)로서 추가된 계정 관리자.</span><span class="sxs-lookup"><span data-stu-id="0d8a3-163">Management of user identity; an [Azure AD tenant](/azure/active-directory/develop/active-directory-howto-tenant) is created by default when your organization's Azure Account is created, and the account administrator is added as the [Azure AD global administrator](/azure/active-directory/active-directory-assign-admin-roles-azure-portal#details-about-the-global-administrator-role) by default.</span></span> <span data-ttu-id="0d8a3-164">조직에서는 [해당 사용자에게 Azure AD 전역 관리자 역할을 할당](/azure/active-directory/active-directory-users-assign-role-azure-portal)하여 사용자 ID를 관리할 다른 사용자를 선택할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d8a3-164">Your organization can choose another user to manage user identity by [assigning the Azure AD global administrator role to that user](/azure/active-directory/active-directory-users-assign-role-azure-portal).</span></span> 
    * <span data-ttu-id="0d8a3-165">이러한 사용자를 의미하는 구독입니다.</span><span class="sxs-lookup"><span data-stu-id="0d8a3-165">Subscriptions, which means these users:</span></span>
        * <span data-ttu-id="0d8a3-166">해당 구독에서 리소스 사용량과 연결된 비용을 관리하고</span><span class="sxs-lookup"><span data-stu-id="0d8a3-166">Manage costs associated with resource usage in that subscription,</span></span>
        * <span data-ttu-id="0d8a3-167">리소스 액세스에 대한 최소 권한 모델을 구현 및 관리하고</span><span class="sxs-lookup"><span data-stu-id="0d8a3-167">Implement and maintain least permission model for resource access, and</span></span>
        * <span data-ttu-id="0d8a3-168">서비스 제한을 추적합니다.</span><span class="sxs-lookup"><span data-stu-id="0d8a3-168">Keep track of service limits.</span></span>
    * <span data-ttu-id="0d8a3-169">공유 인프라 서비스(조직이 이 모델을 사용하기로 결정하는 경우)는 이 사용자가 다음을 담당하는 것을 의미합니다.</span><span class="sxs-lookup"><span data-stu-id="0d8a3-169">Shared infrastructure services (if your organization decides to use this model), which means this user is responsible for:</span></span>
        * <span data-ttu-id="0d8a3-170">온-프레미스와 Azure 네트워크 연결 및</span><span class="sxs-lookup"><span data-stu-id="0d8a3-170">On-premises to Azure network connectivity, and</span></span> 
        * <span data-ttu-id="0d8a3-171">가상 네트워크 피어링을 통해 Azure 내에서 네트워크 연결의 소유권입니다.</span><span class="sxs-lookup"><span data-stu-id="0d8a3-171">Ownership of network connectivity within Azure through virtual network peering.</span></span>
    * <span data-ttu-id="0d8a3-172">워크로드 소유자입니다.</span><span class="sxs-lookup"><span data-stu-id="0d8a3-172">Workload owners.</span></span> 
3. <span data-ttu-id="0d8a3-173">Azure AD 전역 관리자는 다음에 대한 [새 사용자 계정을 만듭니다](/azure/active-directory/add-users-azure-active-directory).</span><span class="sxs-lookup"><span data-stu-id="0d8a3-173">The Azure AD global administrator [creates the new user accounts](/azure/active-directory/add-users-azure-active-directory) for:</span></span>
    * <span data-ttu-id="0d8a3-174">각 환경과 연결된 각 구독에 대한 **구독 소유자**가 될 사용자입니다.</span><span class="sxs-lookup"><span data-stu-id="0d8a3-174">The person who will be the **subscription owner** for each subscription associated with each environment.</span></span> <span data-ttu-id="0d8a3-175">구독 **서비스 관리자**가 각 구독/환경에 대한 리소스 액세스를 관리하는 작업을 담당하지 않을 경우에만 필요합니다.</span><span class="sxs-lookup"><span data-stu-id="0d8a3-175">Note that this is necessary only if the subscription **service administrator** will not be tasked with managing resource access for each subscription/environment.</span></span>
    * <span data-ttu-id="0d8a3-176">**네트워크 작업 사용자**가 될 사용자 및</span><span class="sxs-lookup"><span data-stu-id="0d8a3-176">The person who will be the **network operations user**, and</span></span>
    * <span data-ttu-id="0d8a3-177">**워크로드 소유자**인 사용자입니다.</span><span class="sxs-lookup"><span data-stu-id="0d8a3-177">The people who are **workload owner(s)**.</span></span>
4. <span data-ttu-id="0d8a3-178">Azure 계정 관리자는 사[Azure 계정 포털](https://account.azure.com)을 사용하여 다음과 같은 세 개의 구독을 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0d8a3-178">The Azure account administrator creates the following three subscriptions using the [Azure account portal](https://account.azure.com):</span></span>
    * <span data-ttu-id="0d8a3-179">**공유 인프라** 환경에 대한 구독,</span><span class="sxs-lookup"><span data-stu-id="0d8a3-179">A subscription for the **shared infrastructure** environment,</span></span>
    * <span data-ttu-id="0d8a3-180">**프로덕션** 환경에 대한 구독 및</span><span class="sxs-lookup"><span data-stu-id="0d8a3-180">A subscription for the **production** environment, and</span></span> 
    * <span data-ttu-id="0d8a3-181">**개발** 환경에 대한 구독입니다.</span><span class="sxs-lookup"><span data-stu-id="0d8a3-181">A subscription for the **development** environment.</span></span> 
5. <span data-ttu-id="0d8a3-182">Azure 계정 관리자는 [각 구독에 구독 서비스 소유자를 추가](/azure/billing/billing-add-change-azure-subscription-administrator#add-an-rbac-owner-admin-for-a-subscription-in-azure-portal)합니다.</span><span class="sxs-lookup"><span data-stu-id="0d8a3-182">The Azure account administrator [adds the subscription service owner to each subscription](/azure/billing/billing-add-change-azure-subscription-administrator#add-an-rbac-owner-admin-for-a-subscription-in-azure-portal).</span></span>
6. <span data-ttu-id="0d8a3-183">리소스 그룹의 생성을 요청하려면 **워크로드 소유자**에 대한 승인 프로세스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0d8a3-183">Create an approval process for **workload owners** to request the creation of resource groups.</span></span> <span data-ttu-id="0d8a3-184">승인 프로세스는 이메일 등의 다양한 방식으로 구현될 수 있습니다. 또는 [Sharepoint 워크플로](https://support.office.com/article/introduction-to-sharepoint-workflow-07982276-54e8-4e17-8699-5056eff4d9e3) 같은 프로세스 관리 도구를 사용하여 구현합니다.</span><span class="sxs-lookup"><span data-stu-id="0d8a3-184">The approval process can be implemented in many ways, such as over email, or you can using a process management tool such as [Sharepoint workflows](https://support.office.com/article/introduction-to-sharepoint-workflow-07982276-54e8-4e17-8699-5056eff4d9e3).</span></span> <span data-ttu-id="0d8a3-185">승인 프로세스는 다음 단계를 수행할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d8a3-185">The approval process can follow these steps:</span></span>  
    * <span data-ttu-id="0d8a3-186">**워크로드 소유자**는 **개발** 환경이나 **프로덕션** 환경 또는 둘 다에서 필요한 Azure 리소스에 대한 제품 구성 정보를 준비하여 **구독 소유자**에게 전송합니다.</span><span class="sxs-lookup"><span data-stu-id="0d8a3-186">The **workload owner** prepares a bill of materials for required Azure resources in either the **development** environment, **production** environment, or both, and submits it to the **subscription owner**.</span></span>
    * <span data-ttu-id="0d8a3-187">**구독 소유자**는 제품 구성 정보를 검토하고 요청한 리소스의 유효성을 검사하여 요청된 리소스가 계획된 용도에 적절한지 확인합니다. 예를 들어 요청된 [ 가상 머신 크기](/azure/virtual-machines/windows/sizes)가 올바른지 확인합니다.</span><span class="sxs-lookup"><span data-stu-id="0d8a3-187">The **subscription owner** reviews the bill of materials and validates the requested resources to ensure that the requested resources are appropriate for their planned use - for example, checking that the requested [virtual machine sizes](/azure/virtual-machines/windows/sizes) are correct.</span></span>
    * <span data-ttu-id="0d8a3-188">요청이 승인되지 않은 경우 **워크로드 소유자**에게 알립니다.</span><span class="sxs-lookup"><span data-stu-id="0d8a3-188">If the request is not approved, the **workload owner** is notified.</span></span> <span data-ttu-id="0d8a3-189">요청이 승인된 경우 **구독 소유자**는 조직의 [명명 규칙](/azure/architecture/best-practices/naming-conventions)에 따라 [요청된 리소스 그룹을 만들고](/azure/azure-resource-manager/resource-group-portal#manage-resource-groups), [[**기여자** 역할이 있는 **워크로드 소유자**](/azure/role-based-access-control/role-assignments-portal#add-access)를 추가하고](/azure/role-based-access-control/built-in-roles#contributor), **워크로드 소유자**에게 리소스 그룹을 생성했다는 알림을 보냅니다.</span><span class="sxs-lookup"><span data-stu-id="0d8a3-189">If the request is approved, the **subscription owner** [creates the requested resource group](/azure/azure-resource-manager/resource-group-portal#manage-resource-groups) following your organization's [naming conventions](/azure/architecture/best-practices/naming-conventions), [adds the **workload owner**](/azure/role-based-access-control/role-assignments-portal#add-access) with the [**contributor** role](/azure/role-based-access-control/built-in-roles#contributor) and sends notification to the **workload owner** that the resource group has been created.</span></span>
7. <span data-ttu-id="0d8a3-190">워크로드 소유자가 공유 인프라 소유자에게서 가상 네트워크 피어링 연결을 요청하려면 승인 프로세스를 만듭니다.</span><span class="sxs-lookup"><span data-stu-id="0d8a3-190">Create an approval process for workload owners to request a virtual network peering connection from the shared infrastructure owner.</span></span> <span data-ttu-id="0d8a3-191">이전 단계에서와 마찬가지로 이 승인 프로세스는 이메일 또는 프로세스 관리 도구를 사용하여 구현할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d8a3-191">As with the previous step, this approval process can be implemented using email or a process management tool.</span></span>

<span data-ttu-id="0d8a3-192">거버넌스 모델을 구현했으므로 공유 인프라 서비스를 배포할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d8a3-192">Now that you've implemented your governance model, you can deploy your shared infrastructure services.</span></span>

## <a name="section-4-deploy-shared-infrastructure-services"></a><span data-ttu-id="0d8a3-193">섹션 4: 공유 인프라 서비스 배포</span><span class="sxs-lookup"><span data-stu-id="0d8a3-193">Section 4: deploy shared infrastructure services</span></span>

<span data-ttu-id="0d8a3-194">조직이 Azure에 온-프레미스 네트워크를 연결하는 데 사용할 수 있는 [하이브리드 네트워크 참조 아키텍처](/azure/architecture/reference-architectures/hybrid-networking/)가 여럿 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d8a3-194">There are several [hybrid network reference architectures](/azure/architecture/reference-architectures/hybrid-networking/) that your organization can use to connect your on-premises network to Azure.</span></span> <span data-ttu-id="0d8a3-195">이러한 참조 아키텍처 각각은 구독 식별자를 요구하는 배포를 포함합니다.</span><span class="sxs-lookup"><span data-stu-id="0d8a3-195">Each of these reference architectures includes a deployment that requires a subscription identifier.</span></span> <span data-ttu-id="0d8a3-196">배포 동안 **공유 인프라** 환경과 연결된 구독에 대한 구독 식별자를 지정합니다.</span><span class="sxs-lookup"><span data-stu-id="0d8a3-196">During deployment, specify the subscription identifier for the subscription associated with your **shared infrastructre** environment.</span></span> <span data-ttu-id="0d8a3-197">또한 **네트워크 작업** 사용자가 관리하는 리소스 그룹을 지정하려면 템플릿 파일을 편집해야 합니다. 또는 배포에서 기본 리소스 그룹을 사용하고 이 그룹에 **기여자** 역할이 있는 **네트워크 작업** 사용자를 추가할 수 있습니다.</span><span class="sxs-lookup"><span data-stu-id="0d8a3-197">You will also need to edit the template files to specify the resource group that is managed by your **network operations** user, or, you can use the default resource groups in the deployment and add the **network operations** user with the **contributor** role to them.</span></span>

<!-- links -->
[understand-resource-access-in-azure]: /azure/role-based-access-control/rbac-and-directory-admin-roles