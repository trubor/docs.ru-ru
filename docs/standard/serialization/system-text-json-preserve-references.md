---
title: Как сохранять ссылки с помощью System.Text.Json
description: Узнайте, как в .NET сохранять ссылки и обрабатывать циклические ссылки при сериализации в JSON и десериализации из JSON.
ms.date: 12/09/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
zone_pivot_groups: dotnet-version
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: d358c953c0979ca097c080fcd750d5ef95b07de0
ms.sourcegitcommit: 81f1bba2c97a67b5ca76bcc57b37333ffca60c7b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/10/2020
ms.locfileid: "97008738"
---
# <a name="how-to-preserve-references-and-handle-circular-references-with-no-locsystemtextjson"></a><span data-ttu-id="60ff6-103">Сохранение ссылок и обработка циклических ссылок с помощью System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="60ff6-103">How to preserve references and handle circular references with System.Text.Json</span></span>

::: zone pivot="dotnet-5-0"

<span data-ttu-id="60ff6-104">Для сохранения ссылок и обработки циклических ссылок задайте для свойства <xref:System.Text.Json.JsonSerializerOptions.ReferenceHandler%2A> значение <xref:System.Text.Json.Serialization.ReferenceHandler.Preserve%2A>.</span><span class="sxs-lookup"><span data-stu-id="60ff6-104">To preserve references and handle circular references, set <xref:System.Text.Json.JsonSerializerOptions.ReferenceHandler%2A> to <xref:System.Text.Json.Serialization.ReferenceHandler.Preserve%2A>.</span></span> <span data-ttu-id="60ff6-105">Этот параметр приводит к следующему поведению:</span><span class="sxs-lookup"><span data-stu-id="60ff6-105">This setting causes the following behavior:</span></span>

* <span data-ttu-id="60ff6-106">При сериализации:</span><span class="sxs-lookup"><span data-stu-id="60ff6-106">On serialize:</span></span>

  <span data-ttu-id="60ff6-107">При написании сложных типов сериализатор также записывает свойства метаданных (`$id`, `$values`, а также `$ref`).</span><span class="sxs-lookup"><span data-stu-id="60ff6-107">When writing complex types, the serializer also writes metadata properties (`$id`, `$values`, and `$ref`).</span></span>

* <span data-ttu-id="60ff6-108">При десериализации:</span><span class="sxs-lookup"><span data-stu-id="60ff6-108">On deserialize:</span></span>

  <span data-ttu-id="60ff6-109">Ожидаются метаданные (не обязательно), и десериализатор пытается их распознать.</span><span class="sxs-lookup"><span data-stu-id="60ff6-109">Metadata is expected (although not mandatory), and the deserializer tries to understand it.</span></span>

<span data-ttu-id="60ff6-110">В следующем коде показано использование параметра `Preserve`.</span><span class="sxs-lookup"><span data-stu-id="60ff6-110">The following code illustrates use of the `Preserve` setting.</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/PreserveReferences.cs" highlight="34":::

<span data-ttu-id="60ff6-111">Эту функцию нельзя использовать для сохранения типов значений или неизменяемых типов.</span><span class="sxs-lookup"><span data-stu-id="60ff6-111">This feature can't be used to preserve value types or immutable types.</span></span> <span data-ttu-id="60ff6-112">При десериализации экземпляр неизменяемого типа создается после считывания всех полезных данных.</span><span class="sxs-lookup"><span data-stu-id="60ff6-112">On deserialization, the instance of an immutable type is created after the entire payload is read.</span></span> <span data-ttu-id="60ff6-113">Поэтому для того же экземпляра невозможно будет выполнить десериализацию, если в полезных данных JSON появляется ссылка на него.</span><span class="sxs-lookup"><span data-stu-id="60ff6-113">So it would be impossible to deserialize the same instance if a reference to it appears within the JSON payload.</span></span>

<span data-ttu-id="60ff6-114">Для типов значений, неизменяемых типов и массивов ссылочные метаданные не сериализуются.</span><span class="sxs-lookup"><span data-stu-id="60ff6-114">For value types, immutable types, and arrays, no reference metadata is serialized.</span></span> <span data-ttu-id="60ff6-115">Если при десериализации было найдено `$ref` или `$id`, создается исключение.</span><span class="sxs-lookup"><span data-stu-id="60ff6-115">On deserialization, an exception is thrown if `$ref` or `$id` is found.</span></span> <span data-ttu-id="60ff6-116">Однако типы значений игнорируют `$id` (и `$values` для коллекций), чтобы позволить десериализацию полезных данных, сериализованных с помощью Newtonsoft.Json.</span><span class="sxs-lookup"><span data-stu-id="60ff6-116">However, value types ignore `$id` (and `$values` in the case of collections) to make it possible to deserialize payloads that were serialized by using Newtonsoft.Json.</span></span>  <span data-ttu-id="60ff6-117">Newtonsoft.Json выполняет сериализацию метаданных для таких типов.</span><span class="sxs-lookup"><span data-stu-id="60ff6-117">Newtonsoft.Json does serialize metadata for such types.</span></span>

