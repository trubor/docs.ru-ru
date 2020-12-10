---
title: Как сохранять ссылки с помощью System.Text.Json
description: Узнайте, как в .NET сохранять ссылки и обрабатывать циклические ссылки при сериализации в JSON и десериализации из JSON.
ms.date: 11/30/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
zone_pivot_groups: dotnet-version
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 9254ca261c7d748c04c311fa56359014f752ff31
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/01/2020
ms.locfileid: "96439837"
---
# <a name="how-to-handle-circular-references-with-no-locsystemtextjson"></a><span data-ttu-id="51858-103">Как обрабатывать циклические ссылки с помощью System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="51858-103">How to handle circular references with System.Text.Json</span></span>

<span data-ttu-id="51858-104">Из этой статьи вы узнаете, как обрабатывать циклические ссылки с помощью пространства имен `System.Text.Json`.</span><span class="sxs-lookup"><span data-stu-id="51858-104">In this article, you will learn how to handle circular references with the `System.Text.Json` namespace.</span></span>

## <a name="preserve-references-and-handle-circular-references"></a><span data-ttu-id="51858-105">Сохранение ссылок и обработка циклических ссылок</span><span class="sxs-lookup"><span data-stu-id="51858-105">Preserve references and handle circular references</span></span>

::: zone pivot="dotnet-5-0"

<span data-ttu-id="51858-106">Для сохранения ссылок и обработки циклических ссылок задайте для свойства <xref:System.Text.Json.JsonSerializerOptions.ReferenceHandler%2A> значение <xref:System.Text.Json.Serialization.ReferenceHandler.Preserve%2A>.</span><span class="sxs-lookup"><span data-stu-id="51858-106">To preserve references and handle circular references, set <xref:System.Text.Json.JsonSerializerOptions.ReferenceHandler%2A> to <xref:System.Text.Json.Serialization.ReferenceHandler.Preserve%2A>.</span></span> <span data-ttu-id="51858-107">Этот параметр приводит к следующему поведению:</span><span class="sxs-lookup"><span data-stu-id="51858-107">This setting causes the following behavior:</span></span>

* <span data-ttu-id="51858-108">При сериализации:</span><span class="sxs-lookup"><span data-stu-id="51858-108">On serialize:</span></span>

  <span data-ttu-id="51858-109">При написании сложных типов сериализатор также записывает свойства метаданных (`$id`, `$values`, а также `$ref`).</span><span class="sxs-lookup"><span data-stu-id="51858-109">When writing complex types, the serializer also writes metadata properties (`$id`, `$values`, and `$ref`).</span></span>

* <span data-ttu-id="51858-110">При десериализации:</span><span class="sxs-lookup"><span data-stu-id="51858-110">On deserialize:</span></span>

  <span data-ttu-id="51858-111">Ожидаются метаданные (не обязательно), и десериализатор пытается их распознать.</span><span class="sxs-lookup"><span data-stu-id="51858-111">Metadata is expected (although not mandatory), and the deserializer tries to understand it.</span></span>

<span data-ttu-id="51858-112">В следующем коде показано использование параметра `Preserve`.</span><span class="sxs-lookup"><span data-stu-id="51858-112">The following code illustrates use of the `Preserve` setting.</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/PreserveReferences.cs" highlight="34":::

<span data-ttu-id="51858-113">Эту функцию нельзя использовать для сохранения типов значений или неизменяемых типов.</span><span class="sxs-lookup"><span data-stu-id="51858-113">This feature can't be used to preserve value types or immutable types.</span></span> <span data-ttu-id="51858-114">При десериализации экземпляр неизменяемого типа создается после считывания всех полезных данных.</span><span class="sxs-lookup"><span data-stu-id="51858-114">On deserialization, the instance of an immutable type is created after the entire payload is read.</span></span> <span data-ttu-id="51858-115">Поэтому для того же экземпляра невозможно будет выполнить десериализацию, если в полезных данных JSON появляется ссылка на него.</span><span class="sxs-lookup"><span data-stu-id="51858-115">So it would be impossible to deserialize the same instance if a reference to it appears within the JSON payload.</span></span>

<span data-ttu-id="51858-116">Для типов значений, неизменяемых типов и массивов ссылочные метаданные не сериализуются.</span><span class="sxs-lookup"><span data-stu-id="51858-116">For value types, immutable types, and arrays, no reference metadata is serialized.</span></span> <span data-ttu-id="51858-117">Если при десериализации было найдено `$ref` или `$id`, создается исключение.</span><span class="sxs-lookup"><span data-stu-id="51858-117">On deserialization, an exception is thrown if `$ref` or `$id` is found.</span></span> <span data-ttu-id="51858-118">Однако типы значений игнорируют `$id` (и `$values` для коллекций), чтобы позволить десериализацию полезных данных, сериализованных с помощью Newtonsoft.Json.</span><span class="sxs-lookup"><span data-stu-id="51858-118">However, value types ignore `$id` (and `$values` in the case of collections) to make it possible to deserialize payloads that were serialized by using Newtonsoft.Json.</span></span>  <span data-ttu-id="51858-119">Newtonsoft.Json выполняет сериализацию метаданных для таких типов.</span><span class="sxs-lookup"><span data-stu-id="51858-119">Newtonsoft.Json does serialize metadata for such types.</span></span>

