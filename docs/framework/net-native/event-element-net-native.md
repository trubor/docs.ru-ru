---
description: 'Дополнительные сведения об <Event> элементе: Element (.NET Native)'
title: <Event> Элемент (.NET Native)
ms.date: 03/30/2017
ms.assetid: e53b029c-9d6d-4c0a-9cdc-5cfca8a5ca47
ms.openlocfilehash: 16ef4376e5953da514598bd7cdcbe0c196ee4da5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99747885"
---
# <a name="event-element-net-native"></a><span data-ttu-id="f3bf5-103">\<Event> Элемент (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="f3bf5-103">\<Event> Element (.NET Native)</span></span>

<span data-ttu-id="f3bf5-104">Применяет политику отражения среды выполнения к событию.</span><span class="sxs-lookup"><span data-stu-id="f3bf5-104">Applies runtime reflection policy to an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3bf5-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f3bf5-105">Syntax</span></span>  
  
```xml  
<Event Name="event_name"
       Browse="policy_type"
       Dynamic="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f3bf5-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="f3bf5-106">Attributes and Elements</span></span>  

 <span data-ttu-id="f3bf5-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="f3bf5-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f3bf5-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="f3bf5-108">Attributes</span></span>  
  
|<span data-ttu-id="f3bf5-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="f3bf5-109">Attribute</span></span>|<span data-ttu-id="f3bf5-110">Тип атрибута</span><span class="sxs-lookup"><span data-stu-id="f3bf5-110">Attribute type</span></span>|<span data-ttu-id="f3bf5-111">Описание</span><span class="sxs-lookup"><span data-stu-id="f3bf5-111">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="f3bf5-112">Общие сведения</span><span class="sxs-lookup"><span data-stu-id="f3bf5-112">General</span></span>|<span data-ttu-id="f3bf5-113">Обязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="f3bf5-113">Required attribute.</span></span> <span data-ttu-id="f3bf5-114">Задает имя события.</span><span class="sxs-lookup"><span data-stu-id="f3bf5-114">Specifies the event name.</span></span>|  
|`Browse`|<span data-ttu-id="f3bf5-115">Отражение</span><span class="sxs-lookup"><span data-stu-id="f3bf5-115">Reflection</span></span>|<span data-ttu-id="f3bf5-116">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="f3bf5-116">Optional attribute.</span></span> <span data-ttu-id="f3bf5-117">Определяет запрос для получения сведений о событиях или перечисляет события, но не включает динамический доступ во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="f3bf5-117">Controls querying for information about or enumerating the event but does not enable any dynamic access at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="f3bf5-118">Отражение</span><span class="sxs-lookup"><span data-stu-id="f3bf5-118">Reflection</span></span>|<span data-ttu-id="f3bf5-119">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="f3bf5-119">Optional attribute.</span></span> <span data-ttu-id="f3bf5-120">Управляет доступом среды выполнения к событию для включения динамического программирования.</span><span class="sxs-lookup"><span data-stu-id="f3bf5-120">Controls runtime access to the event to enable dynamic programming.</span></span> <span data-ttu-id="f3bf5-121">Эта политика гарантирует, что события могут обрабатываться динамически во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="f3bf5-121">This policy ensures that an event can be handled dynamically at run time.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="f3bf5-122">Name - атрибут</span><span class="sxs-lookup"><span data-stu-id="f3bf5-122">Name attribute</span></span>  
  
|<span data-ttu-id="f3bf5-123">Значение</span><span class="sxs-lookup"><span data-stu-id="f3bf5-123">Value</span></span>|<span data-ttu-id="f3bf5-124">Описание</span><span class="sxs-lookup"><span data-stu-id="f3bf5-124">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f3bf5-125">*method_name*</span><span class="sxs-lookup"><span data-stu-id="f3bf5-125">*method_name*</span></span>|<span data-ttu-id="f3bf5-126">Имя события.</span><span class="sxs-lookup"><span data-stu-id="f3bf5-126">The event name.</span></span> <span data-ttu-id="f3bf5-127">Тип события определяется родительским [\<Type>](type-element-net-native.md) [\<TypeInstantiation>](typeinstantiation-element-net-native.md) элементом или.</span><span class="sxs-lookup"><span data-stu-id="f3bf5-127">The type of the event is defined by the parent [\<Type>](type-element-net-native.md) or [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="f3bf5-128">Все остальные атрибуты</span><span class="sxs-lookup"><span data-stu-id="f3bf5-128">All other attributes</span></span>  
  
|<span data-ttu-id="f3bf5-129">Значение</span><span class="sxs-lookup"><span data-stu-id="f3bf5-129">Value</span></span>|<span data-ttu-id="f3bf5-130">Описание</span><span class="sxs-lookup"><span data-stu-id="f3bf5-130">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f3bf5-131">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="f3bf5-131">*policy_setting*</span></span>|<span data-ttu-id="f3bf5-132">Параметр, применяемый к этому типу политики для события.</span><span class="sxs-lookup"><span data-stu-id="f3bf5-132">The setting to apply to this policy type for the event.</span></span> <span data-ttu-id="f3bf5-133">Допустимые значения: `Auto`, `Excluded`, `Included` и `Required`.</span><span class="sxs-lookup"><span data-stu-id="f3bf5-133">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="f3bf5-134">Дополнительные сведения см. в разделе [Параметры политики директив среды выполнения](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="f3bf5-134">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f3bf5-135">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="f3bf5-135">Child Elements</span></span>  

 <span data-ttu-id="f3bf5-136">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="f3bf5-136">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f3bf5-137">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="f3bf5-137">Parent Elements</span></span>  
  
|<span data-ttu-id="f3bf5-138">Элемент</span><span class="sxs-lookup"><span data-stu-id="f3bf5-138">Element</span></span>|<span data-ttu-id="f3bf5-139">Описание</span><span class="sxs-lookup"><span data-stu-id="f3bf5-139">Description</span></span>|  
|-------------|-----------------|  
|[\<Type>](type-element-net-native.md)|<span data-ttu-id="f3bf5-140">Применяет политику отражения к типу и всем его членам.</span><span class="sxs-lookup"><span data-stu-id="f3bf5-140">Applies reflection policy to a type and all its members.</span></span>|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|<span data-ttu-id="f3bf5-141">Применяет политику отражения к сконструированному универсальному типу и всем его членам.</span><span class="sxs-lookup"><span data-stu-id="f3bf5-141">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f3bf5-142">Remarks</span><span class="sxs-lookup"><span data-stu-id="f3bf5-142">Remarks</span></span>  

 <span data-ttu-id="f3bf5-143">Если политика события не определена явно, оно наследует политику среды выполнения своего родительского элемента.</span><span class="sxs-lookup"><span data-stu-id="f3bf5-143">If an event's policy is not explicitly defined, it inherits the runtime policy of its parent element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3bf5-144">См. также</span><span class="sxs-lookup"><span data-stu-id="f3bf5-144">See also</span></span>

- [<span data-ttu-id="f3bf5-145">Ссылка на файл конфигурации директив среды выполнения (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="f3bf5-145">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="f3bf5-146">Элементы директив среды выполнения</span><span class="sxs-lookup"><span data-stu-id="f3bf5-146">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="f3bf5-147">Параметры политики директив среды выполнения</span><span class="sxs-lookup"><span data-stu-id="f3bf5-147">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
