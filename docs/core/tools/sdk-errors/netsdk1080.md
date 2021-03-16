---
title: 'NETSDK1080: элемент PackageReference для Microsoft.AspNetCore.App не обязателен'
description: Сведения об ошибке NETSDK1080 пакета SDK для .NET, которая предупреждает о необязательной записи в файле проекта.
ms.topic: error-reference
ms.date: 02/25/2021
f1_keywords:
- NETSDK1080
ms.openlocfilehash: ebf9484e4a358597a1177f95e92f68330180cd35
ms.sourcegitcommit: bdbf6472de867a0a11aaa5b9384a2506c24f27d2
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/05/2021
ms.locfileid: "102206793"
---
# <a name="netsdk1080-packagereference-to-microsoftaspnetcoreapp-is-not-necessary"></a>NETSDK1080: элемент PackageReference для Microsoft.AspNetCore.App не обязателен

NETSDK1080 предупреждает, что элемент `PackageReference` для `Microsoft.AspNetCore.App` в файле проекта не является обязательным. Полный текст сообщения об ошибке подобен приведенному ниже.

> Предупреждение NETSDK1080: PackageReference для Microsoft.AspNetCore.App не является обязательным при нацеливании на .NET Core 3.0 или более поздней версии. Если используется Microsoft.NET.Sdk.Web, ссылка на общую платформу будет выполняться автоматически. В противном случае PackageReference следует заменить на FrameworkReference.

Эта ошибка обычно возникает после обновления проекта до .NET Core 3.0 или более поздней версии с более ранней версии, которая требовала записи `PackageReference` в файле проекта.

## <a name="aspnet-core-project-files"></a>Файлы проекта ASP.NET Core

Например, исходный файл проекта может выглядеть, как в следующем примере:

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>netcoreapp2.2</TargetFramework>
    <AspNetCoreHostingModel>InProcess</AspNetCoreHostingModel>
  </PropertyGroup>

  <ItemGroup>
    <PackageReference Include="Microsoft.AspNetCore.App"/>
    <PackageReference Include="Microsoft.AspNetCore.Razor.Design" Version="2.2.0" PrivateAssets="All" />
  </ItemGroup>

</Project>
```

После обновления до .NET Core 3.1 файл проекта для того же проекта должен выглядеть, как в следующем примере:

```xml
<Project Sdk="Microsoft.NET.Sdk.Web">

  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>

</Project>
```

Внесите эти изменения, в частности, удалите элемент `PackageReference`, чтобы устранить предупреждение. Дополнительные сведения см. в разделе [Удаление устаревших ссылок на пакеты](/aspnet/core/migration/22-to-30#remove-obsolete-package-references).

## <a name="class-library-project"></a>Проект библиотеки классов

В проекте библиотеки классов, использующем API ASP.NET Core, замените `PackageReference` на `FrameworkReference`, как показано в следующем примере:

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netcoreapp3.1</TargetFramework>
  </PropertyGroup>

  <ItemGroup>
    <FrameworkReference Include="Microsoft.AspNetCore.App" />
  </ItemGroup>

</Project>
```

Дополнительные сведения см. в разделе [Использование API ASP.NET Core в библиотеке классов](/aspnet/core/fundamentals/target-aspnetcore).
