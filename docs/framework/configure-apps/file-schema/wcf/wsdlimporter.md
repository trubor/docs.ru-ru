---
description: 'Дополнительные сведения: <wsdlImporter>'
title: <wsdlImporter>
ms.date: 03/30/2017
ms.assetid: 986b2165-8430-4dba-b1b8-00396841bb96
ms.openlocfilehash: 9f95d4e6b940f36e9142eb9865327c772e3ce4db
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99682154"
---
# \<wsdlImporter>

<span data-ttu-id="99f18-102">Задает все средства импорта WSDL, импортирующие метаданные на языке WSDL 1.1 с вложениями WS-Policy.</span><span class="sxs-lookup"><span data-stu-id="99f18-102">Specifies all the WSDL importers that imports Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<client>**](client.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<metadata>**](metadata.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<wsdlImporters>**](wsdlimporters.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<wsdlImporter>**  
  
## <a name="syntax"></a><span data-ttu-id="99f18-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="99f18-103">Syntax</span></span>  
  
```xml  
<metadata>
  <wsdlImporters>
    <wsdlImporter type="string" />
  </wsdlImporters>
</metadata>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="99f18-104">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="99f18-104">Attributes and Elements</span></span>  

 <span data-ttu-id="99f18-105">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="99f18-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="99f18-106">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="99f18-106">Attributes</span></span>  
  
|<span data-ttu-id="99f18-107">Атрибут</span><span class="sxs-lookup"><span data-stu-id="99f18-107">Attribute</span></span>|<span data-ttu-id="99f18-108">Описание</span><span class="sxs-lookup"><span data-stu-id="99f18-108">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="99f18-109">Тип этого элемента.</span><span class="sxs-lookup"><span data-stu-id="99f18-109">The type of this element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="99f18-110">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="99f18-110">Child Elements</span></span>  

 <span data-ttu-id="99f18-111">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="99f18-111">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="99f18-112">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="99f18-112">Parent Elements</span></span>  
  
|<span data-ttu-id="99f18-113">Элемент</span><span class="sxs-lookup"><span data-stu-id="99f18-113">Element</span></span>|<span data-ttu-id="99f18-114">Описание</span><span class="sxs-lookup"><span data-stu-id="99f18-114">Description</span></span>|  
|-------------|-----------------|  
|[\<wsdlImporters>](wsdlimporters.md)|<span data-ttu-id="99f18-115">Задает все средства импорта WSDL, импортирующие метаданные на языке WSDL 1.1 с вложениями WS-Policy.</span><span class="sxs-lookup"><span data-stu-id="99f18-115">Specifies all the WSDL importers that imports Web Services Description Language (WSDL) 1.1 metadata with WS-Policy attachments.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="99f18-116">Remarks</span><span class="sxs-lookup"><span data-stu-id="99f18-116">Remarks</span></span>  

 <span data-ttu-id="99f18-117">Средство импорта WSDL используется для импорта метаданных, а также для их преобразования в различные классы, представляющие данные контракта и конечной точки.</span><span class="sxs-lookup"><span data-stu-id="99f18-117">A WSDL importer is used to import metadata as well as convert that information into various classes that represent contract and endpoint information.</span></span> <span data-ttu-id="99f18-118">Он может выборочно импортировать сведения контракта и конечной точки, а также свойства, предоставляющие сведения об ошибках и принимающие сведения о типах, относящиеся к процессу импорта и преобразования.</span><span class="sxs-lookup"><span data-stu-id="99f18-118">It can selectively import contract and endpoint information and properties that expose any import errors and accept type information relevant to the import and conversion process.</span></span> <span data-ttu-id="99f18-119">Оно также поддерживает импорт данных привязки и свойств, предоставляющих доступ к каким-либо документам политики, документам WSDL, расширениям WSDL и документам схемы XML.</span><span class="sxs-lookup"><span data-stu-id="99f18-119">It also supports importing binding information and properties that provide access to any policy documents, WSDL documents, WSDL extensions, and XML schema documents.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99f18-120">См. также</span><span class="sxs-lookup"><span data-stu-id="99f18-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.WsdlImporterElement>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Configuration.WsdlImporterElementCollection>
- <xref:System.ServiceModel.Description.MetadataImporter>
- <xref:System.ServiceModel.Description.WsdlImporter>
- [<span data-ttu-id="99f18-121">Конфигурация клиента WCF</span><span class="sxs-lookup"><span data-stu-id="99f18-121">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="99f18-122">Клиенты</span><span class="sxs-lookup"><span data-stu-id="99f18-122">Clients</span></span>](../../../wcf/feature-details/clients.md)
