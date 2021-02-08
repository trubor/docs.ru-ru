---
description: 'Дополнительные сведения: <tokenReplayDetection>'
title: <tokenReplayDetection>
ms.date: 03/30/2017
ms.assetid: ac3f588e-5f75-4275-b969-2d492ecc3b47
author: BrucePerlerMS
ms.openlocfilehash: a8a6b754a3282afe4f2932296b06b84c09fb6f1a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786542"
---
# \<tokenReplayDetection>

<span data-ttu-id="5fd21-102">Включает обнаружение воспроизведения маркеров и задает срок действия токенов.</span><span class="sxs-lookup"><span data-stu-id="5fd21-102">Enables token replay detection and specifies the expiration time for tokens.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<tokenReplayDetection>**  
  
## <a name="syntax"></a><span data-ttu-id="5fd21-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="5fd21-103">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <tokenReplayDetection enabled=xs:boolean expirationPeriod=TimeSpan>  
    </tokenReplayDetection>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="type"></a><span data-ttu-id="5fd21-104">Тип</span><span class="sxs-lookup"><span data-stu-id="5fd21-104">Type</span></span>  

 <xref:System.IdentityModel.Configuration.TokenReplayDetectionElement>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5fd21-105">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="5fd21-105">Attributes and Elements</span></span>  

 <span data-ttu-id="5fd21-106">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="5fd21-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5fd21-107">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="5fd21-107">Attributes</span></span>  
  
|<span data-ttu-id="5fd21-108">Атрибут</span><span class="sxs-lookup"><span data-stu-id="5fd21-108">Attribute</span></span>|<span data-ttu-id="5fd21-109">Описание</span><span class="sxs-lookup"><span data-stu-id="5fd21-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5fd21-110">Включено</span><span class="sxs-lookup"><span data-stu-id="5fd21-110">enabled</span></span>|<span data-ttu-id="5fd21-111">Значение типа, указывающее, включено ли обнаружение воспроизведения маркеров. значение true, чтобы включить обнаружение воспроизведения маркеров.</span><span class="sxs-lookup"><span data-stu-id="5fd21-111">A value that specifies whether token replay detection is enabled; "true" to enable token replay detection.</span></span>|  
|<span data-ttu-id="5fd21-112">експиратионпериод</span><span class="sxs-lookup"><span data-stu-id="5fd21-112">expirationPeriod</span></span>|<span data-ttu-id="5fd21-113">Значение типа <xref:System.TimeSpan> , указывающее максимальное количество времени, по истечении которого элемент считается просроченным и удаляется из кэша.</span><span class="sxs-lookup"><span data-stu-id="5fd21-113">A <xref:System.TimeSpan> that specifies the maximum amount of time before an item is considered expired and removed from the cache.</span></span>  <span data-ttu-id="5fd21-114">Дополнительные сведения об указании <xref:System.TimeSpan> значений см. в разделе [значения TimeSpan](../windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="5fd21-114">For more information about how to specify <xref:System.TimeSpan> values, see [Timespan Values](../windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5fd21-115">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="5fd21-115">Child Elements</span></span>  

 <span data-ttu-id="5fd21-116">None</span><span class="sxs-lookup"><span data-stu-id="5fd21-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5fd21-117">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="5fd21-117">Parent Elements</span></span>  
  
|<span data-ttu-id="5fd21-118">Элемент</span><span class="sxs-lookup"><span data-stu-id="5fd21-118">Element</span></span>|<span data-ttu-id="5fd21-119">Описание</span><span class="sxs-lookup"><span data-stu-id="5fd21-119">Description</span></span>|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|<span data-ttu-id="5fd21-120">Задает параметры удостоверений уровня службы.</span><span class="sxs-lookup"><span data-stu-id="5fd21-120">Specifies service-level identity settings.</span></span>|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="5fd21-121">Предоставляет конфигурацию для коллекции обработчиков маркеров безопасности.</span><span class="sxs-lookup"><span data-stu-id="5fd21-121">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5fd21-122">Remarks</span><span class="sxs-lookup"><span data-stu-id="5fd21-122">Remarks</span></span>  

 <span data-ttu-id="5fd21-123">`<tokenReplayDetection>`Элемент можно указать на уровне службы в `<identityConfiguration>` элементе или на уровне коллекции обработчика маркеров безопасности под `<securityTokenHandlerConfiguration>` элементом.</span><span class="sxs-lookup"><span data-stu-id="5fd21-123">A `<tokenReplayDetection>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="5fd21-124">Параметры коллекции обработчиков маркеров переопределяют указанные в службе.</span><span class="sxs-lookup"><span data-stu-id="5fd21-124">Settings on a token handler collection override those specified on the service.</span></span>  
  
 <span data-ttu-id="5fd21-125">Тип кэша воспроизведения токенов задается [\<tokenReplayCache>](tokenreplaycache.md) элементом.</span><span class="sxs-lookup"><span data-stu-id="5fd21-125">The type of the token replay cache is specified by the [\<tokenReplayCache>](tokenreplaycache.md) element.</span></span>
