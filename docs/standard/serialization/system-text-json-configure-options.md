---
title: Создание экземпляров JsonSerializerOptions с помощью System.Text.Json
description: Сведения о том, как избежать проблем с производительностью и использовать доступные конструкторы для экземпляров JsonSerializerOptions.
ms.date: 12/02/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
zone_pivot_groups: dotnet-version
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 5f32e1369e58dd9550f28abc822f187dee46c022
ms.sourcegitcommit: 81f1bba2c97a67b5ca76bcc57b37333ffca60c7b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/10/2020
ms.locfileid: "97009837"
---
# <a name="how-to-instantiate-jsonserializeroptions-instances-with-no-locsystemtextjson"></a><span data-ttu-id="e4e88-103">Создание экземпляров JsonSerializerOptions с помощью System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="e4e88-103">How to instantiate JsonSerializerOptions instances with System.Text.Json</span></span>

<span data-ttu-id="e4e88-104">В этой статье объясняется, как избежать проблем с производительностью при использовании <xref:System.Text.Json.JsonSerializerOptions>.</span><span class="sxs-lookup"><span data-stu-id="e4e88-104">This article explains how to avoid performance problems when you use <xref:System.Text.Json.JsonSerializerOptions>.</span></span> <span data-ttu-id="e4e88-105">В ней также показано, как использовать доступные параметризованные конструкторы.</span><span class="sxs-lookup"><span data-stu-id="e4e88-105">It also shows how to use the parameterized constructors that are available.</span></span>

## <a name="reuse-jsonserializeroptions-instances"></a><span data-ttu-id="e4e88-106">Повторное использование экземпляров JsonSerializerOptions</span><span class="sxs-lookup"><span data-stu-id="e4e88-106">Reuse JsonSerializerOptions instances</span></span>

<span data-ttu-id="e4e88-107">При многократном использовании `JsonSerializerOptions` с одинаковыми параметрами не создавайте новый экземпляр `JsonSerializerOptions` при каждом использовании.</span><span class="sxs-lookup"><span data-stu-id="e4e88-107">If you use `JsonSerializerOptions` repeatedly with the same options, don't create a new `JsonSerializerOptions` instance each time you use it.</span></span> <span data-ttu-id="e4e88-108">Повторно используйте один и тот же экземпляр для каждого вызова.</span><span class="sxs-lookup"><span data-stu-id="e4e88-108">Reuse the same instance for every call.</span></span> <span data-ttu-id="e4e88-109">Это руководство относится к коду для настраиваемых преобразователей, а также при вызове <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> или <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e4e88-109">This guidance applies to code you write for custom converters and when you call <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> or <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="e4e88-110">В следующем примере кода демонстрируется снижение производительности при использовании новых экземпляров параметров.</span><span class="sxs-lookup"><span data-stu-id="e4e88-110">The following code demonstrates the performance penalty for using new options instances.</span></span>

:::code language="csharp" source="snippets/system-text-json-configure-options/csharp/ReuseOptionsInstances.cs":::

<span data-ttu-id="e4e88-111">Предыдущий код сериализует небольшой объект 100 000 раз с помощью одного и того же экземпляра параметров.</span><span class="sxs-lookup"><span data-stu-id="e4e88-111">The preceding code serializes a small object 100,000 times using the same options instance.</span></span> <span data-ttu-id="e4e88-112">Затем он сериализует тот же объект такое же количество раз и каждый раз создает новый экземпляр параметров.</span><span class="sxs-lookup"><span data-stu-id="e4e88-112">Then it serializes the same object the same number of times and creates a new options instance each time.</span></span> <span data-ttu-id="e4e88-113">Типичная разница во времени выполнения — 190 и 40 140 миллисекунд.</span><span class="sxs-lookup"><span data-stu-id="e4e88-113">A typical run time difference is 190 compared to 40,140 milliseconds.</span></span> <span data-ttu-id="e4e88-114">Разница станет еще больше, если увеличить число итераций.</span><span class="sxs-lookup"><span data-stu-id="e4e88-114">The difference is even greater if you increase the number of iterations.</span></span>

