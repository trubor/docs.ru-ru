---
description: 'Дополнительные сведения о: <System. Runtime. Serialization>'
title: <system.runtime.serialization>
ms.date: 03/30/2017
ms.assetid: a8cebf4c-06d2-4667-8f5b-c3e1fc90df6f
ms.openlocfilehash: cf1d95c8650e4b6979d4f34b0bed1fa395911f2d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786633"
---
# \<system.runtime.serialization>

<span data-ttu-id="e24a3-103">Представляет корневой элемент для раздела пространства имен <xref:System.Runtime.Serialization> и содержит элементы для установки параметров <xref:System.Runtime.Serialization.DataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="e24a3-103">Represents the root element for the <xref:System.Runtime.Serialization> namespace section and contains elements for setting options of the <xref:System.Runtime.Serialization.DataContractSerializer>.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;**\<system.runtime.serialization>**  
  
## <a name="syntax"></a><span data-ttu-id="e24a3-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e24a3-104">Syntax</span></span>  
  
```xml  
<configuration>
  <system.runtime.serialization>
    <dataContractSerializer ignoreExtensionDataObject="Boolean"
                            maxItemsInObjectGraph="Integer">
      <declaredTypes>
        <add type="String">
          <knownType type="String">
            <parameter index="Integer" />
          </knownType>
        </add>
      </declaredTypes>
    <dataContractSerializer>
  </system.runtime.serialization>
</configuration>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e24a3-105">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="e24a3-105">Attributes and Elements</span></span>  

 <span data-ttu-id="e24a3-106">В следующих разделах описываются атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="e24a3-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e24a3-107">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="e24a3-107">Attributes</span></span>  

 <span data-ttu-id="e24a3-108">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="e24a3-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e24a3-109">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="e24a3-109">Child Elements</span></span>  
  
|<span data-ttu-id="e24a3-110">Элемент</span><span class="sxs-lookup"><span data-stu-id="e24a3-110">Element</span></span>|<span data-ttu-id="e24a3-111">Описание</span><span class="sxs-lookup"><span data-stu-id="e24a3-111">Description</span></span>|  
|-------------|-----------------|  
|[\<dataContractSerializer>](datacontractserializer-of-system-runtime-serialization.md)|<span data-ttu-id="e24a3-112">Включает добавление известных типов при десериализации.</span><span class="sxs-lookup"><span data-stu-id="e24a3-112">Enables addition of known types to be used when deserialization.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e24a3-113">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="e24a3-113">Parent Elements</span></span>  
  
|<span data-ttu-id="e24a3-114">Элемент</span><span class="sxs-lookup"><span data-stu-id="e24a3-114">Element</span></span>|<span data-ttu-id="e24a3-115">Описание</span><span class="sxs-lookup"><span data-stu-id="e24a3-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e24a3-116">\<configuration> Элемент</span><span class="sxs-lookup"><span data-stu-id="e24a3-116">\<configuration> Element</span></span>](../configuration-element.md)|<span data-ttu-id="e24a3-117">Элемент конфигурации верхнего уровня.</span><span class="sxs-lookup"><span data-stu-id="e24a3-117">The top level element for configuration.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e24a3-118">См. также</span><span class="sxs-lookup"><span data-stu-id="e24a3-118">See also</span></span>

- <xref:System.Runtime.Serialization>
- [<span data-ttu-id="e24a3-119">Использование контрактов данных</span><span class="sxs-lookup"><span data-stu-id="e24a3-119">Using Data Contracts</span></span>](../../../wcf/feature-details/using-data-contracts.md)
- [<span data-ttu-id="e24a3-120">Известные типы контрактов данных</span><span class="sxs-lookup"><span data-stu-id="e24a3-120">Data Contract Known Types</span></span>](../../../wcf/feature-details/data-contract-known-types.md)
