---
description: 'Дополнительные сведения: <NetFx40_PInvokeStackResilience элемент>'
title: Элемент <NetFx40_PInvokeStackResilience>
ms.date: 03/30/2017
helpviewer_keywords:
- <NetFx40_PInvokeStackResilience> element
- NetFx40_PInvokeStackResilience element
ms.assetid: 39fb1588-72a4-4479-af74-0605233b68bd
ms.openlocfilehash: 59e2a5845868ebfa186344c9a731871739a29c47
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782303"
---
# <a name="netfx40_pinvokestackresilience-element"></a><span data-ttu-id="ba5f9-103">Элемент \<NetFx40_PInvokeStackResilience></span><span class="sxs-lookup"><span data-stu-id="ba5f9-103">\<NetFx40_PInvokeStackResilience> Element</span></span>

<span data-ttu-id="ba5f9-104">Указывает, исправляет ли автоматически среда выполнения неправильные объявления вызова неуправляемого кода во время выполнения за счет скорости перехода между управляемыми и неуправляемым кодом.</span><span class="sxs-lookup"><span data-stu-id="ba5f9-104">Specifies whether the runtime automatically fixes incorrect platform invoke declarations at run time, at the cost of slower transitions between managed and unmanaged code.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<runtime>**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<NetFx40_PInvokeStackResilience>**  

## <a name="syntax"></a><span data-ttu-id="ba5f9-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ba5f9-105">Syntax</span></span>

