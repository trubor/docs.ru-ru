---
title: Критическое изменение. API удаленного взаимодействия устарели
description: Сведения о критическом изменении .NET 5 в основных библиотеках .NET, где некоторые API, связанные с удаленным взаимодействием, помечены как устаревшие и приводят к созданию предупреждения с настраиваемым идентификатором диагностики.
ms.date: 11/01/2020
ms.openlocfilehash: 3c4f7cd200cadd11321da60f2b4a0d191497aae8
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257174"
---
# <a name="remoting-apis-are-obsolete"></a>API удаленного взаимодействия устарели

Некоторые API, связанные с удаленным взаимодействием, помечены как устаревшие и приводят к созданию предупреждения `SYSLIB0010` во время компиляции. В последующей версии .NET эти API могут быть исключены.

## <a name="change-description"></a>Описание изменений

Следующие API удаленного взаимодействия помечены как устаревшие.

| API | Версия, в которой API помечен как устаревший... |
| - | - |
| <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=nameWithType> | 5.0 (RC1) |
| <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=nameWithType> | 5.0 (RC1) |

В .NET Framework версий с 2.x по 4.x методы <xref:System.MarshalByRefObject.GetLifetimeService> и <xref:System.MarshalByRefObject.InitializeLifetimeService> управляют временем существования экземпляров, участвующих в удаленном взаимодействии .NET. В .NET Core версий с 2.x по 3.x эти методы всегда приводят к созданию исключения <xref:System.PlatformNotSupportedException> во время выполнения.

В .NET 5 и более поздних версий методы <xref:System.MarshalByRefObject.GetLifetimeService> и <xref:System.MarshalByRefObject.InitializeLifetimeService> помечены как устаревшие с помощью предупреждения, но по-прежнему приводят к созданию исключения <xref:System.PlatformNotSupportedException> во время выполнения.

```csharp
// MemoryStream, like all Stream instances, subclasses MarshalByRefObject.
MemoryStream stream = new MemoryStream();
// Throws PlatformNotSupportedException; also produces warning SYSLIB0010.
obj.InitializeLifetimeService();
```

Это изменение происходит только во время компиляции. Относительно предыдущих версий .NET Core во время выполнения нет никаких изменений.

## <a name="reason-for-change"></a>Причина изменения

Технология [удаленного взаимодействия .NET](/previous-versions/dotnet/netframework-1.1/kwdt6w2k(v=vs.71)) устарела. Она позволяет создать экземпляр объекта в другом процессе (потенциально даже на другом компьютере) и взаимодействовать с этим объектом, как если бы он был обычным внутрипроцессным экземпляром объекта .NET. Инфраструктура удаленного взаимодействия .NET существует только в .NET Framework версий с 2.x по 4.x. .NET Core и .NET 5 и более поздних версий не поддерживают удаленное взаимодействие .NET, а API удаленного взаимодействия в них либо не существуют, либо всегда создают исключения в этих средах выполнения.

Чтобы помочь разработчикам отказаться от этих API, некоторые связанные с удаленным взаимодействием API были помечены как устаревшие. В последующей версии .NET эти API могут быть окончательно исключены.

## <a name="version-introduced"></a>Представленная версия

.NET 5.0

## <a name="recommended-action"></a>Рекомендованное действие

- Для взаимодействия с объектами в других приложениях или на других компьютерах рекомендуется использовать WCF или службы RESTFUL на основе HTTP. Дополнительные сведения см. в разделе [Технологии .NET Framework, недоступные в .NET Core](../../../porting/net-framework-tech-unavailable.md).

- Если вам по-прежнему требуется вызывать устаревшие API, вы можете отключить предупреждение `SYSLIB0010` в коде.

  ```csharp
  MarshalByRefObject obj = GetMarshalByRefObj();
  #pragma warning disable SYSLIB0010 // Disable the warning.
  obj.InitializeLifetimeService(); // Still throws PNSE.
  obj.GetLifetimeService(); // Still throws PNSE.
  #pragma warning restore SYSLIB0010 // Reenable the warning.
  ```

  Также вы можете отключить это предупреждение в файле проекта, что приведет к его отключению для всех исходных файлов в проекте.

  ```xml
  <Project Sdk="Microsoft.NET.Sdk">
    <PropertyGroup>
     <TargetFramework>net5.0</TargetFramework>
     <!-- NoWarn below will suppress SYSLIB0010 project-wide -->
     <NoWarn>$(NoWarn);SYSLIB0010</NoWarn>
    </PropertyGroup>
  </Project>
  ```

  В случае отключения `SYSLIB0010` будет отключено только предупреждение об устаревшем API удаленного взаимодействия. Другие предупреждения не отключаются. Кроме того, при этом не изменяется жестко заданное поведение во время выполнения, которое во всех случаях подразумевает создание исключения <xref:System.PlatformNotSupportedException>.

## <a name="affected-apis"></a>Затронутые API

- <xref:System.MarshalByRefObject.GetLifetimeService?displayProperty=fullName>
- <xref:System.MarshalByRefObject.InitializeLifetimeService?displayProperty=fullName>

<!--

#### Category

Core .NET libraries

### Affected APIs

- `M:System.MarshalByRefObject.GetLifetimeService`
- `M:System.MarshalByRefObject.InitializeLifetimeService`

-->
