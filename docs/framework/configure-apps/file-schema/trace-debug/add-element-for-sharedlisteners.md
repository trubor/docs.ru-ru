---
description: 'Дополнительные сведения о: <add> Element для <sharedListeners>'
title: Элемент <add> для <sharedListeners>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sharedListeners/add
helpviewer_keywords:
- initializeData attribute
- <add> element for <sharedListeners>
- add element for <sharedListeners>
ms.assetid: 1595e1bc-2492-421f-8384-7f382eb8eb57
ms.openlocfilehash: df3348fa0cbb357b2ceeb5d9db940a1ae3ae102c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99726082"
---
# <a name="add-element-for-sharedlisteners"></a><span data-ttu-id="4b18f-103">Элемент \<add> для \<sharedListeners></span><span class="sxs-lookup"><span data-stu-id="4b18f-103">\<add> Element for \<sharedListeners></span></span>

<span data-ttu-id="4b18f-104">Добавляет прослушиватель в коллекцию `sharedListeners`.</span><span class="sxs-lookup"><span data-stu-id="4b18f-104">Adds a listener to the `sharedListeners` collection.</span></span> <span data-ttu-id="4b18f-105">`sharedListeners` — Это коллекция прослушивателей, [\<source>](source-element.md) на которые [\<trace>](trace-element.md) могут ссылаться любые или.</span><span class="sxs-lookup"><span data-stu-id="4b18f-105">`sharedListeners` is a collection of listeners that any [\<source>](source-element.md) or [\<trace>](trace-element.md) can reference.</span></span>  <span data-ttu-id="4b18f-106">По умолчанию прослушиватели в `sharedListeners` коллекции не помещаются в `Listeners` коллекцию.</span><span class="sxs-lookup"><span data-stu-id="4b18f-106">By default, listeners in the `sharedListeners` collection are not placed in a `Listeners` collection.</span></span> <span data-ttu-id="4b18f-107">Они должны быть добавлены по имени в [\<source>](source-element.md) или [\<trace>](trace-element.md) .</span><span class="sxs-lookup"><span data-stu-id="4b18f-107">They must be added by name to the [\<source>](source-element.md) or [\<trace>](trace-element.md).</span></span> <span data-ttu-id="4b18f-108">Невозможно получить прослушиватели в `sharedListeners` коллекции в коде во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="4b18f-108">It is not possible to get the listeners in the `sharedListeners` collection in code at run time.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sharedListeners>**](sharedlisteners-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="4b18f-109">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="4b18f-109">Syntax</span></span>  
  
```xml  
<add name="name"
  type="TraceListenerClassName, Version, Culture, PublicKeyToken"  
  initializeData="data"
  traceOutputOptions = "None"
/>  
```
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4b18f-110">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="4b18f-110">Attributes and Elements</span></span>  

 <span data-ttu-id="4b18f-111">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="4b18f-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4b18f-112">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="4b18f-112">Attributes</span></span>  
  
|<span data-ttu-id="4b18f-113">Атрибут</span><span class="sxs-lookup"><span data-stu-id="4b18f-113">Attribute</span></span>|<span data-ttu-id="4b18f-114">Описание</span><span class="sxs-lookup"><span data-stu-id="4b18f-114">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="4b18f-115">Обязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="4b18f-115">Required attribute.</span></span><br /><br /> <span data-ttu-id="4b18f-116">Указывает имя прослушивателя, который используется для добавления общего прослушивателя в `Listeners` коллекцию.</span><span class="sxs-lookup"><span data-stu-id="4b18f-116">Specifies the name of the listener that is used to add the shared listener to a `Listeners` collection.</span></span>|  
|`type`|<span data-ttu-id="4b18f-117">Обязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="4b18f-117">Required attribute.</span></span><br /><br /> <span data-ttu-id="4b18f-118">Указывает тип прослушивателя.</span><span class="sxs-lookup"><span data-stu-id="4b18f-118">Specifies the type of the listener.</span></span> <span data-ttu-id="4b18f-119">Необходимо использовать строку, которая соответствует требованиям, указанным в указании [полных имен типов](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="4b18f-119">You must use a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|`initializeData`|<span data-ttu-id="4b18f-120">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="4b18f-120">Optional attribute.</span></span><br /><br /> <span data-ttu-id="4b18f-121">Строка, передаваемая конструктору для указанного класса.</span><span class="sxs-lookup"><span data-stu-id="4b18f-121">The string passed to the constructor for the specified class.</span></span>|  
|`traceOutputOptions`|<span data-ttu-id="4b18f-122">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="4b18f-122">Optional attribute.</span></span><br/><br/><span data-ttu-id="4b18f-123">Строковое представление одного или нескольких <xref:System.Diagnostics.TraceOptions> элементов перечисления, которое указывает данные, записываемые в выходные данные трассировки.</span><span class="sxs-lookup"><span data-stu-id="4b18f-123">The string representation of one or more <xref:System.Diagnostics.TraceOptions> enumeration members that indicates the data to be written to the trace output.</span></span> <span data-ttu-id="4b18f-124">Несколько элементов разделяются запятыми.</span><span class="sxs-lookup"><span data-stu-id="4b18f-124">Multiple items are separated by commas.</span></span> <span data-ttu-id="4b18f-125">Значение по умолчанию — None.</span><span class="sxs-lookup"><span data-stu-id="4b18f-125">The default value is "None".</span></span>|

### <a name="child-elements"></a><span data-ttu-id="4b18f-126">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="4b18f-126">Child Elements</span></span>  
  
|<span data-ttu-id="4b18f-127">Элемент</span><span class="sxs-lookup"><span data-stu-id="4b18f-127">Element</span></span>|<span data-ttu-id="4b18f-128">Описание</span><span class="sxs-lookup"><span data-stu-id="4b18f-128">Description</span></span>|  
|-------------|-----------------|  
|[\<filter>](filter-element-for-add-for-sharedlisteners.md)|<span data-ttu-id="4b18f-129">Добавляет фильтр к прослушивателю в коллекции `sharedListeners`.</span><span class="sxs-lookup"><span data-stu-id="4b18f-129">Adds a filter to a listener in the `sharedListeners` collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4b18f-130">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="4b18f-130">Parent Elements</span></span>  
  
|<span data-ttu-id="4b18f-131">Элемент</span><span class="sxs-lookup"><span data-stu-id="4b18f-131">Element</span></span>|<span data-ttu-id="4b18f-132">Описание</span><span class="sxs-lookup"><span data-stu-id="4b18f-132">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="4b18f-133">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4b18f-133">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="4b18f-134">Задает прослушиватели трассировки, собирающие, хранящие и маршрутизирующие сообщения, а также уровень, на котором установлен ключ трассировки.</span><span class="sxs-lookup"><span data-stu-id="4b18f-134">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sharedListeners`|<span data-ttu-id="4b18f-135">Коллекция прослушивателей, на которые может ссылаться любой источник или элемент трассировки.</span><span class="sxs-lookup"><span data-stu-id="4b18f-135">A collection of listeners that any source or trace element can reference.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4b18f-136">Remarks</span><span class="sxs-lookup"><span data-stu-id="4b18f-136">Remarks</span></span>  

 <span data-ttu-id="4b18f-137">Классы прослушивателей, поставляемые с платформа .NET Framework, являются производными от <xref:System.Diagnostics.TraceListener> класса.</span><span class="sxs-lookup"><span data-stu-id="4b18f-137">The listener classes shipped with the .NET Framework derive from the <xref:System.Diagnostics.TraceListener> class.</span></span> <span data-ttu-id="4b18f-138">Значение `name` атрибута используется для добавления общего прослушивателя в `Listeners` коллекцию либо для трассировки, либо для источника трассировки.</span><span class="sxs-lookup"><span data-stu-id="4b18f-138">The value for the `name` attribute is used to add the shared listener to a `Listeners` collection for either a trace or a trace source.</span></span> <span data-ttu-id="4b18f-139">Значение `initializeData` атрибута зависит от типа создаваемого прослушивателя.</span><span class="sxs-lookup"><span data-stu-id="4b18f-139">The value for the `initializeData` attribute depends on the type of listener you create.</span></span> <span data-ttu-id="4b18f-140">Не все прослушиватели трассировки нуждаются в указании `initializeData` .</span><span class="sxs-lookup"><span data-stu-id="4b18f-140">Not all trace listeners require that you specify `initializeData`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4b18f-141">При использовании `initializeData` атрибута может появиться предупреждение компилятора "атрибут initializeData не объявлен".</span><span class="sxs-lookup"><span data-stu-id="4b18f-141">When you use the `initializeData` attribute, you may get the compiler warning "The 'initializeData' attribute is not declared."</span></span> <span data-ttu-id="4b18f-142">Это предупреждение возникает из-за того, что параметры конфигурации проверяются по абстрактному базовому классу <xref:System.Diagnostics.TraceListener> , который не распознает `initializeData` атрибут.</span><span class="sxs-lookup"><span data-stu-id="4b18f-142">This warning occurs because the configuration settings are validated against the abstract base class <xref:System.Diagnostics.TraceListener>, which does not recognize the `initializeData` attribute.</span></span> <span data-ttu-id="4b18f-143">Как правило, это предупреждение можно игнорировать для реализаций прослушивателя трассировки, имеющих конструктор, принимающий параметр.</span><span class="sxs-lookup"><span data-stu-id="4b18f-143">Typically, you can ignore this warning for trace listener implementations that have a constructor that takes a parameter.</span></span>  
  
 <span data-ttu-id="4b18f-144">В следующей таблице показаны прослушиватели трассировки, которые включены в состав платформа .NET Framework и описываются значения их `initializeData` атрибутов.</span><span class="sxs-lookup"><span data-stu-id="4b18f-144">The following table shows the trace listeners that are included with the .NET Framework and describes the value of their `initializeData` attributes.</span></span>  
  
|<span data-ttu-id="4b18f-145">Класс прослушивателя трассировки</span><span class="sxs-lookup"><span data-stu-id="4b18f-145">Trace listener class</span></span>|<span data-ttu-id="4b18f-146">значение атрибута initializeData</span><span class="sxs-lookup"><span data-stu-id="4b18f-146">initializeData attribute value</span></span>|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener>|<span data-ttu-id="4b18f-147">`useErrorStream`Значение для <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> конструктора.</span><span class="sxs-lookup"><span data-stu-id="4b18f-147">The `useErrorStream` value for the <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> constructor.</span></span>  <span data-ttu-id="4b18f-148">Задайте для `initializeData` атрибута значение " `true` ", чтобы записывать выходные данные трассировки и отладки в стандартный поток ошибок; задайте для него значение " `false` ", чтобы выполнить запись в стандартный выходной поток.</span><span class="sxs-lookup"><span data-stu-id="4b18f-148">Set the `initializeData` attribute to "`true`" to write trace and debug output to the standard error stream; set it to "`false`" to write to the standard output stream.</span></span>|  
|<xref:System.Diagnostics.DelimitedListTraceListener>|<span data-ttu-id="4b18f-149">Имя файла, в который осуществляет запись объект <xref:System.Diagnostics.DelimitedListTraceListener>.</span><span class="sxs-lookup"><span data-stu-id="4b18f-149">The name of the file the <xref:System.Diagnostics.DelimitedListTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|<span data-ttu-id="4b18f-150">Имя существующего источника журнала событий.</span><span class="sxs-lookup"><span data-stu-id="4b18f-150">The name of an existing event log source.</span></span>|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<span data-ttu-id="4b18f-151">Имя файла, <xref:System.Diagnostics.EventSchemaTraceListener> в который производится запись.</span><span class="sxs-lookup"><span data-stu-id="4b18f-151">The name of the file that the <xref:System.Diagnostics.EventSchemaTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="4b18f-152">Имя файла, <xref:System.Diagnostics.TextWriterTraceListener> в который производится запись.</span><span class="sxs-lookup"><span data-stu-id="4b18f-152">The name of the file that the <xref:System.Diagnostics.TextWriterTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.XmlWriterTraceListener>|<span data-ttu-id="4b18f-153">Имя файла, <xref:System.Diagnostics.XmlWriterTraceListener> в который производится запись.</span><span class="sxs-lookup"><span data-stu-id="4b18f-153">The name of the file that the <xref:System.Diagnostics.XmlWriterTraceListener> writes to.</span></span>|  
  
## <a name="configuration-file"></a><span data-ttu-id="4b18f-154">Файл конфигурации</span><span class="sxs-lookup"><span data-stu-id="4b18f-154">Configuration File</span></span>  

 <span data-ttu-id="4b18f-155">Этот элемент можно использовать в файле конфигурации компьютера (Machine.config) и файле конфигурации приложения.</span><span class="sxs-lookup"><span data-stu-id="4b18f-155">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4b18f-156">Пример</span><span class="sxs-lookup"><span data-stu-id="4b18f-156">Example</span></span>  

 <span data-ttu-id="4b18f-157">В следующем примере показано, как использовать `<add>` элементы для добавления в <xref:System.Diagnostics.TextWriterTraceListener> `textListener` `sharedListeners` коллекцию.</span><span class="sxs-lookup"><span data-stu-id="4b18f-157">The following example shows how to use `<add>` elements to add the <xref:System.Diagnostics.TextWriterTraceListener>`textListener` to the `sharedListeners` collection.</span></span>   <span data-ttu-id="4b18f-158">`textListener` добавляется по имени в `Listeners` коллекцию для источника трассировки `TraceSourceApp` .</span><span class="sxs-lookup"><span data-stu-id="4b18f-158">`textListener` is added by name to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span> <span data-ttu-id="4b18f-159">`textListener`Прослушиватель записывает выходные данные трассировки в файл myListener. log.</span><span class="sxs-lookup"><span data-stu-id="4b18f-159">The `textListener` listener writes trace output to the file myListener.log.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="TraceSourceApp" switchName="sourceSwitch"
        switchType="System.Diagnostics.SourceSwitch">  
        <listeners>  
          <add name="console"
            type="System.Diagnostics.ConsoleTraceListener"/>  
          <add name="textListener"/>  
          <remove name="Default"/>  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add name="textListener"
        type="System.Diagnostics.TextWriterTraceListener"
        initializeData="myListener.log"/>  
    </sharedListeners>  
    <switches>  
      <add name="sourceSwitch" value="Warning"/>  
    </switches>  
  </system.diagnostics>  
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="4b18f-160">См. также</span><span class="sxs-lookup"><span data-stu-id="4b18f-160">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="4b18f-161">Схема параметров трассировки и отладки</span><span class="sxs-lookup"><span data-stu-id="4b18f-161">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="4b18f-162">Прослушиватели трассировки</span><span class="sxs-lookup"><span data-stu-id="4b18f-162">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
