---
description: 'Дополнительные сведения о: <filter> Element для <add> для <listeners><trace>'
title: <filter>Элемент для <add> для <listeners><trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add/filter
helpviewer_keywords:
- initializeData attribute
- filter element for <add> for <listeners> for <trace>
- <filter> element for <add> for <listeners> for <trace>
ms.assetid: eb9c18f5-dfa8-47c5-b91b-e4b93e76e1cc
ms.openlocfilehash: a47903a696fcbf2cd7f4eecda526f93955a31f11
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754489"
---
# <a name="filter-element-for-add-for-listeners-for-trace"></a><span data-ttu-id="b9858-103">\<filter>Элемент для \<add> для \<listeners>\<trace></span><span class="sxs-lookup"><span data-stu-id="b9858-103">\<filter> Element for \<add> for \<listeners> for \<trace></span></span>

<span data-ttu-id="b9858-104">Добавляет фильтр в прослушиватель в `Listeners` коллекции для трассировки.</span><span class="sxs-lookup"><span data-stu-id="b9858-104">Adds a filter to a listener in the `Listeners` collection for a trace.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-trace.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add-element-for-listeners-for-trace.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filter>**

## <a name="syntax"></a><span data-ttu-id="b9858-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b9858-105">Syntax</span></span>  
  
```xml  
<filter
  type="traceFilterClassName"
  initializeData="data" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b9858-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="b9858-106">Attributes and Elements</span></span>  

 <span data-ttu-id="b9858-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="b9858-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b9858-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="b9858-108">Attributes</span></span>  
  
|<span data-ttu-id="b9858-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="b9858-109">Attribute</span></span>|<span data-ttu-id="b9858-110">Описание</span><span class="sxs-lookup"><span data-stu-id="b9858-110">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="b9858-111">Обязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="b9858-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="b9858-112">Указывает тип фильтра, который должен наследоваться от <xref:System.Diagnostics.TraceFilter> класса.</span><span class="sxs-lookup"><span data-stu-id="b9858-112">Specifies the type of the filter, which should inherit from the <xref:System.Diagnostics.TraceFilter> class.</span></span> <span data-ttu-id="b9858-113">Можно использовать имя, уточненное пространством имен типа, которое соответствует <xref:System.Type.FullName%2A> свойству типа, или можно использовать полное имя типа, включая сведения о сборке, соответствующие <xref:System.Type.AssemblyQualifiedName%2A> свойству.</span><span class="sxs-lookup"><span data-stu-id="b9858-113">You can use the namespace-qualified name of the type, which corresponds to the type's <xref:System.Type.FullName%2A> property, or you can use the fully qualified type name including the assembly information, which corresponds to the <xref:System.Type.AssemblyQualifiedName%2A> property.</span></span> <span data-ttu-id="b9858-114">Дополнительные сведения о полных именах типов см. в разделе Указание полных [имен типов](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="b9858-114">For information about fully qualified type names, see [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="b9858-115">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="b9858-115">Optional attribute.</span></span><br /><br /> <span data-ttu-id="b9858-116">Строка, передаваемая конструктору для указанного класса фильтра.</span><span class="sxs-lookup"><span data-stu-id="b9858-116">The string passed to the constructor for the specified filter class.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b9858-117">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="b9858-117">Child Elements</span></span>  

 <span data-ttu-id="b9858-118">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="b9858-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b9858-119">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="b9858-119">Parent Elements</span></span>  
  
|<span data-ttu-id="b9858-120">Элемент</span><span class="sxs-lookup"><span data-stu-id="b9858-120">Element</span></span>|<span data-ttu-id="b9858-121">Описание</span><span class="sxs-lookup"><span data-stu-id="b9858-121">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="b9858-122">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b9858-122">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="b9858-123">Задает прослушиватели трассировки, собирающие, хранящие и маршрутизирующие сообщения, а также уровень, на котором установлен ключ трассировки.</span><span class="sxs-lookup"><span data-stu-id="b9858-123">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="b9858-124">Содержит прослушиватели, которые собирают, хранят и маршрутизируют сообщения трассировки.</span><span class="sxs-lookup"><span data-stu-id="b9858-124">Contains listeners that collect, store, and route tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="b9858-125">Содержит прослушиватели, собирающие, сохраняющие и направляющие сообщения.</span><span class="sxs-lookup"><span data-stu-id="b9858-125">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="b9858-126">Прослушиватели направляют выходные данные трассировки в соответствующий целевой объект.</span><span class="sxs-lookup"><span data-stu-id="b9858-126">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`add`|<span data-ttu-id="b9858-127">Добавляет прослушиватель в коллекцию `Listeners`.</span><span class="sxs-lookup"><span data-stu-id="b9858-127">Adds a listener to the `Listeners` collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b9858-128">Remarks</span><span class="sxs-lookup"><span data-stu-id="b9858-128">Remarks</span></span>  

 <span data-ttu-id="b9858-129">`<filter>`Элемент должен содержаться в `<add>` элементе для прослушивателя трассировки, который указывает тип прослушивателя, а не только имя прослушивателя, определенного в [\<sharedListeners>](sharedlisteners-element.md) .</span><span class="sxs-lookup"><span data-stu-id="b9858-129">The `<filter>` element must be contained in an `<add>` element for a trace listener that specifies the type of the listener, not just the name of a listener defined in a [\<sharedListeners>](sharedlisteners-element.md).</span></span> <span data-ttu-id="b9858-130">Если прослушиватель определен в [\<sharedListeners>](sharedlisteners-element.md) , то фильтр для этого прослушивателя должен быть определен в этом элементе.</span><span class="sxs-lookup"><span data-stu-id="b9858-130">If the listener is defined in a [\<sharedListeners>](sharedlisteners-element.md), the filter for that listener must be defined in that element.</span></span>  
  
 <span data-ttu-id="b9858-131">Этот элемент можно использовать в файле конфигурации компьютера (Machine.config) и файле конфигурации приложения.</span><span class="sxs-lookup"><span data-stu-id="b9858-131">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b9858-132">Пример</span><span class="sxs-lookup"><span data-stu-id="b9858-132">Example</span></span>  

 <span data-ttu-id="b9858-133">В следующем примере показано, как с помощью `<filter>` элемента добавить фильтр в прослушиватель `console` в `Listeners` коллекции для трассировки, указав уровень события фильтра в качестве `Error` .</span><span class="sxs-lookup"><span data-stu-id="b9858-133">The following example shows how to use the `<filter>` element to add a filter to the listener `console` in the `Listeners` collection for trace, specifying the filter event level as `Error`.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <trace autoflush="false" indentsize="4">  
      <listeners>  
        <add name="console"
          type="System.Diagnostics.ConsoleTraceListener" >  
          <filter type="System.Diagnostics.EventTypeFilter"
            initializeData="Error" />  
        </add>  
        <remove name="Default" />  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b9858-134">См. также</span><span class="sxs-lookup"><span data-stu-id="b9858-134">See also</span></span>

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.TraceListener.Filter%2A?displayProperty=nameWithType>
- <xref:System.Diagnostics.TraceFilter>
- [<span data-ttu-id="b9858-135">Схема параметров трассировки и отладки</span><span class="sxs-lookup"><span data-stu-id="b9858-135">Trace and Debug Settings Schema</span></span>](index.md)
