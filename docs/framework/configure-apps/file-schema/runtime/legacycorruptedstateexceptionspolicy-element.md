---
description: 'Дополнительные сведения о: <legacyCorruptedStateExceptionsPolicy> element'
title: Элемент <legacyCorruptedStateExceptionsPolicy>
ms.date: 03/30/2017
helpviewer_keywords:
- <legacyCorruptedStateExceptionsPolicy> element
- legacyCorruptedStateExceptionsPolicy element
ms.assetid: e0a55ddc-bfa8-4f3e-ac14-d1fc3330e4bb
ms.openlocfilehash: 34082c0779b09400a875894359cf7cf501173508
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99786958"
---
# <a name="legacycorruptedstateexceptionspolicy-element"></a><span data-ttu-id="a2f11-103">Элемент \<legacyCorruptedStateExceptionsPolicy></span><span class="sxs-lookup"><span data-stu-id="a2f11-103">\<legacyCorruptedStateExceptionsPolicy> Element</span></span>

<span data-ttu-id="a2f11-104">Указывает, позволяет ли среда CLR использовать управляемый код для перехвата нарушений доступа и других исключений поврежденного состояния.</span><span class="sxs-lookup"><span data-stu-id="a2f11-104">Specifies whether the common language runtime allows managed code to catch access violations and other corrupted state exceptions.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<legacyCorruptedStateExceptionsPolicy>**  
  
## <a name="syntax"></a><span data-ttu-id="a2f11-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a2f11-105">Syntax</span></span>  
  
