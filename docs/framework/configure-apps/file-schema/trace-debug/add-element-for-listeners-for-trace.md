---
description: 'Дополнительные сведения о: <add> Element для <listeners> for <trace>'
title: <add> Элемент для <listeners> для <trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add
helpviewer_keywords:
- initializeData attribute
- <add> element for <listeners>
- add element for <listeners>
ms.assetid: 81e804a3-ef11-4d39-bbde-bfa012c179e2
ms.openlocfilehash: ffc0823e0c0ce1dcd9d9f19853929496b3248177
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639787"
---
# <a name="add-element-for-listeners-for-trace"></a><span data-ttu-id="30c56-103">\<add> Элемент для \<listeners> для \<trace></span><span class="sxs-lookup"><span data-stu-id="30c56-103">\<add> Element for \<listeners> for \<trace></span></span>

<span data-ttu-id="30c56-104">Добавляет прослушиватель в коллекцию **Listeners** .</span><span class="sxs-lookup"><span data-stu-id="30c56-104">Adds a listener to the **Listeners** collection.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-trace.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="30c56-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="30c56-105">Syntax</span></span>  
  
```xml  
<add name="name"
     type="trace listener class name, Version, Culture, PublicKeyToken"  
     initializeData="data"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="30c56-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="30c56-106">Attributes and Elements</span></span>  

 <span data-ttu-id="30c56-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="30c56-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="30c56-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="30c56-108">Attributes</span></span>  
  
|<span data-ttu-id="30c56-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="30c56-109">Attribute</span></span>|<span data-ttu-id="30c56-110">Описание</span><span class="sxs-lookup"><span data-stu-id="30c56-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="30c56-111">**type**</span><span class="sxs-lookup"><span data-stu-id="30c56-111">**type**</span></span>|<span data-ttu-id="30c56-112">Обязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="30c56-112">Required attribute.</span></span><br /><br /> <span data-ttu-id="30c56-113">Указывает тип прослушивателя.</span><span class="sxs-lookup"><span data-stu-id="30c56-113">Specifies the type of the listener.</span></span> <span data-ttu-id="30c56-114">Необходимо использовать строку, которая соответствует требованиям, указанным в указании [полных имен типов](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span><span class="sxs-lookup"><span data-stu-id="30c56-114">You must use a string that meets the requirements specified in [Specifying Fully Qualified Type Names](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).</span></span>|  
|<span data-ttu-id="30c56-115">**initializeData**</span><span class="sxs-lookup"><span data-stu-id="30c56-115">**initializeData**</span></span>|<span data-ttu-id="30c56-116">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="30c56-116">Optional attribute.</span></span><br /><br /> <span data-ttu-id="30c56-117">Строка, передаваемая конструктору для указанного класса.</span><span class="sxs-lookup"><span data-stu-id="30c56-117">The string passed to the constructor for the specified class.</span></span>|  
|<span data-ttu-id="30c56-118">**name**</span><span class="sxs-lookup"><span data-stu-id="30c56-118">**name**</span></span>|<span data-ttu-id="30c56-119">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="30c56-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="30c56-120">Указывает имя прослушивателя.</span><span class="sxs-lookup"><span data-stu-id="30c56-120">Specifies the name of the listener.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="30c56-121">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="30c56-121">Child Elements</span></span>  
  
|<span data-ttu-id="30c56-122">Элемент</span><span class="sxs-lookup"><span data-stu-id="30c56-122">Element</span></span>|<span data-ttu-id="30c56-123">Описание</span><span class="sxs-lookup"><span data-stu-id="30c56-123">Description</span></span>|  
|-------------|-----------------|  
|[\<filter>](filter-element-for-add-for-listeners-for-trace.md)|<span data-ttu-id="30c56-124">Добавляет фильтр в прослушиватель в `Listeners` коллекции для трассировки.</span><span class="sxs-lookup"><span data-stu-id="30c56-124">Adds a filter to a listener in the `Listeners` collection for a trace.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="30c56-125">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="30c56-125">Parent Elements</span></span>  
  
|<span data-ttu-id="30c56-126">Элемент</span><span class="sxs-lookup"><span data-stu-id="30c56-126">Element</span></span>|<span data-ttu-id="30c56-127">Описание</span><span class="sxs-lookup"><span data-stu-id="30c56-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="30c56-128">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="30c56-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`listeners`|<span data-ttu-id="30c56-129">Указывает прослушиватель, который собирает, хранит и маршрутизирует сообщения.</span><span class="sxs-lookup"><span data-stu-id="30c56-129">Specifies a listener that collects, stores, and routes messages.</span></span> <span data-ttu-id="30c56-130">Прослушиватели направляют выходные данные трассировки в соответствующий целевой объект.</span><span class="sxs-lookup"><span data-stu-id="30c56-130">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="30c56-131">Задает корневой элемент для раздела конфигурации ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="30c56-131">Specifies the root element for the ASP.NET configuration section.</span></span>|  
|`trace`|<span data-ttu-id="30c56-132">Содержит прослушиватели, которые собирают, хранят и маршрутизируют сообщения трассировки.</span><span class="sxs-lookup"><span data-stu-id="30c56-132">Contains listeners that collect, store, and route tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="30c56-133">Remarks</span><span class="sxs-lookup"><span data-stu-id="30c56-133">Remarks</span></span>  

 <span data-ttu-id="30c56-134"><xref:System.Diagnostics.Debug>Классы и <xref:System.Diagnostics.Trace> совместно используют одну и ту же коллекцию **Listeners** .</span><span class="sxs-lookup"><span data-stu-id="30c56-134">The <xref:System.Diagnostics.Debug> and <xref:System.Diagnostics.Trace> classes share the same **Listeners** collection.</span></span> <span data-ttu-id="30c56-135">При добавлении объекта прослушивателя в коллекцию в одном из этих классов другой класс использует тот же прослушиватель.</span><span class="sxs-lookup"><span data-stu-id="30c56-135">If you add a listener object to the collection in one of these classes, the other class uses the same listener.</span></span> <span data-ttu-id="30c56-136">Классы прослушивателей являются производными от <xref:System.Diagnostics.TraceListener> .</span><span class="sxs-lookup"><span data-stu-id="30c56-136">The listener classes derive from the <xref:System.Diagnostics.TraceListener>.</span></span>  
  
 <span data-ttu-id="30c56-137">Если `name` атрибут прослушивателя трассировки не указан, то <xref:System.Diagnostics.TraceListener.Name%2A> для прослушивателя трассировки по умолчанию используется пустая строка ("").</span><span class="sxs-lookup"><span data-stu-id="30c56-137">If you do not specify the `name` attribute of the trace listener, the <xref:System.Diagnostics.TraceListener.Name%2A> of the trace listener defaults to an empty string ("").</span></span> <span data-ttu-id="30c56-138">Если у приложения есть только один прослушиватель, можно добавить его без указания имени и удалить его, указав в качестве имени пустую строку.</span><span class="sxs-lookup"><span data-stu-id="30c56-138">If your application has only one listener, you can add it without specifying a name, and remove it by specifying an empty string for the name.</span></span> <span data-ttu-id="30c56-139">Однако если приложение имеет более одного прослушивателя, необходимо указать уникальные имена для каждого прослушивателя трассировки, что позволяет определять отдельные прослушиватели трассировки в <xref:System.Diagnostics.Debug.Listeners%2A> коллекциях и управлять ими <xref:System.Diagnostics.Trace.Listeners%2A> .</span><span class="sxs-lookup"><span data-stu-id="30c56-139">However, if your application has more than one listener, you should specify unique names for each trace listener, which allows you to identify and manage individual trace listeners within the <xref:System.Diagnostics.Debug.Listeners%2A> and <xref:System.Diagnostics.Trace.Listeners%2A> collections.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="30c56-140">Добавление нескольких прослушивателей трассировки одного и того же типа и с одним и тем же именем приводит к тому, что только один прослушиватель трассировки этого типа и имя добавляются в `Listeners` коллекцию.</span><span class="sxs-lookup"><span data-stu-id="30c56-140">Adding more than one trace listener of the same type and with the same name results in only one trace listener of that type and name being added to the `Listeners` collection.</span></span> <span data-ttu-id="30c56-141">Тем не менее можно программно добавить несколько идентичных прослушивателей в `Listeners` коллекцию.</span><span class="sxs-lookup"><span data-stu-id="30c56-141">However, you can programmatically add multiple identical listeners to the `Listeners` collection.</span></span>  
  
 <span data-ttu-id="30c56-142">Значение атрибута **initializeData** зависит от типа создаваемого прослушивателя.</span><span class="sxs-lookup"><span data-stu-id="30c56-142">The value for the **initializeData** attribute depends on the type of listener you create.</span></span> <span data-ttu-id="30c56-143">Не все прослушиватели трассировки нуждаются в указании **initializeData**.</span><span class="sxs-lookup"><span data-stu-id="30c56-143">Not all trace listeners require that you specify **initializeData**.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="30c56-144">При использовании `initializeData` атрибута может появиться предупреждение компилятора "атрибут initializeData не объявлен".</span><span class="sxs-lookup"><span data-stu-id="30c56-144">When you use the `initializeData` attribute, you may get the compiler warning "The 'initializeData' attribute is not declared."</span></span> <span data-ttu-id="30c56-145">Это предупреждение возникает из-за того, что параметры конфигурации проверяются по абстрактному базовому классу <xref:System.Diagnostics.TraceListener> , который не распознает `initializeData` атрибут.</span><span class="sxs-lookup"><span data-stu-id="30c56-145">This warning occurs because the configuration settings are validated against the abstract base class <xref:System.Diagnostics.TraceListener>, which does not recognize the `initializeData` attribute.</span></span> <span data-ttu-id="30c56-146">Как правило, это предупреждение можно игнорировать для реализаций прослушивателя трассировки, имеющих конструктор, принимающий параметр.</span><span class="sxs-lookup"><span data-stu-id="30c56-146">Typically, you can ignore this warning for trace listener implementations that have a constructor that takes a parameter.</span></span>  
  
 <span data-ttu-id="30c56-147">В следующей таблице показаны прослушиватели трассировки, которые включены в платформа .NET Framework и описаны значения их атрибутов **initializeData** .</span><span class="sxs-lookup"><span data-stu-id="30c56-147">The following table shows the trace listeners that are included with the .NET Framework and describes the value of their **initializeData** attributes.</span></span>  
  
|<span data-ttu-id="30c56-148">Класс прослушивателя трассировки</span><span class="sxs-lookup"><span data-stu-id="30c56-148">Trace listener class</span></span>|<span data-ttu-id="30c56-149">значение атрибута initializeData</span><span class="sxs-lookup"><span data-stu-id="30c56-149">initializeData attribute value</span></span>|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|<span data-ttu-id="30c56-150">`useErrorStream`Значение для <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> конструктора.</span><span class="sxs-lookup"><span data-stu-id="30c56-150">The `useErrorStream` value for the <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> constructor.</span></span>  <span data-ttu-id="30c56-151">Задайте для `initializeData` атрибута значение " `true` ", чтобы записывать выходные данные трассировки и отладки в <xref:System.Console.Error%2A?displayProperty=nameWithType> ; " `false` " для записи <xref:System.Console.Out%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="30c56-151">Set the `initializeData` attribute to "`true`" to write trace and debug output to <xref:System.Console.Error%2A?displayProperty=nameWithType>; "`false`" to write to <xref:System.Console.Out%2A?displayProperty=nameWithType>.</span></span>|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|<span data-ttu-id="30c56-152">Имя файла, в который осуществляет запись объект <xref:System.Diagnostics.DelimitedListTraceListener>.</span><span class="sxs-lookup"><span data-stu-id="30c56-152">The name of the file the <xref:System.Diagnostics.DelimitedListTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|<span data-ttu-id="30c56-153">Имя существующего источника журнала событий.</span><span class="sxs-lookup"><span data-stu-id="30c56-153">The name of the name of an existing event log source.</span></span>|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|<span data-ttu-id="30c56-154">Имя файла, <xref:System.Diagnostics.EventSchemaTraceListener> в который производится запись.</span><span class="sxs-lookup"><span data-stu-id="30c56-154">The name of the file that the <xref:System.Diagnostics.EventSchemaTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="30c56-155">Имя файла, <xref:System.Diagnostics.TextWriterTraceListener> в который производится запись.</span><span class="sxs-lookup"><span data-stu-id="30c56-155">The name of the file that the <xref:System.Diagnostics.TextWriterTraceListener> writes to.</span></span>|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|<span data-ttu-id="30c56-156">Имя файла, <xref:System.Diagnostics.XmlWriterTraceListener> в который производится запись.</span><span class="sxs-lookup"><span data-stu-id="30c56-156">The name of the file that the <xref:System.Diagnostics.XmlWriterTraceListener> writes to.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="30c56-157">Пример</span><span class="sxs-lookup"><span data-stu-id="30c56-157">Example</span></span>  

 <span data-ttu-id="30c56-158">В следующем примере показано, как использовать **\<add>** элементы для добавления прослушивателей `MyListener` и `MyEventListener` в коллекцию **Listeners** .</span><span class="sxs-lookup"><span data-stu-id="30c56-158">The following example shows how to use **\<add>** elements to add the listeners `MyListener` and `MyEventListener` to the **Listeners** collection.</span></span> <span data-ttu-id="30c56-159">`MyListener` создает файл с именем `MyListener.log` и записывает выходные данные в файл.</span><span class="sxs-lookup"><span data-stu-id="30c56-159">`MyListener` creates a file called `MyListener.log` and writes the output to the file.</span></span> <span data-ttu-id="30c56-160">`MyEventListener` создает запись в журнале событий.</span><span class="sxs-lookup"><span data-stu-id="30c56-160">`MyEventListener` creates an entry in the event log.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <trace autoflush="true" indentsize="0">  
         <listeners>  
            <add name="myListener" type="System.Diagnostics.TextWriterTraceListener, system, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="c:\myListener.log" />  
            <add name="MyEventListener"  
                 type="System.Diagnostics.EventLogTraceListener, system, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"                 initializeData="MyConfigEventLog"/>  
            <add name="configConsoleListener"  
                 type="System.Diagnostics.ConsoleTraceListener, system, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"/>  
         </listeners>  
      </trace>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="30c56-161">См. также</span><span class="sxs-lookup"><span data-stu-id="30c56-161">See also</span></span>

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- [<span data-ttu-id="30c56-162">Схема параметров трассировки и отладки</span><span class="sxs-lookup"><span data-stu-id="30c56-162">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="30c56-163">Прослушиватели трассировки</span><span class="sxs-lookup"><span data-stu-id="30c56-163">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
