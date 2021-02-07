---
description: 'Дополнительные сведения о: <remove> Element для <listeners> for <trace>'
title: <remove> Элемент для <listeners> для <trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/remove
helpviewer_keywords:
- remove element
- <remove> element
ms.assetid: 9a5cd1b5-be1a-485f-8f0c-2890ad3ef3e0
ms.openlocfilehash: 8b863cb535c28f090374e284717d5bf38f22e881
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99750602"
---
# <a name="remove-element-for-listeners-for-trace"></a><span data-ttu-id="5503a-103">\<remove> Элемент для \<listeners> для \<trace></span><span class="sxs-lookup"><span data-stu-id="5503a-103">\<remove> Element for \<listeners> for \<trace></span></span>

<span data-ttu-id="5503a-104">Удаляет прослушиватель из коллекции **Listeners** .</span><span class="sxs-lookup"><span data-stu-id="5503a-104">Removes a listener from the **Listeners** collection.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<trace>**](trace-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-trace.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**

## <a name="syntax"></a><span data-ttu-id="5503a-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="5503a-105">Syntax</span></span>  
  
```xml  
<remove name="listener name" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5503a-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="5503a-106">Attributes and Elements</span></span>  

 <span data-ttu-id="5503a-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="5503a-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5503a-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="5503a-108">Attributes</span></span>  
  
|<span data-ttu-id="5503a-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="5503a-109">Attribute</span></span>|<span data-ttu-id="5503a-110">Описание</span><span class="sxs-lookup"><span data-stu-id="5503a-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5503a-111">**name**</span><span class="sxs-lookup"><span data-stu-id="5503a-111">**name**</span></span>|<span data-ttu-id="5503a-112">Обязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="5503a-112">Required attribute.</span></span><br /><br /> <span data-ttu-id="5503a-113">Имя прослушивателя, удаляемого из коллекции **прослушивателей** .</span><span class="sxs-lookup"><span data-stu-id="5503a-113">The name of the listener to remove from the **Listeners** collection.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5503a-114">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="5503a-114">Child Elements</span></span>  

 <span data-ttu-id="5503a-115">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="5503a-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5503a-116">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="5503a-116">Parent Elements</span></span>  
  
|<span data-ttu-id="5503a-117">Элемент</span><span class="sxs-lookup"><span data-stu-id="5503a-117">Element</span></span>|<span data-ttu-id="5503a-118">Описание</span><span class="sxs-lookup"><span data-stu-id="5503a-118">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="5503a-119">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5503a-119">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`listeners`|<span data-ttu-id="5503a-120">Указывает прослушиватель, который собирает, хранит и маршрутизирует сообщения.</span><span class="sxs-lookup"><span data-stu-id="5503a-120">Specifies a listener that collects, stores, and routes messages.</span></span> <span data-ttu-id="5503a-121">Прослушиватели направляют выходные данные трассировки в соответствующий целевой объект.</span><span class="sxs-lookup"><span data-stu-id="5503a-121">Listeners direct the tracing output to an appropriate target.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="5503a-122">Задает прослушиватели трассировки, собирающие, хранящие и маршрутизирующие сообщения, а также уровень, на котором установлен ключ трассировки.</span><span class="sxs-lookup"><span data-stu-id="5503a-122">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`trace`|<span data-ttu-id="5503a-123">Настройка службы трассировки ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="5503a-123">Configures the ASP.NET trace service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5503a-124">Remarks</span><span class="sxs-lookup"><span data-stu-id="5503a-124">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5503a-125">При удалении <xref:System.Diagnostics.DefaultTraceListener> из `Listeners` коллекции изменяется поведение <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType> методов,, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType> и <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="5503a-125">Removing the <xref:System.Diagnostics.DefaultTraceListener> from the `Listeners` collection alters the behavior of the <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=nameWithType>, <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType>, and <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="5503a-126">Вызов `Assert` метода или `Fail` обычно приводит к отображению окна сообщения, однако окно сообщения не отображается, если объект <xref:System.Diagnostics.DefaultTraceListener> отсутствует в `Listeners` коллекции.</span><span class="sxs-lookup"><span data-stu-id="5503a-126">Calling an `Assert` or `Fail` method normally results in the display of a message box, however the message box is not displayed if the <xref:System.Diagnostics.DefaultTraceListener> is not in the `Listeners` collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5503a-127">Пример</span><span class="sxs-lookup"><span data-stu-id="5503a-127">Example</span></span>  

 <span data-ttu-id="5503a-128">В следующем примере показано, как удалить прослушиватель трассировки по умолчанию из коллекции **прослушивателей** трассировки.</span><span class="sxs-lookup"><span data-stu-id="5503a-128">The following example shows how to remove the default trace listener from the trace **Listeners** collection.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <trace autoflush="true" indentsize="0">  
         <listeners>  
            <remove name="Default" />  
         </listeners>  
      </trace>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="5503a-129">См. также</span><span class="sxs-lookup"><span data-stu-id="5503a-129">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- [<span data-ttu-id="5503a-130">Схема параметров трассировки и отладки</span><span class="sxs-lookup"><span data-stu-id="5503a-130">Trace and Debug Settings Schema</span></span>](index.md)
