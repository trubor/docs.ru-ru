---
description: 'Дополнительные сведения о: <trace> element'
title: Элемент <trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace
- http://schemas.microsoft.com/.NetConfiguration/v2.0#trace
helpviewer_keywords:
- <trace> element
- listeners
- trace element
- trace listener, <trace> element
ms.assetid: 7931c942-63c1-47c3-a045-9d9de3cacdbf
ms.openlocfilehash: 470bc300911656a9c9951e52e3883ba5c8b01c59
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99750329"
---
# <a name="trace-element"></a><span data-ttu-id="a4cbb-103">Элемент \<trace></span><span class="sxs-lookup"><span data-stu-id="a4cbb-103">\<trace> Element</span></span>

<span data-ttu-id="a4cbb-104">Содержит прослушиватели, которые собирают, хранят и маршрутизируют сообщения трассировки.</span><span class="sxs-lookup"><span data-stu-id="a4cbb-104">Contains listeners that collect, store, and route tracing messages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<trace>**  
  
## <a name="syntax"></a><span data-ttu-id="a4cbb-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a4cbb-105">Syntax</span></span>  
  
```xml  
<trace autoflush="true|false"
       indentsize="indent value"  
       useGlobalLock="true| false"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a4cbb-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="a4cbb-106">Attributes and Elements</span></span>  

 <span data-ttu-id="a4cbb-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="a4cbb-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a4cbb-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="a4cbb-108">Attributes</span></span>  
  
|<span data-ttu-id="a4cbb-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="a4cbb-109">Attribute</span></span>|<span data-ttu-id="a4cbb-110">Описание</span><span class="sxs-lookup"><span data-stu-id="a4cbb-110">Description</span></span>|  
|---------------|-----------------|  
|`autoflush`|<span data-ttu-id="a4cbb-111">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="a4cbb-111">Optional attribute.</span></span><br /><br /> <span data-ttu-id="a4cbb-112">Указывает, будут ли прослушиватели трассировки автоматически сбрасывать выходной буфер после каждой операции записи.</span><span class="sxs-lookup"><span data-stu-id="a4cbb-112">Specifies whether the trace listeners automatically flush the output buffer after every write operation.</span></span>|  
|`indentsize`|<span data-ttu-id="a4cbb-113">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="a4cbb-113">Optional attribute.</span></span><br /><br /> <span data-ttu-id="a4cbb-114">Задает количество пробелов для отступа.</span><span class="sxs-lookup"><span data-stu-id="a4cbb-114">Specifies the number of spaces to indent.</span></span>|  
|`useGlobalLock`|<span data-ttu-id="a4cbb-115">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="a4cbb-115">Optional attribute.</span></span><br /><br /> <span data-ttu-id="a4cbb-116">Указывает, следует ли использовать глобальную блокировку.</span><span class="sxs-lookup"><span data-stu-id="a4cbb-116">Indicates whether the global lock should be used.</span></span>|  
  
## <a name="autoflush-attribute"></a><span data-ttu-id="a4cbb-117">Атрибут автозаписи</span><span class="sxs-lookup"><span data-stu-id="a4cbb-117">autoflush Attribute</span></span>  
  
|<span data-ttu-id="a4cbb-118">Значение</span><span class="sxs-lookup"><span data-stu-id="a4cbb-118">Value</span></span>|<span data-ttu-id="a4cbb-119">Описание</span><span class="sxs-lookup"><span data-stu-id="a4cbb-119">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="a4cbb-120">Не очищает выходной буфер автоматически.</span><span class="sxs-lookup"><span data-stu-id="a4cbb-120">Does not automatically flush the output buffer.</span></span> <span data-ttu-id="a4cbb-121">Это значение по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="a4cbb-121">This is the default.</span></span>|  
|`true`|<span data-ttu-id="a4cbb-122">Автоматически очищает выходной буфер.</span><span class="sxs-lookup"><span data-stu-id="a4cbb-122">Automatically flushes the output buffer.</span></span>|  
  
## <a name="usegloballock-attribute"></a><span data-ttu-id="a4cbb-123">Атрибут useGlobalLock</span><span class="sxs-lookup"><span data-stu-id="a4cbb-123">useGlobalLock Attribute</span></span>  
  
|<span data-ttu-id="a4cbb-124">Значение</span><span class="sxs-lookup"><span data-stu-id="a4cbb-124">Value</span></span>|<span data-ttu-id="a4cbb-125">Описание</span><span class="sxs-lookup"><span data-stu-id="a4cbb-125">Description</span></span>|  
|-----------|-----------------|  
|`false`|<span data-ttu-id="a4cbb-126">Не использует глобальную блокировку, если прослушиватель является потокобезопасным; в противном случае использует глобальную блокировку.</span><span class="sxs-lookup"><span data-stu-id="a4cbb-126">Does not use the global lock if the listener is thread safe; otherwise, uses the global lock.</span></span>|  
|`true`|<span data-ttu-id="a4cbb-127">Использует глобальную блокировку независимо от того, является ли прослушиватель потокобезопасным.</span><span class="sxs-lookup"><span data-stu-id="a4cbb-127">Uses the global lock regardless of whether the listener is thread safe.</span></span> <span data-ttu-id="a4cbb-128">Это значение по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="a4cbb-128">This is the default.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a4cbb-129">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="a4cbb-129">Child Elements</span></span>  
  
|<span data-ttu-id="a4cbb-130">Элемент</span><span class="sxs-lookup"><span data-stu-id="a4cbb-130">Element</span></span>|<span data-ttu-id="a4cbb-131">Описание</span><span class="sxs-lookup"><span data-stu-id="a4cbb-131">Description</span></span>|  
|-------------|-----------------|  
|[\<listeners>](listeners-element-for-trace.md)|<span data-ttu-id="a4cbb-132">Указывает прослушиватель, который собирает, хранит и маршрутизирует сообщения.</span><span class="sxs-lookup"><span data-stu-id="a4cbb-132">Specifies a listener that collects, stores, and routes messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="a4cbb-133">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="a4cbb-133">Parent Elements</span></span>  
  
|<span data-ttu-id="a4cbb-134">Элемент</span><span class="sxs-lookup"><span data-stu-id="a4cbb-134">Element</span></span>|<span data-ttu-id="a4cbb-135">Описание</span><span class="sxs-lookup"><span data-stu-id="a4cbb-135">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="a4cbb-136">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a4cbb-136">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="a4cbb-137">Задает прослушиватели трассировки, собирающие, хранящие и маршрутизирующие сообщения, а также уровень, на котором установлен ключ трассировки.</span><span class="sxs-lookup"><span data-stu-id="a4cbb-137">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="a4cbb-138">Пример</span><span class="sxs-lookup"><span data-stu-id="a4cbb-138">Example</span></span>  

 <span data-ttu-id="a4cbb-139">В следующем примере показано, как использовать `<trace>` элемент для добавления прослушивателя `MyListener` в `Listeners` коллекцию.</span><span class="sxs-lookup"><span data-stu-id="a4cbb-139">The following example shows how to use the `<trace>` element to add the listener `MyListener` to the `Listeners` collection.</span></span> <span data-ttu-id="a4cbb-140">`MyListener` создает файл с именем `MyListener.log` и записывает выходные данные в файл.</span><span class="sxs-lookup"><span data-stu-id="a4cbb-140">`MyListener` creates a file that is named `MyListener.log` and writes the output to the file.</span></span> <span data-ttu-id="a4cbb-141">`useGlobalLock`Атрибут имеет значение `false` , что приводит к тому, что глобальная блокировка не будет использоваться, если прослушиватель трассировки является потокобезопасным.</span><span class="sxs-lookup"><span data-stu-id="a4cbb-141">The `useGlobalLock` attribute is set to `false`, which causes the global lock not to be used if the trace listener is thread safe.</span></span> <span data-ttu-id="a4cbb-142">`autoflush`Атрибут имеет значение `true` , что приводит к тому, что прослушиватель трассировки выполняет запись в файл независимо от того, <xref:System.Diagnostics.Trace.Flush%2A?displayProperty=nameWithType> вызывается ли метод.</span><span class="sxs-lookup"><span data-stu-id="a4cbb-142">The `autoflush` attribute is set to `true`, which causes the trace listener to write to the file regardless of whether the <xref:System.Diagnostics.Trace.Flush%2A?displayProperty=nameWithType> method is called.</span></span> <span data-ttu-id="a4cbb-143">Атрибуту присваивается значение `indentsize` 0 (ноль), что приводит к тому, что при вызове метода прослушиватель устанавливает отступы в ноль пробелов <xref:System.Diagnostics.Trace.Indent%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="a4cbb-143">The `indentsize` attribute is set to 0 (zero), which causes the listener to indent zero spaces when the <xref:System.Diagnostics.Trace.Indent%2A?displayProperty=nameWithType> method is called.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <trace useGlobalLock="false" autoflush="true" indentsize="0">  
         <listeners>  
            <add name="myListener" type="System.Diagnostics.TextWriterTraceListener, system version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="c:\myListener.log" />  
         </listeners>  
      </trace>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a4cbb-144">См. также</span><span class="sxs-lookup"><span data-stu-id="a4cbb-144">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- [<span data-ttu-id="a4cbb-145">Схема параметров трассировки и отладки</span><span class="sxs-lookup"><span data-stu-id="a4cbb-145">Trace and Debug Settings Schema</span></span>](index.md)
