---
description: 'Дополнительные сведения о: <source> element'
title: Элемент <source>
ms.date: 09/29/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source
- http://schemas.microsoft.com/.NetConfiguration/v2.0#source
helpviewer_keywords:
- <source> element
- source element
ms.openlocfilehash: acf510dd5813900f36ac431418d55bbc6c2f364a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99750589"
---
# <a name="source-element"></a><span data-ttu-id="047f8-103">Элемент \<source></span><span class="sxs-lookup"><span data-stu-id="047f8-103">\<source> Element</span></span>

<span data-ttu-id="047f8-104">Содержит источник трассировки, который инициирует сообщения трассировки.</span><span class="sxs-lookup"><span data-stu-id="047f8-104">Specifies a trace source that initiates tracing messages.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sources>**](sources-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<source>**

## <a name="syntax"></a><span data-ttu-id="047f8-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="047f8-105">Syntax</span></span>  
  
```xml  
<source>
  <listeners>...</listeners>  
</source>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="047f8-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="047f8-106">Attributes and Elements</span></span>  

 <span data-ttu-id="047f8-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="047f8-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="047f8-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="047f8-108">Attributes</span></span>  
  
|<span data-ttu-id="047f8-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="047f8-109">Attribute</span></span>|<span data-ttu-id="047f8-110">Описание</span><span class="sxs-lookup"><span data-stu-id="047f8-110">Description</span></span>|  
|---------------|-----------------|  
|`name`|<span data-ttu-id="047f8-111">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="047f8-111">Optional attribute.</span></span><br /><br /> <span data-ttu-id="047f8-112">Задает имя источника трассировки.</span><span class="sxs-lookup"><span data-stu-id="047f8-112">Specifies the name of the trace source.</span></span>|  
|`switchName`|<span data-ttu-id="047f8-113">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="047f8-113">Optional attribute.</span></span><br /><br /> <span data-ttu-id="047f8-114">Задает имя экземпляра переключателя трассировки в приложении.</span><span class="sxs-lookup"><span data-stu-id="047f8-114">Specifies the name of a trace switch instance in the application.</span></span> <span data-ttu-id="047f8-115">Если параметр не определен в `<switches>` элементе, значение указывает уровень для переключателя.</span><span class="sxs-lookup"><span data-stu-id="047f8-115">If the switch is not identified in a `<switches>` element, the value specifies the level for the switch.</span></span>|  
|`switchType`|<span data-ttu-id="047f8-116">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="047f8-116">Optional attribute.</span></span><br /><br /> <span data-ttu-id="047f8-117">Указывает тип переключателя трассировки.</span><span class="sxs-lookup"><span data-stu-id="047f8-117">Specifies the type of the trace switch.</span></span> <span data-ttu-id="047f8-118">При наличии тип должен быть допустимым именем класса и не может быть пустой строкой.</span><span class="sxs-lookup"><span data-stu-id="047f8-118">If present, the type must be a valid class name and cannot be an empty string.</span></span>|  
|`extraAttribute`|<span data-ttu-id="047f8-119">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="047f8-119">Optional attribute.</span></span><br /><br /> <span data-ttu-id="047f8-120">Задает значение для атрибута, зависящего от источника трассировки, определяемого <xref:System.Diagnostics.TraceSource.GetSupportedAttributes%2A> методом для этого источника трассировки.</span><span class="sxs-lookup"><span data-stu-id="047f8-120">Specifies the value for a trace source-specific attribute identified by the <xref:System.Diagnostics.TraceSource.GetSupportedAttributes%2A> method for that trace source.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="047f8-121">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="047f8-121">Child Elements</span></span>  
  
|<span data-ttu-id="047f8-122">Элемент</span><span class="sxs-lookup"><span data-stu-id="047f8-122">Element</span></span>|<span data-ttu-id="047f8-123">Описание</span><span class="sxs-lookup"><span data-stu-id="047f8-123">Description</span></span>|  
|-------------|-----------------|  
|[\<listeners>](listeners-element-for-source.md)|<span data-ttu-id="047f8-124">Содержит прослушиватели, собирающие, сохраняющие и направляющие сообщения.</span><span class="sxs-lookup"><span data-stu-id="047f8-124">Contains listeners that collect, store, and route messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="047f8-125">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="047f8-125">Parent Elements</span></span>  
  
|<span data-ttu-id="047f8-126">Элемент</span><span class="sxs-lookup"><span data-stu-id="047f8-126">Element</span></span>|<span data-ttu-id="047f8-127">Описание</span><span class="sxs-lookup"><span data-stu-id="047f8-127">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="047f8-128">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="047f8-128">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="047f8-129">Задает прослушиватели трассировки, собирающие, хранящие и маршрутизирующие сообщения, а также уровень, на котором установлен ключ трассировки.</span><span class="sxs-lookup"><span data-stu-id="047f8-129">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
|`sources`|<span data-ttu-id="047f8-130">Содержит источники трассировки, которые инициируют сообщения трассировки.</span><span class="sxs-lookup"><span data-stu-id="047f8-130">Contains trace sources that initiate tracing messages.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="047f8-131">Remarks</span><span class="sxs-lookup"><span data-stu-id="047f8-131">Remarks</span></span>  

 <span data-ttu-id="047f8-132">Этот элемент можно использовать в файле конфигурации компьютера (Machine.config) и файле конфигурации приложения.</span><span class="sxs-lookup"><span data-stu-id="047f8-132">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="047f8-133">Пример</span><span class="sxs-lookup"><span data-stu-id="047f8-133">Example</span></span>  

 <span data-ttu-id="047f8-134">В следующем примере показано, как с помощью `<source>` элемента добавить источник трассировки `mySource` и задать уровень для коммутатора источника с именем `sourceSwitch` .</span><span class="sxs-lookup"><span data-stu-id="047f8-134">The following example shows how to use the `<source>` element to add the trace source `mySource` and to set the level for the source switch named `sourceSwitch`.</span></span> <span data-ttu-id="047f8-135">Добавляется прослушиватель трассировки консоли, который записывает данные трассировки на консоль.</span><span class="sxs-lookup"><span data-stu-id="047f8-135">A console trace listener is added that writes trace information to the console.</span></span>  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="mySource" switchName="sourceSwitch" switchType="System.Diagnostics.SourceSwitch"  >  
        <listeners>  
          <add name="console" type="System.Diagnostics.ConsoleTraceListener" >  
            <filter type="System.Diagnostics.EventTypeFilter" initializeData="Error" />  
          </add>  
          <remove name="Default" />  
        </listeners>  
      </source>  
    </sources>  
        <switches>  
           <add name="sourceSwitch" value="Warning" />  
        </switches>
  </system.diagnostics>
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="047f8-136">См. также</span><span class="sxs-lookup"><span data-stu-id="047f8-136">See also</span></span>

- [<span data-ttu-id="047f8-137">Схема параметров трассировки и отладки</span><span class="sxs-lookup"><span data-stu-id="047f8-137">Trace and Debug Settings Schema</span></span>](index.md)
- [<span data-ttu-id="047f8-138">Переключатели трассировки</span><span class="sxs-lookup"><span data-stu-id="047f8-138">Trace Switches</span></span>](../../../debug-trace-profile/trace-switches.md)
