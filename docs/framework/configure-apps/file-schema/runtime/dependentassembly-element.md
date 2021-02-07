---
description: 'Дополнительные сведения о: <dependentAssembly> element'
title: Элемент <dependentAssembly>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/dependentAssembly
- http://schemas.microsoft.com/.NetConfiguration/v2.0#dependentAssembly
helpviewer_keywords:
- container tags, <dependentAssembly> element
- dependentAssembly element
- <dependentAssembly> element
ms.assetid: 14e95627-dd79-4b82-ac85-e682aa3a31d8
ms.openlocfilehash: c804920de961fc609fd04a0853ecbdbc9202e5be
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99719088"
---
# <a name="dependentassembly-element"></a><span data-ttu-id="ec3cd-103">Элемент \<dependentAssembly></span><span class="sxs-lookup"><span data-stu-id="ec3cd-103">\<dependentAssembly> Element</span></span>

<span data-ttu-id="ec3cd-104">Инкапсулирует политику привязки и расположение каждой сборки.</span><span class="sxs-lookup"><span data-stu-id="ec3cd-104">Encapsulates binding policy and assembly location for each assembly.</span></span> <span data-ttu-id="ec3cd-105">`dependentAssembly`Для каждой сборки используется один элемент.</span><span class="sxs-lookup"><span data-stu-id="ec3cd-105">Use one `dependentAssembly` element for each assembly.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dependentAssembly>**  
  
## <a name="syntax"></a><span data-ttu-id="ec3cd-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ec3cd-106">Syntax</span></span>  
  
```xml  
<dependentAssembly>
</dependentAssembly>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ec3cd-107">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="ec3cd-107">Attributes and Elements</span></span>  

 <span data-ttu-id="ec3cd-108">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="ec3cd-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ec3cd-109">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="ec3cd-109">Attributes</span></span>  

 <span data-ttu-id="ec3cd-110">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="ec3cd-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ec3cd-111">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="ec3cd-111">Child Elements</span></span>  
  
|<span data-ttu-id="ec3cd-112">Элемент</span><span class="sxs-lookup"><span data-stu-id="ec3cd-112">Element</span></span>|<span data-ttu-id="ec3cd-113">Описание</span><span class="sxs-lookup"><span data-stu-id="ec3cd-113">Description</span></span>|  
|-------------|-----------------|  
|`assemblyIdentity`|<span data-ttu-id="ec3cd-114">Содержит идентифицирующие сведения о сборке.</span><span class="sxs-lookup"><span data-stu-id="ec3cd-114">Contains identifying information about the assembly.</span></span> <span data-ttu-id="ec3cd-115">Этот элемент должен включаться в каждый `dependentAssembly` элемент.</span><span class="sxs-lookup"><span data-stu-id="ec3cd-115">This element must be included in each `dependentAssembly` element.</span></span>|  
|`codeBase`|<span data-ttu-id="ec3cd-116">Указывает, где среда выполнения может найти общую сборку, если она не установлена на компьютере.</span><span class="sxs-lookup"><span data-stu-id="ec3cd-116">Specifies where the runtime can find a shared assembly if it is not installed on the computer.</span></span>|  
|`bindingRedirect`|<span data-ttu-id="ec3cd-117">Перенаправляет одну версию сборки на другую.</span><span class="sxs-lookup"><span data-stu-id="ec3cd-117">Redirects one assembly version to another.</span></span>|  
|`publisherPolicy`|<span data-ttu-id="ec3cd-118">Указывает, применяет ли среда выполнения политику издателя для этой сборки.</span><span class="sxs-lookup"><span data-stu-id="ec3cd-118">Specifies whether the runtime applies publisher policy for this assembly.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ec3cd-119">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="ec3cd-119">Parent Elements</span></span>  
  
|<span data-ttu-id="ec3cd-120">Элемент</span><span class="sxs-lookup"><span data-stu-id="ec3cd-120">Element</span></span>|<span data-ttu-id="ec3cd-121">Описание</span><span class="sxs-lookup"><span data-stu-id="ec3cd-121">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="ec3cd-122">Содержит сведения о перенаправлении версии сборки и о расположениях сборок.</span><span class="sxs-lookup"><span data-stu-id="ec3cd-122">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="ec3cd-123">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ec3cd-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="ec3cd-124">Содержит сведения о привязке сборок и сборке мусора.</span><span class="sxs-lookup"><span data-stu-id="ec3cd-124">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ec3cd-125">Пример</span><span class="sxs-lookup"><span data-stu-id="ec3cd-125">Example</span></span>  

 <span data-ttu-id="ec3cd-126">В следующем примере показано, как инкапсулировать сведения о сборке для двух сборок.</span><span class="sxs-lookup"><span data-stu-id="ec3cd-126">The following example shows how to encapsulate assembly information for two assemblies.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <dependentAssembly>  
            <assemblyIdentity name="myAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <!--Redirection and codeBase policy for myAssembly.-->  
         </dependentAssembly>  
         <dependentAssembly>  
            <assemblyIdentity name="mySecondAssembly"  
                              publicKeyToken="32ab4ba45e0a69a1"  
                              culture="neutral" />  
            <!--Redirection and codeBase policy for mySecondAssembly.-->  
         </dependentAssembly>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="ec3cd-127">См. также</span><span class="sxs-lookup"><span data-stu-id="ec3cd-127">See also</span></span>

- [<span data-ttu-id="ec3cd-128">Схема параметров среды выполнения</span><span class="sxs-lookup"><span data-stu-id="ec3cd-128">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="ec3cd-129">Схема файла конфигурации</span><span class="sxs-lookup"><span data-stu-id="ec3cd-129">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="ec3cd-130">Перенаправление версий сборки</span><span class="sxs-lookup"><span data-stu-id="ec3cd-130">Redirecting Assembly Versions</span></span>](../../redirect-assembly-versions.md)
