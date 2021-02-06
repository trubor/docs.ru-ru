---
description: 'Дополнительные сведения о: <add> Element для <switches>'
title: Элемент <add> для <switches>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/switches/add
helpviewer_keywords:
- <add> element for <switches>
- add element for <switches>
ms.assetid: 712ac3a7-7abf-4a9e-8db4-acd241c2f369
ms.openlocfilehash: fc47a8518aca1e4e6390d9d7eba97d5fb7a7664e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639722"
---
# <a name="add-element-for-switches"></a><span data-ttu-id="e6e6d-103">Элемент \<add> для \<switches></span><span class="sxs-lookup"><span data-stu-id="e6e6d-103">\<add> Element for \<switches></span></span>

<span data-ttu-id="e6e6d-104">Задает уровень, на котором установлен ключ трассировки.</span><span class="sxs-lookup"><span data-stu-id="e6e6d-104">Specifies the level where a trace switch is set.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<switches>**](switches-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="e6e6d-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e6e6d-105">Syntax</span></span>  
  
```xml  
<add name="switch name"  
     value="value"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e6e6d-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="e6e6d-106">Attributes and Elements</span></span>  

 <span data-ttu-id="e6e6d-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="e6e6d-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e6e6d-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="e6e6d-108">Attributes</span></span>  
  
|<span data-ttu-id="e6e6d-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="e6e6d-109">Attribute</span></span>|<span data-ttu-id="e6e6d-110">Описание</span><span class="sxs-lookup"><span data-stu-id="e6e6d-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e6e6d-111">**name**</span><span class="sxs-lookup"><span data-stu-id="e6e6d-111">**name**</span></span>|<span data-ttu-id="e6e6d-112">Обязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="e6e6d-112">Required attribute.</span></span><br /><br /> <span data-ttu-id="e6e6d-113">Указывает имя переключателя.</span><span class="sxs-lookup"><span data-stu-id="e6e6d-113">Specifies the name of the switch.</span></span> <span data-ttu-id="e6e6d-114">Значение этого атрибута соответствует параметру *DisplayName* , переданному в конструктор переключателя.</span><span class="sxs-lookup"><span data-stu-id="e6e6d-114">The value of this attribute corresponds to the *displayName* parameter that is passed to switch constructor.</span></span>|  
|<span data-ttu-id="e6e6d-115">**value**</span><span class="sxs-lookup"><span data-stu-id="e6e6d-115">**value**</span></span>|<span data-ttu-id="e6e6d-116">Обязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="e6e6d-116">Required attribute.</span></span><br /><br /> <span data-ttu-id="e6e6d-117">Задает уровень переключателя.</span><span class="sxs-lookup"><span data-stu-id="e6e6d-117">Specifies the level of the switch.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e6e6d-118">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="e6e6d-118">Child Elements</span></span>  

 <span data-ttu-id="e6e6d-119">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="e6e6d-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e6e6d-120">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="e6e6d-120">Parent Elements</span></span>  
  
|<span data-ttu-id="e6e6d-121">Элемент</span><span class="sxs-lookup"><span data-stu-id="e6e6d-121">Element</span></span>|<span data-ttu-id="e6e6d-122">Описание</span><span class="sxs-lookup"><span data-stu-id="e6e6d-122">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="e6e6d-123">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e6e6d-123">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`switches`|<span data-ttu-id="e6e6d-124">Содержит ключи трассировки и уровень, на котором они установлены.</span><span class="sxs-lookup"><span data-stu-id="e6e6d-124">Contains trace switches and the level where the trace switches are set.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="e6e6d-125">Задает прослушиватели трассировки, собирающие, хранящие и маршрутизирующие сообщения, а также уровень, на котором установлен ключ трассировки.</span><span class="sxs-lookup"><span data-stu-id="e6e6d-125">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e6e6d-126">Remarks</span><span class="sxs-lookup"><span data-stu-id="e6e6d-126">Remarks</span></span>  

 <span data-ttu-id="e6e6d-127">Уровень переключателя трассировки можно изменить, поместив его в файл конфигурации.</span><span class="sxs-lookup"><span data-stu-id="e6e6d-127">You can change the level of a trace switch by putting it in a configuration file.</span></span> <span data-ttu-id="e6e6d-128">Если параметр имеет значение <xref:System.Diagnostics.BooleanSwitch> , его можно включить и отключить.</span><span class="sxs-lookup"><span data-stu-id="e6e6d-128">If the switch is a <xref:System.Diagnostics.BooleanSwitch>, you can turn it on and off.</span></span> <span data-ttu-id="e6e6d-129">Если параметр имеет значение <xref:System.Diagnostics.TraceSwitch> , можно назначить для него разные уровни, чтобы указать типы трассировки или сообщения отладки, выданные приложением.</span><span class="sxs-lookup"><span data-stu-id="e6e6d-129">If the switch is a <xref:System.Diagnostics.TraceSwitch>, you can assign different levels to it to specify the types of trace or debug messages the application outputs.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e6e6d-130">Пример</span><span class="sxs-lookup"><span data-stu-id="e6e6d-130">Example</span></span>  

 <span data-ttu-id="e6e6d-131">В следующем примере показано использование **\<add>** элемента для задания `General` переключателя трассировки на <xref:System.Diagnostics.TraceLevel> уровне и включения `Data` логического переключателя трассировки.</span><span class="sxs-lookup"><span data-stu-id="e6e6d-131">The following example shows how to use the **\<add>** element to set the `General` trace switch to the <xref:System.Diagnostics.TraceLevel> level, and enable the `Data` Boolean trace switch.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e6e6d-132">См. также</span><span class="sxs-lookup"><span data-stu-id="e6e6d-132">See also</span></span>

- <xref:System.Diagnostics.Switch>
- <xref:System.Diagnostics.TraceSwitch>
- <xref:System.Diagnostics.BooleanSwitch>
- [<span data-ttu-id="e6e6d-133">Схема параметров трассировки и отладки</span><span class="sxs-lookup"><span data-stu-id="e6e6d-133">Trace and Debug Settings Schema</span></span>](index.md)