<span data-ttu-id="e4e88-115">Сериализатор выполняет этап прогрева во время первой сериализации каждого типа в графе объектов при передаче ему нового экземпляра параметров.</span><span class="sxs-lookup"><span data-stu-id="e4e88-115">The serializer undergoes a warm-up phase during the first serialization of each type in the object graph when a new options instance is passed to it.</span></span> <span data-ttu-id="e4e88-116">Этот прогрев включает создание кэша метаданных, необходимых для сериализации.</span><span class="sxs-lookup"><span data-stu-id="e4e88-116">This warm-up includes creating a cache of metadata that is needed for serialization.</span></span> <span data-ttu-id="e4e88-117">Метаданные содержат делегаты для методов получения свойств, методов задания свойств, аргументов конструктора, заданных атрибутов и т. д.</span><span class="sxs-lookup"><span data-stu-id="e4e88-117">The metadata includes delegates to property getters, setters, constructor arguments, specified attributes, and so forth.</span></span> <span data-ttu-id="e4e88-118">Этот кэш метаданных хранится в экземпляре параметров.</span><span class="sxs-lookup"><span data-stu-id="e4e88-118">This metadata cache is stored in the options instance.</span></span> <span data-ttu-id="e4e88-119">Тот же процесс прогрева и создания кэша относится к десериализации.</span><span class="sxs-lookup"><span data-stu-id="e4e88-119">The same warm-up process and cache applies to deserialization.</span></span>

<span data-ttu-id="e4e88-120">Размер кэша метаданных в экземпляре `JsonSerializerOptions` зависит от числа сериализуемых типов.</span><span class="sxs-lookup"><span data-stu-id="e4e88-120">The size of the metadata cache in a `JsonSerializerOptions` instance depends on the number of types to be serialized.</span></span> <span data-ttu-id="e4e88-121">Если в сериализатор передается большое число типов, например, динамически создаваемые типы, то размер кэша будет продолжать расти и может привести к появлению `OutOfMemoryException`.</span><span class="sxs-lookup"><span data-stu-id="e4e88-121">If you pass numerous types—for example, dynamically generated types—to the serializer, the cache size will continue to grow and can end up causing an `OutOfMemoryException`.</span></span>

## <a name="copy-jsonserializeroptions"></a><span data-ttu-id="e4e88-122">Копирование JsonSerializerOptions</span><span class="sxs-lookup"><span data-stu-id="e4e88-122">Copy JsonSerializerOptions</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="e4e88-123">Существует [конструктор JsonSerializerOptions](xref:System.Text.Json.JsonSerializerOptions.%23ctor(System.Text.Json.JsonSerializerOptions)), который позволяет создавать новый экземпляр с параметрами, использованными для существующего экземпляра:</span><span class="sxs-lookup"><span data-stu-id="e4e88-123">There is a [JsonSerializerOptions constructor](xref:System.Text.Json.JsonSerializerOptions.%23ctor(System.Text.Json.JsonSerializerOptions)) that lets you create a new instance with the same options as an existing instance, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/CopyOptions.cs" highlight="29":::
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="e4e88-124">Конструктор `JsonSerializerOptions`, который принимает существующий экземпляр, недоступен в .NET Core 3.1.</span><span class="sxs-lookup"><span data-stu-id="e4e88-124">A `JsonSerializerOptions` constructor that takes an existing instance is not available in .NET Core 3.1.</span></span>
::: zone-end

## <a name="web-defaults-for-jsonserializeroptions"></a><span data-ttu-id="e4e88-125">Стандартные параметры веб-приложений для JsonSerializerOptions</span><span class="sxs-lookup"><span data-stu-id="e4e88-125">Web defaults for JsonSerializerOptions</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="e4e88-126">Ниже приведены параметры с различными значениями по умолчанию для веб-приложений:</span><span class="sxs-lookup"><span data-stu-id="e4e88-126">Here are the options that have different defaults for web apps:</span></span>

* <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive%2A> = `true`
* <xref:System.Text.Json.JsonNamingPolicy> = <xref:System.Text.Json.JsonNamingPolicy.CamelCase>
* <xref:System.Text.Json.JsonSerializerOptions.NumberHandling%2A> = <xref:System.Text.Json.Serialization.JsonNumberHandling.AllowReadingFromString>

