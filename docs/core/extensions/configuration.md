---
title: Конфигурация в .NET
description: Узнайте, как использовать API конфигурации для настройки приложений .NET.
author: IEvangelist
ms.author: dapine
ms.date: 09/16/2020
ms.topic: overview
ms.openlocfilehash: 5955e46c2f5acb6776ada4e3fd6a65507d3faa1f
ms.sourcegitcommit: ecd9e9bb2225eb76f819722ea8b24988fe46f34c
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 12/05/2020
ms.locfileid: "102402110"
---
# <a name="configuration-in-net"></a>Конфигурация в .NET

Настройка в .NET выполняется с помощью одного или нескольких [поставщиков конфигурации](#configuration-providers). Поставщики конфигурации получают данные конфигурации в парах "ключ-значение" из различных источников:

- файлы параметров, например *appsettings.json*;
- Переменные среды
- [Azure Key Vault](/azure/key-vault/general/overview);
- [Конфигурация приложений Azure](/azure/azure-app-configuration/overview)
- аргументов командной строки;
- пользовательские поставщики, установленные или созданные;
- справочных файлов;
- объектов .NET в памяти;

## <a name="configure-console-apps"></a>Конфигурация консольных приложений

Новые консольные приложения .NET, созданные с помощью команды [dotnet new](../tools/dotnet-new.md) или в Visual Studio по умолчанию, *не* предоставляют возможности конфигурации. Чтобы добавить конфигурацию в новое консольное приложение .NET, [добавьте ссылку на пакет](../tools/dotnet-add-package.md) в `Microsoft.Extensions.Hosting`. Измените файл *Program.cs* в соответствии с приведенным ниже кодом:

:::code language="csharp" source="snippets/configuration/console/Program.cs" highlight="18":::

Метод <xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder(System.String[])?displayProperty=nameWithType> предоставляет конфигурацию по умолчанию для приложения в следующем порядке:

1. [ChainedConfigurationProvider](xref:Microsoft.Extensions.Configuration.ChainedConfigurationSource): добавляет существующий `IConfiguration` в качестве источника.
1. Файл *appsettings.json*, использующий [поставщик конфигурации JSON](configuration-providers.md#file-configuration-provider).
1. Файл *appsettings.* `Environment` *.json*, использующий [поставщик конфигурации JSON](configuration-providers.md#file-configuration-provider). Например, *appsettings*.***Production**_._json* и *appsettings*.***Development** _._json*.
1. Секреты приложения, когда приложение выполняется в среде `Development`.
1. Переменные среды, использующие [поставщик конфигурации переменных среды](configuration-providers.md#environment-variable-configuration-provider).
1. Аргументы командной строки, использующие [поставщик конфигурации командной строки](configuration-providers.md#command-line-configuration-provider).

Поставщики конфигурации, добавленные позже, переопределяют предыдущие параметры ключа. Например, если `SomeKey` задан в *appsettings.json* и в среде, используется значение среды. При использовании поставщиков конфигурации по умолчанию [поставщик конфигурации командной строки](configuration-providers.md#command-line-configuration-provider) переопределяет остальных поставщиков.

### <a name="binding"></a>Привязка

Одним из ключевых преимуществ конфигурации в .NET является возможность привязки значений конфигурации к экземплярам объектов .NET. Например, поставщика конфигурации JSON можно использовать для сопоставления файлов *appsettings.json* с объектами .NET и использовать с помощью внедрения зависимостей. Это позволяет применять шаблоны параметров, которые используют классы для обеспечения строго типизированного доступа к группам связанных параметров.

## <a name="configuration-providers"></a>Поставщики конфигурации

В следующей таблице показаны поставщики конфигурации, доступные для приложений .NET Core.

| Поставщик                                                                                                               | Предоставляет конфигурацию из        |
|------------------------------------------------------------------------------------------------------------------------|------------------------------------|
| [Поставщик конфигурации приложения Azure](/azure/azure-app-configuration/quickstart-aspnet-core-app)                          | конфигурация приложения Azure;            |
| [Поставщик конфигурации Azure Key Vault](/azure/key-vault/general/tutorial-net-virtual-machine)                        | Хранилище ключей Azure;                    |
| [Поставщик конфигурации командной строки](configuration-providers.md#command-line-configuration-provider)                  | Параметры командной строки            |
| [Поставщик пользовательской конфигурации](custom-configuration-provider.md)                                                      | Источник пользователя                      |
| [Поставщик конфигурации переменных среды](configuration-providers.md#environment-variable-configuration-provider) | Переменные среды              |
| [Поставщик конфигурации файла](configuration-providers.md#file-configuration-provider)                                  | Файлы JSON, XML и INI           |
| [Поставщик конфигурации ключа для каждого файла](configuration-providers.md#key-per-file-configuration-provider)                  | справочных файлов;                    |
| [Поставщик конфигурации памяти](configuration-providers.md#memory-configuration-provider)                              | Коллекции оперативной памяти              |
| [Секреты приложения (диспетчер секретов)](/aspnet/core/security/app-secrets)                                                      | Файл в каталоге профиля пользователя |

Дополнительные сведения о различных поставщиках конфигурации см. в разделе [Поставщики конфигурации в .NET](configuration-providers.md).

## <a name="see-also"></a>См. также раздел

- [Поставщики конфигурации в .NET](configuration-providers.md)
- [Реализация пользовательского поставщика конфигурации](custom-configuration-provider.md)
- Ошибки, связанные с конфигурацией, следует создавать в репозитории [github.com/dotnet/extensions](https://github.com/dotnet/extensions/issues)
