---
title: Реализация пользовательского поставщика конфигурации в .NET
description: Узнайте, как реализовать пользовательский поставщик конфигурации в приложениях .NET.
author: IEvangelist
ms.author: dapine
ms.date: 12/04/2020
ms.topic: how-to
ms.openlocfilehash: 22e46b7df8b02421633d6be251d990879baa8b2b
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2020
ms.locfileid: "102402109"
---
# <a name="implement-a-custom-configuration-provider-in-net"></a><span data-ttu-id="8f8d6-103">Реализация пользовательского поставщика конфигурации в .NET</span><span class="sxs-lookup"><span data-stu-id="8f8d6-103">Implement a custom configuration provider in .NET</span></span>

<span data-ttu-id="8f8d6-104">Есть много [поставщиков конфигурации](configuration-providers.md), доступных для распространенных источников конфигурации, включая файлы JSON, XML и INI.</span><span class="sxs-lookup"><span data-stu-id="8f8d6-104">There are many [configuration providers](configuration-providers.md) available for common configuration sources such as JSON, XML, and INI files.</span></span> <span data-ttu-id="8f8d6-105">Вам может потребоваться реализовать свой поставщик конфигурации, если ни один из доступных поставщиков не соответствует потребностям вашего приложения.</span><span class="sxs-lookup"><span data-stu-id="8f8d6-105">You may need to implement a custom configuration provider when one of the available providers doesn't suit your application needs.</span></span> <span data-ttu-id="8f8d6-106">В этой статье показано, как реализовать настраиваемый поставщик конфигурации, который использует базу данных в качестве источника конфигурации.</span><span class="sxs-lookup"><span data-stu-id="8f8d6-106">In this article, you'll learn how to implement a custom configuration provider that relies on a database as its configuration source.</span></span>

## <a name="custom-configuration-provider"></a><span data-ttu-id="8f8d6-107">Поставщик пользовательской конфигурации</span><span class="sxs-lookup"><span data-stu-id="8f8d6-107">Custom configuration provider</span></span>

<span data-ttu-id="8f8d6-108">Пример приложения демонстрирует, как создать базовый поставщик конфигурации, который считывает пары "ключ — значение" конфигурации из базы данных, используя [Entity Framework (EF) Core](/ef/core).</span><span class="sxs-lookup"><span data-stu-id="8f8d6-108">The sample app demonstrates how to create a basic configuration provider that reads configuration key-value pairs from a database using [Entity Framework (EF) Core](/ef/core).</span></span>

<span data-ttu-id="8f8d6-109">Поставщик имеет следующие характеристики.</span><span class="sxs-lookup"><span data-stu-id="8f8d6-109">The provider has the following characteristics:</span></span>

- <span data-ttu-id="8f8d6-110">База данных в памяти EF используется для демонстрационных целей.</span><span class="sxs-lookup"><span data-stu-id="8f8d6-110">The EF in-memory database is used for demonstration purposes.</span></span> <span data-ttu-id="8f8d6-111">Чтобы использовать базу данных, для которой требуется строка подключения, выполните вторичный `ConfigurationBuilder`, чтобы предоставить строку подключения от другого поставщика конфигурации.</span><span class="sxs-lookup"><span data-stu-id="8f8d6-111">To use a database that requires a connection string, implement a secondary `ConfigurationBuilder` to supply the connection string from another configuration provider.</span></span>
- <span data-ttu-id="8f8d6-112">Поставщик считывает таблицу базы данных в конфигурации при запуске.</span><span class="sxs-lookup"><span data-stu-id="8f8d6-112">The provider reads a database table into configuration at startup.</span></span> <span data-ttu-id="8f8d6-113">Поставщик не запрашивает базу данных для каждого ключа.</span><span class="sxs-lookup"><span data-stu-id="8f8d6-113">The provider doesn't query the database on a per-key basis.</span></span>
- <span data-ttu-id="8f8d6-114">Функция перезагрузки на изменение не реализована, поэтому обновление базы данных после запуска приложения не влияет на конфигурацию приложения.</span><span class="sxs-lookup"><span data-stu-id="8f8d6-114">Reload-on-change isn't implemented, so updating the database after the app starts has no effect on the app's configuration.</span></span>

<span data-ttu-id="8f8d6-115">Определите сущность типа записи `Settings` для хранения значений конфигурации в базе данных.</span><span class="sxs-lookup"><span data-stu-id="8f8d6-115">Define a `Settings` record type entity for storing configuration values in the database.</span></span> <span data-ttu-id="8f8d6-116">Например, можно добавить файл *Settings.cs* в папку *Models*:</span><span class="sxs-lookup"><span data-stu-id="8f8d6-116">For example, you could add a *Settings.cs* file in your *Models* folder:</span></span>

:::code language="csharp" source="snippets/configuration/custom-provider/Models/Settings.cs":::

