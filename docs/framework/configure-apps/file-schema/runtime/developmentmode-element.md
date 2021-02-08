---
description: 'Дополнительные сведения о: <developmentMode> element'
title: Элемент <developmentMode>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/developmentMode
- http://schemas.microsoft.com/.NetConfiguration/v2.0#developmentMode
helpviewer_keywords:
- developmentMode element
- container tags, <developmentMode> element
- <developmentMode> element
ms.assetid: 60e79a8c-415a-497d-be29-b9d0fd9bdee3
ms.openlocfilehash: 668461d13c8a1767268692804e9783bb6d4b9a56
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99787127"
---
# <a name="developmentmode-element"></a><span data-ttu-id="e815f-103">Элемент \<developmentMode></span><span class="sxs-lookup"><span data-stu-id="e815f-103">\<developmentMode> Element</span></span>

<span data-ttu-id="e815f-104">Указывает, выполняет ли среда поиск сборок в каталогах, указанных в переменной среды DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="e815f-104">Specifies whether the runtime searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<developmentMode>**  
  
## <a name="syntax"></a><span data-ttu-id="e815f-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e815f-105">Syntax</span></span>  
  
```xml  
<developmentMode developerInstallation="true | false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e815f-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="e815f-106">Attributes and Elements</span></span>  

 <span data-ttu-id="e815f-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="e815f-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e815f-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="e815f-108">Attributes</span></span>  
  
|<span data-ttu-id="e815f-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="e815f-109">Attribute</span></span>|<span data-ttu-id="e815f-110">Описание</span><span class="sxs-lookup"><span data-stu-id="e815f-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e815f-111">**девелоперинсталлатион**</span><span class="sxs-lookup"><span data-stu-id="e815f-111">**developerInstallation**</span></span>|<span data-ttu-id="e815f-112">Указывает, выполняет ли среда поиск сборок в каталогах, указанных в переменной среды DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="e815f-112">Specifies whether the runtime searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>|  
  
## <a name="developerinstallation-attribute"></a><span data-ttu-id="e815f-113">Атрибут Девелоперинсталлатион</span><span class="sxs-lookup"><span data-stu-id="e815f-113">developerInstallation Attribute</span></span>  
  
|<span data-ttu-id="e815f-114">Значение</span><span class="sxs-lookup"><span data-stu-id="e815f-114">Value</span></span>|<span data-ttu-id="e815f-115">Описание</span><span class="sxs-lookup"><span data-stu-id="e815f-115">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="e815f-116">**true**</span><span class="sxs-lookup"><span data-stu-id="e815f-116">**true**</span></span>|<span data-ttu-id="e815f-117">Выполняет поиск сборок в каталогах, заданных переменной среды DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="e815f-117">Searches for assemblies in directories specified by the DEVPATH environment variable.</span></span>|  
|<span data-ttu-id="e815f-118">**false**</span><span class="sxs-lookup"><span data-stu-id="e815f-118">**false**</span></span>|<span data-ttu-id="e815f-119">Не выполняет поиск сборок в каталогах, заданных переменной среды DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="e815f-119">Does not search for assemblies in directories specified by the DEVPATH environment variable.</span></span> <span data-ttu-id="e815f-120">Это значение установлено по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="e815f-120">This is the default</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e815f-121">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="e815f-121">Child Elements</span></span>  

 <span data-ttu-id="e815f-122">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="e815f-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e815f-123">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="e815f-123">Parent Elements</span></span>  
  
|<span data-ttu-id="e815f-124">Элемент</span><span class="sxs-lookup"><span data-stu-id="e815f-124">Element</span></span>|<span data-ttu-id="e815f-125">Описание</span><span class="sxs-lookup"><span data-stu-id="e815f-125">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="e815f-126">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e815f-126">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="e815f-127">Содержит сведения о привязке сборок и сборке мусора.</span><span class="sxs-lookup"><span data-stu-id="e815f-127">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e815f-128">Remarks</span><span class="sxs-lookup"><span data-stu-id="e815f-128">Remarks</span></span>  

 <span data-ttu-id="e815f-129">Используйте этот параметр только во время разработки.</span><span class="sxs-lookup"><span data-stu-id="e815f-129">Use this setting only at development time.</span></span> <span data-ttu-id="e815f-130">Среда выполнения не проверяет версии сборок со строгими именами, найденных в DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="e815f-130">The runtime does not check the versions on strong-named assemblies found in the DEVPATH.</span></span> <span data-ttu-id="e815f-131">Он просто использует первую найденную сборку.</span><span class="sxs-lookup"><span data-stu-id="e815f-131">It simply uses the first assembly it finds.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e815f-132">Пример</span><span class="sxs-lookup"><span data-stu-id="e815f-132">Example</span></span>  

 <span data-ttu-id="e815f-133">В следующем примере показано, как заставить среду выполнения искать сборки в каталогах, заданных переменной среды DEVPATH.</span><span class="sxs-lookup"><span data-stu-id="e815f-133">The following example shows how to cause the runtime to search for assemblies in directories specified by the DEVPATH environment variable.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <developmentMode developerInstallation="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e815f-134">См. также</span><span class="sxs-lookup"><span data-stu-id="e815f-134">See also</span></span>

- [<span data-ttu-id="e815f-135">Схема параметров среды выполнения</span><span class="sxs-lookup"><span data-stu-id="e815f-135">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="e815f-136">Схема файла конфигурации</span><span class="sxs-lookup"><span data-stu-id="e815f-136">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="e815f-137">Практическое руководство. Поиск сборок с помощью DEVPATH</span><span class="sxs-lookup"><span data-stu-id="e815f-137">How to: Locate Assemblies by Using DEVPATH</span></span>](../../how-to-locate-assemblies-by-using-devpath.md)