<span data-ttu-id="e4e88-127">Существует [конструктор JsonSerializerOptions](xref:System.Text.Json.JsonSerializerOptions.%23ctor(System.Text.Json.JsonSerializerDefaults)?view=net-5.0&preserve-view=true), который позволяет создавать новый экземпляр со стандартными параметрами, которые ASP.NET Core использует для веб-приложений, как показано ниже:</span><span class="sxs-lookup"><span data-stu-id="e4e88-127">There's a [JsonSerializerOptions constructor](xref:System.Text.Json.JsonSerializerOptions.%23ctor(System.Text.Json.JsonSerializerDefaults)?view=net-5.0&preserve-view=true) that lets you create a new instance with the default options that ASP.NET Core uses for web apps, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/OptionsDefaults.cs" highlight="24":::
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="e4e88-128">Ниже приведены параметры с различными значениями по умолчанию для веб-приложений:</span><span class="sxs-lookup"><span data-stu-id="e4e88-128">Here are the options that have different defaults for web apps:</span></span>

* <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive%2A> = `true`
* <xref:System.Text.Json.JsonNamingPolicy> = <xref:System.Text.Json.JsonNamingPolicy.CamelCase>

<span data-ttu-id="e4e88-129">Конструктор `JsonSerializerOptions`, указывающий набор значений по умолчанию, недоступен в .NET Core 3.1.</span><span class="sxs-lookup"><span data-stu-id="e4e88-129">A `JsonSerializerOptions` constructor that specifies a set of defaults is not available in .NET Core 3.1.</span></span>
::: zone-end

## <a name="see-also"></a><span data-ttu-id="e4e88-130">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="e4e88-130">See also</span></span>

* [<span data-ttu-id="e4e88-131">Общие сведения о System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="e4e88-131">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="e4e88-132">Практическое руководство. Сериализация и десериализация JSON</span><span class="sxs-lookup"><span data-stu-id="e4e88-132">How to serialize and deserialize JSON</span></span>](system-text-json-how-to.md)
* [<span data-ttu-id="e4e88-133">Сопоставление без учета регистра</span><span class="sxs-lookup"><span data-stu-id="e4e88-133">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="e4e88-134">Настройка имен и значений свойств</span><span class="sxs-lookup"><span data-stu-id="e4e88-134">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="e4e88-135">Игнорирование свойств</span><span class="sxs-lookup"><span data-stu-id="e4e88-135">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="e4e88-136">Применение недействительного кода JSON</span><span class="sxs-lookup"><span data-stu-id="e4e88-136">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="e4e88-137">Обработка переполнения JSON</span><span class="sxs-lookup"><span data-stu-id="e4e88-137">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="e4e88-138">Сохранение ссылок</span><span class="sxs-lookup"><span data-stu-id="e4e88-138">Preserve references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="e4e88-139">Неизменяемые типы и непубличные методы доступа</span><span class="sxs-lookup"><span data-stu-id="e4e88-139">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="e4e88-140">Полиморфная сериализация</span><span class="sxs-lookup"><span data-stu-id="e4e88-140">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* [<span data-ttu-id="e4e88-141">Миграция из Newtonsoft.Json в System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="e4e88-141">Migrate from Newtonsoft.Json to System.Text.Json</span></span>](system-text-json-migrate-from-newtonsoft-how-to.md)
* [<span data-ttu-id="e4e88-142">Настройка кодировки символов</span><span class="sxs-lookup"><span data-stu-id="e4e88-142">Customize character encoding</span></span>](system-text-json-character-encoding.md)
* [<span data-ttu-id="e4e88-143">Написание пользовательских сериализаторов и десериализаторов</span><span class="sxs-lookup"><span data-stu-id="e4e88-143">Write custom serializers and deserializers</span></span>](write-custom-serializer-deserializer.md)
* [<span data-ttu-id="e4e88-144">Написание пользовательских преобразователей для сериализации JSON</span><span class="sxs-lookup"><span data-stu-id="e4e88-144">Write custom converters for JSON serialization</span></span>](system-text-json-converters-how-to.md)
* [<span data-ttu-id="e4e88-145">Поддержка DateTime и DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="e4e88-145">DateTime and DateTimeOffset support</span></span>](../datetime/system-text-json-support.md)
* <span data-ttu-id="e4e88-146">[Справочник по API System.Text.Json](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="e4e88-146">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
* <span data-ttu-id="e4e88-147">[Справочник по API System.Text.Json.Serialization](xref:System.Text.Json.Serialization)</span><span class="sxs-lookup"><span data-stu-id="e4e88-147">[System.Text.Json.Serialization API reference](xref:System.Text.Json.Serialization)</span></span>
