---
description: 'Дополнительные сведения о: <shadowCopyVerifyByTimestamp> element'
title: Элемент <shadowCopyVerifyByTimestamp>
ms.date: 03/30/2017
helpviewer_keywords:
- <shadowCopyTimeStampVerification> element
- shadowCopyTimeStampVerification element
ms.assetid: 2f1648e5-997b-435e-a4f9-d236c574c66c
ms.openlocfilehash: 273bf4c5b01b300cfd564de4ee29c402c6f3e7ff
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99740097"
---
# <a name="shadowcopyverifybytimestamp-element"></a><span data-ttu-id="a03c0-103">Элемент \<shadowCopyVerifyByTimestamp></span><span class="sxs-lookup"><span data-stu-id="a03c0-103">\<shadowCopyVerifyByTimestamp> Element</span></span>

<span data-ttu-id="a03c0-104">Указывает, использует ли теневое копирование поведение при запуске по умолчанию, представленное в платформа .NET Framework 4, или возвращается к поведению при запуске более ранних версий платформа .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a03c0-104">Specifies whether shadow copying uses the default startup behavior introduced in the .NET Framework 4, or reverts to the startup behavior of earlier versions of the .NET Framework.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<shadowCopyVerifyByTimestamp>**  
  
## <a name="syntax"></a><span data-ttu-id="a03c0-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a03c0-105">Syntax</span></span>  
  
```xml  
<shadowCopyVerifyByTimestamp enabled="true|false" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a03c0-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="a03c0-106">Attributes and Elements</span></span>  

 <span data-ttu-id="a03c0-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="a03c0-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a03c0-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="a03c0-108">Attributes</span></span>  
  
|<span data-ttu-id="a03c0-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="a03c0-109">Attribute</span></span>|<span data-ttu-id="a03c0-110">Описание</span><span class="sxs-lookup"><span data-stu-id="a03c0-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a03c0-111">Включено</span><span class="sxs-lookup"><span data-stu-id="a03c0-111">enabled</span></span>|<span data-ttu-id="a03c0-112">Обязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="a03c0-112">Required attribute.</span></span><br /><br /> <span data-ttu-id="a03c0-113">Указывает, были ли домены приложений, использующие теневое копирование, сравниваются метки времени сборки при запуске, чтобы определить, обновлена ли сборка перед теневым копированием сборки.</span><span class="sxs-lookup"><span data-stu-id="a03c0-113">Specifies whether application domains that use shadow copying compare assembly time stamps when starting up, to determine whether an assembly has been updated before shadow copying the assembly.</span></span>|  
  
## <a name="enabled-attribute"></a><span data-ttu-id="a03c0-114">Атрибут enabled</span><span class="sxs-lookup"><span data-stu-id="a03c0-114">enabled Attribute</span></span>  
  
|<span data-ttu-id="a03c0-115">Значение</span><span class="sxs-lookup"><span data-stu-id="a03c0-115">Value</span></span>|<span data-ttu-id="a03c0-116">Описание</span><span class="sxs-lookup"><span data-stu-id="a03c0-116">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="a03c0-117">Да</span><span class="sxs-lookup"><span data-stu-id="a03c0-117">true</span></span>|<span data-ttu-id="a03c0-118">При запуске копирует только сборки, которые были обновлены с момента последнего копирования в каталог теневых копий.</span><span class="sxs-lookup"><span data-stu-id="a03c0-118">At startup, copies only assemblies that have been updated since they were last copied to the shadow copy directory.</span></span> <span data-ttu-id="a03c0-119">Это значение по умолчанию для платформа .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="a03c0-119">This is the default for the .NET Framework 4.</span></span>|  
|<span data-ttu-id="a03c0-120">false</span><span class="sxs-lookup"><span data-stu-id="a03c0-120">false</span></span>|<span data-ttu-id="a03c0-121">Восстанавливает поведение при запуске предыдущих версий платформа .NET Framework, при запуске которого были скопированы все файлы.</span><span class="sxs-lookup"><span data-stu-id="a03c0-121">Reverts to the startup behavior of previous versions of the .NET Framework, which was to copy all files at startup.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a03c0-122">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="a03c0-122">Child Elements</span></span>  

 <span data-ttu-id="a03c0-123">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="a03c0-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a03c0-124">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="a03c0-124">Parent Elements</span></span>  
  
|<span data-ttu-id="a03c0-125">Элемент</span><span class="sxs-lookup"><span data-stu-id="a03c0-125">Element</span></span>|<span data-ttu-id="a03c0-126">Описание</span><span class="sxs-lookup"><span data-stu-id="a03c0-126">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="a03c0-127">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a03c0-127">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="a03c0-128">Содержит сведения о привязке сборок и сборке мусора.</span><span class="sxs-lookup"><span data-stu-id="a03c0-128">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a03c0-129">Remarks</span><span class="sxs-lookup"><span data-stu-id="a03c0-129">Remarks</span></span>  

 <span data-ttu-id="a03c0-130">Начиная с платформа .NET Framework 4 сборки копируются только в том случае, если их метки времени указывают, что они изменились с момента последнего копирования в каталог теневых копий.</span><span class="sxs-lookup"><span data-stu-id="a03c0-130">Starting with the .NET Framework 4, assemblies are shadow copied only if their time stamps indicate that they have changed since they were last copied to the shadow copy directory.</span></span> <span data-ttu-id="a03c0-131">Это улучшает время запуска для многих приложений, использующих теневое копирование, как описано в разделе [теневое копирование сборок](../../../app-domains/shadow-copy-assemblies.md).</span><span class="sxs-lookup"><span data-stu-id="a03c0-131">This improves startup times for many applications that use shadow copying, as described in [Shadow Copying Assemblies](../../../app-domains/shadow-copy-assemblies.md).</span></span> <span data-ttu-id="a03c0-132">Для приложений с большим процентом и высокой частотой обновления сборок это изменение в поведении может не быть выгодно.</span><span class="sxs-lookup"><span data-stu-id="a03c0-132">Applications that have a high percentage and frequency of assembly updates might not benefit from this change in behavior.</span></span> <span data-ttu-id="a03c0-133">В этом случае можно использовать этот элемент для восстановления поведения предыдущих версий платформы .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a03c0-133">In that case, you can use this element to restore the behavior of previous versions of the .NET Framework.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a03c0-134">Пример</span><span class="sxs-lookup"><span data-stu-id="a03c0-134">Example</span></span>  

 <span data-ttu-id="a03c0-135">В следующем примере показано, как отключить поведение при запуске теневого копирования по умолчанию в платформа .NET Framework 4 и вернуться к режиму запуска предыдущих версий платформа .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a03c0-135">The following example shows how to disable the default startup behavior of shadow copying in the .NET Framework 4, and revert to the startup behavior of previous versions of the .NET Framework.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <shadowCopyVerifyByTimestamp enabled="false" />  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a03c0-136">См. также</span><span class="sxs-lookup"><span data-stu-id="a03c0-136">See also</span></span>

- [<span data-ttu-id="a03c0-137">Схема параметров среды выполнения</span><span class="sxs-lookup"><span data-stu-id="a03c0-137">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="a03c0-138">Схема файла конфигурации</span><span class="sxs-lookup"><span data-stu-id="a03c0-138">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="a03c0-139">Теневое копирование сборок</span><span class="sxs-lookup"><span data-stu-id="a03c0-139">Shadow Copying Assemblies</span></span>](../../../app-domains/shadow-copy-assemblies.md)
