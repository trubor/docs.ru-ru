---
description: 'Дополнительные сведения: <useManagedPresentation>'
title: <useManagedPresentation>
ms.date: 03/30/2017
ms.assetid: 17a0dd77-af54-41db-a9d0-4b17ff42878f
ms.openlocfilehash: 9203daedcc0553c7a1308b2763b9e818ca6560c1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99749042"
---
# \<useManagedPresentation>

<span data-ttu-id="394b3-102">Элемент привязки, используемый для связи со службой маркеров безопасности CardSpace, которая поддерживает CardSpace-профиль WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="394b3-102">A binding element used to communicate with a CardSpace Security Token Service that supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="394b3-103">Этот элемент не имеет атрибутов и представлен как пустой переключатель.</span><span class="sxs-lookup"><span data-stu-id="394b3-103">This element has no attribute and is present as an empty switch.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<useManagedPresentation>**  
  
## <a name="syntax"></a><span data-ttu-id="394b3-104">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="394b3-104">Syntax</span></span>  
  
```xml  
<useManagedPresentation />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="394b3-105">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="394b3-105">Attributes and Elements</span></span>  

 <span data-ttu-id="394b3-106">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="394b3-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="394b3-107">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="394b3-107">Attributes</span></span>  

 <span data-ttu-id="394b3-108">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="394b3-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="394b3-109">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="394b3-109">Child Elements</span></span>  

 <span data-ttu-id="394b3-110">None</span><span class="sxs-lookup"><span data-stu-id="394b3-110">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="394b3-111">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="394b3-111">Parent Elements</span></span>  
  
|<span data-ttu-id="394b3-112">Элемент</span><span class="sxs-lookup"><span data-stu-id="394b3-112">Element</span></span>|<span data-ttu-id="394b3-113">Описание</span><span class="sxs-lookup"><span data-stu-id="394b3-113">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="394b3-114">Определяет все возможности пользовательской привязки.</span><span class="sxs-lookup"><span data-stu-id="394b3-114">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="394b3-115">Remarks</span><span class="sxs-lookup"><span data-stu-id="394b3-115">Remarks</span></span>  

 <span data-ttu-id="394b3-116">Этот элемент используется поставщиком удостоверения для отражения в своей политике поддержки CardSpace-профиля WS-Trust.</span><span class="sxs-lookup"><span data-stu-id="394b3-116">This element is used by an identity provider to express in its policy the fact that it supports the CardSpace profile of WS-Trust.</span></span> <span data-ttu-id="394b3-117">Поставщики удостоверений, которые предоставляют такое утверждение политики, должны быть способны выдавать маркеры на основе этого профиля CardSpace.</span><span class="sxs-lookup"><span data-stu-id="394b3-117">Identity providers that publish such a policy assertion should be able to issue tokens based on that CardSpace profile.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="394b3-118">См. также</span><span class="sxs-lookup"><span data-stu-id="394b3-118">See also</span></span>

- <xref:System.ServiceModel.Configuration.UseManagedPresentationElement>
- <xref:System.ServiceModel.Channels.UseManagedPresentationBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="394b3-119">Привязки</span><span class="sxs-lookup"><span data-stu-id="394b3-119">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="394b3-120">Расширение привязок</span><span class="sxs-lookup"><span data-stu-id="394b3-120">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="394b3-121">Пользовательские привязки</span><span class="sxs-lookup"><span data-stu-id="394b3-121">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