<span data-ttu-id="51858-120">Для определения равенства объектов System.Text.Json использует свойство <xref:System.Collections.Generic.ReferenceEqualityComparer.Instance%2A?displayProperty=nameWithType>, которое при сравнении двух экземпляров объекта использует эквивалентность ссылок (<xref:System.Object.ReferenceEquals(System.Object,System.Object)?displayProperty=nameWithType>), а не эквивалентность значений (<xref:System.Object.Equals(System.Object)?displayProperty=nameWithType>).</span><span class="sxs-lookup"><span data-stu-id="51858-120">To determine if objects are equal, System.Text.Json uses <xref:System.Collections.Generic.ReferenceEqualityComparer.Instance%2A?displayProperty=nameWithType>, which uses reference equality (<xref:System.Object.ReferenceEquals(System.Object,System.Object)?displayProperty=nameWithType>) instead of value equality (<xref:System.Object.Equals(System.Object)?displayProperty=nameWithType> when comparing two object instances.</span></span>

<span data-ttu-id="51858-121">Больше о сериализации и десериализации ссылок см. в статье <xref:System.Text.Json.Serialization.ReferenceHandler.Preserve%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="51858-121">For more information about how references are serialized and deserialized, see <xref:System.Text.Json.Serialization.ReferenceHandler.Preserve%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="51858-122">Класс <xref:System.Text.Json.Serialization.ReferenceResolver> определяет поведение сохранения ссылок при сериализации и десериализации.</span><span class="sxs-lookup"><span data-stu-id="51858-122">The <xref:System.Text.Json.Serialization.ReferenceResolver> class defines the behavior of preserving references on serialization and deserialization.</span></span> <span data-ttu-id="51858-123">Создайте производный класс, чтобы указать настраиваемое поведение.</span><span class="sxs-lookup"><span data-stu-id="51858-123">Create a derived class to specify custom behavior.</span></span> <span data-ttu-id="51858-124">Пример см. в статье [GuidReferenceResolver](https://github.com/dotnet/docs/blob/9d5e88edbd7f12be463775ffebbf07ac8415fe18/docs/standard/serialization/snippets/system-text-json-how-to-5-0/csharp/GuidReferenceResolverExample.cs).</span><span class="sxs-lookup"><span data-stu-id="51858-124">For an example, see [GuidReferenceResolver](https://github.com/dotnet/docs/blob/9d5e88edbd7f12be463775ffebbf07ac8415fe18/docs/standard/serialization/snippets/system-text-json-how-to-5-0/csharp/GuidReferenceResolverExample.cs).</span></span>

::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="51858-125">System.Text.Json в .NET Core 3.1 поддерживает сериализацию только по значению и вызывает исключение для циклических ссылок.</span><span class="sxs-lookup"><span data-stu-id="51858-125">System.Text.Json in .NET Core 3.1 only supports serialization by value and throws an exception for circular references.</span></span>
::: zone-end

## <a name="see-also"></a><span data-ttu-id="51858-126">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="51858-126">See also</span></span>

* [<span data-ttu-id="51858-127">Общие сведения о System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="51858-127">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="51858-128">Создание экземпляров JsonSerializerOptions</span><span class="sxs-lookup"><span data-stu-id="51858-128">Instantiate JsonSerializerOptions</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="51858-129">Сопоставление без учета регистра</span><span class="sxs-lookup"><span data-stu-id="51858-129">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="51858-130">Настройка имен и значений свойств</span><span class="sxs-lookup"><span data-stu-id="51858-130">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="51858-131">Игнорирование свойств</span><span class="sxs-lookup"><span data-stu-id="51858-131">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="51858-132">Применение недействительного кода JSON</span><span class="sxs-lookup"><span data-stu-id="51858-132">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="51858-133">Обработка переполнения JSON</span><span class="sxs-lookup"><span data-stu-id="51858-133">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="51858-134">Неизменяемые типы и непубличные методы доступа</span><span class="sxs-lookup"><span data-stu-id="51858-134">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="51858-135">Полиморфная сериализация</span><span class="sxs-lookup"><span data-stu-id="51858-135">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* <span data-ttu-id="51858-136">[Справочник по API System.Text.Json](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="51858-136">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