```xml  
<legacyCorruptedStateExceptionsPolicy enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a2f11-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="a2f11-106">Attributes and Elements</span></span>  

 <span data-ttu-id="a2f11-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="a2f11-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a2f11-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="a2f11-108">Attributes</span></span>  
  
|<span data-ttu-id="a2f11-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="a2f11-109">Attribute</span></span>|<span data-ttu-id="a2f11-110">Описание</span><span class="sxs-lookup"><span data-stu-id="a2f11-110">Description</span></span>|  
|---------------|-----------------|  
|`enabled`|<span data-ttu-id="a2f11-111">Обязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="a2f11-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="a2f11-112">Указывает, что приложение будет перехватывать сбои исключения состояния, такие как нарушения прав доступа.</span><span class="sxs-lookup"><span data-stu-id="a2f11-112">Specifies that the application will catch corrupting state exception failures such as access violations.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="a2f11-113">Атрибут enabled</span><span class="sxs-lookup"><span data-stu-id="a2f11-113">enabled Attribute</span></span>  
  
|<span data-ttu-id="a2f11-114">Значение</span><span class="sxs-lookup"><span data-stu-id="a2f11-114">Value</span></span>|<span data-ttu-id="a2f11-115">Описание</span><span class="sxs-lookup"><span data-stu-id="a2f11-115">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="a2f11-116">Приложение не будет перехватывать сбои повреждения состояния, такие как нарушения прав доступа.</span><span class="sxs-lookup"><span data-stu-id="a2f11-116">The application will not catch corrupting state exception failures such as access violations.</span></span> <span data-ttu-id="a2f11-117">Это значение по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="a2f11-117">This is the default.</span></span>|  
|`true`|<span data-ttu-id="a2f11-118">Приложение будет перехватывать сбои исключения состояния, такие как нарушения прав доступа.</span><span class="sxs-lookup"><span data-stu-id="a2f11-118">The application will catch corrupting state exception failures such as access violations.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a2f11-119">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="a2f11-119">Child Elements</span></span>  

 <span data-ttu-id="a2f11-120">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="a2f11-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a2f11-121">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="a2f11-121">Parent Elements</span></span>  
  
|<span data-ttu-id="a2f11-122">Элемент</span><span class="sxs-lookup"><span data-stu-id="a2f11-122">Element</span></span>|<span data-ttu-id="a2f11-123">Описание</span><span class="sxs-lookup"><span data-stu-id="a2f11-123">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="a2f11-124">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a2f11-124">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="a2f11-125">Содержит сведения о привязке сборок и сборке мусора.</span><span class="sxs-lookup"><span data-stu-id="a2f11-125">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a2f11-126">Remarks</span><span class="sxs-lookup"><span data-stu-id="a2f11-126">Remarks</span></span>  

 <span data-ttu-id="a2f11-127">В платформа .NET Framework версии 3,5 и более ранних версиях среда CLR позволяла управляемому коду перехватывать исключения, которые были вызваны поврежденными состояниями процессов.</span><span class="sxs-lookup"><span data-stu-id="a2f11-127">In the .NET Framework version 3.5 and earlier, the common language runtime allowed managed code to catch exceptions that were raised by corrupted process states.</span></span> <span data-ttu-id="a2f11-128">Нарушение прав доступа — это пример исключения этого типа.</span><span class="sxs-lookup"><span data-stu-id="a2f11-128">An access violation is an example of this type of exception.</span></span>  
  
 <span data-ttu-id="a2f11-129">Начиная с платформа .NET Framework 4 управляемый код больше не перехватывает исключения этих типов в `catch` блоках.</span><span class="sxs-lookup"><span data-stu-id="a2f11-129">Starting with the .NET Framework 4, managed code no longer catches these types of exceptions in `catch` blocks.</span></span> <span data-ttu-id="a2f11-130">Однако это изменение можно переопределить и обрабатывать исключения поврежденного состояния двумя способами:</span><span class="sxs-lookup"><span data-stu-id="a2f11-130">However, you can override this change and maintain the handling of corrupted state exceptions in two ways:</span></span>  
  
- <span data-ttu-id="a2f11-131">Задайте `<legacyCorruptedStateExceptionsPolicy>` `enabled` для атрибута элемента значение `true` .</span><span class="sxs-lookup"><span data-stu-id="a2f11-131">Set the `<legacyCorruptedStateExceptionsPolicy>` element's `enabled` attribute to `true`.</span></span> <span data-ttu-id="a2f11-132">Этот параметр конфигурации применяется процессвиде и влияет на все методы.</span><span class="sxs-lookup"><span data-stu-id="a2f11-132">This configuration setting is applied processwide and affects all methods.</span></span>  
  
 <span data-ttu-id="a2f11-133">-или-</span><span class="sxs-lookup"><span data-stu-id="a2f11-133">-or-</span></span>  
  
- <span data-ttu-id="a2f11-134">Примените <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=nameWithType> атрибут к методу, содержащему `catch` блок исключений.</span><span class="sxs-lookup"><span data-stu-id="a2f11-134">Apply the <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=nameWithType> attribute to the method that contains the exceptions `catch` block.</span></span>  
  
 <span data-ttu-id="a2f11-135">Этот элемент конфигурации доступен только в платформа .NET Framework 4 и более поздних версиях.</span><span class="sxs-lookup"><span data-stu-id="a2f11-135">This configuration element is available only in the .NET Framework 4 and later.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a2f11-136">Пример</span><span class="sxs-lookup"><span data-stu-id="a2f11-136">Example</span></span>  

 <span data-ttu-id="a2f11-137">В следующем примере показано, как указать, что приложение должно вернуться к поведению до платформа .NET Framework 4, и перехватить все сбои исключений состояния.</span><span class="sxs-lookup"><span data-stu-id="a2f11-137">The following example shows how to specify that the application should revert to the behavior before the .NET Framework 4, and catch all corrupting state exception failures.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <legacyCorruptedStateExceptionsPolicy enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a2f11-138">См. также</span><span class="sxs-lookup"><span data-stu-id="a2f11-138">See also</span></span>

- <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute>
- [<span data-ttu-id="a2f11-139">Схема параметров среды выполнения</span><span class="sxs-lookup"><span data-stu-id="a2f11-139">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="a2f11-140">Схема файла конфигурации</span><span class="sxs-lookup"><span data-stu-id="a2f11-140">Configuration File Schema</span></span>](../index.md)
