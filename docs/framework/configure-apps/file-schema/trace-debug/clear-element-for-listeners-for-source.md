---
description: 'Дополнительные сведения о: <clear> Element для <listeners> for <source>'
title: <clear> Элемент для <listeners> для <source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/clear
helpviewer_keywords:
- <clear> element for <listeners> for <source>
- clear element for <listeners> for <source>
ms.assetid: 76796bb2-9c0b-4526-8135-8bf18b16d8d9
ms.openlocfilehash: 731c23c73b6d149bd37672e91eca1d70431b2789
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639709"
---
# <a name="clear-element-for-listeners-for-source"></a><span data-ttu-id="d6fa7-103">\<clear> Элемент для \<listeners> для \<source></span><span class="sxs-lookup"><span data-stu-id="d6fa7-103">\<clear> Element for \<listeners> for \<source></span></span>

<span data-ttu-id="d6fa7-104">Очищает коллекцию `Listeners` для источника трассировки.</span><span class="sxs-lookup"><span data-stu-id="d6fa7-104">Clears the `Listeners` collection for a trace source.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<source>**](source-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<listeners>**](listeners-element-for-source.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a><span data-ttu-id="d6fa7-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d6fa7-105">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d6fa7-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="d6fa7-106">Attributes and Elements</span></span>  

 <span data-ttu-id="d6fa7-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="d6fa7-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d6fa7-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="d6fa7-108">Attributes</span></span>  

 <span data-ttu-id="d6fa7-109">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="d6fa7-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d6fa7-110">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="d6fa7-110">Child Elements</span></span>  

 <span data-ttu-id="d6fa7-111">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="d6fa7-111">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d6fa7-112">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="d6fa7-112">Parent Elements</span></span>  
  
|<span data-ttu-id="d6fa7-113">Элемент</span><span class="sxs-lookup"><span data-stu-id="d6fa7-113">Element</span></span>|<span data-ttu-id="d6fa7-114">Описание</span><span class="sxs-lookup"><span data-stu-id="d6fa7-114">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="d6fa7-115">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d6fa7-115">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="d6fa7-116">Задает прослушиватели трассировки, собирающие, хранящие и маршрутизирующие сообщения, а также уровень, на котором установлен ключ трассировки.</span><span class="sxs-lookup"><span data-stu-id="d6fa7-116">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="d6fa7-117">Содержит источники трассировки, которые инициируют сообщения трассировки.</span><span class="sxs-lookup"><span data-stu-id="d6fa7-117">Contains trace sources that initiate tracing messages.</span></span>|  
|`source`|<span data-ttu-id="d6fa7-118">Содержит источник трассировки, который инициирует сообщения трассировки.</span><span class="sxs-lookup"><span data-stu-id="d6fa7-118">Specifies a trace source that initiates tracing messages.</span></span>|  
|`listeners`|<span data-ttu-id="d6fa7-119">Указывает прослушиватели, собирающие, хранящие и направляющие сообщения.</span><span class="sxs-lookup"><span data-stu-id="d6fa7-119">Specifies listeners that collect, store, and route messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d6fa7-120">Remarks</span><span class="sxs-lookup"><span data-stu-id="d6fa7-120">Remarks</span></span>  

 <span data-ttu-id="d6fa7-121">`<clear>`Элемент удаляет все прослушиватели из `Listeners` коллекции для источника трассировки, включая <xref:System.Diagnostics.DefaultTraceListener> .</span><span class="sxs-lookup"><span data-stu-id="d6fa7-121">The `<clear>` element removes all listeners from the `Listeners` collection for a trace source, including the <xref:System.Diagnostics.DefaultTraceListener>.</span></span> <span data-ttu-id="d6fa7-122">Элемент можно использовать `<clear>` перед использованием `<add>` элемента, чтобы убедиться в отсутствии других активных прослушивателей в коллекции.</span><span class="sxs-lookup"><span data-stu-id="d6fa7-122">You can use the `<clear>` element before using the `<add>` element to be certain there are no other active listeners in the collection.</span></span>  
  
## <a name="configuration-file"></a><span data-ttu-id="d6fa7-123">Файл конфигурации</span><span class="sxs-lookup"><span data-stu-id="d6fa7-123">Configuration File</span></span>  

 <span data-ttu-id="d6fa7-124">Этот элемент можно использовать в файле конфигурации компьютера (Machine.config) и файле конфигурации приложения.</span><span class="sxs-lookup"><span data-stu-id="d6fa7-124">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d6fa7-125">Пример</span><span class="sxs-lookup"><span data-stu-id="d6fa7-125">Example</span></span>  

 <span data-ttu-id="d6fa7-126">В следующем примере показано, как использовать `<clear>` элемент перед использованием `<add>` элементов для добавления прослушивателей `console` и `textListener` в `Listeners` коллекцию для источника трассировки `TraceSourceApp` .</span><span class="sxs-lookup"><span data-stu-id="d6fa7-126">The following example shows how to use the `<clear>` element before using the `<add>` elements to add the listeners `console` and `textListener` to the `Listeners` collection for the trace source `TraceSourceApp`.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
       <source name="TraceSourceApp" switchName="sourceSwitch"
         switchType="System.Diagnostics.SourceSwitch">  
        <listeners>  
          <clear/>  
          <add name="console"
            type="System.Diagnostics.ConsoleTraceListener"/>  
          <add name="textListener"/>  
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
  
## <a name="see-also"></a><span data-ttu-id="d6fa7-127">См. также</span><span class="sxs-lookup"><span data-stu-id="d6fa7-127">See also</span></span>

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- [<span data-ttu-id="d6fa7-128">Схема параметров трассировки и отладки</span><span class="sxs-lookup"><span data-stu-id="d6fa7-128">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="d6fa7-129">Прослушиватели трассировки</span><span class="sxs-lookup"><span data-stu-id="d6fa7-129">Trace Listeners</span></span>](../../../debug-trace-profile/trace-listeners.md)
