---
title: 'Критическое изменение. Azure: Пакеты интеграции Azure с префиксом Майкрософт удалены'
description: 'Сведения о критическом изменении в ASP.NET Core 5.0 под названием Azure: Пакеты интеграции Azure с префиксом Майкрософт удалены'
ms.author: scaddie
ms.date: 10/01/2020
ms.openlocfilehash: be7b2eeb6b12d033517c15ecb29e0d5364d64817
ms.sourcegitcommit: 089068389671f6f9e15fd67dcbfb0145bf72f1fb
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/06/2021
ms.locfileid: "106498234"
---
# <a name="azure-microsoft-prefixed-azure-integration-packages-removed"></a>Azure Пакеты интеграции Azure с префиксом Майкрософт удалены

Следующие пакеты `Microsoft.*`, обеспечивающие интеграцию между ASP.NET Core и пакетами SDK для Azure, не входят в ASP.NET Core 5.0:

* [Microsoft.Extensions.Configuration.AzureKeyVault](https://www.nuget.org/packages/Microsoft.Extensions.Configuration.AzureKeyVault/), который интегрирует [Azure Key Vault](/azure/key-vault/) в [систему конфигурации](/aspnet/core/fundamentals/configuration/).
* [Microsoft.AspNetCore.Data Protection.AzureKeyVault](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.AzureKeyVault/), который интегрирует Azure Key Vault в [систему защиты данных ASP.NET Core](/aspnet/core/security/data-protection/introduction).
* [Microsoft.AspNetCore.Data Protection.AzureStorage](https://www.nuget.org/packages/Microsoft.AspNetCore.DataProtection.AzureStorage/), который интегрирует [хранилище BLOB-объектов Azure](/azure/storage/blobs/) в систему защиты данных ASP.NET Core.

Обсуждение этого вопроса см. на странице [dotnet/aspnetcore#19570](https://github.com/dotnet/aspnetcore/issues/19570).

## <a name="version-introduced"></a>Представленная версия

5.0 Предварительная версия 1

## <a name="old-behavior"></a>Старое поведение

Пакеты `Microsoft.*` интегрированных служб Azure с API конфигурации и защиты данных.

## <a name="new-behavior"></a>Новое поведение

Новые пакеты `Azure.*` интегрируют службы Azure с API конфигурации и защиты данных.

## <a name="reason-for-change"></a>Причина изменения

Изменение внесено, поскольку `Microsoft.*` пакеты:

* использовали устаревшие версии пакета SDK Azure; Простые обновления не были доступны, поскольку новые версии пакета SDK для Azure включали критические изменения.
* связаны с расписанием выпуска .NET Core; Передача прав владения пакетами в группу пакета SDK Azure позволяет обновлять пакеты при обновлении пакета SDK для Azure.

## <a name="recommended-action"></a>Рекомендованное действие

В проектах ASP.NET Core 2.1 или более поздней версии замените старые `Microsoft.*` на новые пакеты `Azure.*`.

| Прежний вариант | Оператор new |
|--|--|
| `Microsoft.AspNetCore.DataProtection.AzureKeyVault` | [Azure.Extensions.AspNetCore.DataProtection.Keys](https://www.nuget.org/packages/Azure.Extensions.AspNetCore.DataProtection.Keys) |
| `Microsoft.AspNetCore.DataProtection.AzureStorage` | [Azure.Extensions.AspNetCore.DataProtection.Blobs](https://www.nuget.org/packages/Azure.Extensions.AspNetCore.DataProtection.Blobs) |
| `Microsoft.Extensions.Configuration.AzureKeyVault` | [Azure.Extensions.AspNetCore.Configuration.Secrets](https://www.nuget.org/packages/Azure.Extensions.AspNetCore.Configuration.Secrets) |

Новые пакеты используют новую версию пакета SDK для Azure, включающую критические изменения. Шаблоны общего использования не изменяются. Некоторые перегрузки и параметры могут отличаться для адаптации к изменениям в базовых API пакета SDK для Azure.

Старые пакеты будут:

* поддерживаться командой ASP.NET Core в течение времени существования версий .NET Core 2.1 и 3.1;
* исключены в .NET 5.

Для поддержки при обновлении проекта до версии .NET 5 переходите к пакетам `Azure.*`.

## <a name="affected-apis"></a>Затронутые API

- <xref:Microsoft.Extensions.Configuration.AzureKeyVaultConfigurationExtensions.AddAzureKeyVault%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.ProtectKeysWithAzureKeyVault%2A?displayProperty=nameWithType>
- <xref:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.PersistKeysToAzureBlobStorage%2A?displayProperty=nameWithType>

<!--

### Category

ASP.NET Core

### Affected APIs

- `Overload:Microsoft.Extensions.Configuration.AzureKeyVaultConfigurationExtensions.AddAzureKeyVault`
- `Overload:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.ProtectKeysWithAzureKeyVault`
- `Overload:Microsoft.AspNetCore.DataProtection.AzureDataProtectionBuilderExtensions.PersistKeysToAzureBlobStorage`

-->
