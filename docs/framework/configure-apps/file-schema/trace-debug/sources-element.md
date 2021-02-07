---
description: 'Дополнительные сведения о: <sources> element'
title: Элемент <sources>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources
- http://schemas.microsoft.com/.NetConfiguration/v2.0#sources
helpviewer_keywords:
- sources element
- trace sources
- <sources> element
ms.assetid: c727b2e2-423a-4463-a223-013f40ff16a3
ms.openlocfilehash: 8e5bf2af74d80cf7766de0992623d4792f17bf37
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99750550"
---
# <a name="sources-element"></a><span data-ttu-id="08ddd-103">Элемент \<sources></span><span class="sxs-lookup"><span data-stu-id="08ddd-103">\<sources> Element</span></span>

<span data-ttu-id="08ddd-104">Указывает источники трассировки, инициирующие сообщения трассировки.</span><span class="sxs-lookup"><span data-stu-id="08ddd-104">Specifies trace sources that initiate tracing messages.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<sources>**

## <a name="syntax"></a><span data-ttu-id="08ddd-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="08ddd-105">Syntax</span></span>  
  
```xml  
<sources>  
   <source>...</source>  
</sources>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="08ddd-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="08ddd-106">Attributes and Elements</span></span>  

 <span data-ttu-id="08ddd-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="08ddd-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="08ddd-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="08ddd-108">Attributes</span></span>  

 <span data-ttu-id="08ddd-109">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="08ddd-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="08ddd-110">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="08ddd-110">Child Elements</span></span>  
  
|<span data-ttu-id="08ddd-111">Элемент</span><span class="sxs-lookup"><span data-stu-id="08ddd-111">Element</span></span>|<span data-ttu-id="08ddd-112">Описание</span><span class="sxs-lookup"><span data-stu-id="08ddd-112">Description</span></span>|  
|-------------|-----------------|  
|[\<source>](source-element.md)|<span data-ttu-id="08ddd-113">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="08ddd-113">Required element.</span></span><br /><br /> <span data-ttu-id="08ddd-114">Содержит источник трассировки, который инициирует сообщения трассировки.</span><span class="sxs-lookup"><span data-stu-id="08ddd-114">Specifies a trace source that initiates tracing messages.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="08ddd-115">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="08ddd-115">Parent Elements</span></span>  
  
|<span data-ttu-id="08ddd-116">Элемент</span><span class="sxs-lookup"><span data-stu-id="08ddd-116">Element</span></span>|<span data-ttu-id="08ddd-117">Описание</span><span class="sxs-lookup"><span data-stu-id="08ddd-117">Description</span></span>|  
|-------------|-----------------|  
|`configuration`|<span data-ttu-id="08ddd-118">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="08ddd-118">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|  
|`system.diagnostics`|<span data-ttu-id="08ddd-119">Задает прослушиватели трассировки, собирающие, хранящие и маршрутизирующие сообщения, а также уровень, на котором установлен ключ трассировки.</span><span class="sxs-lookup"><span data-stu-id="08ddd-119">Specifies trace listeners that collect, store, and route messages and the level where a trace switch is set.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="08ddd-120">Remarks</span><span class="sxs-lookup"><span data-stu-id="08ddd-120">Remarks</span></span>  

 <span data-ttu-id="08ddd-121">Этот элемент можно использовать в файле конфигурации компьютера (Machine.config) и файле конфигурации приложения.</span><span class="sxs-lookup"><span data-stu-id="08ddd-121">This element can be used in the machine configuration file (Machine.config) and the application configuration file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="08ddd-122">Пример</span><span class="sxs-lookup"><span data-stu-id="08ddd-122">Example</span></span>  

 <span data-ttu-id="08ddd-123">В следующем примере показано, как с помощью `<sources>` элемента добавить источник трассировки `mySource` и задать уровень для коммутатора источника с именем `sourceSwitch` .</span><span class="sxs-lookup"><span data-stu-id="08ddd-123">The following example shows how to use the `<sources>` element to add the trace source `mySource` and to set the level for the source switch named `sourceSwitch`.</span></span> <span data-ttu-id="08ddd-124">Добавляется прослушиватель трассировки консоли, который записывает данные трассировки на консоль.</span><span class="sxs-lookup"><span data-stu-id="08ddd-124">A console trace listener is added that writes trace information to the console.</span></span>  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <sources>  
         <source name="mySource" switchName="sourceSwitch"
            switchType="System.Diagnostics.SourceSwitch"  >  
            <listeners>  
               <add name="console"
                  type="System.Diagnostics.ConsoleTraceListener" >  
                  <filter type="System.Diagnostics.EventTypeFilter"
                     initializeData="Error" />  
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
  
## <a name="see-also"></a><span data-ttu-id="08ddd-125">См. также</span><span class="sxs-lookup"><span data-stu-id="08ddd-125">See also</span></span>

- <xref:System.Diagnostics.TraceListener>
- <xref:System.Diagnostics.DefaultTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.XmlWriterTraceListener>
- [<span data-ttu-id="08ddd-126">Схема параметров трассировки и отладки</span><span class="sxs-lookup"><span data-stu-id="08ddd-126">Trace and Debug Settings Schema</span></span>](index.md)
- [\<source>](source-element.md)
