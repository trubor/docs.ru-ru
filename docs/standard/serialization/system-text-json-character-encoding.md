---
title: Как настроить кодировку символов с помощью System.Text.Json
description: Узнайте, как в .NET настроить кодировку символов при сериализации в JSON и десериализации из JSON.
ms.date: 11/30/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: cfb83af0c58e0c9dfb73ecb8e2177d255e403fae
ms.sourcegitcommit: 81f1bba2c97a67b5ca76bcc57b37333ffca60c7b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/10/2020
ms.locfileid: "97009629"
---
# <a name="how-to-customize-character-encoding-with-no-locsystemtextjson"></a><span data-ttu-id="dc7e8-103">Как настроить кодировку символов с помощью System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="dc7e8-103">How to customize character encoding with System.Text.Json</span></span>

<span data-ttu-id="dc7e8-104">По умолчанию сериализатор экранирует символы, отличные от ASCII.</span><span class="sxs-lookup"><span data-stu-id="dc7e8-104">By default, the serializer escapes all non-ASCII characters.</span></span> <span data-ttu-id="dc7e8-105">То есть он заменяет их на `\uxxxx`, где `xxxx` является кодом в кодировке Юникода символа.</span><span class="sxs-lookup"><span data-stu-id="dc7e8-105">That is, it replaces them with `\uxxxx` where `xxxx` is the Unicode code of the character.</span></span> <span data-ttu-id="dc7e8-106">Например, если свойству `Summary` в следующем коде JSON присвоено кириллическое значение `жарко`, то объект `WeatherForecast` сериализуется, как показано в этом примере:</span><span class="sxs-lookup"><span data-stu-id="dc7e8-106">For example, if the `Summary` property in the following JSON is set to Cyrillic `жарко`, the `WeatherForecast` object is serialized as shown in this example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "\u0436\u0430\u0440\u043A\u043E"
}
```

## <a name="serialize-language-character-sets"></a><span data-ttu-id="dc7e8-107">Сериализация кодировки языка</span><span class="sxs-lookup"><span data-stu-id="dc7e8-107">Serialize language character sets</span></span>

<span data-ttu-id="dc7e8-108">Чтобы сериализовать кодировки одного или нескольких языков без экранирования, укажите [диапазон символов Юникода](xref:System.Text.Unicode.UnicodeRanges) при создании экземпляра <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName>, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="dc7e8-108">To serialize the character set(s) of one or more languages without escaping, specify [Unicode range(s)](xref:System.Text.Unicode.UnicodeRanges) when creating an instance of <xref:System.Text.Encodings.Web.JavaScriptEncoder?displayProperty=fullName>, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs" id="Usings":::

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs" id="LanguageSets":::

<span data-ttu-id="dc7e8-109">Этот код не поддерживает символы кириллицы или греческого языка.</span><span class="sxs-lookup"><span data-stu-id="dc7e8-109">This code doesn't escape Cyrillic or Greek characters.</span></span> <span data-ttu-id="dc7e8-110">Если свойству `Summary` присвоено кириллическое значение `жарко`, то объект `WeatherForecast` сериализуется, как показано в этом примере:</span><span class="sxs-lookup"><span data-stu-id="dc7e8-110">If the `Summary` property is set to Cyrillic `жарко`, the `WeatherForecast` object is serialized as shown in this example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жарко"
}
```

<span data-ttu-id="dc7e8-111">Чтобы сериализовать все кодировки языка без экранирования, используйте <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="dc7e8-111">To serialize all language sets without escaping, use <xref:System.Text.Unicode.UnicodeRanges.All?displayProperty=nameWithType>.</span></span>

## <a name="serialize-specific-characters"></a><span data-ttu-id="dc7e8-112">Сериализация определенных символов</span><span class="sxs-lookup"><span data-stu-id="dc7e8-112">Serialize specific characters</span></span>

<span data-ttu-id="dc7e8-113">В качестве альтернативного способа вы можете указать отдельные символы, которые нужно разрешить, без экранирования.</span><span class="sxs-lookup"><span data-stu-id="dc7e8-113">An alternative is to specify individual characters that you want to allow through without being escaped.</span></span> <span data-ttu-id="dc7e8-114">В следующем примере сериализуются только первые два символа слова `жарко`:</span><span class="sxs-lookup"><span data-stu-id="dc7e8-114">The following example serializes only the first two characters of `жарко`:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs" id="Usings":::

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs" id="SelectedCharacters":::

