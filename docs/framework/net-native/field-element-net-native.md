---
description: 'Дополнительные сведения об <Field> элементе: Element (.NET Native)'
title: <Field> Элемент (.NET Native)
ms.date: 03/30/2017
ms.assetid: 6a14125f-1a8d-41a1-8a32-659ca0ad12de
ms.openlocfilehash: 1f8c8b6720fb90bdc5855da7b17694253bbb7629
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99747846"
---
# <a name="field-element-net-native"></a><span data-ttu-id="56cdd-103">\<Field> Элемент (.NET Native)</span><span class="sxs-lookup"><span data-stu-id="56cdd-103">\<Field> Element (.NET Native)</span></span>

<span data-ttu-id="56cdd-104">Применяет политику отражения среды выполнения к полю.</span><span class="sxs-lookup"><span data-stu-id="56cdd-104">Applies runtime reflection policy to a field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="56cdd-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="56cdd-105">Syntax</span></span>  
  
```xml  
<Field Name="field_name"  
       Browse="policy_type"  
       Dynamic="policy_type"  
       Serialize="policy_type" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="56cdd-106">Атрибуты и элементы</span><span class="sxs-lookup"><span data-stu-id="56cdd-106">Attributes and Elements</span></span>  

 <span data-ttu-id="56cdd-107">В следующих разделах описаны атрибуты, дочерние и родительские элементы.</span><span class="sxs-lookup"><span data-stu-id="56cdd-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="56cdd-108">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="56cdd-108">Attributes</span></span>  
  
|<span data-ttu-id="56cdd-109">Атрибут</span><span class="sxs-lookup"><span data-stu-id="56cdd-109">Attribute</span></span>|<span data-ttu-id="56cdd-110">Тип атрибута</span><span class="sxs-lookup"><span data-stu-id="56cdd-110">Attribute type</span></span>|<span data-ttu-id="56cdd-111">Описание</span><span class="sxs-lookup"><span data-stu-id="56cdd-111">Description</span></span>|  
|---------------|--------------------|-----------------|  
|`Name`|<span data-ttu-id="56cdd-112">Общие сведения</span><span class="sxs-lookup"><span data-stu-id="56cdd-112">General</span></span>|<span data-ttu-id="56cdd-113">Обязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="56cdd-113">Required attribute.</span></span> <span data-ttu-id="56cdd-114">Определяет имя поля.</span><span class="sxs-lookup"><span data-stu-id="56cdd-114">Specifies the field name.</span></span>|  
|`Browse`|<span data-ttu-id="56cdd-115">Отражение</span><span class="sxs-lookup"><span data-stu-id="56cdd-115">Reflection</span></span>|<span data-ttu-id="56cdd-116">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="56cdd-116">Optional attribute.</span></span> <span data-ttu-id="56cdd-117">Определяет запрос для получения сведений о поле или перечисляет поле, но не включает динамический доступ во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="56cdd-117">Controls querying for information about or enumerating the field but does not enable any dynamic access at run time.</span></span>|  
|`Dynamic`|<span data-ttu-id="56cdd-118">Отражение</span><span class="sxs-lookup"><span data-stu-id="56cdd-118">Reflection</span></span>|<span data-ttu-id="56cdd-119">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="56cdd-119">Optional attribute.</span></span> <span data-ttu-id="56cdd-120">Управляет доступом среды выполнения к полю для включения динамического программирования.</span><span class="sxs-lookup"><span data-stu-id="56cdd-120">Controls runtime access to the field to enable dynamic programming.</span></span> <span data-ttu-id="56cdd-121">Эта политика гарантирует, что поле можно задать или получить динамически во время выполнения.</span><span class="sxs-lookup"><span data-stu-id="56cdd-121">This policy ensures that a field can be set or retrieved dynamically at run time.</span></span>|  
|`Serialize`|<span data-ttu-id="56cdd-122">Сериализация</span><span class="sxs-lookup"><span data-stu-id="56cdd-122">Serialization</span></span>|<span data-ttu-id="56cdd-123">Необязательный атрибут.</span><span class="sxs-lookup"><span data-stu-id="56cdd-123">Optional attribute.</span></span> <span data-ttu-id="56cdd-124">Управляет доступом среды выполнения к полю, чтобы включить экземпляры типов, предназначенных для сериализации в таких библиотеках, как, например, сериализатор Newtonsoft JSON или для привязки данных.</span><span class="sxs-lookup"><span data-stu-id="56cdd-124">Controls runtime access to a field to enable type instances to be serialized by libraries such as the Newtonsoft JSON serializer or to be used for data binding.</span></span>|  
  
## <a name="name-attribute"></a><span data-ttu-id="56cdd-125">Name - атрибут</span><span class="sxs-lookup"><span data-stu-id="56cdd-125">Name attribute</span></span>  
  
|<span data-ttu-id="56cdd-126">Значение</span><span class="sxs-lookup"><span data-stu-id="56cdd-126">Value</span></span>|<span data-ttu-id="56cdd-127">Описание</span><span class="sxs-lookup"><span data-stu-id="56cdd-127">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="56cdd-128">*method_name*</span><span class="sxs-lookup"><span data-stu-id="56cdd-128">*method_name*</span></span>|<span data-ttu-id="56cdd-129">Имя поля.</span><span class="sxs-lookup"><span data-stu-id="56cdd-129">The field name.</span></span> <span data-ttu-id="56cdd-130">Тип поля определяется родительским [\<Type>](type-element-net-native.md) [\<TypeInstantiation>](typeinstantiation-element-net-native.md) элементом или.</span><span class="sxs-lookup"><span data-stu-id="56cdd-130">The type of the field is defined by the parent [\<Type>](type-element-net-native.md) or [\<TypeInstantiation>](typeinstantiation-element-net-native.md) element.</span></span>|  
  
## <a name="all-other-attributes"></a><span data-ttu-id="56cdd-131">Все остальные атрибуты</span><span class="sxs-lookup"><span data-stu-id="56cdd-131">All other attributes</span></span>  
  
|<span data-ttu-id="56cdd-132">Значение</span><span class="sxs-lookup"><span data-stu-id="56cdd-132">Value</span></span>|<span data-ttu-id="56cdd-133">Описание</span><span class="sxs-lookup"><span data-stu-id="56cdd-133">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="56cdd-134">*policy_setting*</span><span class="sxs-lookup"><span data-stu-id="56cdd-134">*policy_setting*</span></span>|<span data-ttu-id="56cdd-135">Параметр, применяемый к этому типу политики для поля.</span><span class="sxs-lookup"><span data-stu-id="56cdd-135">The setting to apply to this policy type for the field.</span></span> <span data-ttu-id="56cdd-136">Допустимые значения: `Auto`, `Excluded`, `Included` и `Required`.</span><span class="sxs-lookup"><span data-stu-id="56cdd-136">Possible values are `Auto`, `Excluded`, `Included`, and `Required`.</span></span> <span data-ttu-id="56cdd-137">Дополнительные сведения см. в разделе [Параметры политики директив среды выполнения](runtime-directive-policy-settings.md).</span><span class="sxs-lookup"><span data-stu-id="56cdd-137">For more information, see [Runtime Directive Policy Settings](runtime-directive-policy-settings.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="56cdd-138">Дочерние элементы</span><span class="sxs-lookup"><span data-stu-id="56cdd-138">Child Elements</span></span>  

 <span data-ttu-id="56cdd-139">Отсутствует.</span><span class="sxs-lookup"><span data-stu-id="56cdd-139">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="56cdd-140">Родительские элементы</span><span class="sxs-lookup"><span data-stu-id="56cdd-140">Parent Elements</span></span>  
  
|<span data-ttu-id="56cdd-141">Элемент</span><span class="sxs-lookup"><span data-stu-id="56cdd-141">Element</span></span>|<span data-ttu-id="56cdd-142">Описание</span><span class="sxs-lookup"><span data-stu-id="56cdd-142">Description</span></span>|  
|-------------|-----------------|  
|[\<Type>](type-element-net-native.md)|<span data-ttu-id="56cdd-143">Применяет политику отражения к типу и всем его членам.</span><span class="sxs-lookup"><span data-stu-id="56cdd-143">Applies reflection policy to a type and all its members.</span></span>|  
|[\<TypeInstantiation>](typeinstantiation-element-net-native.md)|<span data-ttu-id="56cdd-144">Применяет политику отражения к сконструированному универсальному типу и всем его членам.</span><span class="sxs-lookup"><span data-stu-id="56cdd-144">Applies reflection policy to a constructed generic type and all its members.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="56cdd-145">Remarks</span><span class="sxs-lookup"><span data-stu-id="56cdd-145">Remarks</span></span>  

 <span data-ttu-id="56cdd-146">Если политика поля не определена явно, оно наследует политику среды выполнения своего родительского элемента.</span><span class="sxs-lookup"><span data-stu-id="56cdd-146">If a field's policy is not explicitly defined, it inherits the runtime policy of its parent element.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56cdd-147">См. также</span><span class="sxs-lookup"><span data-stu-id="56cdd-147">See also</span></span>

- [<span data-ttu-id="56cdd-148">Элементы директив среды выполнения</span><span class="sxs-lookup"><span data-stu-id="56cdd-148">Runtime Directive Elements</span></span>](runtime-directive-elements.md)
- [<span data-ttu-id="56cdd-149">Ссылка на файл конфигурации директив среды выполнения (rd.xml)</span><span class="sxs-lookup"><span data-stu-id="56cdd-149">Runtime Directives (rd.xml) Configuration File Reference</span></span>](runtime-directives-rd-xml-configuration-file-reference.md)
- [<span data-ttu-id="56cdd-150">Параметры политики директив среды выполнения</span><span class="sxs-lookup"><span data-stu-id="56cdd-150">Runtime Directive Policy Settings</span></span>](runtime-directive-policy-settings.md)
