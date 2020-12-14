---
title: Сериализация и десериализация JSON с помощью C# — .NET
description: В статье описаны функциональные возможности пространства имен System.Text.Json для сериализации объектов в JSON из .NET и их десериализации наоборот.
ms.date: 01/10/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
ms.openlocfilehash: cb5c15c2a5c336e2d5b4a3754fa7a02a370602f3
ms.sourcegitcommit: 81f1bba2c97a67b5ca76bcc57b37333ffca60c7b
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/10/2020
ms.locfileid: "97009889"
---
# <a name="json-serialization-and-deserialization-marshalling-and-unmarshalling-in-net---overview"></a><span data-ttu-id="f805f-103">Сериализация и десериализация JSON (маршалинг и демаршалинг) в .NET — обзор</span><span class="sxs-lookup"><span data-stu-id="f805f-103">JSON serialization and deserialization (marshalling and unmarshalling) in .NET - overview</span></span>

<span data-ttu-id="f805f-104">Пространство имен `System.Text.Json` предоставляет функциональные возможности для сериализации в нотацию объектов JavaScript (JSON) и десериализации объектов из этой нотации.</span><span class="sxs-lookup"><span data-stu-id="f805f-104">The `System.Text.Json` namespace provides functionality for serializing to and deserializing from JavaScript Object Notation (JSON).</span></span>

<span data-ttu-id="f805f-105">Архитектура библиотеки позволяет обеспечить высокую производительность и низкое выделение памяти для обширного набора функций.</span><span class="sxs-lookup"><span data-stu-id="f805f-105">The library design emphasizes high performance and low memory allocation over an extensive feature set.</span></span> <span data-ttu-id="f805f-106">Встроенная поддержка UTF-8 оптимизирует процесс чтения и записи текста JSON в кодировке UTF-8, которая является наиболее распространенной кодировкой для данных в Интернете и файлов на диске.</span><span class="sxs-lookup"><span data-stu-id="f805f-106">Built-in UTF-8 support optimizes the process of reading and writing JSON text encoded as UTF-8, which is the most prevalent encoding for data on the web and files on disk.</span></span>

<span data-ttu-id="f805f-107">Библиотека также предоставляет классы для работы с объектной моделью документов (DOM) в памяти.</span><span class="sxs-lookup"><span data-stu-id="f805f-107">The library also provides classes for working with an in-memory document object model (DOM).</span></span> <span data-ttu-id="f805f-108">Эта возможность обеспечивает произвольный доступ только для чтения к элементам в файле JSON или строке.</span><span class="sxs-lookup"><span data-stu-id="f805f-108">This feature enables random read-only access of the elements in a JSON file or string.</span></span>

## <a name="how-to-get-the-library"></a><span data-ttu-id="f805f-109">Получение библиотеки</span><span class="sxs-lookup"><span data-stu-id="f805f-109">How to get the library</span></span>

