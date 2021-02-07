---
description: 'Дополнительные сведения: <privacyNoticeAt>'
title: <privacyNoticeAt>
ms.date: 03/30/2017
ms.assetid: 4cc96942-4eb9-4241-b2fd-45aa239915e8
ms.openlocfilehash: 2e38d43becd783cc50afba5a029d3ab9905ec15a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99683506"
---
# \<privacyNoticeAt>

<span data-ttu-id="1303b-102">Представляет элемент конфигурации, который задает уведомление о конфиденциальности, используемое в привязке `wsFederationHttp`.</span><span class="sxs-lookup"><span data-stu-id="1303b-102">Represents a configuration element that specifies a privacy notice used in `wsFederationHttp` binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<privacyNotice>**  
  
## <a name="syntax"></a><span data-ttu-id="1303b-103">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="1303b-103">Syntax</span></span>  
  
```xml  
<privacyNotice url="String"
               version="Integer" />
```  
  
## <a name="type"></a><span data-ttu-id="1303b-104">Тип</span><span class="sxs-lookup"><span data-stu-id="1303b-104">Type</span></span>  

 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1303b-105">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="1303b-105">Attributes and Elements</span></span>  

 <span data-ttu-id="1303b-106">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="1303b-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1303b-107">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="1303b-107">Attributes</span></span>  
  
|<span data-ttu-id="1303b-108">Атрибут</span><span class="sxs-lookup"><span data-stu-id="1303b-108">Attribute</span></span>|<span data-ttu-id="1303b-109">Описание</span><span class="sxs-lookup"><span data-stu-id="1303b-109">Description</span></span>|  
|---------------|-----------------|  
|`url`|<span data-ttu-id="1303b-110">Строка, задающая универсальный код ресурса (URI), определяющий расположение примечания о конфиденциальности.</span><span class="sxs-lookup"><span data-stu-id="1303b-110">A string that specifies the URI at which the privacy notice is located.</span></span>|  
|`version`|<span data-ttu-id="1303b-111">Целое число, определяющее версию этого уведомления о конфиденциальности.</span><span class="sxs-lookup"><span data-stu-id="1303b-111">An integer that specifies the version of this privacy notice.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1303b-112">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="1303b-112">Child Elements</span></span>  

 <span data-ttu-id="1303b-113">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="1303b-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1303b-114">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="1303b-114">Parent Elements</span></span>  
  
|<span data-ttu-id="1303b-115">Элемент</span><span class="sxs-lookup"><span data-stu-id="1303b-115">Element</span></span>|<span data-ttu-id="1303b-116">Описание</span><span class="sxs-lookup"><span data-stu-id="1303b-116">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="1303b-117">Определяет все возможности пользовательской привязки.</span><span class="sxs-lookup"><span data-stu-id="1303b-117">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1303b-118">См. также</span><span class="sxs-lookup"><span data-stu-id="1303b-118">See also</span></span>

- <xref:System.ServiceModel.Configuration.PrivacyNoticeElement>
- <xref:System.ServiceModel.Channels.PrivacyNoticeBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="1303b-119">Привязки</span><span class="sxs-lookup"><span data-stu-id="1303b-119">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="1303b-120">Расширение привязок</span><span class="sxs-lookup"><span data-stu-id="1303b-120">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="1303b-121">Пользовательские привязки</span><span class="sxs-lookup"><span data-stu-id="1303b-121">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
