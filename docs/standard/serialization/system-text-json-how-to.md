---
title: Как сериализировать и десериализировать JSON с помощью C# для .NET
description: Сведения об использовании пространства имен System.Text.Json для сериализации и десериализации формата JSON в .NET. Содержит пример кода.
ms.date: 11/30/2020
ms.custom: contperfq2
no-loc:
- System.Text.Json
- Newtonsoft.Json
zone_pivot_groups: dotnet-version
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: 9ea9e2fef5ef66f2a5ff816168abfbd7b2e75276
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/01/2020
ms.locfileid: "96437672"
---
# <a name="how-to-serialize-and-deserialize-marshal-and-unmarshal-json-in-net"></a><span data-ttu-id="4afa4-104">Как сериализировать и десериализировать (маршалирование и демаршалирование) JSON в .NET</span><span class="sxs-lookup"><span data-stu-id="4afa4-104">How to serialize and deserialize (marshal and unmarshal) JSON in .NET</span></span>

<span data-ttu-id="4afa4-105">Эта статья содержит сведения об использовании пространства имен <xref:System.Text.Json?displayProperty=fullName> для сериализации и десериализации в нотации объектов JavaScript (JSON) и из нее.</span><span class="sxs-lookup"><span data-stu-id="4afa4-105">This article shows how to use the <xref:System.Text.Json?displayProperty=fullName> namespace to serialize to and deserialize from JavaScript Object Notation (JSON).</span></span> <span data-ttu-id="4afa4-106">Если вы переносите существующий код из `Newtonsoft.Json`, ознакомьтесь со статьей [Переход с Newtonsoft.Json на System.Text.Json`System.Text.Json`](system-text-json-migrate-from-newtonsoft-how-to.md).</span><span class="sxs-lookup"><span data-stu-id="4afa4-106">If you're porting existing code from `Newtonsoft.Json`, see [How to migrate to `System.Text.Json`](system-text-json-migrate-from-newtonsoft-how-to.md).</span></span>

<span data-ttu-id="4afa4-107">В направлениях и образце кода библиотека используется напрямую, а не с помощью платформы, например [ASP.NET Core](/aspnet/core/).</span><span class="sxs-lookup"><span data-stu-id="4afa4-107">The directions and sample code use the library directly, not through a framework such as [ASP.NET Core](/aspnet/core/).</span></span>

<span data-ttu-id="4afa4-108">Большая часть примера кода сериализации устанавливает для параметра <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> значение `true` для структурирования JSON (с отступами и пробелами для удобства чтения).</span><span class="sxs-lookup"><span data-stu-id="4afa4-108">Most of the serialization sample code sets <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> to `true` to "pretty-print" the JSON (with indentation and whitespace for human readability).</span></span> <span data-ttu-id="4afa4-109">При использовании в рабочей среде для этого параметра обычно принимается значение по умолчанию `false`.</span><span class="sxs-lookup"><span data-stu-id="4afa4-109">For production use, you would typically accept the default value of `false` for this setting.</span></span>

<span data-ttu-id="4afa4-110">Примеры кода относятся к следующему классу и его вариантам:</span><span class="sxs-lookup"><span data-stu-id="4afa4-110">The code examples refer to the following class and variants of it:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WF":::

## <a name="namespaces"></a><span data-ttu-id="4afa4-111">Пространства имен</span><span class="sxs-lookup"><span data-stu-id="4afa4-111">Namespaces</span></span>

<span data-ttu-id="4afa4-112">Пространство имен <xref:System.Text.Json> содержит все точки входа и основные типы.</span><span class="sxs-lookup"><span data-stu-id="4afa4-112">The <xref:System.Text.Json> namespace contains all the entry points and the main types.</span></span> <span data-ttu-id="4afa4-113">Пространство имен <xref:System.Text.Json.Serialization> содержит атрибуты и интерфейсы API для сложных сценариев и настройки, характерной для сериализации и десериализации.</span><span class="sxs-lookup"><span data-stu-id="4afa4-113">The <xref:System.Text.Json.Serialization> namespace contains attributes and APIs for advanced scenarios and customization specific to serialization and deserialization.</span></span> <span data-ttu-id="4afa4-114">В примерах кода, приведенных в этой статье, для одного или обоих пространств имен необходимо добавить директивы `using`:</span><span class="sxs-lookup"><span data-stu-id="4afa4-114">The code examples shown in this article require `using` directives for one or both of these namespaces:</span></span>

```csharp
using System.Text.Json;
using System.Text.Json.Serialization;
```

> [!IMPORTANT]
> <span data-ttu-id="4afa4-115">Атрибуты из пространства имен <xref:System.Runtime.Serialization> не поддерживаются в `System.Text.Json`.</span><span class="sxs-lookup"><span data-stu-id="4afa4-115">Attributes from the <xref:System.Runtime.Serialization> namespace aren't supported in `System.Text.Json`.</span></span>

## <a name="how-to-write-net-objects-as-json-serialize"></a><span data-ttu-id="4afa4-116">Как записать объекты .NET в формате JSON (сериализация)</span><span class="sxs-lookup"><span data-stu-id="4afa4-116">How to write .NET objects as JSON (serialize)</span></span>