<span data-ttu-id="dc7e8-115">Ниже приведен пример JSON, созданный с помощью приведенного выше кода.</span><span class="sxs-lookup"><span data-stu-id="dc7e8-115">Here's an example of JSON produced by the preceding code:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "жа\u0440\u043A\u043E"
}
```

## <a name="serialize-all-characters"></a><span data-ttu-id="dc7e8-116">Сериализация всех символов</span><span class="sxs-lookup"><span data-stu-id="dc7e8-116">Serialize all characters</span></span>

<span data-ttu-id="dc7e8-117">Чтобы минимизировать экранирование, можно использовать <xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType>, как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="dc7e8-117">To minimize escaping you can use <xref:System.Text.Encodings.Web.JavaScriptEncoder.UnsafeRelaxedJsonEscaping?displayProperty=nameWithType>, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs" id="Usings":::

:::code language="csharp" source="snippets/system-text-json-how-to/csharp/SerializeCustomEncoding.cs" id="UnsafeRelaxed":::

> [!CAUTION]
> <span data-ttu-id="dc7e8-118">По сравнению с кодировщиком по умолчанию, кодировщик `UnsafeRelaxedJsonEscaping` более предпочтителен в отношении передачи символов без экранирования:</span><span class="sxs-lookup"><span data-stu-id="dc7e8-118">Compared to the default encoder, the `UnsafeRelaxedJsonEscaping` encoder is more permissive about allowing characters to pass through unescaped:</span></span>
>
> * <span data-ttu-id="dc7e8-119">Он не выполняет экранирование символов, учитывающих HTML, например `<`, `>`, `&` и `'`.</span><span class="sxs-lookup"><span data-stu-id="dc7e8-119">It doesn't escape HTML-sensitive characters such as `<`, `>`, `&`, and `'`.</span></span>
> * <span data-ttu-id="dc7e8-120">Он не предоставляет никаких дополнительных средств защиты от атак с помощью XSS или раскрытия информации, которые, например, могут возникать из-за того, что клиент и сервер не согласны с *кодировкой*.</span><span class="sxs-lookup"><span data-stu-id="dc7e8-120">It doesn't offer any additional defense-in-depth protections against XSS or information disclosure attacks, such as those which might result from the client and server disagreeing on the *charset*.</span></span>
>
> <span data-ttu-id="dc7e8-121">Используйте ненадежный кодировщик, только если известно, что клиент будет интерпретировать полученные полезные данные как JSON в кодировке UTF-8.</span><span class="sxs-lookup"><span data-stu-id="dc7e8-121">Use the unsafe encoder only when it's known that the client will be interpreting the resulting payload as UTF-8 encoded JSON.</span></span> <span data-ttu-id="dc7e8-122">Например, его можно использовать, если сервер отправляет заголовок ответа `Content-Type: application/json; charset=utf-8`.</span><span class="sxs-lookup"><span data-stu-id="dc7e8-122">For example, you can use it if the server is sending the response header `Content-Type: application/json; charset=utf-8`.</span></span> <span data-ttu-id="dc7e8-123">Никогда не допускайте, чтобы необработанные выходные данные `UnsafeRelaxedJsonEscaping` выводились на HTML-страницу или в элемент `<script>`.</span><span class="sxs-lookup"><span data-stu-id="dc7e8-123">Never allow the raw `UnsafeRelaxedJsonEscaping` output to be emitted into an HTML page or a `<script>` element.</span></span>

## <a name="see-also"></a><span data-ttu-id="dc7e8-124">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="dc7e8-124">See also</span></span>

* [<span data-ttu-id="dc7e8-125">Общие сведения о System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="dc7e8-125">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="dc7e8-126">Практическое руководство. Сериализация и десериализация JSON</span><span class="sxs-lookup"><span data-stu-id="dc7e8-126">How to serialize and deserialize JSON</span></span>](system-text-json-how-to.md)
* [<span data-ttu-id="dc7e8-127">Создание экземпляров JsonSerializerOptions</span><span class="sxs-lookup"><span data-stu-id="dc7e8-127">Instantiate JsonSerializerOptions instances</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="dc7e8-128">Сопоставление без учета регистра</span><span class="sxs-lookup"><span data-stu-id="dc7e8-128">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="dc7e8-129">Настройка имен и значений свойств</span><span class="sxs-lookup"><span data-stu-id="dc7e8-129">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="dc7e8-130">Игнорирование свойств</span><span class="sxs-lookup"><span data-stu-id="dc7e8-130">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="dc7e8-131">Применение недействительного кода JSON</span><span class="sxs-lookup"><span data-stu-id="dc7e8-131">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="dc7e8-132">Обработка переполнения JSON</span><span class="sxs-lookup"><span data-stu-id="dc7e8-132">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="dc7e8-133">Сохранение ссылок</span><span class="sxs-lookup"><span data-stu-id="dc7e8-133">Preserve references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="dc7e8-134">Неизменяемые типы и непубличные методы доступа</span><span class="sxs-lookup"><span data-stu-id="dc7e8-134">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="dc7e8-135">Полиморфная сериализация</span><span class="sxs-lookup"><span data-stu-id="dc7e8-135">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* [<span data-ttu-id="dc7e8-136">Миграция из Newtonsoft.Json в System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="dc7e8-136">Migrate from Newtonsoft.Json to System.Text.Json</span></span>](system-text-json-migrate-from-newtonsoft-how-to.md)
* [<span data-ttu-id="dc7e8-137">Написание пользовательских сериализаторов и десериализаторов</span><span class="sxs-lookup"><span data-stu-id="dc7e8-137">Write custom serializers and deserializers</span></span>](write-custom-serializer-deserializer.md)
* [<span data-ttu-id="dc7e8-138">Написание пользовательских преобразователей для сериализации JSON</span><span class="sxs-lookup"><span data-stu-id="dc7e8-138">Write custom converters for JSON serialization</span></span>](system-text-json-converters-how-to.md)
* [<span data-ttu-id="dc7e8-139">Поддержка DateTime и DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="dc7e8-139">DateTime and DateTimeOffset support</span></span>](../datetime/system-text-json-support.md)
* <span data-ttu-id="dc7e8-140">[Справочник по API System.Text.Json](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="dc7e8-140">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
* <span data-ttu-id="dc7e8-141">[Справочник по API System.Text.Json.Serialization](xref:System.Text.Json.Serialization)</span><span class="sxs-lookup"><span data-stu-id="dc7e8-141">[System.Text.Json.Serialization API reference](xref:System.Text.Json.Serialization)</span></span>