```xml
<NetFx40_PInvokeStackResilience  enabled="1|0"/>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ba5f9-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="ba5f9-106">Attributes and Elements</span></span>

<span data-ttu-id="ba5f9-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="ba5f9-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="ba5f9-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="ba5f9-108">Attributes</span></span>

|<span data-ttu-id="ba5f9-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="ba5f9-109">Attribute</span></span>|<span data-ttu-id="ba5f9-110">Описание</span><span class="sxs-lookup"><span data-stu-id="ba5f9-110">Description</span></span>|
|---------------|-----------------|
|`enabled`|<span data-ttu-id="ba5f9-111">Обязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="ba5f9-111">Required attribute.</span></span><br /><br /> <span data-ttu-id="ba5f9-112">Указывает, обнаруживает ли среда выполнения неверные объявления вызова неуправляемого кода и автоматически исправляет стек во время выполнения на 32-разрядных платформах.</span><span class="sxs-lookup"><span data-stu-id="ba5f9-112">Specifies whether the runtime detects incorrect platform invoke declarations and automatically fixes the stack at run time on 32-bit platforms.</span></span>|

## <a name="enabled-attribute"></a><span data-ttu-id="ba5f9-113">Атрибут enabled</span><span class="sxs-lookup"><span data-stu-id="ba5f9-113">enabled Attribute</span></span>

|<span data-ttu-id="ba5f9-114">Значение</span><span class="sxs-lookup"><span data-stu-id="ba5f9-114">Value</span></span>|<span data-ttu-id="ba5f9-115">Описание</span><span class="sxs-lookup"><span data-stu-id="ba5f9-115">Description</span></span>|
|-----------|-----------------|
|`0`|<span data-ttu-id="ba5f9-116">Среда выполнения использует более быструю архитектуру маршалинга взаимодействия, представленную в платформа .NET Framework 4, которая не обнаруживает и не устраняет неверные объявления вызова неуправляемого кода.</span><span class="sxs-lookup"><span data-stu-id="ba5f9-116">The runtime uses the faster interop marshaling architecture introduced in the .NET Framework 4, which does not detect and fix incorrect platform invoke declarations.</span></span> <span data-ttu-id="ba5f9-117">Это значение по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="ba5f9-117">This is the default.</span></span>|
|`1`|<span data-ttu-id="ba5f9-118">Среда выполнения использует медленные переходы, которые обнаруживают и исправляют неверные объявления вызова неуправляемого кода.</span><span class="sxs-lookup"><span data-stu-id="ba5f9-118">The runtime uses slower transitions that detect and fix incorrect platform invoke declarations.</span></span>|

### <a name="child-elements"></a><span data-ttu-id="ba5f9-119">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="ba5f9-119">Child Elements</span></span>

<span data-ttu-id="ba5f9-120">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="ba5f9-120">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ba5f9-121">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="ba5f9-121">Parent Elements</span></span>

|<span data-ttu-id="ba5f9-122">Элемент</span><span class="sxs-lookup"><span data-stu-id="ba5f9-122">Element</span></span>|<span data-ttu-id="ba5f9-123">Описание</span><span class="sxs-lookup"><span data-stu-id="ba5f9-123">Description</span></span>|
|-------------|-----------------|
|`configuration`|<span data-ttu-id="ba5f9-124">Корневой элемент в любом файле конфигурации, используемом средой CLR и приложениями .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ba5f9-124">The root element in every configuration file used by the common language runtime and .NET Framework applications.</span></span>|
|`runtime`|<span data-ttu-id="ba5f9-125">Содержит сведения о параметрах инициализации среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="ba5f9-125">Contains information about runtime initialization options.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ba5f9-126">Remarks</span><span class="sxs-lookup"><span data-stu-id="ba5f9-126">Remarks</span></span>

<span data-ttu-id="ba5f9-127">Этот элемент позволяет ускорить маршалинг взаимодействия для устойчивости во время выполнения по неправильным объявлениям вызова неуправляемого кода.</span><span class="sxs-lookup"><span data-stu-id="ba5f9-127">This element enables you to trade faster interop marshaling for run-time resilience against incorrect platform invoke declarations.</span></span>

<span data-ttu-id="ba5f9-128">Начиная с платформа .NET Framework 4, оптимизированная архитектура маршалинга взаимодействия обеспечивает значительное повышение производительности при переходе от управляемого кода к неуправляемому.</span><span class="sxs-lookup"><span data-stu-id="ba5f9-128">Starting with the .NET Framework 4, a streamlined interop marshaling architecture provides a significant performance improvement for transitions from managed code to unmanaged code.</span></span> <span data-ttu-id="ba5f9-129">В более ранних версиях платформа .NET Framework слой упаковки обнаружил неверные объявления вызова неуправляемого кода на 32-разрядных платформах и автоматически устранил стек.</span><span class="sxs-lookup"><span data-stu-id="ba5f9-129">In earlier versions of the .NET Framework, the marshaling layer detected incorrect platform invoke declarations on 32-bit platforms and automatically fixed the stack.</span></span> <span data-ttu-id="ba5f9-130">Новая архитектура маршалирования устраняет этот шаг.</span><span class="sxs-lookup"><span data-stu-id="ba5f9-130">The new marshaling architecture eliminates this step.</span></span> <span data-ttu-id="ba5f9-131">В результате переходы выполняются очень быстро, но неправильное объявление вызова неуправляемого кода может привести к сбою программы.</span><span class="sxs-lookup"><span data-stu-id="ba5f9-131">As a result, transitions are very fast, but an incorrect platform invoke declaration can cause a program failure.</span></span>

<span data-ttu-id="ba5f9-132">Чтобы упростить обнаружение неверных объявлений во время разработки, улучшен процесс отладки в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ba5f9-132">To make it easy to detect incorrect declarations during development, the Visual Studio debugging experience has been improved.</span></span> <span data-ttu-id="ba5f9-133">Помощник по отладке управляемого кода [пинвокестаккимбаланце](../../../debug-trace-profile/pinvokestackimbalance-mda.md) (MDA) уведомляет вас о неправильном объявлении вызова платформы, когда приложение выполняется с присоединенным отладчиком.</span><span class="sxs-lookup"><span data-stu-id="ba5f9-133">The [pInvokeStackImbalance](../../../debug-trace-profile/pinvokestackimbalance-mda.md) managed debugging assistant (MDA) notifies you of incorrect platform invoke declarations when your application is running with the debugger attached.</span></span>

<span data-ttu-id="ba5f9-134">Для решения сценариев, в которых приложение использует компоненты, которые нельзя перекомпилировать, с неправильными объявлениями вызова неуправляемого кода, можно использовать `NetFx40_PInvokeStackResilience` элемент.</span><span class="sxs-lookup"><span data-stu-id="ba5f9-134">To address scenarios where your application uses components that you cannot recompile, and that have incorrect platform invoke declarations, you can use the `NetFx40_PInvokeStackResilience` element.</span></span> <span data-ttu-id="ba5f9-135">Добавление этого элемента в файл конфигурации приложения с `enabled="1"` режимом совместимости с поведением более ранних версий платформа .NET Framework за счет более медленных переходов.</span><span class="sxs-lookup"><span data-stu-id="ba5f9-135">Adding this element to your application configuration file with `enabled="1"` opts into a compatibility mode with the behavior of earlier versions of the .NET Framework, at the cost of slower transitions.</span></span> <span data-ttu-id="ba5f9-136">Сборки, скомпилированные для более ранних версий платформа .NET Framework, автоматически включаются в этот режим совместимости и не нуждаются в этом элементе.</span><span class="sxs-lookup"><span data-stu-id="ba5f9-136">Assemblies that have been compiled against earlier versions of the .NET Framework are automatically opted into this compatibility mode, and do not need this element.</span></span>

## <a name="configuration-file"></a><span data-ttu-id="ba5f9-137">Файл конфигурации</span><span class="sxs-lookup"><span data-stu-id="ba5f9-137">Configuration File</span></span>

<span data-ttu-id="ba5f9-138">Этот элемент может использоваться только в файле конфигурации приложения.</span><span class="sxs-lookup"><span data-stu-id="ba5f9-138">This element can be used only in the application configuration file.</span></span>

## <a name="example"></a><span data-ttu-id="ba5f9-139">Пример</span><span class="sxs-lookup"><span data-stu-id="ba5f9-139">Example</span></span>

<span data-ttu-id="ba5f9-140">В следующем примере показано, как выбрать повышенную устойчивость к неправильным объявлениям вызова неуправляемого кода для приложения за счет более медленных переходов между управляемым и неуправляемым кодом.</span><span class="sxs-lookup"><span data-stu-id="ba5f9-140">The following example shows how to opt into increased resilience against incorrect platform invoke declarations for an application, at the cost of slower transitions between managed and unmanaged code.</span></span>

```xml
<configuration>
   <runtime>
      <NetFx40_PInvokeStackResilience enabled="1"/>
   </runtime>
</configuration>
```

## <a name="see-also"></a><span data-ttu-id="ba5f9-141">См. также</span><span class="sxs-lookup"><span data-stu-id="ba5f9-141">See also</span></span>

- [<span data-ttu-id="ba5f9-142">Схема параметров среды выполнения</span><span class="sxs-lookup"><span data-stu-id="ba5f9-142">Runtime Settings Schema</span></span>](index.md)
- [<span data-ttu-id="ba5f9-143">Схема файла конфигурации</span><span class="sxs-lookup"><span data-stu-id="ba5f9-143">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="ba5f9-144">pInvokeStackImbalance</span><span class="sxs-lookup"><span data-stu-id="ba5f9-144">pInvokeStackImbalance</span></span>](../../../debug-trace-profile/pinvokestackimbalance-mda.md)
