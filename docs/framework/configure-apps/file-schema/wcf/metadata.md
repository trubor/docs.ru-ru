---
description: 'Дополнительные сведения: <metadata>'
title: <metadata>
ms.date: 03/30/2017
ms.assetid: d09653eb-e355-4c73-b87b-28f93d56480d
ms.openlocfilehash: 6cc1e472dbada72fe6a375a6832e7c9128dcda6b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99684429"
---
# \<metadata>

<span data-ttu-id="0fee5-102">Задает способ обработки метаданных службы.</span><span class="sxs-lookup"><span data-stu-id="0fee5-102">Specifies how service metadata can be processed.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<metadata>**  
  
## <a name="syntax"></a><span data-ttu-id="0fee5-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0fee5-103">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <client>
    <metadata>
      <policyImporters>
        <policyImporter type="string" />
      </policyImporters>
      <wsdlImporters>
        <wsdlImporter type="string" />
      </wsdlImporters>
    </metadata>
  </client>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0fee5-104">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="0fee5-104">Attributes and Elements</span></span>  

 <span data-ttu-id="0fee5-105">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="0fee5-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0fee5-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="0fee5-106">Attributes</span></span>  

 <span data-ttu-id="0fee5-107">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="0fee5-107">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0fee5-108">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="0fee5-108">Child Elements</span></span>  
  
|<span data-ttu-id="0fee5-109">Элемент</span><span class="sxs-lookup"><span data-stu-id="0fee5-109">Element</span></span>|<span data-ttu-id="0fee5-110">Описание</span><span class="sxs-lookup"><span data-stu-id="0fee5-110">Description</span></span>|  
|-------------|-----------------|  
|[\<policyImporters>](policyimporters.md)|<span data-ttu-id="0fee5-111">Задает все средства импорта политики, контролирующие импорт утверждений пользовательской политики о привязках.</span><span class="sxs-lookup"><span data-stu-id="0fee5-111">Specifies all the policy importers that control the import of custom policy assertions about bindings.</span></span> <span data-ttu-id="0fee5-112">Средство импорта политики используется для поиска утверждений пользовательской политики о свойствах привязки, а также для подключения пользовательского элемента привязки, реализующего свойства, необходимые для утверждения.</span><span class="sxs-lookup"><span data-stu-id="0fee5-112">A policy importer is used to search custom policy assertions about binding features, as well as attach a custom binding element that implements the features the assertion requires.</span></span>|  
|[\<wsdlImporters>](wsdlimporters.md)|<span data-ttu-id="0fee5-113">Задает все средства импорта WSDL, импортирующие метаданные на языке WSDL 1.1 с вложениями WS-Policy.</span><span class="sxs-lookup"><span data-stu-id="0fee5-113">Specifies all the WSDL importers that import Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span> <span data-ttu-id="0fee5-114">Средство импорта WSDL используется для импорта метаданных, а также для их преобразования в различные классы, представляющие данные контракта и конечной точки.</span><span class="sxs-lookup"><span data-stu-id="0fee5-114">A WSDL importer is used to import metadata as well as convert that information into various classes that represent contract and endpoint information.</span></span> <span data-ttu-id="0fee5-115">Он может выборочно импортировать сведения контракта и конечной точки, а также свойства, предоставляющие сведения об ошибках и принимающие сведения о типах, относящиеся к процессу импорта и преобразования.</span><span class="sxs-lookup"><span data-stu-id="0fee5-115">It can selectively import contract and endpoint information and properties that expose any import errors and accept type information relevant to the import and conversion process.</span></span> <span data-ttu-id="0fee5-116">Оно также поддерживает импорт данных привязки и свойств, предоставляющих доступ к каким-либо документам политики, документам WSDL, расширениям WSDL и документам схемы XML.</span><span class="sxs-lookup"><span data-stu-id="0fee5-116">It also supports importing binding information and properties that provide access to any policy documents, WSDL documents, WSDL extensions, and XML schema documents.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0fee5-117">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="0fee5-117">Parent Elements</span></span>  
  
|<span data-ttu-id="0fee5-118">Элемент</span><span class="sxs-lookup"><span data-stu-id="0fee5-118">Element</span></span>|<span data-ttu-id="0fee5-119">Описание</span><span class="sxs-lookup"><span data-stu-id="0fee5-119">Description</span></span>|  
|-------------|-----------------|  
|[\<client>](client.md)|<span data-ttu-id="0fee5-120">В разделе client определяется список конечных точек, к которым может подключаться клиент.</span><span class="sxs-lookup"><span data-stu-id="0fee5-120">The client section defines a list of endpoints that a client can connect to.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0fee5-121">См. также</span><span class="sxs-lookup"><span data-stu-id="0fee5-121">See also</span></span>

- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>
- <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>
- <xref:System.ServiceModel.Description.MetadataImporter>
- <xref:System.ServiceModel.Description.WsdlImporter>
- [<span data-ttu-id="0fee5-122">Конфигурация клиента WCF</span><span class="sxs-lookup"><span data-stu-id="0fee5-122">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="0fee5-123">Клиенты</span><span class="sxs-lookup"><span data-stu-id="0fee5-123">Clients</span></span>](../../../wcf/feature-details/clients.md)
