---
title: Создание экземпляров JsonSerializerOptions с помощью System.Text.Json
description: Узнайте, как создавать экземпляры JsonSerializerOptions путем копирования существующих экземпляров или с помощью стандартных параметров веб-приложения.
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
ms.openlocfilehash: 0febfe15f36856f10699fd327fb17c146277eb9b
ms.sourcegitcommit: 721c3e4bdbb1ea0bb420818ec944c538fe5c513a
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/01/2020
ms.locfileid: "96439871"
---
# <a name="how-to-instantiate-jsonserializeroptions-instances-with-no-locsystemtextjson"></a><span data-ttu-id="61e07-103">Создание экземпляров JsonSerializerOptions с помощью System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="61e07-103">How to instantiate JsonSerializerOptions instances with System.Text.Json</span></span>

<span data-ttu-id="61e07-104">Из этой статьи вы узнаете, как создавать экземпляры <xref:System.Text.Json.JsonSerializerOptions> путем копирования существующих экземпляров или с помощью стандартных параметров веб-приложения.</span><span class="sxs-lookup"><span data-stu-id="61e07-104">In this article, you'll learn how to instantiate <xref:System.Text.Json.JsonSerializerOptions> instances by copying existing instances or with web defaults.</span></span>

## <a name="copy-jsonserializeroptions"></a><span data-ttu-id="61e07-105">Копирование JsonSerializerOptions</span><span class="sxs-lookup"><span data-stu-id="61e07-105">Copy JsonSerializerOptions</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="61e07-106">Существует [конструктор JsonSerializerOptions](xref:System.Text.Json.JsonSerializerOptions.%23ctor(System.Text.Json.JsonSerializerOptions)), который позволяет создавать новый экземпляр с параметрами, использованными для существующего экземпляра:</span><span class="sxs-lookup"><span data-stu-id="61e07-106">There is a [JsonSerializerOptions constructor](xref:System.Text.Json.JsonSerializerOptions.%23ctor(System.Text.Json.JsonSerializerOptions)) that lets you create a new instance with the same options as an existing instance, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/CopyOptions.cs" highlight="29":::
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="61e07-107">Конструктор `JsonSerializerOptions`, который принимает существующий экземпляр, недоступен в .NET Core 3.1.</span><span class="sxs-lookup"><span data-stu-id="61e07-107">A `JsonSerializerOptions` constructor that takes an existing instance is not available in .NET Core 3.1.</span></span>
::: zone-end

## <a name="web-defaults-for-jsonserializeroptions"></a><span data-ttu-id="61e07-108">Стандартные параметры веб-приложений для JsonSerializerOptions</span><span class="sxs-lookup"><span data-stu-id="61e07-108">Web defaults for JsonSerializerOptions</span></span>

::: zone pivot="dotnet-5-0"
<span data-ttu-id="61e07-109">Ниже приведены параметры с различными значениями по умолчанию для веб-приложений:</span><span class="sxs-lookup"><span data-stu-id="61e07-109">Here are the options that have different defaults for web apps:</span></span>

* <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive%2A> = `true`
* <xref:System.Text.Json.JsonNamingPolicy> = <xref:System.Text.Json.JsonNamingPolicy.CamelCase>
* <xref:System.Text.Json.JsonSerializerOptions.NumberHandling%2A> = <xref:System.Text.Json.Serialization.JsonNumberHandling.AllowReadingFromString>

<span data-ttu-id="61e07-110">Существует [конструктор JsonSerializerOptions](xref:System.Text.Json.JsonSerializerOptions.%23ctor(System.Text.Json.JsonSerializerDefaults)?view=net-5.0&preserve-view=true), который позволяет создавать новый экземпляр со стандартными параметрами, которые ASP.NET Core использует для веб-приложений, как показано ниже:</span><span class="sxs-lookup"><span data-stu-id="61e07-110">There's a [JsonSerializerOptions constructor](xref:System.Text.Json.JsonSerializerOptions.%23ctor(System.Text.Json.JsonSerializerDefaults)?view=net-5.0&preserve-view=true) that lets you create a new instance with the default options that ASP.NET Core uses for web apps, as shown in the following example:</span></span>

:::code language="csharp" source="snippets/system-text-json-how-to-5-0/csharp/OptionsDefaults.cs" highlight="24":::
::: zone-end

::: zone pivot="dotnet-core-3-1"
<span data-ttu-id="61e07-111">Ниже приведены параметры с различными значениями по умолчанию для веб-приложений:</span><span class="sxs-lookup"><span data-stu-id="61e07-111">Here are the options that have different defaults for web apps:</span></span>

* <xref:System.Text.Json.JsonSerializerOptions.PropertyNameCaseInsensitive%2A> = `true`
* <xref:System.Text.Json.JsonNamingPolicy> = <xref:System.Text.Json.JsonNamingPolicy.CamelCase>

<span data-ttu-id="61e07-112">Конструктор `JsonSerializerOptions`, указывающий набор значений по умолчанию, недоступен в .NET Core 3.1.</span><span class="sxs-lookup"><span data-stu-id="61e07-112">A `JsonSerializerOptions` constructor that specifies a set of defaults is not available in .NET Core 3.1.</span></span>
::: zone-end

## <a name="see-also"></a><span data-ttu-id="61e07-113">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="61e07-113">See also</span></span>

* [<span data-ttu-id="61e07-114">Общие сведения о System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="61e07-114">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="61e07-115">Сопоставление без учета регистра</span><span class="sxs-lookup"><span data-stu-id="61e07-115">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="61e07-116">Настройка имен и значений свойств</span><span class="sxs-lookup"><span data-stu-id="61e07-116">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="61e07-117">Игнорирование свойств</span><span class="sxs-lookup"><span data-stu-id="61e07-117">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="61e07-118">Применение недействительного кода JSON</span><span class="sxs-lookup"><span data-stu-id="61e07-118">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="61e07-119">Обработка переполнения JSON</span><span class="sxs-lookup"><span data-stu-id="61e07-119">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="61e07-120">Сохранение циклических ссылок</span><span class="sxs-lookup"><span data-stu-id="61e07-120">Preserve circular references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="61e07-121">Неизменяемые типы и непубличные методы доступа</span><span class="sxs-lookup"><span data-stu-id="61e07-121">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="61e07-122">Полиморфная сериализация</span><span class="sxs-lookup"><span data-stu-id="61e07-122">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* <span data-ttu-id="61e07-123">[Справочник по API System.Text.Json](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="61e07-123">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
