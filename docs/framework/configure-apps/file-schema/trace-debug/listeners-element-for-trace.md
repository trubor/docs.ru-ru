---
description: 'Дополнительные сведения о: <listeners> Element для <trace>'
title: Элемент <listeners> для <trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners
helpviewer_keywords:
- <listeners> element
- listeners element
ms.assetid: 1394c2c3-6304-46db-87c1-8e8b16f5ad5b
ms.openlocfilehash: 25f6d4b49eeb57b25b4afbbdfdba484d6d7eea3e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639631"
---
# <a name="listeners-element-for-trace"></a><span data-ttu-id="71378-103">Элемент \<listeners> для \<trace></span><span class="sxs-lookup"><span data-stu-id="71378-103">\<listeners> Element for \<trace></span></span>

<span data-ttu-id="71378-104">Указывает прослушиватель, который собирает, хранит и маршрутизирует сообщения.</span><span class="sxs-lookup"><span data-stu-id="71378-104">Specifies a listener that collects, stores, and routes messages.</span></span> <span data-ttu-id="71378-105">Прослушиватели направляют выходные данные трассировки в соответствующий целевой объект.</span><span class="sxs-lookup"><span data-stu-id="71378-105">Listeners direct the tracing output to an appropriate target.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<listeners>**

## <a name="syntax"></a><span data-ttu-id="71378-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="71378-106">Syntax</span></span>  
  
```xml  
<listeners>
  <add>...</add>  
  <clear/>  
  <remove ... />  
</listeners>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="71378-107">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="71378-107">Attributes and Elements</span></span>  

 <span data-ttu-id="71378-108">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="71378-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="71378-109">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="71378-109">Attributes</span></span>  

 <span data-ttu-id="71378-110">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="71378-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="71378-111">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="71378-111">Child Elements</span></span>  
  
|<span data-ttu-id="71378-112">Элемент</span><span class="sxs-lookup"><span data-stu-id="71378-112">Element</span></span>|<span data-ttu-id="71378-113">Описание</span><span class="sxs-lookup"><span data-stu-id="71378-113">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-element-for-listeners-for-trace.md)|<span data-ttu-id="71378-114">Добавляет прослушиватель в коллекцию `Listeners`.</span><span class="sxs-lookup"><span data-stu-id="71378-114">Adds a listener to the `Listeners` collection.</span></span>|  
|[\<clear>](clear-element-for-listeners-for-trace.md)|<span data-ttu-id="71378-115">Очищает коллекцию `Listeners` для трассировки.</span><span class="sxs-lookup"><span data-stu-id="71378-115">Clears the `Listeners` collection for trace.</span></span>|  
|[\<remove>](remove-element-for-listeners-for-trace.md)|<span data-ttu-id="71378-116">Удаляет прослушиватель из `Listeners` коллекции.</span><span class="sxs-lookup"><span data-stu-id="71378-116">Removes a listener from the `Listeners` collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="71378-117">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="71378-117">Parent Elements</span></span>  
  
|<span data-ttu-id="71378-118">Элемент</span><span class="sxs-lookup"><span data-stu-id="71378-118">Element</span></span>|<span data-ttu-id="71378-119">Описание</span><span class="sxs-lookup"><span data-stu-id="71378-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="71378-120">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="71378-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="71378-121">Задает корневой элемент для раздела конфигурации ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="71378-121">Specifies the root element for the ASP.NET configuration section.</span></span>|  
|`trace`|<span data-ttu-id="71378-122">Содержит прослушиватели, которые собирают, хранят и маршрутизируют сообщения трассировки.</span><span class="sxs-lookup"><span data-stu-id="71378-122">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="71378-123">Remarks</span><span class="sxs-lookup"><span data-stu-id="71378-123">Remarks</span></span>  

 <span data-ttu-id="71378-124"><xref:System.Diagnostics.Debug>Классы и <xref:System.Diagnostics.Trace> совместно используют одну и ту же коллекцию **Listeners** .</span><span class="sxs-lookup"><span data-stu-id="71378-124">The <xref:System.Diagnostics.Debug> and <xref:System.Diagnostics.Trace> classes share the same **Listeners** collection.</span></span> <span data-ttu-id="71378-125">При добавлении объекта прослушивателя в коллекцию в одном из этих классов другой класс использует тот же прослушиватель.</span><span class="sxs-lookup"><span data-stu-id="71378-125">If you add a listener object to the collection in one of these classes, the other class uses the same listener.</span></span> <span data-ttu-id="71378-126">Классы прослушивателей, поставляемые с платформа .NET Framework, являются производными от <xref:System.Diagnostics.TraceListener> класса.</span><span class="sxs-lookup"><span data-stu-id="71378-126">The listener classes shipped with the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="71378-127">Файл конфигурации</span><span class="sxs-lookup"><span data-stu-id="71378-127">Configuration File</span></span>  

 <span data-ttu-id="71378-128">Этот элемент можно использовать в файле конфигурации компьютера (Machine.config) и файле конфигурации приложения.</span><span class="sxs-lookup"><span data-stu-id="71378-128">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="71378-129">Пример</span><span class="sxs-lookup"><span data-stu-id="71378-129">Example</span></span>  

 <span data-ttu-id="71378-130">В следующем примере показано, как использовать **\<listeners>** элемент для добавления прослушивателей `MyListener` и `MyEventListener` в коллекцию **Listeners** .</span><span class="sxs-lookup"><span data-stu-id="71378-130">The following example shows how to use the **\<listeners>** element to add the listeners `MyListener` and `MyEventListener` to the **Listeners** collection.</span></span> <span data-ttu-id="71378-131">`MyListener` создает файл с именем `MyListener.log` и записывает выходные данные в файл.</span><span class="sxs-lookup"><span data-stu-id="71378-131">`MyListener` creates a file called `MyListener.log` and writes the output to the file.</span></span> <span data-ttu-id="71378-132">`MyEventListener` создает запись в журнале событий.</span><span class="sxs-lookup"><span data-stu-id="71378-132">`MyEventListener` creates an entry in the event log.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <trace autoflush="true" indentsize="0">  
      <listeners>  
        <add name="myListener"
          type="System.Diagnostics.TextWriterTraceListener,
            system, version=1.0.3300.0, Culture=neutral,
            PublicKeyToken=b77a5c561934e089"
          initializeData="c:\myListener.log" />  
        <add name="MyEventListener"  
          type="System.Diagnostics.EventLogTraceListener,
            system, version=1.0.3300.0, Culture=neutral,
            PublicKeyToken=b77a5c561934e089"  
          initializeData="MyConfigEventLog"/>  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="71378-133">См. также</span><span class="sxs-lookup"><span data-stu-id="71378-133">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="71378-134">Схема параметров трассировки и отладки</span><span class="sxs-lookup"><span data-stu-id="71378-134">Trace and Debug Settings Schema</span></span>](index.md)
