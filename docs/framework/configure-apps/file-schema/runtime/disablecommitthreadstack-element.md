---
description: 'Дополнительные сведения о: <disableCommitThreadStack> element'
title: Элемент <disableCommitThreadStack>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/disableCommitThreadStack
- http://schemas.microsoft.com/.NetConfiguration/v2.0#disableCommitThreadStack
helpviewer_keywords:
- <disableCommitThreadStack> element
- disableCommitThreadStack element
ms.assetid: 3559d46a-7640-4c72-9a11-7e980768929e
ms.openlocfilehash: f80a23b12f67b9f3df1ddb010edb735225f6f7a8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787101"
---
# <a name="disablecommitthreadstack-element"></a><span data-ttu-id="2073b-103">Элемент \<disableCommitThreadStack></span><span class="sxs-lookup"><span data-stu-id="2073b-103">\<disableCommitThreadStack> Element</span></span>

<span data-ttu-id="2073b-104">Указывает, фиксируется ли весь стек потоков при запуске потока.</span><span class="sxs-lookup"><span data-stu-id="2073b-104">Specifies whether the full thread stack is committed when a thread is started.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<disableCommitThreadStack>**  
  
## <a name="syntax"></a><span data-ttu-id="2073b-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="2073b-105">Syntax</span></span>  
  
```xml  
<disableCommitThreadStack enabled="0|1"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2073b-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="2073b-106">Attributes and Elements</span></span>  

 <span data-ttu-id="2073b-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="2073b-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2073b-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="2073b-108">Attributes</span></span>  
  
|<span data-ttu-id="2073b-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="2073b-109">Attribute</span></span>|<span data-ttu-id="2073b-110">Описание</span><span class="sxs-lookup"><span data-stu-id="2073b-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2073b-111">Включено</span><span class="sxs-lookup"><span data-stu-id="2073b-111">enabled</span></span>|<span data-ttu-id="2073b-112">Обязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="2073b-112">Required attribute.</span></span><br /><br /> <span data-ttu-id="2073b-113">Указывает, отключена ли фиксация всего стека потоков при запуске потока (режим по умолчанию).</span><span class="sxs-lookup"><span data-stu-id="2073b-113">Specifies whether committing the full thread stack on thread startup (the default behavior) is disabled.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="2073b-114">Атрибут enabled</span><span class="sxs-lookup"><span data-stu-id="2073b-114">enabled Attribute</span></span>  
  
|<span data-ttu-id="2073b-115">Значение</span><span class="sxs-lookup"><span data-stu-id="2073b-115">Value</span></span>|<span data-ttu-id="2073b-116">Описание</span><span class="sxs-lookup"><span data-stu-id="2073b-116">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="2073b-117">0</span><span class="sxs-lookup"><span data-stu-id="2073b-117">0</span></span>|<span data-ttu-id="2073b-118">Не отключать для среды CLR режим по умолчанию, который заключается в фиксации всего стека потоков при запуске потока.</span><span class="sxs-lookup"><span data-stu-id="2073b-118">Do not disable the default behavior of the common language runtime, which is to commit the full thread stack when a thread is started.</span></span>|  
|<span data-ttu-id="2073b-119">1</span><span class="sxs-lookup"><span data-stu-id="2073b-119">1</span></span>|<span data-ttu-id="2073b-120">Отключить для среды CLR режим по умолчанию, который заключается в фиксации всего стека потоков при запуске потока.</span><span class="sxs-lookup"><span data-stu-id="2073b-120">Disable the default behavior of the common language runtime, which is to commit the full thread stack when a thread is started.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2073b-121">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="2073b-121">Child Elements</span></span>  

 <span data-ttu-id="2073b-122">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="2073b-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2073b-123">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="2073b-123">Parent Elements</span></span>  
  
|<span data-ttu-id="2073b-124">Элемент</span><span class="sxs-lookup"><span data-stu-id="2073b-124">Element</span></span>|<span data-ttu-id="2073b-125">Описание</span><span class="sxs-lookup"><span data-stu-id="2073b-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="2073b-126">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="2073b-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="2073b-127">Содержит сведения о привязке сборок и сборке мусора.</span><span class="sxs-lookup"><span data-stu-id="2073b-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2073b-128">Remarks</span><span class="sxs-lookup"><span data-stu-id="2073b-128">Remarks</span></span>  

 <span data-ttu-id="2073b-129">Режим по умолчанию для среды CLR заключается в фиксации всего стека потоков при запуске потока.</span><span class="sxs-lookup"><span data-stu-id="2073b-129">The default behavior of the common language runtime is to commit the full thread stack when a thread is started.</span></span> <span data-ttu-id="2073b-130">Если на сервере с ограниченным объемом памяти необходимо создать большое число потоков и большинство из этих потоков будут использовать очень небольшое пространство стека, сервер может работать лучше, если среда не фиксирует весь стек потоков сразу после запуска потока.</span><span class="sxs-lookup"><span data-stu-id="2073b-130">If a large number of threads must be created on a server that has limited memory, and most of those threads will use very little stack space, the server might perform better if the common language runtime does not commit the full thread stack immediately when a thread is started.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2073b-131">Неуправляемые узлы могут использовать флаг запуска `STARTUP_DISABLE_COMMITTHREADSTACK` в перечислении [STARTUP_FLAGS](../../../unmanaged-api/hosting/startup-flags-enumeration.md) для достижения такого же результата.</span><span class="sxs-lookup"><span data-stu-id="2073b-131">Unmanaged hosts can use the `STARTUP_DISABLE_COMMITTHREADSTACK` startup flag in the [STARTUP_FLAGS](../../../unmanaged-api/hosting/startup-flags-enumeration.md) enumeration to accomplish the same result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2073b-132">Пример</span><span class="sxs-lookup"><span data-stu-id="2073b-132">Example</span></span>  

 <span data-ttu-id="2073b-133">В следующем примере показано, как отключить для среды CLR режим по умолчанию, который заключается в фиксации всего стека потоков при запуске потока.</span><span class="sxs-lookup"><span data-stu-id="2073b-133">The following example shows how to disable the default behavior of the common language runtime, which is to commit the full thread stack on thread startup.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <disableCommitThreadStack enabled="1" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2073b-134">См. также</span><span class="sxs-lookup"><span data-stu-id="2073b-134">See also</span></span>

- [<span data-ttu-id="2073b-135">Схема параметров среды выполнения</span><span class="sxs-lookup"><span data-stu-id="2073b-135">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="2073b-136">Схема файла конфигурации</span><span class="sxs-lookup"><span data-stu-id="2073b-136">Configuration File Schema</span></span>](../index.md)
