---
description: 'Дополнительные сведения о: <clear> Element для <listeners> for <trace>'
title: <clear> Элемент для <listeners> для <trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/clear
helpviewer_keywords:
- clear element for <listeners> for <trace>
- <clear> element for <listeners> for <trace>
ms.assetid: b44732a8-271f-4a06-ba9e-fe3298d6f192
ms.openlocfilehash: 3c1b3816f4ccd0ceb9e9bc0fc6acfd9b6e8ade85
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99725978"
---
# <a name="clear-element-for-listeners-for-trace"></a><span data-ttu-id="84e78-103">\<clear> Элемент для \<listeners> для \<trace></span><span class="sxs-lookup"><span data-stu-id="84e78-103">\<clear> Element for \<listeners> for \<trace></span></span>

<span data-ttu-id="84e78-104">Очищает коллекцию `Listeners` для трассировки.</span><span class="sxs-lookup"><span data-stu-id="84e78-104">Clears the `Listeners` collection for trace.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-trace.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a><span data-ttu-id="84e78-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="84e78-105">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="84e78-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="84e78-106">Attributes and Elements</span></span>  

 <span data-ttu-id="84e78-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="84e78-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="84e78-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="84e78-108">Attributes</span></span>  

 <span data-ttu-id="84e78-109">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="84e78-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="84e78-110">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="84e78-110">Child Elements</span></span>  

 <span data-ttu-id="84e78-111">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="84e78-111">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="84e78-112">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="84e78-112">Parent Elements</span></span>  
  
|<span data-ttu-id="84e78-113">Элемент</span><span class="sxs-lookup"><span data-stu-id="84e78-113">Element</span></span>|<span data-ttu-id="84e78-114">Описание</span><span class="sxs-lookup"><span data-stu-id="84e78-114">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="84e78-115">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="84e78-115">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="84e78-116">Задает прослушиватели трассировки, собирающие, хранящие и маршрутизирующие сообщения, а также уровень, на котором установлен ключ трассировки.</span><span class="sxs-lookup"><span data-stu-id="84e78-116">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="84e78-117">Содержит прослушиватели, которые собирают, хранят и маршрутизируют сообщения трассировки.</span><span class="sxs-lookup"><span data-stu-id="84e78-117">Contains listeners that collect, store, and route tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="84e78-118">Содержит прослушиватели, собирающие, сохраняющие и направляющие сообщения.</span><span class="sxs-lookup"><span data-stu-id="84e78-118">Contains listeners that collect, store, and route messages.</span></span> <span data-ttu-id="84e78-119">Прослушиватели направляют выходные данные трассировки в соответствующий целевой объект.</span><span class="sxs-lookup"><span data-stu-id="84e78-119">Listeners direct the tracing output to an appropriate target.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="84e78-120">Remarks</span><span class="sxs-lookup"><span data-stu-id="84e78-120">Remarks</span></span>  

 <span data-ttu-id="84e78-121">`<clear>`Элемент удаляет все прослушиватели из `Listeners` коллекции для трассировки.</span><span class="sxs-lookup"><span data-stu-id="84e78-121">The `<clear>` element removes all listeners from the `Listeners` collection for trace.</span></span> <span data-ttu-id="84e78-122">Элемент можно использовать `<clear>` перед использованием `<add>` элемента, чтобы убедиться в отсутствии других активных прослушивателей в коллекции.</span><span class="sxs-lookup"><span data-stu-id="84e78-122">You can use the `<clear>` element before using the `<add>` element to be certain there are no other active listeners in the collection.</span></span>  
  
 <span data-ttu-id="84e78-123">Можно очистить `Listeners` коллекцию программным путем, вызвав <xref:System.Diagnostics.TraceListenerCollection.Clear%2A> метод для <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> Свойства ( `System.Diagnostics.Trace.Listeners.Clear()` ).</span><span class="sxs-lookup"><span data-stu-id="84e78-123">You can clear the `Listeners` collection programmatically by calling the <xref:System.Diagnostics.TraceListenerCollection.Clear%2A> method on the <xref:System.Diagnostics.Trace.Listeners%2A?displayProperty=nameWithType> property (`System.Diagnostics.Trace.Listeners.Clear()`).</span></span>  
  
 <span data-ttu-id="84e78-124">Этот элемент можно использовать в файле конфигурации компьютера (Machine.config) и файле конфигурации приложения.</span><span class="sxs-lookup"><span data-stu-id="84e78-124">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="84e78-125">`<clear>`Элемент удаляет <xref:System.Diagnostics.DefaultTraceListener> из `Listeners` коллекции, изменяя поведение <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType> методов,, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType> и <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="84e78-125">The `<clear>` element removes the <xref:System.Diagnostics.DefaultTraceListener> from the `Listeners` collection, altering the behavior of the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>, and <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="84e78-126">Вызов `Assert` метода или `Fail` обычно приводит к отображению окна сообщения.</span><span class="sxs-lookup"><span data-stu-id="84e78-126">Calling an `Assert` or `Fail` method normally results in the display of a message box.</span></span> <span data-ttu-id="84e78-127">Однако окно сообщения не отображается, если объект <xref:System.Diagnostics.DefaultTraceListener> отсутствует в `Listeners` коллекции.</span><span class="sxs-lookup"><span data-stu-id="84e78-127">However, the message box is not displayed if the <xref:System.Diagnostics.DefaultTraceListener> is not in the `Listeners` collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="84e78-128">Пример</span><span class="sxs-lookup"><span data-stu-id="84e78-128">Example</span></span>  

 <span data-ttu-id="84e78-129">В следующем примере показано, как использовать `<clear>` элемент перед использованием `<add>` элемента для добавления прослушивателя `console` в `Listeners` коллекцию для трассировки.</span><span class="sxs-lookup"><span data-stu-id="84e78-129">The following example shows how to use the `<clear>` element before using the `<add>` element to add the listener `console` to the `Listeners` collection for trace.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <trace autoflush="false" indentsize="4">  
      <listeners>  
        <clear/>  
        <add name="console"
          type="System.Diagnostics.ConsoleTraceListener" >  
          <filter type="System.Diagnostics.EventTypeFilter"
            initializeData="Error" />  
        </add>  
      </listeners>  
    </trace>  
  </system.diagnostics>  
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="84e78-130">См. также</span><span class="sxs-lookup"><span data-stu-id="84e78-130">See also</span></span>

- <xref:System.Diagnostics.Trace.Listeners%2A>
- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- <xref:System.Diagnostics.TraceSource>
- [<span data-ttu-id="84e78-131">Схема параметров трассировки и отладки</span><span class="sxs-lookup"><span data-stu-id="84e78-131">Trace and Debug Settings Schema</span></span>](index.md)
- [\<remove>](remove-element-for-listeners-for-trace.md)
- [<span data-ttu-id="84e78-132">Прослушиватели трассировки</span><span class="sxs-lookup"><span data-stu-id="84e78-132">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
