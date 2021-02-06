---
description: 'Дополнительные сведения: <bindings>'
title: <bindings>
ms.date: 01/22/2018
ms.assetid: b62cd369-5409-4030-8490-9759a462dd3a
ms.openlocfilehash: 2cf5b42b8478e34a528cd36435023cac62bf0c1e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99639384"
---
# \<bindings>

<span data-ttu-id="89173-102">Элемент можно использовать `bindings` для настройки коллекции стандартных и пользовательских привязок для Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="89173-102">You can use the `bindings` element to configure a collection of standard and custom bindings for Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="89173-103">Каждый элемент коллекции представляет собой элемент `binding`, который может быть идентифицирован по своему уникальному имени `name`.</span><span class="sxs-lookup"><span data-stu-id="89173-103">Each entry is a `binding` element that can be identified by its unique `name`.</span></span> <span data-ttu-id="89173-104">Службы используют привязки, связывая их с помощью параметра `name`.</span><span class="sxs-lookup"><span data-stu-id="89173-104">Services use bindings by linking them using the `name`.</span></span> <span data-ttu-id="89173-105">Начиная с платформа .NET Framework 4, привязки и поведения не обязательно должны иметь имя.</span><span class="sxs-lookup"><span data-stu-id="89173-105">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="89173-106">Дополнительные сведения о конфигурации по умолчанию и привязках и поведении, которые не имеют имен, см. в разделе [упрощенная конфигурация](../../../wcf/simplified-configuration.md) и [упрощенная конфигурация для служб WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="89173-106">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>

## <a name="system-provided-bindings"></a><span data-ttu-id="89173-107">Привязки, предоставляемые системой</span><span class="sxs-lookup"><span data-stu-id="89173-107">System-provided bindings</span></span>

<span data-ttu-id="89173-108">Привязки, предоставляемые системой, скрывают сложность стека обмена сообщениями WCF.</span><span class="sxs-lookup"><span data-stu-id="89173-108">System-provided bindings hide the complexity of the WCF messaging stack.</span></span> <span data-ttu-id="89173-109">Приложениям, использующим предоставляемые системой привязки, не требуется полный контроль над стеком.</span><span class="sxs-lookup"><span data-stu-id="89173-109">Applications using system-provided bindings do not require full control over the stack.</span></span> <span data-ttu-id="89173-110">Атрибутами в каждой привязке, предоставляемой системой, являются атрибуты, наиболее подходящие для области применения привязки.</span><span class="sxs-lookup"><span data-stu-id="89173-110">The attributes exposed on each system-provided binding are the ones most appropriate for the usage scenario the binding addresses.</span></span>

<span data-ttu-id="89173-111">В разделе конфигурации для каждой привязки, предоставляемой системой, можно определить несколько конфигураций, используемых для настройки привязки.</span><span class="sxs-lookup"><span data-stu-id="89173-111">The configuration section for each system-provided binding can define several configurations used to configure the binding.</span></span> <span data-ttu-id="89173-112">Каждая конфигурация идентифицируется по уникальному имени.</span><span class="sxs-lookup"><span data-stu-id="89173-112">Each configuration is identified by a unique name.</span></span>

<span data-ttu-id="89173-113">Невозможно добавить элементы или атрибуты к привязке, предоставляемой системой.</span><span class="sxs-lookup"><span data-stu-id="89173-113">It isn't possible to add elements or attributes to a system-provided binding.</span></span> <span data-ttu-id="89173-114">Для этого следует реализовать пользовательскую привязку, как описано в разделе [пользовательские привязки](#custom-bindings) .</span><span class="sxs-lookup"><span data-stu-id="89173-114">To do so, you should implement a custom binding as described in the [Custom bindings](#custom-bindings) section.</span></span> <span data-ttu-id="89173-115">Можно определить пользовательскую привязку, которая имитирует предоставляемую системой привязку и добавляет несколько параметров, которые пользовательское приложение хочет контролировать.</span><span class="sxs-lookup"><span data-stu-id="89173-115">It's possible to define a custom binding that mimics a system-provided binding perfectly and adds a few settings the user application wants to have control over.</span></span>  

<span data-ttu-id="89173-116">Список привязок, предоставляемых системой, см. в разделе [привязки, предоставляемые системой](../../../wcf/system-provided-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="89173-116">For a list of system-provided bindings, see [System-Provided Bindings](../../../wcf/system-provided-bindings.md).</span></span>

## <a name="custom-bindings"></a><span data-ttu-id="89173-117">Пользовательские привязки</span><span class="sxs-lookup"><span data-stu-id="89173-117">Custom bindings</span></span>

<span data-ttu-id="89173-118">Пользовательские привязки предоставляют полный контроль над стеком обмена сообщениями WCF.</span><span class="sxs-lookup"><span data-stu-id="89173-118">Custom bindings provide full control over the WCF messaging stack.</span></span> <span data-ttu-id="89173-119">Отдельная привязка определяет стек обмена сообщениями, задавая элементы конфигурации для элементов стека в том порядке, в котором они присутствуют в стеке.</span><span class="sxs-lookup"><span data-stu-id="89173-119">An individual binding defines the message stack by specifying the configuration elements for the stack elements in the order they appear on the stack.</span></span> <span data-ttu-id="89173-120">Каждый элемент определяет и настраивает один элемент стека.</span><span class="sxs-lookup"><span data-stu-id="89173-120">Each element defines and configures one element of the stack.</span></span> <span data-ttu-id="89173-121">В каждой пользовательской привязке должен быть один и только один элемент `transport`.</span><span class="sxs-lookup"><span data-stu-id="89173-121">There must be one and only one `transport` element in each custom binding.</span></span> <span data-ttu-id="89173-122">Без этого элемента стек обмена сообщениями является неполным.</span><span class="sxs-lookup"><span data-stu-id="89173-122">Without this element, the messaging stack is incomplete.</span></span>

<span data-ttu-id="89173-123">Важен порядок, в котором элементы присутствуют в стеке, поскольку именно в этом порядке к сообщению применяются операции.</span><span class="sxs-lookup"><span data-stu-id="89173-123">The order in which elements appear in the stack matters, because it is the order in which operations are applied to the message.</span></span> <span data-ttu-id="89173-124">Необходим следующий порядок элементов стека:</span><span class="sxs-lookup"><span data-stu-id="89173-124">The required order of stack elements is the following:</span></span>  

1. <span data-ttu-id="89173-125">Транзакции (необязательный)</span><span class="sxs-lookup"><span data-stu-id="89173-125">Transactions (optional)</span></span>  

2. <span data-ttu-id="89173-126">Надежный обмен сообщениями (необязательно)</span><span class="sxs-lookup"><span data-stu-id="89173-126">Reliable messaging (optional)</span></span>  

3. <span data-ttu-id="89173-127">Безопасность (необязательный)</span><span class="sxs-lookup"><span data-stu-id="89173-127">Security (optional)</span></span>  

4. <span data-ttu-id="89173-128">Кодировщик</span><span class="sxs-lookup"><span data-stu-id="89173-128">Encoder</span></span>  

5. <span data-ttu-id="89173-129">Транспорт</span><span class="sxs-lookup"><span data-stu-id="89173-129">Transport</span></span>  

 <span data-ttu-id="89173-130">Пользовательские привязки идентифицируются по атрибуту `name`.</span><span class="sxs-lookup"><span data-stu-id="89173-130">Custom bindings are identified by their `name` attribute.</span></span> <span data-ttu-id="89173-131">Дополнительные сведения о пользовательских привязках см. в разделе [пользовательские привязки](../../../wcf/extending/custom-bindings.md).</span><span class="sxs-lookup"><span data-stu-id="89173-131">For more information on custom bindings, see [Custom Bindings](../../../wcf/extending/custom-bindings.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="89173-132">См. также</span><span class="sxs-lookup"><span data-stu-id="89173-132">See also</span></span>

- <xref:System.ServiceModel.Configuration.BindingsSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.Binding?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.BindingElement?displayProperty=nameWithType>
- [<span data-ttu-id="89173-133">Привязки</span><span class="sxs-lookup"><span data-stu-id="89173-133">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="89173-134">Пользовательские привязки</span><span class="sxs-lookup"><span data-stu-id="89173-134">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
