---
description: 'Дополнительные сведения о: <etwEnable> element'
title: Элемент <etwEnable>
ms.date: 03/30/2017
helpviewer_keywords:
- etwEnable element
- <etwEnable> element
ms.assetid: 29dde982-6d8b-4099-8867-ad0d7733f6dc
ms.openlocfilehash: 224784f47d15788ded41a5756e1d179a5a25907b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787049"
---
# <a name="etwenable-element"></a><span data-ttu-id="705f8-103">Элемент \<etwEnable></span><span class="sxs-lookup"><span data-stu-id="705f8-103">\<etwEnable> Element</span></span>

<span data-ttu-id="705f8-104">Указывает, следует ли включить трассировку событий Windows для событий среды CLR.</span><span class="sxs-lookup"><span data-stu-id="705f8-104">Specifies whether to enable event tracing for Windows (ETW) for common language runtime events.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<etwEnabled>**  
  
## <a name="syntax"></a><span data-ttu-id="705f8-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="705f8-105">Syntax</span></span>  
  
```xml  
<etwEnable enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="705f8-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="705f8-106">Attributes and Elements</span></span>  

 <span data-ttu-id="705f8-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="705f8-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="705f8-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="705f8-108">Attributes</span></span>  
  
|<span data-ttu-id="705f8-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="705f8-109">Attribute</span></span>|<span data-ttu-id="705f8-110">Описание</span><span class="sxs-lookup"><span data-stu-id="705f8-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="705f8-111">Включено</span><span class="sxs-lookup"><span data-stu-id="705f8-111">enabled</span></span>|<span data-ttu-id="705f8-112">Обязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="705f8-112">Required attribute.</span></span><br /><br /> <span data-ttu-id="705f8-113">Указывает, включена ли трассировка событий Windows.</span><span class="sxs-lookup"><span data-stu-id="705f8-113">Specifies whether ETW should be enabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="705f8-114">Атрибут enabled</span><span class="sxs-lookup"><span data-stu-id="705f8-114">enabled Attribute</span></span>  
  
|<span data-ttu-id="705f8-115">Значение</span><span class="sxs-lookup"><span data-stu-id="705f8-115">Value</span></span>|<span data-ttu-id="705f8-116">Описание</span><span class="sxs-lookup"><span data-stu-id="705f8-116">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="705f8-117">Да</span><span class="sxs-lookup"><span data-stu-id="705f8-117">true</span></span>|<span data-ttu-id="705f8-118">Включите ETW.</span><span class="sxs-lookup"><span data-stu-id="705f8-118">Enable ETW.</span></span> <span data-ttu-id="705f8-119">Это значение по умолчанию для версий Windows, начинающихся с операционных систем Windows Vista и Windows Server 2008.</span><span class="sxs-lookup"><span data-stu-id="705f8-119">This is the default for versions of Windows beginning with the Windows Vista and Windows Server 2008 operating systems.</span></span>|  
|<span data-ttu-id="705f8-120">false</span><span class="sxs-lookup"><span data-stu-id="705f8-120">false</span></span>|<span data-ttu-id="705f8-121">Отключите трассировку событий Windows.</span><span class="sxs-lookup"><span data-stu-id="705f8-121">Disable ETW.</span></span> <span data-ttu-id="705f8-122">Это значение по умолчанию для более ранних версий Windows.</span><span class="sxs-lookup"><span data-stu-id="705f8-122">This is the default for earlier versions of Windows.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="705f8-123">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="705f8-123">Child Elements</span></span>  

 <span data-ttu-id="705f8-124">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="705f8-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="705f8-125">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="705f8-125">Parent Elements</span></span>  
  
|<span data-ttu-id="705f8-126">Элемент</span><span class="sxs-lookup"><span data-stu-id="705f8-126">Element</span></span>|<span data-ttu-id="705f8-127">Описание</span><span class="sxs-lookup"><span data-stu-id="705f8-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="705f8-128">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="705f8-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="705f8-129">Содержит сведения о привязке сборок и сборке мусора.</span><span class="sxs-lookup"><span data-stu-id="705f8-129">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="705f8-130">Remarks</span><span class="sxs-lookup"><span data-stu-id="705f8-130">Remarks</span></span>  

 <span data-ttu-id="705f8-131">Начиная с Windows Vista трассировка событий Windows включена по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="705f8-131">Beginning with Windows Vista, ETW is enabled by default.</span></span> <span data-ttu-id="705f8-132">Используйте этот элемент, чтобы отключить ETW для приложения.</span><span class="sxs-lookup"><span data-stu-id="705f8-132">Use this element to disable ETW for an application.</span></span> <span data-ttu-id="705f8-133">В более ранних версиях Windows этот элемент используется для включения ETW для приложения.</span><span class="sxs-lookup"><span data-stu-id="705f8-133">In earlier versions of Windows, use this element to enable ETW for an application.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="705f8-134">Трассировку событий Windows можно включить или отключить глобально на сервере с помощью параметра реестра.</span><span class="sxs-lookup"><span data-stu-id="705f8-134">ETW can be enabled or disabled globally on a server by using a registry setting.</span></span> <span data-ttu-id="705f8-135">См. раздел [Управление ведением журнала платформа .NET Framework](../../../performance/controlling-logging.md).</span><span class="sxs-lookup"><span data-stu-id="705f8-135">See [Controlling .NET Framework Logging](../../../performance/controlling-logging.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="705f8-136">Пример</span><span class="sxs-lookup"><span data-stu-id="705f8-136">Example</span></span>  

 <span data-ttu-id="705f8-137">В следующем примере показано, как включить трассировку ETW для приложения.</span><span class="sxs-lookup"><span data-stu-id="705f8-137">The following example shows how to enable ETW tracing for an application.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <etwEnable enabled="true" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="705f8-138">См. также</span><span class="sxs-lookup"><span data-stu-id="705f8-138">See also</span></span>

- [<span data-ttu-id="705f8-139">Схема параметров среды выполнения</span><span class="sxs-lookup"><span data-stu-id="705f8-139">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="705f8-140">Схема файла конфигурации</span><span class="sxs-lookup"><span data-stu-id="705f8-140">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="705f8-141">Контроль ведения журнала .NET Framework</span><span class="sxs-lookup"><span data-stu-id="705f8-141">Controlling .NET Framework Logging</span></span>](../../../performance/controlling-logging.md)
