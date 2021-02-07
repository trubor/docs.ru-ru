---
description: 'Дополнительные сведения о: <switches> element'
title: Элемент <switches>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/switches
- http://schemas.microsoft.com/.NetConfiguration/v2.0#switches
helpviewer_keywords:
- <switches> element
- switches element
- trace switches, <switches> element
ms.assetid: 4cf36786-b89a-40e2-a0f1-86bb9b783343
ms.openlocfilehash: d0ffdf2bdc4dacd157d09d34c40063b687595e3d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99750524"
---
# <a name="switches-element"></a><span data-ttu-id="e669f-103">Элемент \<switches></span><span class="sxs-lookup"><span data-stu-id="e669f-103">\<switches> Element</span></span>

<span data-ttu-id="e669f-104">Содержит ключи трассировки и уровень, на котором они установлены.</span><span class="sxs-lookup"><span data-stu-id="e669f-104">Contains trace switches and the level where the trace switches are set.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<switches>**

## <a name="syntax"></a><span data-ttu-id="e669f-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e669f-105">Syntax</span></span>  
  
```xml  
      <switches>
</switches>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e669f-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="e669f-106">Attributes and Elements</span></span>  

 <span data-ttu-id="e669f-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="e669f-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e669f-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="e669f-108">Attributes</span></span>  

 <span data-ttu-id="e669f-109">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="e669f-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e669f-110">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="e669f-110">Child Elements</span></span>  
  
|<span data-ttu-id="e669f-111">Элемент</span><span class="sxs-lookup"><span data-stu-id="e669f-111">Element</span></span>|<span data-ttu-id="e669f-112">Описание</span><span class="sxs-lookup"><span data-stu-id="e669f-112">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-element-for-switches.md)|<span data-ttu-id="e669f-113">Задает уровень, на котором установлен ключ трассировки.</span><span class="sxs-lookup"><span data-stu-id="e669f-113">Specifies the level where a trace switch is set.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e669f-114">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="e669f-114">Parent Elements</span></span>  
  
|<span data-ttu-id="e669f-115">Элемент</span><span class="sxs-lookup"><span data-stu-id="e669f-115">Element</span></span>|<span data-ttu-id="e669f-116">Описание</span><span class="sxs-lookup"><span data-stu-id="e669f-116">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="e669f-117">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e669f-117">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`System.diagnostics`|<span data-ttu-id="e669f-118">Задает прослушиватели трассировки, собирающие, хранящие и маршрутизирующие сообщения, а также уровень, на котором установлен ключ трассировки.</span><span class="sxs-lookup"><span data-stu-id="e669f-118">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e669f-119">Remarks</span><span class="sxs-lookup"><span data-stu-id="e669f-119">Remarks</span></span>  

 <span data-ttu-id="e669f-120">Уровень переключателя трассировки можно изменить, поместив его в файл конфигурации.</span><span class="sxs-lookup"><span data-stu-id="e669f-120">You can change the level of a trace switch by putting it in a configuration file.</span></span> <span data-ttu-id="e669f-121">Если параметр имеет значение <xref:System.Diagnostics.BooleanSwitch> , его можно включить и отключить.</span><span class="sxs-lookup"><span data-stu-id="e669f-121">If the switch is a <xref:System.Diagnostics.BooleanSwitch>, you can turn it on and off.</span></span> <span data-ttu-id="e669f-122">Если параметр имеет значение <xref:System.Diagnostics.TraceSwitch> , можно назначить для него разные уровни, чтобы указать типы трассировки или сообщения отладки, выданные приложением.</span><span class="sxs-lookup"><span data-stu-id="e669f-122">If the switch is a <xref:System.Diagnostics.TraceSwitch>, you can assign different levels to it to specify the types of trace or debug messages the application outputs.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e669f-123">Пример</span><span class="sxs-lookup"><span data-stu-id="e669f-123">Example</span></span>  

 <span data-ttu-id="e669f-124">В следующем примере показано использование **\<switch>** элемента для задания `General` переключателя трассировки на <xref:System.Diagnostics.TraceLevel> уровне и включения `Data` логического переключателя трассировки.</span><span class="sxs-lookup"><span data-stu-id="e669f-124">The following example shows how to use the **\<switch>** element to set the `General` trace switch to the <xref:System.Diagnostics.TraceLevel> level, and enable the `Data` Boolean trace switch.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <switches>  
         <add name="General" value="4" />  
         <add name="Data" value="1" />  
      </switches>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e669f-125">См. также</span><span class="sxs-lookup"><span data-stu-id="e669f-125">See also</span></span>

- <xref:System.Diagnostics.Switch>
- <xref:System.Diagnostics.TraceSwitch>
- <xref:System.Diagnostics.BooleanSwitch>
- [<span data-ttu-id="e669f-126">Схема параметров трассировки и отладки</span><span class="sxs-lookup"><span data-stu-id="e669f-126">Trace and Debug Settings Schema</span></span>](index.md)
