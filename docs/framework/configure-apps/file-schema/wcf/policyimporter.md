---
description: 'Дополнительные сведения: <policyImporter>'
title: <policyImporter>
ms.date: 03/30/2017
ms.assetid: b0d03456-546f-44bb-ab12-1b2ce7f98fca
ms.openlocfilehash: 2103c424aef081b72fa822ed207537195b8fdea9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99683519"
---
# \<policyImporter>

<span data-ttu-id="98cd3-102">Задает средство импорта политики, контролирующее импорт положений пользовательской политики о привязках.</span><span class="sxs-lookup"><span data-stu-id="98cd3-102">Specifies a policy importer that controls the import of custom policy assertions about bindings.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<metadata>**](metadata.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<policyImporters>**](policyimporters.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<policyImporter>**  
  
## <a name="syntax"></a><span data-ttu-id="98cd3-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="98cd3-103">Syntax</span></span>  
  
```xml  
<metadata>
  <policyImporters>
    <policyImporter type="String" />
  </policyImporters>
</metadata>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="98cd3-104">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="98cd3-104">Attributes and Elements</span></span>  

 <span data-ttu-id="98cd3-105">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="98cd3-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="98cd3-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="98cd3-106">Attributes</span></span>  
  
|<span data-ttu-id="98cd3-107">Атрибут</span><span class="sxs-lookup"><span data-stu-id="98cd3-107">Attribute</span></span>|<span data-ttu-id="98cd3-108">Описание</span><span class="sxs-lookup"><span data-stu-id="98cd3-108">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="98cd3-109">Тип этого элемента.</span><span class="sxs-lookup"><span data-stu-id="98cd3-109">The type of this element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="98cd3-110">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="98cd3-110">Child Elements</span></span>  

 <span data-ttu-id="98cd3-111">None</span><span class="sxs-lookup"><span data-stu-id="98cd3-111">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="98cd3-112">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="98cd3-112">Parent Elements</span></span>  
  
|<span data-ttu-id="98cd3-113">Элемент</span><span class="sxs-lookup"><span data-stu-id="98cd3-113">Element</span></span>|<span data-ttu-id="98cd3-114">Описание</span><span class="sxs-lookup"><span data-stu-id="98cd3-114">Description</span></span>|  
|-------------|-----------------|  
|[\<policyImporters>](policyimporters.md)|<span data-ttu-id="98cd3-115">Задает все средства импорта политики, контролирующие импорт утверждений пользовательской политики о привязках.</span><span class="sxs-lookup"><span data-stu-id="98cd3-115">Specifies all the policy importers that control the import of custom policy assertions about bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="98cd3-116">Remarks</span><span class="sxs-lookup"><span data-stu-id="98cd3-116">Remarks</span></span>  

 <span data-ttu-id="98cd3-117">Средство импорта политики используется для поиска утверждений пользовательской политики о свойствах привязки, а также для подключения пользовательского элемента привязки, реализующего свойства, необходимые для утверждения.</span><span class="sxs-lookup"><span data-stu-id="98cd3-117">A policy importer is used to search custom policy assertions about binding features, as well as attach a custom binding element that implements the features the assertion requires.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98cd3-118">См. также</span><span class="sxs-lookup"><span data-stu-id="98cd3-118">See also</span></span>

- <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>
- <xref:System.ServiceModel.Configuration.PolicyImporterElement>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Description.MetadataImporter>
- [<span data-ttu-id="98cd3-119">Конфигурация клиента WCF</span><span class="sxs-lookup"><span data-stu-id="98cd3-119">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="98cd3-120">Клиенты</span><span class="sxs-lookup"><span data-stu-id="98cd3-120">Clients</span></span>](../../../wcf/feature-details/clients.md)
