---
description: 'Дополнительные сведения о: <sharedListeners> element'
title: Элемент <sharedListeners>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#sharedListeners
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sharedListeners
helpviewer_keywords:
- <sharedListeners> element
- listeners
- shared listeners
- trace listeners, <sharedListeners> element
- sharedListeners element
ms.assetid: de200534-19dd-4156-86cf-c50521802c4c
ms.openlocfilehash: 904648754c99464e1109a04a5a19b52ec1a1cace
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99750563"
---
# <a name="sharedlisteners-element"></a><span data-ttu-id="58acd-103">Элемент \<sharedListeners></span><span class="sxs-lookup"><span data-stu-id="58acd-103">\<sharedListeners> Element</span></span>

<span data-ttu-id="58acd-104">Содержит прослушиватели, на которые может ссылаться любой источник или элемент трассировки.</span><span class="sxs-lookup"><span data-stu-id="58acd-104">Contains listeners that any source or trace element can reference.</span></span>  <span data-ttu-id="58acd-105">По умолчанию эти прослушиватели не получают никаких трассировок, поэтому невозможно получить эти прослушиватели во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="58acd-105">These listeners do not receive any traces by default, and it is not possible to retrieve these listeners at run time.</span></span> <span data-ttu-id="58acd-106">Прослушиватели, идентифицированные как общие прослушиватели, можно добавлять в источники или трассировки по имени.</span><span class="sxs-lookup"><span data-stu-id="58acd-106">Listeners identified as shared listeners can be added to sources or traces by name.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<sharedListeners>**  
  
## <a name="syntax"></a><span data-ttu-id="58acd-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="58acd-107">Syntax</span></span>  
  
```xml  
<sharedListeners>
  <add>...</add>  
</sharedListeners>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="58acd-108">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="58acd-108">Attributes and Elements</span></span>  

 <span data-ttu-id="58acd-109">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="58acd-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="58acd-110">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="58acd-110">Attributes</span></span>  

 <span data-ttu-id="58acd-111">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="58acd-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="58acd-112">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="58acd-112">Child Elements</span></span>  
  
|<span data-ttu-id="58acd-113">Элемент</span><span class="sxs-lookup"><span data-stu-id="58acd-113">Element</span></span>|<span data-ttu-id="58acd-114">Описание</span><span class="sxs-lookup"><span data-stu-id="58acd-114">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-element-for-listeners-for-trace.md)|<span data-ttu-id="58acd-115">Добавляет прослушиватель в коллекцию `sharedListeners`.</span><span class="sxs-lookup"><span data-stu-id="58acd-115">Adds a listener to the `sharedListeners` collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="58acd-116">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="58acd-116">Parent Elements</span></span>  
  
|<span data-ttu-id="58acd-117">Элемент</span><span class="sxs-lookup"><span data-stu-id="58acd-117">Element</span></span>|<span data-ttu-id="58acd-118">Описание</span><span class="sxs-lookup"><span data-stu-id="58acd-118">Description</span></span>|  
|-------------|-----------------|  
|`Configuration`|<span data-ttu-id="58acd-119">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="58acd-119">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="58acd-120">Задает корневой элемент для раздела конфигурации ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="58acd-120">Specifies the root element for the ASP.NET configuration section.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="58acd-121">Remarks</span><span class="sxs-lookup"><span data-stu-id="58acd-121">Remarks</span></span>  

 <span data-ttu-id="58acd-122">Добавление прослушивателя в коллекцию общих прослушивателей не сделает его активным прослушивателем.</span><span class="sxs-lookup"><span data-stu-id="58acd-122">Adding a listener to the shared listeners collection does not make it an active listener.</span></span> <span data-ttu-id="58acd-123">Он по-прежнему должен быть добавлен в источник трассировки или в трассировку путем добавления в `Listeners` коллекцию для этого элемента Trace.</span><span class="sxs-lookup"><span data-stu-id="58acd-123">It must still be added to a trace source or a trace by adding it to the `Listeners` collection for that trace element.</span></span> <span data-ttu-id="58acd-124">Классы прослушивателей в платформа .NET Framework являются производными от <xref:System.Diagnostics.TraceListener> класса.</span><span class="sxs-lookup"><span data-stu-id="58acd-124">The listener classes in the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
 <span data-ttu-id="58acd-125">Этот элемент можно использовать в файле конфигурации компьютера (Machine.config) и файле конфигурации приложения.</span><span class="sxs-lookup"><span data-stu-id="58acd-125">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="58acd-126">Пример</span><span class="sxs-lookup"><span data-stu-id="58acd-126">Example</span></span>  

 <span data-ttu-id="58acd-127">В следующем примере показано, как использовать `<sharedListeners>` элемент для добавления прослушивателя `console` в `Listeners` коллекцию для <xref:System.Diagnostics.TraceSource> <xref:System.Diagnostics.Trace> классов и.</span><span class="sxs-lookup"><span data-stu-id="58acd-127">The following example shows how to use the `<sharedListeners>` element to add the listener `console` to the `Listeners` collection for both the <xref:System.Diagnostics.TraceSource> and <xref:System.Diagnostics.Trace> classes.</span></span> <span data-ttu-id="58acd-128">Прослушиватель трассировки консоли записывает данные трассировки в консоль с помощью вызовов либо к, либо к <xref:System.Diagnostics.TraceSource> <xref:System.Diagnostics.Trace> .</span><span class="sxs-lookup"><span data-stu-id="58acd-128">The console trace listener writes trace information to the console through calls to either <xref:System.Diagnostics.TraceSource> or <xref:System.Diagnostics.Trace>.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sharedListeners>  
      <add name="console" type="System.Diagnostics.ConsoleTraceListener" >  
        <filter type="System.Diagnostics.EventTypeFilter"  
          initializeData="Warning" />  
      </add>  
    </sharedListeners>  
    <sources>  
      <source name="mySource" switchName="sourceSwitch"  >  
        <listeners>  
          <add name="console" />  
        </listeners>  
      </source>  
    </sources>  
    <switches>  
      <add name="sourceSwitch" value="Verbose"/>  
    </switches>  
    <trace>  
      <listeners>  
        <add name="console" />  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="58acd-129">См. также</span><span class="sxs-lookup"><span data-stu-id="58acd-129">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="58acd-130">Схема параметров трассировки и отладки</span><span class="sxs-lookup"><span data-stu-id="58acd-130">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="58acd-131">Прослушиватели трассировки</span><span class="sxs-lookup"><span data-stu-id="58acd-131">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