<span data-ttu-id="4afa4-117">Чтобы записать JSON в строку или в файл, вызовите метод <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4afa4-117">To write JSON to a string or to a file, call the <xref:System.Text.Json.JsonSerializer.Serialize%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="4afa4-118">В следующем примере показано создание JSON в виде строки:</span><span class="sxs-lookup"><span data-stu-id="4afa4-118">The following example creates JSON as a string:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToString.cs" id="Serialize":::

<span data-ttu-id="4afa4-119">В примере ниже для создания JSON-файла используется синхронный код:</span><span class="sxs-lookup"><span data-stu-id="4afa4-119">The following example uses synchronous code to create a JSON file:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToFile.cs" id="Serialize":::

<span data-ttu-id="4afa4-120">В следующем примере для создания JSON-файла используется асинхронный код:</span><span class="sxs-lookup"><span data-stu-id="4afa4-120">The following example uses asynchronous code to create a JSON file:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToFileAsync.cs" id="Serialize":::

<span data-ttu-id="4afa4-121">В предыдущих примерах для сериализуемого типа используется определение типа.</span><span class="sxs-lookup"><span data-stu-id="4afa4-121">The preceding examples use type inference for the type being serialized.</span></span> <span data-ttu-id="4afa4-122">Перегрузка `Serialize()` принимает параметр универсального типа:</span><span class="sxs-lookup"><span data-stu-id="4afa4-122">An overload of `Serialize()` takes a generic type parameter:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToString.cs" id="SerializeWithGenericParameter":::

### <a name="serialization-example"></a><span data-ttu-id="4afa4-123">Пример сериализации</span><span class="sxs-lookup"><span data-stu-id="4afa4-123">Serialization example</span></span>

<span data-ttu-id="4afa4-124">Ниже приведен пример класса, который содержит свойства типа коллекции и определяемый пользователем тип:</span><span class="sxs-lookup"><span data-stu-id="4afa4-124">Here's an example class that contains collection-type properties and a user-defined type:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WFWithPOCOs":::