<span data-ttu-id="8f8d6-117">Сведения о типах записей см. в разделе [Типы записей в C# 9](../../csharp/whats-new/csharp-9.md#record-types).</span><span class="sxs-lookup"><span data-stu-id="8f8d6-117">For information on record types, see [Record types in C# 9](../../csharp/whats-new/csharp-9.md#record-types).</span></span>

<span data-ttu-id="8f8d6-118">Добавьте `EntityConfigurationContext` в хранилище и обратитесь к настроенным значениям.</span><span class="sxs-lookup"><span data-stu-id="8f8d6-118">Add an `EntityConfigurationContext` to store and access the configured values.</span></span>

<span data-ttu-id="8f8d6-119">*Providers/EntityConfigurationContext.cs*:</span><span class="sxs-lookup"><span data-stu-id="8f8d6-119">*Providers/EntityConfigurationContext.cs*:</span></span>

:::code language="csharp" source="snippets/configuration/custom-provider/Providers/EntityConfigurationContext.cs":::

<span data-ttu-id="8f8d6-120">Создайте класс, реализующий <xref:Microsoft.Extensions.Configuration.IConfigurationSource>.</span><span class="sxs-lookup"><span data-stu-id="8f8d6-120">Create a class that implements <xref:Microsoft.Extensions.Configuration.IConfigurationSource>.</span></span>

<span data-ttu-id="8f8d6-121">*Providers/EntityConfigurationSource.cs*:</span><span class="sxs-lookup"><span data-stu-id="8f8d6-121">*Providers/EntityConfigurationSource.cs*:</span></span>

:::code language="csharp" source="snippets/configuration/custom-provider/Providers/EntityConfigurationSource.cs":::

<span data-ttu-id="8f8d6-122">Создайте пользовательский поставщик конфигурации путем наследования от <xref:Microsoft.Extensions.Configuration.ConfigurationProvider>.</span><span class="sxs-lookup"><span data-stu-id="8f8d6-122">Create the custom configuration provider by inheriting from <xref:Microsoft.Extensions.Configuration.ConfigurationProvider>.</span></span> <span data-ttu-id="8f8d6-123">Поставщик конфигурации инициализирует пустую базу данных.</span><span class="sxs-lookup"><span data-stu-id="8f8d6-123">The configuration provider initializes the database when it's empty.</span></span> <span data-ttu-id="8f8d6-124">Так как конфигурационные ключи не учитывают регистр, словарь, используемый для инициализации базы данных, создается с помощью функции сравнения без учета регистра ([StringComparer.OrdinalIgnoreCase](xref:System.StringComparer.OrdinalIgnoreCase)).</span><span class="sxs-lookup"><span data-stu-id="8f8d6-124">Since configuration keys are case-insensitive, the dictionary used to initialize the database is created with the case-insensitive comparer ([StringComparer.OrdinalIgnoreCase](xref:System.StringComparer.OrdinalIgnoreCase)).</span></span>

<span data-ttu-id="8f8d6-125">*Providers/EntityConfigurationProvider.cs*:</span><span class="sxs-lookup"><span data-stu-id="8f8d6-125">*Providers/EntityConfigurationProvider.cs*:</span></span>

:::code language="csharp" source="snippets/configuration/custom-provider/Providers/EntityConfigurationProvider.cs":::

<span data-ttu-id="8f8d6-126">Метод расширения `AddEntityConfiguration` позволяет добавить источник конфигурации к экземпляру <xref:Microsoft.Extensions.Configuration.IConfigurationBuilder>.</span><span class="sxs-lookup"><span data-stu-id="8f8d6-126">An `AddEntityConfiguration` extension method permits adding the configuration source to a <xref:Microsoft.Extensions.Configuration.IConfigurationBuilder> instance.</span></span>

<span data-ttu-id="8f8d6-127">*Extensions/ConfigurationBuilderExtensions.cs*:</span><span class="sxs-lookup"><span data-stu-id="8f8d6-127">*Extensions/ConfigurationBuilderExtensions.cs*:</span></span>

:::code language="csharp" source="snippets/configuration/custom-provider/Extensions/ConfigurationBuilderExtensions.cs":::

<span data-ttu-id="8f8d6-128">В следующем коде показано, как использовать пользовательский `EntityConfigurationProvider` в *Program.cs*.</span><span class="sxs-lookup"><span data-stu-id="8f8d6-128">The following code shows how to use the custom `EntityConfigurationProvider` in *Program.cs*:</span></span>

:::code language="csharp" source="snippets/configuration/custom-provider/Program.cs" highlight="27-28":::

## <a name="see-also"></a><span data-ttu-id="8f8d6-129">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="8f8d6-129">See also</span></span>

- [<span data-ttu-id="8f8d6-130">Конфигурация в .NET</span><span class="sxs-lookup"><span data-stu-id="8f8d6-130">Configuration in .NET</span></span>](configuration.md)
- [<span data-ttu-id="8f8d6-131">Поставщики конфигурации в .NET</span><span class="sxs-lookup"><span data-stu-id="8f8d6-131">Configuration providers in .NET</span></span>](configuration-providers.md)
