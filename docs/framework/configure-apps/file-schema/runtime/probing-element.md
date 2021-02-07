---
description: 'Дополнительные сведения о: <probing> element'
title: Элемент <probing>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/assemblyBinding/probing
- http://schemas.microsoft.com/.NetConfiguration/v2.0#probing
helpviewer_keywords:
- <probing> element
- container tags, <probing> element
- probing element
ms.assetid: 09c80fc9-1ba5-4192-89f7-3a79b2e4b024
ms.openlocfilehash: 404e53f735ce02c2a3d7911216f834d38e309789
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99726108"
---
# <a name="probing-element"></a><span data-ttu-id="16d37-103">Элемент \<probing></span><span class="sxs-lookup"><span data-stu-id="16d37-103">\<probing> Element</span></span>

<span data-ttu-id="16d37-104">Задает базовые подкаталоги приложения для поиска средой CLR при загрузке сборок.</span><span class="sxs-lookup"><span data-stu-id="16d37-104">Specifies application base subdirectories for the common language runtime to search when loading assemblies.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-runtime.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<probing>**  
  
## <a name="syntax"></a><span data-ttu-id="16d37-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="16d37-105">Syntax</span></span>  
  
```xml  
<probing privatePath="paths"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="16d37-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="16d37-106">Attributes and Elements</span></span>  

 <span data-ttu-id="16d37-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="16d37-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="16d37-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="16d37-108">Attributes</span></span>  
  
|<span data-ttu-id="16d37-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="16d37-109">Attribute</span></span>|<span data-ttu-id="16d37-110">Описание</span><span class="sxs-lookup"><span data-stu-id="16d37-110">Description</span></span>|  
|---------------|-----------------|  
|`privatePath`|<span data-ttu-id="16d37-111">Обязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="16d37-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="16d37-112">Указывает подкаталоги базового каталога приложения, которые могут содержать сборки.</span><span class="sxs-lookup"><span data-stu-id="16d37-112">Specifies subdirectories of the application's base directory that might contain assemblies.</span></span> <span data-ttu-id="16d37-113">Для каждого подкаталога следует выделить точку с запятой.</span><span class="sxs-lookup"><span data-stu-id="16d37-113">Delimit each subdirectory with a semicolon.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="16d37-114">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="16d37-114">Child Elements</span></span>  

<span data-ttu-id="16d37-115">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="16d37-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="16d37-116">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="16d37-116">Parent Elements</span></span>  
  
|<span data-ttu-id="16d37-117">Элемент</span><span class="sxs-lookup"><span data-stu-id="16d37-117">Element</span></span>|<span data-ttu-id="16d37-118">Описание</span><span class="sxs-lookup"><span data-stu-id="16d37-118">Description</span></span>|  
|-------------|-----------------|  
|`assemblyBinding`|<span data-ttu-id="16d37-119">Содержит сведения о перенаправлении версии сборки и о расположениях сборок.</span><span class="sxs-lookup"><span data-stu-id="16d37-119">Contains information about assembly version redirection and the locations of assemblies.</span></span>|  
|`configuration`|<span data-ttu-id="16d37-120">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="16d37-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`runtime`|<span data-ttu-id="16d37-121">Содержит сведения о привязке сборок и сборке мусора.</span><span class="sxs-lookup"><span data-stu-id="16d37-121">Contains information about assembly binding and garbage collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="16d37-122">Пример</span><span class="sxs-lookup"><span data-stu-id="16d37-122">Example</span></span>  

 <span data-ttu-id="16d37-123">В следующем примере показано, как задать базовые подкаталоги приложения, которые среда выполнения должна использовать для поиска сборок.</span><span class="sxs-lookup"><span data-stu-id="16d37-123">The following example shows how to specify application base subdirectories the runtime should search for assemblies.</span></span>  
  
```xml  
<configuration>  
   <runtime>  
      <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
         <probing privatePath="bin;bin2\subbin;bin3"/>  
      </assemblyBinding>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="16d37-124">См. также</span><span class="sxs-lookup"><span data-stu-id="16d37-124">See also</span></span>

- [<span data-ttu-id="16d37-125">Схема параметров среды выполнения</span><span class="sxs-lookup"><span data-stu-id="16d37-125">Runtime settings schema</span></span>](index.md)
- [<span data-ttu-id="16d37-126">Схема файла конфигурации</span><span class="sxs-lookup"><span data-stu-id="16d37-126">Configuration file schema</span></span>](../index.md)
- [<span data-ttu-id="16d37-127">Укажите расположение сборки</span><span class="sxs-lookup"><span data-stu-id="16d37-127">Specify an assembly's location</span></span>](../../../../standard/assembly/location.md)
- [<span data-ttu-id="16d37-128">Обнаружение сборок в среде выполнения</span><span class="sxs-lookup"><span data-stu-id="16d37-128">How the runtime locates assemblies</span></span>](../../../deployment/how-the-runtime-locates-assemblies.md)
