---
description: 'Дополнительные сведения о: <diagnostics> для активации'
title: <diagnostics> для активации
ms.date: 03/30/2017
ms.assetid: 1486e0eb-fe2a-46c3-b584-c924889477dd
ms.openlocfilehash: aa1529a478ac367ea89c8926571c6c6f2f57cf74
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99698366"
---
# <a name="diagnostics-for-activation"></a><span data-ttu-id="dd870-103">\<diagnostics> для активации</span><span class="sxs-lookup"><span data-stu-id="dd870-103">\<diagnostics> for Activation</span></span>

<span data-ttu-id="dd870-104">Настраивает функции диагностики прослушивателя Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="dd870-104">Configures Windows Communication Foundation (WCF) listener's diagnostics functionalities.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel.activation>**](system-servicemodel-activation.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<diagnostics>**  
  
## <a name="syntax"></a><span data-ttu-id="dd870-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="dd870-105">Syntax</span></span>  
  
```xml  
<configuration>
  <system.serviceModel.activation>
    <diagnostics performanceCountersEnabled="Boolean" />
  </system.serviceModel.activation>
</configuration>
```  
  
## <a name="type"></a><span data-ttu-id="dd870-106">Тип</span><span class="sxs-lookup"><span data-stu-id="dd870-106">Type</span></span>  

 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dd870-107">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="dd870-107">Attributes and Elements</span></span>  

 <span data-ttu-id="dd870-108">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="dd870-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dd870-109">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="dd870-109">Attributes</span></span>  
  
|<span data-ttu-id="dd870-110">Атрибут</span><span class="sxs-lookup"><span data-stu-id="dd870-110">Attribute</span></span>|<span data-ttu-id="dd870-111">Описание</span><span class="sxs-lookup"><span data-stu-id="dd870-111">Description</span></span>|  
|---------------|-----------------|  
|`performanceCountersEnabled`|<span data-ttu-id="dd870-112">Логическое значение, определяющее, включены ли счетчики производительности для целей диагностики.</span><span class="sxs-lookup"><span data-stu-id="dd870-112">A Boolean value that indicates whether performance counters are enabled for diagnostic purposes.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dd870-113">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="dd870-113">Child Elements</span></span>  

 <span data-ttu-id="dd870-114">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="dd870-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="dd870-115">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="dd870-115">Parent Elements</span></span>  
  
|<span data-ttu-id="dd870-116">Элемент</span><span class="sxs-lookup"><span data-stu-id="dd870-116">Element</span></span>|<span data-ttu-id="dd870-117">Описание</span><span class="sxs-lookup"><span data-stu-id="dd870-117">Description</span></span>|  
|-------------|-----------------|  
|[\<system.serviceModel.activation>](system-servicemodel-activation.md)|<span data-ttu-id="dd870-118">Содержит параметры конфигурации для процесса прослушивателя SMSvcHost.exe.</span><span class="sxs-lookup"><span data-stu-id="dd870-118">Contains configuration settings for the listener process SMSvcHost.exe.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dd870-119">См. также</span><span class="sxs-lookup"><span data-stu-id="dd870-119">See also</span></span>

- <xref:System.ServiceModel.Activation.Configuration.DiagnosticSection>
