---
title: 'Критическое изменение: из общей платформы Microsoft.AspNetCore.App удалены сборки'
description: Сведения о критических изменениях в ASP.NET Core 6.0, где некоторые сборки были удалены из общей платформы Microsoft.AspNetCore.App.
ms.date: 04/02/2021
ms.openlocfilehash: e6a0aa97dd97eae2cdc5aa8ae64e277840d6a083
ms.sourcegitcommit: e7e0921d0a10f85e9cb12f8b87cc1639a6c8d3fe
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/09/2021
ms.locfileid: "107255263"
---
# <a name="assemblies-removed-from-microsoftaspnetcoreapp-shared-framework"></a>Сборки, удаленные из общей платформы Microsoft.AspNetCore.App

Из целевого пакета ASP.NET Core были удалены следующие две сборки:

- System.Security.Permissions
- System.Windows.Extensions

Кроме того, следующие сборки были удалены из пакета среды выполнения ASP.NET Core:

- Microsoft.Win32.SystemEvents
- System.Drawing.Common
- System.Security.Permissions
- System.Windows.Extensions

## <a name="version-introduced"></a>Представленная версия

ASP.NET Core 6.0

## <a name="old-behavior"></a>Старое поведение

Приложения могут использовать API из этих библиотек, путем обращения к общей платформе [Microsoft.AspNetCore.App](/aspnet/core/fundamentals/metapackage-app).

## <a name="new-behavior"></a>Новое поведение

Если вы используете API из затронутых сборок без наличия [PackageReference](../../../project-sdk/msbuild-props.md#packagereference) в файле проекта, то могут возникать ошибки во время выполнения кода. Например, в приложении, использующем отражение для доступа к API из одной из этих сборок без добавления явной ссылки на пакет, будут возникать ошибки во время выполнения. Компонент `PackageReference` обеспечивает наличие сборок в выходных данных приложения.

Обсуждение этого вопроса см. на странице <https://github.com/dotnet/aspnetcore/issues/31007>.

## <a name="reason-for-change"></a>Причина изменения

Это изменение было введено для уменьшения размера общей платформы ASP.NET Core.

## <a name="recommended-action"></a>Рекомендованное действие

Чтобы продолжить использование этих API-интерфейсов в проекте, добавьте в него [PackageReference](../../../project-sdk/msbuild-props.md#packagereference). Пример:

```xml
<PackageReference Include="System.Security.Permissions" Version="6.0.0" />
```

## <a name="affected-apis"></a>Затронутые API

- <xref:System.Security.Permissions?displayProperty=fullName>
- <xref:System.Media?displayProperty=fullName>
- <xref:System.Security.Cryptography.X509Certificates.X509Certificate2UI?displayProperty=fullName>
- <xref:System.Xaml.Permissions.XamlAccessLevel?displayProperty=fullName>

<!--

## Category

ASP.NET Core

## Affected APIs

- `N:System.Security.Permissions`
- `N:System.Media`
- `N:System.Security.Cryptography.X509Certificates.X509Certificate2UI`
- `N:System.Xaml.Permissions.XamlAccessLevel`

-->
