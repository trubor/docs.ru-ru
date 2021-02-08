---
description: 'Дополнительные сведения о: <filter> Element для <add> for <sharedListeners>'
title: <filter> Элемент для <add> для <sharedListeners>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sharedListeners/add/filter
helpviewer_keywords:
- filter element for <add> for <sharedListeners>
- initializeData attribute
- <filter> element for <add> for <sharedListeners>
- filters, trace listeners
- trace listeners, filters
ms.assetid: 7d4e7faa-2e4e-4379-ac76-f6cd7f2f8fac
ms.openlocfilehash: 5d6567ff029dea5ed98054dbc524bb7ed405324c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99802376"
---
# <a name="filter-element-for-add-for-sharedlisteners"></a><span data-ttu-id="46fad-103">\<filter> Элемент для \<add> для \<sharedListeners></span><span class="sxs-lookup"><span data-stu-id="46fad-103">\<filter> Element for \<add> for \<sharedListeners></span></span>

<span data-ttu-id="46fad-104">Добавляет фильтр к прослушивателю в коллекции `sharedListeners`.</span><span class="sxs-lookup"><span data-stu-id="46fad-104">Adds a filter to a listener in the `sharedListeners` collection.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sharedListeners>**](sharedlisteners-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-element-for-sharedlisteners.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filter>**

## <a name="syntax"></a><span data-ttu-id="46fad-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="46fad-105">Syntax</span></span>  
  
```xml  
<filter type="System.Diagnostics.EventTypeFilter"
  initializeData="Warning" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="46fad-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="46fad-106">Attributes and Elements</span></span>  

 <span data-ttu-id="46fad-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="46fad-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="46fad-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="46fad-108">Attributes</span></span>  
  
|<span data-ttu-id="46fad-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="46fad-109">Attribute</span></span>|<span data-ttu-id="46fad-110">Описание</span><span class="sxs-lookup"><span data-stu-id="46fad-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="46fad-111">**type**</span><span class="sxs-lookup"><span data-stu-id="46fad-111">**type**</span></span>|<span data-ttu-id="46fad-112">Обязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="46fad-112">Required attribute.</span></span><br /><br /> <span data-ttu-id="46fad-113">Указывает тип фильтра.</span><span class="sxs-lookup"><span data-stu-id="46fad-113">Specifies the type of the filter.</span></span> <span data-ttu-id="46fad-114">Можно использовать только полное имя типа (в формате <xref:System.Type.FullName%2A?displayProperty=nameWithType> Свойства) или можно использовать полное имя типа, включая сведения о сборке (в формате <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType> Свойства).</span><span class="sxs-lookup"><span data-stu-id="46fad-114">You can use only the full name of the type (in the format of the <xref:System.Type.FullName%2A?displayProperty=nameWithType> property), or you can use the fully qualified type name including the assembly information (in the format of the <xref:System.Type.AssemblyQualifiedName%2A?displayProperty=nameWithType> property).</span></span> <span data-ttu-id="46fad-115">Сведения о создании полного имени типа см. в разделе [Указание полных имен типов](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="46fad-115">For information on creating a fully qualified type name, see [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|<span data-ttu-id="46fad-116">**initializeData**</span><span class="sxs-lookup"><span data-stu-id="46fad-116">**initializeData**</span></span>|<span data-ttu-id="46fad-117">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="46fad-117">Optional attribute.</span></span><br /><br /> <span data-ttu-id="46fad-118">Строка, передаваемая конструктору для указанного класса.</span><span class="sxs-lookup"><span data-stu-id="46fad-118">The string passed to the constructor for the specified class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="46fad-119">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="46fad-119">Child Elements</span></span>  

 <span data-ttu-id="46fad-120">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="46fad-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="46fad-121">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="46fad-121">Parent Elements</span></span>  
  
|<span data-ttu-id="46fad-122">Элемент</span><span class="sxs-lookup"><span data-stu-id="46fad-122">Element</span></span>|<span data-ttu-id="46fad-123">Описание</span><span class="sxs-lookup"><span data-stu-id="46fad-123">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="46fad-124">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="46fad-124">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="46fad-125">Задает прослушиватели трассировки, собирающие, хранящие и маршрутизирующие сообщения, а также уровень, на котором установлен ключ трассировки.</span><span class="sxs-lookup"><span data-stu-id="46fad-125">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sharedListeners`|<span data-ttu-id="46fad-126">Коллекция прослушивателей, на которые может ссылаться любой источник или элемент трассировки.</span><span class="sxs-lookup"><span data-stu-id="46fad-126">A collection of listeners that any source or trace element can reference.</span></span>|  
|`add`|<span data-ttu-id="46fad-127">Добавляет прослушиватель в коллекцию **шаредлистенерс** .</span><span class="sxs-lookup"><span data-stu-id="46fad-127">Adds a listener to the **sharedListeners** collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="46fad-128">Remarks</span><span class="sxs-lookup"><span data-stu-id="46fad-128">Remarks</span></span>  

 <span data-ttu-id="46fad-129">Если прослушиватель определен в элементе элемента `<add>` `<sharedListeners>` , то фильтр для этого прослушивателя должен быть определен в `<filter>` элементе, который является дочерним по отношению к `<add>` элементу.</span><span class="sxs-lookup"><span data-stu-id="46fad-129">If a listener is defined in an `<add>` element of the `<sharedListeners>` element, the filter for that listener should be defined in a `<filter>` element that is a child of the `<add>` element.</span></span>  
  
 <span data-ttu-id="46fad-130">Этот элемент можно использовать в файле конфигурации компьютера (Machine.config) и файле конфигурации приложения.</span><span class="sxs-lookup"><span data-stu-id="46fad-130">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="46fad-131">Пример</span><span class="sxs-lookup"><span data-stu-id="46fad-131">Example</span></span>  

 <span data-ttu-id="46fad-132">В следующем примере показано, как использовать `<filter>` элемент для добавления фильтра в прослушиватель трассировки `console` в `sharedListeners` коллекции.</span><span class="sxs-lookup"><span data-stu-id="46fad-132">The following example shows how to use the `<filter>` element to add a filter to the trace listener `console` in the `sharedListeners` collection.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="myTraceSource" >  
        <listeners>  
          <add name="console" />  
          <remove name="Default" />  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add name="console"
        type="System.Diagnostics.ConsoleTraceListener" >  
        <filter type="System.Diagnostics.EventTypeFilter"
          initializeData="Error" />  
      </add>  
    </sharedListeners>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="46fad-133">См. также</span><span class="sxs-lookup"><span data-stu-id="46fad-133">See also</span></span>

- <xref:System.Diagnostics.TraceFilter>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceSource>
- [<span data-ttu-id="46fad-134">Схема параметров трассировки и отладки</span><span class="sxs-lookup"><span data-stu-id="46fad-134">Trace and Debug Settings Schema</span></span>](index.md)
