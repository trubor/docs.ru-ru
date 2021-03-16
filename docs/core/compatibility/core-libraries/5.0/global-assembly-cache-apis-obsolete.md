---
title: Критическое изменение. API глобального кэша сборок устарели
description: Сведения о критическом изменении .NET 5 в основных библиотеках .NET, где API, которые используют глобальный кэш сборок, либо завершают работу сбоем, либо не выполняют никаких действий.
ms.date: 11/01/2020
ms.openlocfilehash: 39c7b092b06754a28723693c0147b7ec3a0b705e
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257483"
---
# <a name="global-assembly-cache-apis-are-obsolete"></a>API глобального кэша сборок устарели

В .NET Core и .NET 5 и более поздних версий больше не используется концепция глобального кэша сборок, которая присутствует в .NET Framework. Таким образом, все API .NET Core и .NET 5 и более поздних версий, которые используют глобальный кэш сборок, либо завершают работу сбоем, либо не выполняют никаких действий.

Чтобы помочь разработчикам отказаться от этих API, некоторые связанные с глобальным кэшем сборок API были помечены как устаревшие и во время компиляции приводят к созданию предупреждения `SYSLIB0005`. В последующей версии .NET эти API могут быть исключены.

## <a name="change-description"></a>Описание изменений

Следующие API помечены как устаревшие.

| API | Версия, в которой API помечен как устаревший... |
| - | - |
| <xref:System.Reflection.Assembly.GlobalAssemblyCache?displayProperty=nameWithType> | 5.0 (RC1) |

В .NET Framework версий с 2.x по 4.x свойство <xref:System.Reflection.Assembly.GlobalAssemblyCache> возвращает `true`, если запрашиваемая сборка была загружена из глобального кэша сборок, и `false`, если она была загружена из другого места на диске. В .NET Core версий с 2.x по 3.x свойство <xref:System.Reflection.Assembly.GlobalAssemblyCache> всегда возвращает `false`, указывая, что глобальный кэш сборок в .NET Core не существует.

```csharp
Assembly asm = typeof(object).Assembly;
// Prints 'True' on .NET Framework, 'False' on .NET Core.
Console.WriteLine(asm.GlobalAssemblyCache);
```

В .NET 5 и более поздних версий свойство <xref:System.Reflection.Assembly.GlobalAssemblyCache> также возвращает значение `false`. Тем не менее, метод получения для этого свойства также помечен как устаревший. Таким образом, вызывающие объекты информируются, что им не следует в дальнейшем использовать это свойство. Библиотеки и приложения не должны использовать API <xref:System.Reflection.Assembly.GlobalAssemblyCache> для определения поведения во время выполнения, так как в .NET Core и .NET 5 и более поздних версий он всегда возвращает `false`.

```csharp
Assembly asm = typeof(object).Assembly;
// Prints 'False' on .NET 5.0+; also produces warning SYSLIB0005 at compile time.
Console.WriteLine(asm.GlobalAssemblyCache);
```

Это изменение происходит только во время компиляции. Относительно предыдущих версий .NET Core во время выполнения нет никаких изменений.

## <a name="reason-for-change"></a>Причина изменения

В .NET Core и .NET 5 более не используется концепция глобального кэша сборок.

## <a name="version-introduced"></a>Представленная версия

.NET 5.0

## <a name="recommended-action"></a>Рекомендованное действие

- Если приложение запрашивает свойство <xref:System.Reflection.Assembly.GlobalAssemblyCache>, рассмотрите возможность удалить вызов. Если вы используете значение <xref:System.Reflection.Assembly.GlobalAssemblyCache> для выбора между потоками сборки в глобальном кэше сборок и вне него во время выполнения, еще раз оцените, требуется ли такой поток по-прежнему в приложении .NET Core или .NET 5.0 и более поздних версий.

- Если вам по-прежнему требуется вызывать устаревшие API, вы можете отключить предупреждение `SYSLIB0005` в коде.

  ```csharp
  Assembly asm = typeof(object).Assembly;
  #pragma warning disable SYSLIB0005 // Disable the warning.
  // Prints 'False' on .NET 5.0+.
  Console.WriteLine(asm.GlobalAssemblyCache);
  #pragma warning restore SYSLIB0005 // Re-enable the warning.
  ```

  Также вы можете отключить это предупреждение в файле проекта, что приведет к его отключению для всех исходных файлов в проекте.

  ```xml
  <Project Sdk="Microsoft.NET.Sdk">
    <PropertyGroup>
     <TargetFramework>net5.0</TargetFramework>
     <!-- NoWarn below will suppress SYSLIB0005 project-wide -->
     <NoWarn>$(NoWarn);SYSLIB0005</NoWarn>
    </PropertyGroup>
  </Project>
  ```

  В случае отключения `SYSLIB0005` будет отключено только предупреждение об устаревшем элементе <xref:System.Reflection.Assembly.GlobalAssemblyCache>. Другие предупреждения не отключаются.

## <a name="affected-apis"></a>Затронутые API

- <xref:System.Reflection.Assembly.GlobalAssemblyCache?displayProperty=fullName>

<!--

### Category

Core .NET libraries

### Affected APIs

- `P:System.Reflection.Assembly.GlobalAssemblyCache`

-->