<span data-ttu-id="60ff6-118">Для определения равенства объектов System.Text.Json использует свойство <xref:System.Collections.Generic.ReferenceEqualityComparer.Instance%2A?displayProperty=nameWithType>, которое при сравнении двух экземпляров объекта использует эквивалентность ссылок (<xref:System.Object.ReferenceEquals(System.Object,System.Object)?displayProperty=nameWithType>), а не эквивалентность значений (<xref:System.Object.Equals(System.Object)?displayProperty=nameWithType>).</span><span class="sxs-lookup"><span data-stu-id="60ff6-118">To determine if objects are equal, System.Text.Json uses <xref:System.Collections.Generic.ReferenceEqualityComparer.Instance%2A?displayProperty=nameWithType>, which uses reference equality (<xref:System.Object.ReferenceEquals(System.Object,System.Object)?displayProperty=nameWithType>) instead of value equality (<xref:System.Object.Equals(System.Object)?displayProperty=nameWithType> when comparing two object instances.</span></span>

<span data-ttu-id="60ff6-119">Больше о сериализации и десериализации ссылок см. в статье <xref:System.Text.Json.Serialization.ReferenceHandler.Preserve%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="60ff6-119">For more information about how references are serialized and deserialized, see <xref:System.Text.Json.Serialization.ReferenceHandler.Preserve%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="60ff6-120">Класс <xref:System.Text.Json.Serialization.ReferenceResolver> определяет поведение сохранения ссылок при сериализации и десериализации.</span><span class="sxs-lookup"><span data-stu-id="60ff6-120">The <xref:System.Text.Json.Serialization.ReferenceResolver> class defines the behavior of preserving references on serialization and deserialization.</span></span> <span data-ttu-id="60ff6-121">Создайте производный класс, чтобы указать настраиваемое поведение.</span><span class="sxs-lookup"><span data-stu-id="60ff6-121">Create a derived class to specify custom behavior.</span></span> <span data-ttu-id="60ff6-122">Пример см. в статье [GuidReferenceResolver](https://github.com/dotnet/docs/blob/9d5e88edbd7f12be463775ffebbf07ac8415fe18/docs/standard/serialization/snippets/system-text-json-how-to-5-0/csharp/GuidReferenceResolverExample.cs).</span><span class="sxs-lookup"><span data-stu-id="60ff6-122">For an example, see [GuidReferenceResolver](https://github.com/dotnet/docs/blob/9d5e88edbd7f12be463775ffebbf07ac8415fe18/docs/standard/serialization/snippets/system-text-json-how-to-5-0/csharp/GuidReferenceResolverExample.cs).</span></span>

::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="60ff6-123">System.Text.Json в .NET Core 3.1 поддерживает сериализацию только по значению и вызывает исключение для циклических ссылок.</span><span class="sxs-lookup"><span data-stu-id="60ff6-123">System.Text.Json in .NET Core 3.1 only supports serialization by value and throws an exception for circular references.</span></span>
::: zone-end

## <a name="see-also"></a><span data-ttu-id="60ff6-124">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="60ff6-124">See also</span></span>

* [<span data-ttu-id="60ff6-125">Общие сведения о System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="60ff6-125">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="60ff6-126">Практическое руководство. Сериализация и десериализация JSON</span><span class="sxs-lookup"><span data-stu-id="60ff6-126">How to serialize and deserialize JSON</span></span>](system-text-json-how-to.md)
* [<span data-ttu-id="60ff6-127">Создание экземпляров JsonSerializerOptions</span><span class="sxs-lookup"><span data-stu-id="60ff6-127">Instantiate JsonSerializerOptions instances</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="60ff6-128">Сопоставление без учета регистра</span><span class="sxs-lookup"><span data-stu-id="60ff6-128">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="60ff6-129">Настройка имен и значений свойств</span><span class="sxs-lookup"><span data-stu-id="60ff6-129">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="60ff6-130">Игнорирование свойств</span><span class="sxs-lookup"><span data-stu-id="60ff6-130">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="60ff6-131">Применение недействительного кода JSON</span><span class="sxs-lookup"><span data-stu-id="60ff6-131">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="60ff6-132">Обработка переполнения JSON</span><span class="sxs-lookup"><span data-stu-id="60ff6-132">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="60ff6-133">Неизменяемые типы и непубличные методы доступа</span><span class="sxs-lookup"><span data-stu-id="60ff6-133">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="60ff6-134">Полиморфная сериализация</span><span class="sxs-lookup"><span data-stu-id="60ff6-134">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* [<span data-ttu-id="60ff6-135">Миграция из Newtonsoft.Json в System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="60ff6-135">Migrate from Newtonsoft.Json to System.Text.Json</span></span>](system-text-json-migrate-from-newtonsoft-how-to.md)
* [<span data-ttu-id="60ff6-136">Настройка кодировки символов</span><span class="sxs-lookup"><span data-stu-id="60ff6-136">Customize character encoding</span></span>](system-text-json-character-encoding.md)
* [<span data-ttu-id="60ff6-137">Написание пользовательских сериализаторов и десериализаторов</span><span class="sxs-lookup"><span data-stu-id="60ff6-137">Write custom serializers and deserializers</span></span>](write-custom-serializer-deserializer.md)
* [<span data-ttu-id="60ff6-138">Написание пользовательских преобразователей для сериализации JSON</span><span class="sxs-lookup"><span data-stu-id="60ff6-138">Write custom converters for JSON serialization</span></span>](system-text-json-converters-how-to.md)
* [<span data-ttu-id="60ff6-139">Поддержка DateTime и DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="60ff6-139">DateTime and DateTimeOffset support</span></span>](../datetime/system-text-json-support.md)
* <span data-ttu-id="60ff6-140">[Справочник по API System.Text.Json](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="60ff6-140">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
* <span data-ttu-id="60ff6-141">[Справочник по API System.Text.Json.Serialization](xref:System.Text.Json.Serialization)</span><span class="sxs-lookup"><span data-stu-id="60ff6-141">[System.Text.Json.Serialization API reference](xref:System.Text.Json.Serialization)</span></span>
