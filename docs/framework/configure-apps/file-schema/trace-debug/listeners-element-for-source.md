---
description: 'Дополнительные сведения о: <listeners> Element для <source>'
title: Элемент <listeners> для <source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners
helpviewer_keywords:
- listeners element for <source>
- <listeners> element for <source>
ms.assetid: a2991f43-b4d3-4614-a8e7-da392de9697f
ms.openlocfilehash: 6b857d4b114366d268eec1859afc7f33cc5b04a2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639646"
---
# <a name="listeners-element-for-source"></a><span data-ttu-id="b9c86-103">Элемент \<listeners> для \<source></span><span class="sxs-lookup"><span data-stu-id="b9c86-103">\<listeners> Element for \<source></span></span>

<span data-ttu-id="b9c86-104">Добавляет или удаляет прослушиватели в <xref:System.Diagnostics.TraceSource.Listeners%2A> коллекции для <xref:System.Diagnostics.TraceSource> .</span><span class="sxs-lookup"><span data-stu-id="b9c86-104">Adds or removes listeners in the <xref:System.Diagnostics.TraceSource.Listeners%2A> collection for a <xref:System.Diagnostics.TraceSource>.</span></span> <span data-ttu-id="b9c86-105">Прослушиватель направляет выходные данные трассировки в соответствующий целевой объект, например журнал, окно или текстовый файл.</span><span class="sxs-lookup"><span data-stu-id="b9c86-105">A listener directs the tracing output to an appropriate target, such as a log, window, or text file.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<listeners>**  
  
## <a name="syntax"></a><span data-ttu-id="b9c86-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b9c86-106">Syntax</span></span>  
  
```xml  
<listeners>
  <add>...</add>  
  <remove ... />  
  <clear/>  
</listeners>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b9c86-107">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="b9c86-107">Attributes and Elements</span></span>  

 <span data-ttu-id="b9c86-108">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="b9c86-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b9c86-109">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="b9c86-109">Attributes</span></span>  

 <span data-ttu-id="b9c86-110">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="b9c86-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b9c86-111">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="b9c86-111">Child Elements</span></span>  
  
|<span data-ttu-id="b9c86-112">Элемент</span><span class="sxs-lookup"><span data-stu-id="b9c86-112">Element</span></span>|<span data-ttu-id="b9c86-113">Описание</span><span class="sxs-lookup"><span data-stu-id="b9c86-113">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-element-for-listeners-for-source.md)|<span data-ttu-id="b9c86-114">Добавляет прослушиватель в коллекцию `Listeners`.</span><span class="sxs-lookup"><span data-stu-id="b9c86-114">Adds a listener to the `Listeners` collection.</span></span>|  
|[\<remove>](remove-element-for-listeners-for-source.md)|<span data-ttu-id="b9c86-115">Удаляет прослушиватель из `Listeners` коллекции.</span><span class="sxs-lookup"><span data-stu-id="b9c86-115">Removes a listener from the `Listeners` collection.</span></span>|  
|[\<clear>](clear-element-for-listeners-for-source.md)|<span data-ttu-id="b9c86-116">Очищает коллекцию `Listeners` для источника трассировки.</span><span class="sxs-lookup"><span data-stu-id="b9c86-116">Clears the `Listeners` collection for a trace source.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b9c86-117">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="b9c86-117">Parent Elements</span></span>  
  
|<span data-ttu-id="b9c86-118">Элемент</span><span class="sxs-lookup"><span data-stu-id="b9c86-118">Element</span></span>|<span data-ttu-id="b9c86-119">Описание</span><span class="sxs-lookup"><span data-stu-id="b9c86-119">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="b9c86-120">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b9c86-120">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="b9c86-121">Задает прослушиватели трассировки, собирающие, хранящие и маршрутизирующие сообщения, а также уровень, на котором установлен ключ трассировки.</span><span class="sxs-lookup"><span data-stu-id="b9c86-121">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="b9c86-122">Содержит источники трассировки, которые инициируют сообщения трассировки.</span><span class="sxs-lookup"><span data-stu-id="b9c86-122">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="b9c86-123">Содержит источник трассировки, который инициирует сообщения трассировки.</span><span class="sxs-lookup"><span data-stu-id="b9c86-123">Specifies a trace source that initiates tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b9c86-124">Remarks</span><span class="sxs-lookup"><span data-stu-id="b9c86-124">Remarks</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="b9c86-125">Файл конфигурации</span><span class="sxs-lookup"><span data-stu-id="b9c86-125">Configuration File</span></span>  

 <span data-ttu-id="b9c86-126">Этот элемент можно использовать в файле конфигурации компьютера (Machine.config) и файле конфигурации приложения.</span><span class="sxs-lookup"><span data-stu-id="b9c86-126">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b9c86-127">Пример</span><span class="sxs-lookup"><span data-stu-id="b9c86-127">Example</span></span>  

 <span data-ttu-id="b9c86-128">В следующем примере показано, как использовать `<listeners>` элемент для добавления прослушивателя трассировки консоли в `mySource` источник и для удаления прослушивателя трассировки по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="b9c86-128">The following example shows how to use the `<listeners>` element to add a console trace listener to the `mySource` source and to remove the default trace listener.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="mySource" switchName="sourceSwitch"
        switchType="System.Diagnostics.SourceSwitch">  
        <listeners>  
          <add name="console"
            type="System.Diagnostics.ConsoleTraceListener">  
            <filter type="System.Diagnostics.EventTypeFilter"
              initializeData="Error"/>  
          </add>  
          <remove name="Default"/>  
        </listeners>  
      </source>  
    </sources>  
    <switches>  
      <add name="sourceSwitch" value="Warning"/>  
    </switches>  
  </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b9c86-129">См. также</span><span class="sxs-lookup"><span data-stu-id="b9c86-129">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="b9c86-130">Схема параметров трассировки и отладки</span><span class="sxs-lookup"><span data-stu-id="b9c86-130">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="b9c86-131">Прослушиватели трассировки</span><span class="sxs-lookup"><span data-stu-id="b9c86-131">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
