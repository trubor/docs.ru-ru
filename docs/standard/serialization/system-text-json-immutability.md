---
title: Как использовать неизменяемые типы и частные методы доступа с помощью System.Text.Json
description: Узнайте, как в .NET использовать неизменяемые типы и частные методы доступа при сериализации в JSON и десериализации из JSON.
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
ms.openlocfilehash: d3e61d44ce22b7f50838b6d3ba9cf64004bd3725
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/01/2020
ms.locfileid: "96439831"
---
# <a name="how-to-use-immutable-types-and-non-public-accessors-with-no-locsystemtextjson"></a><span data-ttu-id="972d6-103">Как использовать неизменяемые типы и частные методы доступа с помощью System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="972d6-103">How to use immutable types and non-public accessors with System.Text.Json</span></span>

<span data-ttu-id="972d6-104">Из этой статьи вы узнаете, как использовать неизменяемые типы, например записи, с помощью пространства имен `System.Text.Json`.</span><span class="sxs-lookup"><span data-stu-id="972d6-104">In this article, you will learn how to use immutable types, such as Records, with the `System.Text.Json` namespace.</span></span>

## <a name="immutable-types-and-records"></a><span data-ttu-id="972d6-105">Неизменяемые типы и записи</span><span class="sxs-lookup"><span data-stu-id="972d6-105">Immutable types and Records</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="972d6-106">`System.Text.Json` может использовать параметризованный конструктор, позволяющий десериализовать неизменяемый класс или структуру.</span><span class="sxs-lookup"><span data-stu-id="972d6-106">`System.Text.Json` can use a parameterized constructor, which makes it possible to deserialize an immutable class or struct.</span></span> <span data-ttu-id="972d6-107">Если для класса существует только параметризованный конструктор, тогда будет использован этот конструктор.</span><span class="sxs-lookup"><span data-stu-id="972d6-107">For a class, if the only constructor is a parameterized one, that constructor will be used.</span></span> <span data-ttu-id="972d6-108">Для структуры или класса с несколькими конструкторами укажите необходимый, применив атрибут [[JsonConstructor]](xref:System.Text.Json.Serialization.JsonConstructorAttribute.%23ctor%2A).</span><span class="sxs-lookup"><span data-stu-id="972d6-108">For a struct, or a class with multiple constructors, specify the one to use by applying the [[JsonConstructor]](xref:System.Text.Json.Serialization.JsonConstructorAttribute.%23ctor%2A) attribute.</span></span> <span data-ttu-id="972d6-109">Если атрибут не используется, тогда всегда применяется общедоступный конструктор без параметров.</span><span class="sxs-lookup"><span data-stu-id="972d6-109">When the attribute is not used, a public parameterless constructor is always used if present.</span></span> <span data-ttu-id="972d6-110">Атрибут используется только с общедоступными конструкторами.</span><span class="sxs-lookup"><span data-stu-id="972d6-110">The attribute can only be used with public constructors.</span></span> <span data-ttu-id="972d6-111">В следующем примере используется атрибут `[JsonConstructor]`.</span><span class="sxs-lookup"><span data-stu-id="972d6-111">The following example uses the `[JsonConstructor]` attribute:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/ImmutableTypes.cs" highlight="13":::

<span data-ttu-id="972d6-112">Записи в C# 9 поддерживаются, как показано в примере:</span><span class="sxs-lookup"><span data-stu-id="972d6-112">Records in C# 9 are also supported, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/Records.cs":::

<span data-ttu-id="972d6-113">Подробнее о неизменяемых типах, чьи методы задания не являются общедоступными, см. в разделе о [методах доступа к свойствам, не являющимся общедоступными](#non-public-property-accessors).</span><span class="sxs-lookup"><span data-stu-id="972d6-113">For types that are immutable because all their property setters are non-public, see the following section about [non-public property accessors](#non-public-property-accessors).</span></span>
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="972d6-114">`JsonConstructorAttribute` и поддержка записи C# 9 недоступны в .NET Core 3.1.</span><span class="sxs-lookup"><span data-stu-id="972d6-114">`JsonConstructorAttribute` and C# 9 Record support aren't available in .NET Core 3.1.</span></span>
::: zone-end

## <a name="non-public-property-accessors"></a><span data-ttu-id="972d6-115">Методы доступа к свойствам, не являющимся общедоступными</span><span class="sxs-lookup"><span data-stu-id="972d6-115">Non-public property accessors</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="972d6-116">Для включения метода доступа к свойству, не являющемуся общедоступным, используйте атрибут [[JsonInclude]](xref:System.Text.Json.Serialization.JsonIncludeAttribute), как показано ниже:</span><span class="sxs-lookup"><span data-stu-id="972d6-116">To enable use of a non-public property accessor, use the [[JsonInclude]](xref:System.Text.Json.Serialization.JsonIncludeAttribute) attribute, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/NonPublicAccessors.cs" highlight="12,15":::
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="972d6-117">Методы доступа к свойству, не являющемуся общедоступным, не поддерживаются в .NET Core 3.1.</span><span class="sxs-lookup"><span data-stu-id="972d6-117">Non-public property accessors are not supported in .NET Core 3.1.</span></span> <span data-ttu-id="972d6-118">Дополнительные сведения см. в статье [о переходе с Newtonsoft.Json](system-text-json-migrate-from-newtonsoft-how-to.md#non-public-property-setters-and-getters).</span><span class="sxs-lookup"><span data-stu-id="972d6-118">For more information, see [the Migrate from Newtonsoft.Json article](system-text-json-migrate-from-newtonsoft-how-to.md#non-public-property-setters-and-getters).</span></span>
::: zone-end

## <a name="see-also"></a><span data-ttu-id="972d6-119">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="972d6-119">See also</span></span>

* [<span data-ttu-id="972d6-120">Общие сведения о System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="972d6-120">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="972d6-121">Создание экземпляров JsonSerializerOptions</span><span class="sxs-lookup"><span data-stu-id="972d6-121">Instantiate JsonSerializerOptions</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="972d6-122">Сопоставление без учета регистра</span><span class="sxs-lookup"><span data-stu-id="972d6-122">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="972d6-123">Настройка имен и значений свойств</span><span class="sxs-lookup"><span data-stu-id="972d6-123">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="972d6-124">Игнорирование свойств</span><span class="sxs-lookup"><span data-stu-id="972d6-124">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="972d6-125">Применение недействительного кода JSON</span><span class="sxs-lookup"><span data-stu-id="972d6-125">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="972d6-126">Обработка переполнения JSON</span><span class="sxs-lookup"><span data-stu-id="972d6-126">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="972d6-127">Сохранение циклических ссылок</span><span class="sxs-lookup"><span data-stu-id="972d6-127">Preserve circular references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="972d6-128">Полиморфная сериализация</span><span class="sxs-lookup"><span data-stu-id="972d6-128">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* <span data-ttu-id="972d6-129">[Справочник по API System.Text.Json](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="972d6-129">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