> [!TIP]
> <span data-ttu-id="4afa4-125">POCO означает [традиционный объект среды CLR](https://en.wikipedia.org/wiki/Plain_old_CLR_object).</span><span class="sxs-lookup"><span data-stu-id="4afa4-125">"POCO" stands for [plain old CLR object](https://en.wikipedia.org/wiki/Plain_old_CLR_object).</span></span> <span data-ttu-id="4afa4-126">POCO — это тип .NET, который не зависит от каких-либо типов платформы, например посредством наследования или атрибутов.</span><span class="sxs-lookup"><span data-stu-id="4afa4-126">A POCO is a .NET type that doesn't depend on any framework-specific types, for example, through inheritance or attributes.</span></span>

<span data-ttu-id="4afa4-127">Выходные данные JSON из сериализации экземпляра предыдущего типа выглядят следующим образом.</span><span class="sxs-lookup"><span data-stu-id="4afa4-127">The JSON output from serializing an instance of the preceding type looks like the following example.</span></span> <span data-ttu-id="4afa4-128">По умолчанию выходные данные JSON сокращены (удалены пробелы, отступы и символы новой строки):</span><span class="sxs-lookup"><span data-stu-id="4afa4-128">The JSON output is minified (whitespace, indentation, and new-line characters are removed) by default:</span></span>

```json
{"Date":"2019-08-01T00:00:00-07:00","TemperatureCelsius":25,"Summary":"Hot","DatesAvailable":["2019-08-01T00:00:00-07:00","2019-08-02T00:00:00-07:00"],"TemperatureRanges":{"Cold":{"High":20,"Low":-10},"Hot":{"High":60,"Low":20}},"SummaryWords":["Cool","Windy","Humid"]}
```

<span data-ttu-id="4afa4-129">В следующем примере показан тот же объект JSON, но с форматированием (т. е. структурированный с пробелами и отступами):</span><span class="sxs-lookup"><span data-stu-id="4afa4-129">The following example shows the same JSON, but formatted (that is, pretty-printed with whitespace and indentation):</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "DatesAvailable": [
    "2019-08-01T00:00:00-07:00",
    "2019-08-02T00:00:00-07:00"
  ],
  "TemperatureRanges": {
    "Cold": {
      "High": 20,
      "Low": -10
    },
    "Hot": {
      "High": 60,
      "Low": 20
    }
  },
  "SummaryWords": [
    "Cool",
    "Windy",
    "Humid"
  ]
}
```

## <a name="serialize-to-utf-8"></a><span data-ttu-id="4afa4-130">Сериализация в UTF-8</span><span class="sxs-lookup"><span data-stu-id="4afa4-130">Serialize to UTF-8</span></span>

<span data-ttu-id="4afa4-131">Чтобы выполнить сериализацию в UTF-8, вызовите метод <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="4afa4-131">To serialize to UTF-8, call the <xref:System.Text.Json.JsonSerializer.SerializeToUtf8Bytes%2A?displayProperty=nameWithType> method:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs" id="Serialize":::

<span data-ttu-id="4afa4-132">Также доступна перегрузка <xref:System.Text.Json.JsonSerializer.Serialize%2A>, которая принимает <xref:System.Text.Json.Utf8JsonWriter>.</span><span class="sxs-lookup"><span data-stu-id="4afa4-132">A <xref:System.Text.Json.JsonSerializer.Serialize%2A> overload that takes a <xref:System.Text.Json.Utf8JsonWriter> is also available.</span></span>

<span data-ttu-id="4afa4-133">Сериализация в UTF-8 происходит примерно на 5-10 % быстрее, чем при использовании строковых методов.</span><span class="sxs-lookup"><span data-stu-id="4afa4-133">Serializing to UTF-8 is about 5-10% faster than using the string-based methods.</span></span> <span data-ttu-id="4afa4-134">Разница заключается в том, что байты (например, UTF-8) не нужно преобразовывать в строки (UTF-16).</span><span class="sxs-lookup"><span data-stu-id="4afa4-134">The difference is because the bytes (as UTF-8) don't need to be converted to strings (UTF-16).</span></span>

## <a name="serialization-behavior"></a><span data-ttu-id="4afa4-135">Поведение сериализации</span><span class="sxs-lookup"><span data-stu-id="4afa4-135">Serialization behavior</span></span>

::: zone pivot="dotnet-5-0"

* <span data-ttu-id="4afa4-136">По умолчанию все открытые свойства сериализуются.</span><span class="sxs-lookup"><span data-stu-id="4afa4-136">By default, all public properties are serialized.</span></span> <span data-ttu-id="4afa4-137">Вы можете [указать свойства, которые нужно игнорировать](system-text-json-ignore-properties.md).</span><span class="sxs-lookup"><span data-stu-id="4afa4-137">You can [specify properties to ignore](system-text-json-ignore-properties.md).</span></span>
* <span data-ttu-id="4afa4-138">[Кодировщик по умолчанию](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) экранирует символы, не относящиеся к ASCII, символы, учитывающие HTML, в пределах диапазона ASCII и символы, которые должны быть экранированы в соответствии со [спецификацией JSON RFC 8259](https://tools.ietf.org/html/rfc8259#section-7).</span><span class="sxs-lookup"><span data-stu-id="4afa4-138">The [default encoder](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) escapes non-ASCII characters, HTML-sensitive characters within the ASCII-range, and characters that must be escaped according to [the RFC 8259 JSON spec](https://tools.ietf.org/html/rfc8259#section-7).</span></span>
* <span data-ttu-id="4afa4-139">По умолчанию JSON сокращается.</span><span class="sxs-lookup"><span data-stu-id="4afa4-139">By default, JSON is minified.</span></span> <span data-ttu-id="4afa4-140">Вы можете [структурировать JSON](#serialize-to-formatted-json).</span><span class="sxs-lookup"><span data-stu-id="4afa4-140">You can [pretty-print the JSON](#serialize-to-formatted-json).</span></span>
* <span data-ttu-id="4afa4-141">По умолчанию регистр имен JSON соответствует именам в .NET.</span><span class="sxs-lookup"><span data-stu-id="4afa4-141">By default, casing of JSON names matches the .NET names.</span></span> <span data-ttu-id="4afa4-142">Вы можете [настроить регистр имен JSON](system-text-json-customize-properties.md).</span><span class="sxs-lookup"><span data-stu-id="4afa4-142">You can [customize JSON name casing](system-text-json-customize-properties.md).</span></span>
* <span data-ttu-id="4afa4-143">По умолчанию обнаруживаются циклические ссылки и создаются исключения.</span><span class="sxs-lookup"><span data-stu-id="4afa4-143">By default, circular references are detected and exceptions thrown.</span></span> <span data-ttu-id="4afa4-144">Вы можете [сохранять ссылки и обрабатывать циклические ссылки](system-text-json-preserve-references.md).</span><span class="sxs-lookup"><span data-stu-id="4afa4-144">You can [preserve references and handle circular references](system-text-json-preserve-references.md).</span></span>
* <span data-ttu-id="4afa4-145">По умолчанию [поля](../../csharp/programming-guide/classes-and-structs/fields.md) игнорируются.</span><span class="sxs-lookup"><span data-stu-id="4afa4-145">By default, [fields](../../csharp/programming-guide/classes-and-structs/fields.md) are ignored.</span></span> <span data-ttu-id="4afa4-146">Вы можете [включить поля](#include-fields).</span><span class="sxs-lookup"><span data-stu-id="4afa4-146">You can [include fields](#include-fields).</span></span>

<span data-ttu-id="4afa4-147">При косвенном использовании System.Text.Json в приложении ASP.NET Core некоторые поведения по умолчанию отличаются.</span><span class="sxs-lookup"><span data-stu-id="4afa4-147">When you use System.Text.Json indirectly in an ASP.NET Core app, some default behaviors are different.</span></span> <span data-ttu-id="4afa4-148">Дополнительные сведения см. в разделе [Стандартные параметры веб-приложений для JsonSerializerOptions](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions).</span><span class="sxs-lookup"><span data-stu-id="4afa4-148">For more information, see [Web defaults for JsonSerializerOptions](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions).</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"

* <span data-ttu-id="4afa4-149">По умолчанию все открытые свойства сериализуются.</span><span class="sxs-lookup"><span data-stu-id="4afa4-149">By default, all public properties are serialized.</span></span> <span data-ttu-id="4afa4-150">Вы можете [указать свойства, которые нужно игнорировать](system-text-json-ignore-properties.md).</span><span class="sxs-lookup"><span data-stu-id="4afa4-150">You can [specify properties to ignore](system-text-json-ignore-properties.md).</span></span>
* <span data-ttu-id="4afa4-151">[Кодировщик по умолчанию](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) экранирует символы, не относящиеся к ASCII, символы, учитывающие HTML, в пределах диапазона ASCII и символы, которые должны быть экранированы в соответствии со [спецификацией JSON RFC 8259](https://tools.ietf.org/html/rfc8259#section-7).</span><span class="sxs-lookup"><span data-stu-id="4afa4-151">The [default encoder](xref:System.Text.Encodings.Web.JavaScriptEncoder.Default) escapes non-ASCII characters, HTML-sensitive characters within the ASCII-range, and characters that must be escaped according to [the RFC 8259 JSON spec](https://tools.ietf.org/html/rfc8259#section-7).</span></span>
* <span data-ttu-id="4afa4-152">По умолчанию JSON сокращается.</span><span class="sxs-lookup"><span data-stu-id="4afa4-152">By default, JSON is minified.</span></span> <span data-ttu-id="4afa4-153">Вы можете [структурировать JSON](#serialize-to-formatted-json).</span><span class="sxs-lookup"><span data-stu-id="4afa4-153">You can [pretty-print the JSON](#serialize-to-formatted-json).</span></span>
* <span data-ttu-id="4afa4-154">По умолчанию регистр имен JSON соответствует именам в .NET.</span><span class="sxs-lookup"><span data-stu-id="4afa4-154">By default, casing of JSON names matches the .NET names.</span></span> <span data-ttu-id="4afa4-155">Вы можете [настроить регистр имен JSON](system-text-json-customize-properties.md).</span><span class="sxs-lookup"><span data-stu-id="4afa4-155">You can [customize JSON name casing](system-text-json-customize-properties.md).</span></span>
* <span data-ttu-id="4afa4-156">Обнаруживаются циклические ссылки и создаются исключения.</span><span class="sxs-lookup"><span data-stu-id="4afa4-156">Circular references are detected and exceptions thrown.</span></span>
* <span data-ttu-id="4afa4-157">[Поля](../../csharp/programming-guide/classes-and-structs/fields.md) игнорируются.</span><span class="sxs-lookup"><span data-stu-id="4afa4-157">[Fields](../../csharp/programming-guide/classes-and-structs/fields.md) are ignored.</span></span>
::: zone-end

<span data-ttu-id="4afa4-158">К поддерживаемым типам относятся:</span><span class="sxs-lookup"><span data-stu-id="4afa4-158">Supported types include:</span></span>
::: zone pivot="dotnet-5-0"

* <span data-ttu-id="4afa4-159">Примитивы .NET, которые сопоставляются с примитивами JavaScript, например числовыми типами, строками и логическими значениями.</span><span class="sxs-lookup"><span data-stu-id="4afa4-159">.NET primitives that map to JavaScript primitives, such as numeric types, strings, and Boolean.</span></span>
* <span data-ttu-id="4afa4-160">Определяемые пользователем [объекты POCO (традиционные объекты среды CLR)](https://en.wikipedia.org/wiki/Plain_old_CLR_object).</span><span class="sxs-lookup"><span data-stu-id="4afa4-160">User-defined [plain old CLR objects (POCOs)](https://en.wikipedia.org/wiki/Plain_old_CLR_object).</span></span>
* <span data-ttu-id="4afa4-161">Одномерные массивы и массивы массивов (`T[][]`).</span><span class="sxs-lookup"><span data-stu-id="4afa4-161">One-dimensional and jagged arrays (`T[][]`).</span></span>
* <span data-ttu-id="4afa4-162">Коллекции и словари из следующих пространств имен.</span><span class="sxs-lookup"><span data-stu-id="4afa4-162">Collections and dictionaries from the following namespaces.</span></span>
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>
  * <xref:System.Collections.Concurrent>
  * <xref:System.Collections.Specialized>
  * <xref:System.Collections.ObjectModel>
::: zone-end

::: zone pivot="dotnet-core-3-1"

* <span data-ttu-id="4afa4-163">Примитивы .NET, которые сопоставляются с примитивами JavaScript, например числовыми типами, строками и логическими значениями.</span><span class="sxs-lookup"><span data-stu-id="4afa4-163">.NET primitives that map to JavaScript primitives, such as numeric types, strings, and Boolean.</span></span>
* <span data-ttu-id="4afa4-164">Определяемые пользователем [объекты POCO (традиционные объекты среды CLR)](https://en.wikipedia.org/wiki/Plain_old_CLR_object).</span><span class="sxs-lookup"><span data-stu-id="4afa4-164">User-defined [plain old CLR objects (POCOs)](https://en.wikipedia.org/wiki/Plain_old_CLR_object).</span></span>
* <span data-ttu-id="4afa4-165">Одномерные массивы и массивы массивов (`ArrayName[][]`).</span><span class="sxs-lookup"><span data-stu-id="4afa4-165">One-dimensional and jagged arrays (`ArrayName[][]`).</span></span>
* <span data-ttu-id="4afa4-166">`Dictionary<string,TValue>` где `TValue` — это `object`, `JsonElement` или POCO.</span><span class="sxs-lookup"><span data-stu-id="4afa4-166">`Dictionary<string,TValue>` where `TValue` is `object`, `JsonElement`, or a POCO.</span></span>
* <span data-ttu-id="4afa4-167">Коллекции из следующих пространств имен.</span><span class="sxs-lookup"><span data-stu-id="4afa4-167">Collections from the following namespaces.</span></span>
  * <xref:System.Collections>
  * <xref:System.Collections.Generic>
  * <xref:System.Collections.Immutable>
  * <xref:System.Collections.Concurrent>
  * <xref:System.Collections.Specialized>
  * <xref:System.Collections.ObjectModel>
::: zone-end

<span data-ttu-id="4afa4-168">Для обработки дополнительных типов или для обеспечения функциональности, которая не поддерживается встроенными преобразователями, можно [реализовать пользовательские преобразователи](system-text-json-converters-how-to.md).</span><span class="sxs-lookup"><span data-stu-id="4afa4-168">You can [implement custom converters](system-text-json-converters-how-to.md) to handle additional types or to provide functionality that isn't supported by the built-in converters.</span></span>

## <a name="how-to-read-json-as-net-objects-deserialize"></a><span data-ttu-id="4afa4-169">Как считать JSON как объекты .NET (десериализация)</span><span class="sxs-lookup"><span data-stu-id="4afa4-169">How to read JSON as .NET objects (deserialize)</span></span>

<span data-ttu-id="4afa4-170">Чтобы выполнить десериализацию из строки или файла, вызовите метод <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4afa4-170">To deserialize from a string or a file, call the <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="4afa4-171">В следующем примере показано считывание JSON из строки и создание экземпляра класса `WeatherForecastWithPOCOs`, показанного ранее для [примера сериализации](#serialization-example):</span><span class="sxs-lookup"><span data-stu-id="4afa4-171">The following example reads JSON from a string and creates an instance of the `WeatherForecastWithPOCOs` class shown earlier for the [serialization example](#serialization-example):</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToString.cs" id="Deserialize":::

<span data-ttu-id="4afa4-172">Чтобы выполнить десериализацию из файла с помощью синхронного кода, выполните считывание файла в строку, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="4afa4-172">To deserialize from a file by using synchronous code, read the file into a string, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToFile.cs" id="Deserialize":::

<span data-ttu-id="4afa4-173">Чтобы выполнить десериализацию из файла с помощью асинхронного кода, вызовите метод <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A>:</span><span class="sxs-lookup"><span data-stu-id="4afa4-173">To deserialize from a file by using asynchronous code, call the <xref:System.Text.Json.JsonSerializer.DeserializeAsync%2A> method:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToFileAsync.cs" id="Deserialize":::

## <a name="deserialize-from-utf-8"></a><span data-ttu-id="4afa4-174">Десериализация из UTF-8</span><span class="sxs-lookup"><span data-stu-id="4afa4-174">Deserialize from UTF-8</span></span>

<span data-ttu-id="4afa4-175">Для десериализации из UTF-8 вызовите перегрузку <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType>, которая принимает значения `ReadOnlySpan<byte>` или `Utf8JsonReader`, как показано в следующих примерах.</span><span class="sxs-lookup"><span data-stu-id="4afa4-175">To deserialize from UTF-8, call a <xref:System.Text.Json.JsonSerializer.Deserialize%2A?displayProperty=nameWithType> overload that takes a `ReadOnlySpan<byte>` or a `Utf8JsonReader`, as shown in the following examples.</span></span> <span data-ttu-id="4afa4-176">В примерах предполагается, что JSON находится в массиве байтов jsonUtf8Bytes.</span><span class="sxs-lookup"><span data-stu-id="4afa4-176">The examples assume the JSON is in a byte array named jsonUtf8Bytes.</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs" id="Deserialize1":::

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToUtf8.cs" id="Deserialize2":::

## <a name="deserialization-behavior"></a><span data-ttu-id="4afa4-177">Поведение десериализации</span><span class="sxs-lookup"><span data-stu-id="4afa4-177">Deserialization behavior</span></span>

<span data-ttu-id="4afa4-178">При десериализации JSON применяются следующие правила поведения:</span><span class="sxs-lookup"><span data-stu-id="4afa4-178">The following behaviors apply when deserializing JSON:</span></span>

::: zone pivot="dotnet-5-0"

* <span data-ttu-id="4afa4-179">По умолчанию при сопоставлении имен свойств учитывается регистр.</span><span class="sxs-lookup"><span data-stu-id="4afa4-179">By default, property name matching is case-sensitive.</span></span> <span data-ttu-id="4afa4-180">Вы можете [указать учет регистра](system-text-json-character-casing.md).</span><span class="sxs-lookup"><span data-stu-id="4afa4-180">You can [specify case-insensitivity](system-text-json-character-casing.md).</span></span>
* <span data-ttu-id="4afa4-181">Если JSON содержит значение для свойства, доступного только для чтения, значение игнорируется, а исключение не создается.</span><span class="sxs-lookup"><span data-stu-id="4afa4-181">If the JSON contains a value for a read-only property, the value is ignored and no exception is thrown.</span></span>
* <span data-ttu-id="4afa4-182">Сериализатор не учитывает конструкторы, которые не являются открытыми.</span><span class="sxs-lookup"><span data-stu-id="4afa4-182">Non-public constructors are ignored by the serializer.</span></span>
* <span data-ttu-id="4afa4-183">Поддерживается десериализация в неизменяемые объекты или свойства "только для чтения".</span><span class="sxs-lookup"><span data-stu-id="4afa4-183">Deserialization to immutable objects or read-only properties is supported.</span></span> <span data-ttu-id="4afa4-184">См. статью [Неизменяемые типы и записи](system-text-json-immutability.md).</span><span class="sxs-lookup"><span data-stu-id="4afa4-184">See [Immutable types and Records](system-text-json-immutability.md).</span></span>
* <span data-ttu-id="4afa4-185">По умолчанию перечисления поддерживаются в виде чисел.</span><span class="sxs-lookup"><span data-stu-id="4afa4-185">By default, enums are supported as numbers.</span></span> <span data-ttu-id="4afa4-186">Вы можете [сериализовать имена перечислений в качестве строк](system-text-json-customize-properties.md#enums-as-strings).</span><span class="sxs-lookup"><span data-stu-id="4afa4-186">You can [serialize enum names as strings](system-text-json-customize-properties.md#enums-as-strings).</span></span>
* <span data-ttu-id="4afa4-187">По умолчанию поля игнорируются.</span><span class="sxs-lookup"><span data-stu-id="4afa4-187">By default, fields are ignored.</span></span> <span data-ttu-id="4afa4-188">Вы можете [включить поля](#include-fields).</span><span class="sxs-lookup"><span data-stu-id="4afa4-188">You can [include fields](#include-fields).</span></span>
* <span data-ttu-id="4afa4-189">По умолчанию комментарии или завершающие запятые в JSON вызывают исключения.</span><span class="sxs-lookup"><span data-stu-id="4afa4-189">By default, comments or trailing commas in the JSON throw exceptions.</span></span> <span data-ttu-id="4afa4-190">Вы можете разрешить [комментарии и завершающие запятые](system-text-json-invalid-json.md).</span><span class="sxs-lookup"><span data-stu-id="4afa4-190">You can [allow comments and trailing commas](system-text-json-invalid-json.md).</span></span>
* <span data-ttu-id="4afa4-191">Максимальная глубина [по умолчанию](xref:System.Text.Json.JsonReaderOptions.MaxDepth) равна 64.</span><span class="sxs-lookup"><span data-stu-id="4afa4-191">The [default maximum depth](xref:System.Text.Json.JsonReaderOptions.MaxDepth) is 64.</span></span>

<span data-ttu-id="4afa4-192">При косвенном использовании System.Text.Json в приложении ASP.NET Core некоторые поведения по умолчанию отличаются.</span><span class="sxs-lookup"><span data-stu-id="4afa4-192">When you use System.Text.Json indirectly in an ASP.NET Core app, some default behaviors are different.</span></span> <span data-ttu-id="4afa4-193">Дополнительные сведения см. в разделе [Стандартные параметры веб-приложений для JsonSerializerOptions](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions).</span><span class="sxs-lookup"><span data-stu-id="4afa4-193">For more information, see [Web defaults for JsonSerializerOptions](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions).</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"

* <span data-ttu-id="4afa4-194">По умолчанию при сопоставлении имен свойств учитывается регистр.</span><span class="sxs-lookup"><span data-stu-id="4afa4-194">By default, property name matching is case-sensitive.</span></span> <span data-ttu-id="4afa4-195">Вы можете [указать учет регистра](system-text-json-character-casing.md).</span><span class="sxs-lookup"><span data-stu-id="4afa4-195">You can [specify case-insensitivity](system-text-json-character-casing.md).</span></span> <span data-ttu-id="4afa4-196">Приложения ASP.NET Core [указывают учет регистра по умолчанию](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions).</span><span class="sxs-lookup"><span data-stu-id="4afa4-196">ASP.NET Core apps [specify case-insensitivity by default](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions).</span></span>
* <span data-ttu-id="4afa4-197">Если JSON содержит значение для свойства, доступного только для чтения, значение игнорируется, а исключение не создается.</span><span class="sxs-lookup"><span data-stu-id="4afa4-197">If the JSON contains a value for a read-only property, the value is ignored and no exception is thrown.</span></span>
* <span data-ttu-id="4afa4-198">Для десериализации используется конструктор без параметров, который может быть общедоступным, внутренним или частным.</span><span class="sxs-lookup"><span data-stu-id="4afa4-198">A parameterless constructor, which can be public, internal, or private, is used for deserialization.</span></span>
* <span data-ttu-id="4afa4-199">Десериализация в неизменяемые объекты или свойства только для чтения не поддерживается.</span><span class="sxs-lookup"><span data-stu-id="4afa4-199">Deserialization to immutable objects or read-only properties isn't supported.</span></span>
* <span data-ttu-id="4afa4-200">По умолчанию перечисления поддерживаются в виде чисел.</span><span class="sxs-lookup"><span data-stu-id="4afa4-200">By default, enums are supported as numbers.</span></span> <span data-ttu-id="4afa4-201">Вы можете [сериализовать имена перечислений в качестве строк](system-text-json-customize-properties.md#enums-as-strings).</span><span class="sxs-lookup"><span data-stu-id="4afa4-201">You can [serialize enum names as strings](system-text-json-customize-properties.md#enums-as-strings).</span></span>
* <span data-ttu-id="4afa4-202">Поля не поддерживаются.</span><span class="sxs-lookup"><span data-stu-id="4afa4-202">Fields aren't supported.</span></span>
* <span data-ttu-id="4afa4-203">По умолчанию комментарии или завершающие запятые в JSON вызывают исключения.</span><span class="sxs-lookup"><span data-stu-id="4afa4-203">By default, comments or trailing commas in the JSON throw exceptions.</span></span> <span data-ttu-id="4afa4-204">Вы можете разрешить [комментарии и завершающие запятые](system-text-json-invalid-json.md).</span><span class="sxs-lookup"><span data-stu-id="4afa4-204">You can [allow comments and trailing commas](system-text-json-invalid-json.md).</span></span>
* <span data-ttu-id="4afa4-205">Максимальная глубина [по умолчанию](xref:System.Text.Json.JsonReaderOptions.MaxDepth) равна 64.</span><span class="sxs-lookup"><span data-stu-id="4afa4-205">The [default maximum depth](xref:System.Text.Json.JsonReaderOptions.MaxDepth) is 64.</span></span>

<span data-ttu-id="4afa4-206">При косвенном использовании System.Text.Json в приложении ASP.NET Core некоторые поведения по умолчанию отличаются.</span><span class="sxs-lookup"><span data-stu-id="4afa4-206">When you use System.Text.Json indirectly in an ASP.NET Core app, some default behaviors are different.</span></span> <span data-ttu-id="4afa4-207">Дополнительные сведения см. в разделе [Стандартные параметры веб-приложений для JsonSerializerOptions](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions).</span><span class="sxs-lookup"><span data-stu-id="4afa4-207">For more information, see [Web defaults for JsonSerializerOptions](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions).</span></span>
::: zone-end

<span data-ttu-id="4afa4-208">Для обеспечения функциональности, которая не поддерживается встроенными преобразователями, можно [реализовать пользовательские преобразователи](system-text-json-converters-how-to.md).</span><span class="sxs-lookup"><span data-stu-id="4afa4-208">You can [implement custom converters](system-text-json-converters-how-to.md) to provide functionality that isn't supported by the built-in converters.</span></span>

## <a name="serialize-to-formatted-json"></a><span data-ttu-id="4afa4-209">Сериализация в форматированный JSON</span><span class="sxs-lookup"><span data-stu-id="4afa4-209">Serialize to formatted JSON</span></span>

<span data-ttu-id="4afa4-210">Чтобы структурировать выходные данные JSON, задайте для <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> значение `true`.</span><span class="sxs-lookup"><span data-stu-id="4afa4-210">To pretty-print the JSON output, set <xref:System.Text.Json.JsonSerializerOptions.WriteIndented?displayProperty=nameWithType> to `true`:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/RoundtripToString.cs" id="SerializePrettyPrint":::

<span data-ttu-id="4afa4-211">Ниже приведен пример типа для сериализации и структурирования данных JSON:</span><span class="sxs-lookup"><span data-stu-id="4afa4-211">Here's an example type to be serialized and pretty-printed JSON output:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/WeatherForecast.cs" id="WF":::

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

## <a name="include-fields"></a><span data-ttu-id="4afa4-212">Включение полей</span><span class="sxs-lookup"><span data-stu-id="4afa4-212">Include fields</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="4afa4-213">Используйте глобальный параметр <xref:System.Text.Json.JsonSerializerOptions.IncludeFields?displayProperty=nameWithType> или атрибут [[JsonInclude]](xref:System.Text.Json.Serialization.JsonIncludeAttribute) для включения поля при сериализации или десериализации, как показано ниже:</span><span class="sxs-lookup"><span data-stu-id="4afa4-213">Use the <xref:System.Text.Json.JsonSerializerOptions.IncludeFields?displayProperty=nameWithType> global setting or the [[JsonInclude]](xref:System.Text.Json.Serialization.JsonIncludeAttribute) attribute to include fields when serializing or deserializing, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/Fields.cs" highlight="16,18,20,32-35":::

<span data-ttu-id="4afa4-214">Чтобы пропустить поля, предназначенные только для чтения, используйте глобальный параметр <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyFields%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4afa4-214">To ignore read-only fields, use the <xref:System.Text.Json.JsonSerializerOptions.IgnoreReadOnlyFields%2A?displayProperty=nameWithType> global setting.</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="4afa4-215">Поля не поддерживаются в System.Text.Json в .NET Core 3.1.</span><span class="sxs-lookup"><span data-stu-id="4afa4-215">Fields are not supported in System.Text.Json in .NET Core 3.1.</span></span> <span data-ttu-id="4afa4-216">Эта функция может быть предоставлена [пользовательскими преобразователями](system-text-json-converters-how-to.md).</span><span class="sxs-lookup"><span data-stu-id="4afa4-216">[Custom converters](system-text-json-converters-how-to.md) can provide this functionality.</span></span>
::: zone-end

## <a name="httpclient-and-httpcontent-extension-methods"></a><span data-ttu-id="4afa4-217">Методы расширения HttpClient и HttpContent</span><span class="sxs-lookup"><span data-stu-id="4afa4-217">HttpClient and HttpContent extension methods</span></span>

::: zone pivot="dotnet-5-0"

<span data-ttu-id="4afa4-218">Сериализация и десериализация полезных данных JSON из сети являются обычными операциями.</span><span class="sxs-lookup"><span data-stu-id="4afa4-218">Serializing and deserializing JSON payloads from the network are common operations.</span></span> <span data-ttu-id="4afa4-219">Методы расширения в [HttpClient](xref:System.Net.Http.Json.HttpClientJsonExtensions) и [HttpContent](xref:System.Net.Http.Json.HttpContentJsonExtensions) позволяют выполнять эти операции в одной строке кода.</span><span class="sxs-lookup"><span data-stu-id="4afa4-219">Extension methods on [HttpClient](xref:System.Net.Http.Json.HttpClientJsonExtensions) and [HttpContent](xref:System.Net.Http.Json.HttpContentJsonExtensions) let you do these operations in a single line of code.</span></span> <span data-ttu-id="4afa4-220">Эти методы расширения используют [стандартные параметры веб-приложений для JsonSerializerOptions](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions).</span><span class="sxs-lookup"><span data-stu-id="4afa4-220">These extension methods use [web defaults for JsonSerializerOptions](system-text-json-configure-options.md#web-defaults-for-jsonserializeroptions).</span></span>

<span data-ttu-id="4afa4-221">В следующем примере демонстрируется применение <xref:System.Net.Http.Json.HttpClientJsonExtensions.GetFromJsonAsync%2A?displayProperty=nameWithType> и <xref:System.Net.Http.Json.HttpClientJsonExtensions.PostAsJsonAsync%2A?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="4afa4-221">The following example illustrates use of <xref:System.Net.Http.Json.HttpClientJsonExtensions.GetFromJsonAsync%2A?displayProperty=nameWithType> and <xref:System.Net.Http.Json.HttpClientJsonExtensions.PostAsJsonAsync%2A?displayProperty=nameWithType>:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/HttpClientExtensionMethods.cs" highlight="26,33":::

<span data-ttu-id="4afa4-222">Для System.Text.Json существуют также методы расширения на [HttpContent](xref:System.Net.Http.Json.HttpContentJsonExtensions).</span><span class="sxs-lookup"><span data-stu-id="4afa4-222">There are also extension methods for System.Text.Json on [HttpContent](xref:System.Net.Http.Json.HttpContentJsonExtensions).</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="4afa4-223">Методы расширения на `HttpClient` и `HttpContent` недоступны в System.Text.Json для .NET Core 3.1.</span><span class="sxs-lookup"><span data-stu-id="4afa4-223">Extension methods on `HttpClient` and `HttpContent` are not available in System.Text.Json in .NET Core 3.1.</span></span>
::: zone-end

## <a name="see-also"></a><span data-ttu-id="4afa4-224">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="4afa4-224">See also</span></span>

* [<span data-ttu-id="4afa4-225">Общие сведения о System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="4afa4-225">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="4afa4-226">Как написать пользовательские преобразователи для сериализации JSON (маршалинг) в .NET</span><span class="sxs-lookup"><span data-stu-id="4afa4-226">How to write custom converters</span></span>](system-text-json-converters-how-to.md)
* [<span data-ttu-id="4afa4-227">Как выполнить миграцию из Newtonsoft.Json</span><span class="sxs-lookup"><span data-stu-id="4afa4-227">How to migrate from Newtonsoft.Json</span></span>](system-text-json-migrate-from-newtonsoft-how-to.md)
* [<span data-ttu-id="4afa4-228">Поддержка DateTime и DateTimeOffset в System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="4afa4-228">DateTime and DateTimeOffset support in System.Text.Json</span></span>](../datetime/system-text-json-support.md)
* <span data-ttu-id="4afa4-229">[Справочник по API System.Text.Json](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="4afa4-229">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
<!-- * [System.Text.Json roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md)-->
