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
# <a name="implement-a-custom-configuration-provider-in-net"></a>Реализация пользовательского поставщика конфигурации в .NET

Есть много [поставщиков конфигурации](configuration-providers.md), доступных для распространенных источников конфигурации, включая файлы JSON, XML и INI. Вам может потребоваться реализовать свой поставщик конфигурации, если ни один из доступных поставщиков не соответствует потребностям вашего приложения. В этой статье показано, как реализовать настраиваемый поставщик конфигурации, который использует базу данных в качестве источника конфигурации.

## <a name="custom-configuration-provider"></a>Поставщик пользовательской конфигурации

Пример приложения демонстрирует, как создать базовый поставщик конфигурации, который считывает пары "ключ — значение" конфигурации из базы данных, используя [Entity Framework (EF) Core](/ef/core).

Поставщик имеет следующие характеристики.

- База данных в памяти EF используется для демонстрационных целей. Чтобы использовать базу данных, для которой требуется строка подключения, выполните вторичный `ConfigurationBuilder`, чтобы предоставить строку подключения от другого поставщика конфигурации.
- Поставщик считывает таблицу базы данных в конфигурации при запуске. Поставщик не запрашивает базу данных для каждого ключа.
- Функция перезагрузки на изменение не реализована, поэтому обновление базы данных после запуска приложения не влияет на конфигурацию приложения.

Определите сущность типа записи `Settings` для хранения значений конфигурации в базе данных. Например, можно добавить файл *Settings.cs* в папку *Models*:

:::code language="csharp" source="snippets/configuration/custom-provider/Models/Settings.cs":::

Сведения о типах записей см. в разделе [Типы записей в C# 9](../../csharp/whats-new/csharp-9.md#record-types).

Добавьте `EntityConfigurationContext` в хранилище и обратитесь к настроенным значениям.

*Providers/EntityConfigurationContext.cs*:

:::code language="csharp" source="snippets/configuration/custom-provider/Providers/EntityConfigurationContext.cs":::

Создайте класс, реализующий <xref:Microsoft.Extensions.Configuration.IConfigurationSource>.

*Providers/EntityConfigurationSource.cs*:

:::code language="csharp" source="snippets/configuration/custom-provider/Providers/EntityConfigurationSource.cs":::

Создайте пользовательский поставщик конфигурации путем наследования от <xref:Microsoft.Extensions.Configuration.ConfigurationProvider>. Поставщик конфигурации инициализирует пустую базу данных. Так как конфигурационные ключи не учитывают регистр, словарь, используемый для инициализации базы данных, создается с помощью функции сравнения без учета регистра ([StringComparer.OrdinalIgnoreCase](xref:System.StringComparer.OrdinalIgnoreCase)).

*Providers/EntityConfigurationProvider.cs*:

:::code language="csharp" source="snippets/configuration/custom-provider/Providers/EntityConfigurationProvider.cs":::

Метод расширения `AddEntityConfiguration` позволяет добавить источник конфигурации к экземпляру <xref:Microsoft.Extensions.Configuration.IConfigurationBuilder>.

*Extensions/ConfigurationBuilderExtensions.cs*:

:::code language="csharp" source="snippets/configuration/custom-provider/Extensions/ConfigurationBuilderExtensions.cs":::

В следующем коде показано, как использовать пользовательский `EntityConfigurationProvider` в *Program.cs*.

:::code language="csharp" source="snippets/configuration/custom-provider/Program.cs" highlight="27-28":::

## <a name="see-also"></a>См. также раздел

- [Конфигурация в .NET](configuration.md)
- [Поставщики конфигурации в .NET](configuration-providers.md)