* <span data-ttu-id="f805f-110">Библиотека входит в состав общей платформы для .NET Core 3.0 и более поздних версий.</span><span class="sxs-lookup"><span data-stu-id="f805f-110">The library is built-in as part of the shared framework for .NET Core 3.0 and later versions.</span></span>
* <span data-ttu-id="f805f-111">Для более ранних версий платформы установите пакет NuGet [System.Text.Json](https://www.nuget.org/packages/System.Text.Json).</span><span class="sxs-lookup"><span data-stu-id="f805f-111">For earlier framework versions, install the [System.Text.Json](https://www.nuget.org/packages/System.Text.Json) NuGet package.</span></span> <span data-ttu-id="f805f-112">Пакет поддерживает:</span><span class="sxs-lookup"><span data-stu-id="f805f-112">The package supports:</span></span>

  * <span data-ttu-id="f805f-113">.NET Standard 2.0 и более поздних версий</span><span class="sxs-lookup"><span data-stu-id="f805f-113">.NET Standard 2.0 and later versions</span></span>
  * <span data-ttu-id="f805f-114">.NET Framework 4.7.2 и более поздних версий</span><span class="sxs-lookup"><span data-stu-id="f805f-114">.NET Framework 4.7.2 and later versions</span></span>
  * <span data-ttu-id="f805f-115">.NET Core 2.0, 2.1 и 2.2</span><span class="sxs-lookup"><span data-stu-id="f805f-115">.NET Core 2.0, 2.1, and 2.2</span></span>

## <a name="additional-resources"></a><span data-ttu-id="f805f-116">Дополнительные ресурсы</span><span class="sxs-lookup"><span data-stu-id="f805f-116">Additional resources</span></span>

* [<span data-ttu-id="f805f-117">Использование библиотеки</span><span class="sxs-lookup"><span data-stu-id="f805f-117">How to use the library</span></span>](system-text-json-how-to.md)
* [<span data-ttu-id="f805f-118">Создание экземпляров JsonSerializerOptions</span><span class="sxs-lookup"><span data-stu-id="f805f-118">Instantiate JsonSerializerOptions instances</span></span>](system-text-json-configure-options.md)
* [<span data-ttu-id="f805f-119">Сопоставление без учета регистра</span><span class="sxs-lookup"><span data-stu-id="f805f-119">Enable case-insensitive matching</span></span>](system-text-json-character-casing.md)
* [<span data-ttu-id="f805f-120">Настройка имен и значений свойств</span><span class="sxs-lookup"><span data-stu-id="f805f-120">Customize property names and values</span></span>](system-text-json-customize-properties.md)
* [<span data-ttu-id="f805f-121">Игнорирование свойств</span><span class="sxs-lookup"><span data-stu-id="f805f-121">Ignore properties</span></span>](system-text-json-ignore-properties.md)
* [<span data-ttu-id="f805f-122">Применение недействительного кода JSON</span><span class="sxs-lookup"><span data-stu-id="f805f-122">Allow invalid JSON</span></span>](system-text-json-invalid-json.md)
* [<span data-ttu-id="f805f-123">Обработка переполнения JSON</span><span class="sxs-lookup"><span data-stu-id="f805f-123">Handle overflow JSON</span></span>](system-text-json-handle-overflow.md)
* [<span data-ttu-id="f805f-124">Сохранение ссылок</span><span class="sxs-lookup"><span data-stu-id="f805f-124">Preserve references</span></span>](system-text-json-preserve-references.md)
* [<span data-ttu-id="f805f-125">Неизменяемые типы и непубличные методы доступа</span><span class="sxs-lookup"><span data-stu-id="f805f-125">Immutable types and non-public accessors</span></span>](system-text-json-immutability.md)
* [<span data-ttu-id="f805f-126">Полиморфная сериализация</span><span class="sxs-lookup"><span data-stu-id="f805f-126">Polymorphic serialization</span></span>](system-text-json-polymorphism.md)
* [<span data-ttu-id="f805f-127">Миграция из Newtonsoft.Json в System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="f805f-127">Migrate from Newtonsoft.Json to System.Text.Json</span></span>](system-text-json-migrate-from-newtonsoft-how-to.md)
* [<span data-ttu-id="f805f-128">Настройка кодировки символов</span><span class="sxs-lookup"><span data-stu-id="f805f-128">Customize character encoding</span></span>](system-text-json-character-encoding.md)
* [<span data-ttu-id="f805f-129">Написание пользовательских сериализаторов и десериализаторов</span><span class="sxs-lookup"><span data-stu-id="f805f-129">Write custom serializers and deserializers</span></span>](write-custom-serializer-deserializer.md)
* [<span data-ttu-id="f805f-130">Написание пользовательских преобразователей для сериализации JSON</span><span class="sxs-lookup"><span data-stu-id="f805f-130">Write custom converters for JSON serialization</span></span>](system-text-json-converters-how-to.md)
* [<span data-ttu-id="f805f-131">Поддержка DateTime и DateTimeOffset</span><span class="sxs-lookup"><span data-stu-id="f805f-131">DateTime and DateTimeOffset support</span></span>](../datetime/system-text-json-support.md)
* <span data-ttu-id="f805f-132">[Справочник по API System.Text.Json](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="f805f-132">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
* <span data-ttu-id="f805f-133">[Справочник по API System.Text.Json.Serialization](xref:System.Text.Json.Serialization)</span><span class="sxs-lookup"><span data-stu-id="f805f-133">[System.Text.Json.Serialization API reference](xref:System.Text.Json.Serialization)</span></span>
