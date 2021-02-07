---
description: 'Дополнительные сведения: <persistableType>'
title: <persistableType>
ms.date: 03/30/2017
ms.assetid: e5425fe6-523a-4076-aab4-2c2515b1d830
ms.openlocfilehash: eadbb951d751dd88ce974edc8d5b343a1469b758
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99683636"
---
# \<persistableType>

<span data-ttu-id="280fd-102">Задает все восстанавливаемые типы.</span><span class="sxs-lookup"><span data-stu-id="280fd-102">Specifies all the persistable types.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContracts>**](comcontracts.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<comContract>**](comcontract.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<persistableTypes>**](persistabletypes.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<persistableType>**  
  
## <a name="syntax"></a><span data-ttu-id="280fd-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="280fd-103">Syntax</span></span>  
  
```xml  
<comContracts>
  <comContract>
    <persistableTypes>
      <persistableType id="String"
                       name="String">
      </persistableType>
    </persistableTypes>
  </comContract>
</comContracts>
```  
  
## <a name="type"></a><span data-ttu-id="280fd-104">Тип</span><span class="sxs-lookup"><span data-stu-id="280fd-104">Type</span></span>  

 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="280fd-105">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="280fd-105">Attributes and Elements</span></span>  

 <span data-ttu-id="280fd-106">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="280fd-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="280fd-107">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="280fd-107">Attributes</span></span>  
  
|<span data-ttu-id="280fd-108">Атрибут</span><span class="sxs-lookup"><span data-stu-id="280fd-108">Attribute</span></span>|<span data-ttu-id="280fd-109">Описание</span><span class="sxs-lookup"><span data-stu-id="280fd-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="280fd-110">идентификатор</span><span class="sxs-lookup"><span data-stu-id="280fd-110">id</span></span>|<span data-ttu-id="280fd-111">Обязательный атрибут, содержащий строку, которая задает уникальный идентификатор для восстанавливаемого типа.</span><span class="sxs-lookup"><span data-stu-id="280fd-111">A required attribute that contains a string that specifies a unique identifier for a persistable type.</span></span>|  
|<span data-ttu-id="280fd-112">name</span><span class="sxs-lookup"><span data-stu-id="280fd-112">name</span></span>|<span data-ttu-id="280fd-113">Необязательный атрибут, содержащий строку, которая задает имя восстанавливаемого типа.</span><span class="sxs-lookup"><span data-stu-id="280fd-113">An optional attribute that contains a string that specifies the name of the persistable type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="280fd-114">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="280fd-114">Child Elements</span></span>  

 <span data-ttu-id="280fd-115">None</span><span class="sxs-lookup"><span data-stu-id="280fd-115">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="280fd-116">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="280fd-116">Parent Elements</span></span>  
  
|<span data-ttu-id="280fd-117">Элемент</span><span class="sxs-lookup"><span data-stu-id="280fd-117">Element</span></span>|<span data-ttu-id="280fd-118">Описание</span><span class="sxs-lookup"><span data-stu-id="280fd-118">Description</span></span>|  
|-------------|-----------------|  
|[\<persistableTypes>](persistabletypes.md)|<span data-ttu-id="280fd-119">Коллекция элементов `persistableType`.</span><span class="sxs-lookup"><span data-stu-id="280fd-119">A collection of `persistableType` elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="280fd-120">См. также</span><span class="sxs-lookup"><span data-stu-id="280fd-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.ComPersistableTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ComPersistableTypeElement>
- [\<comContracts>](comcontracts.md)
- [<span data-ttu-id="280fd-121">Интеграция с приложениями COM+</span><span class="sxs-lookup"><span data-stu-id="280fd-121">Integrating with COM+ Applications</span></span>](../../../wcf/feature-details/integrating-with-com-plus-applications.md)
- [<span data-ttu-id="280fd-122">Практическое руководство. Настройка параметров службы COM+</span><span class="sxs-lookup"><span data-stu-id="280fd-122">How to: Configure COM+ Service Settings</span></span>](../../../wcf/feature-details/how-to-configure-com-service-settings.md)
