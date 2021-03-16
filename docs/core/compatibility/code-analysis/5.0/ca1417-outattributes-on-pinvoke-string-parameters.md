---
title: Критическое изменение. CA1417. OutAttribute в строковом параметре для P/Invoke
description: Узнайте о критическом изменении в .NET 5, вызванном включением правила анализа кода CA1417.
ms.date: 09/29/2020
ms.openlocfilehash: 74aa6dc867bc1eb62e32dd086dd6b43f62e7f01f
ms.sourcegitcommit: 9c589b25b005b9a7f87327646020eb85c3b6306f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/06/2021
ms.locfileid: "102257834"
---
# <a name="warning-ca1417-outattribute-on-string-parameter-for-pinvoke"></a>Предупреждение CA1417: OutAttribute в строковом параметре для P/Invoke

Правило [CA1417](/visualstudio/code-quality/ca1417) анализатора кода .NET включено по умолчанию начиная с .NET 5.0. Оно создает предупреждение сборки для любого определения метода [вызова неуправляемого кода (P/Invoke)](../../../../standard/native-interop/pinvoke.md), в которых параметр <xref:System.String> передается по значению и отмечается с помощью <xref:System.Runtime.InteropServices.OutAttribute>.

## <a name="change-description"></a>Описание изменений

Начиная с .NET 5, пакет SDK для .NET включает [анализаторы исходного кода .NET](../../../../fundamentals/code-analysis/overview.md). Некоторые из этих правил включены по умолчанию, включая [CA1417](/visualstudio/code-quality/ca1417). Если проект содержит код, нарушающий это правило и настроенный на обработку предупреждений как ошибок, это изменение может нарушить сборку.

Флаги правила CA1417 определения методов [P/Invoke](../../../../standard/native-interop/pinvoke.md), в которых параметр <xref:System.String> отмечен атрибутом <xref:System.Runtime.InteropServices.OutAttribute> и передается по значению. Пример:

```csharp
[DllImport("MyLibrary")]
private static extern void PIMethod([Out] string s);
```

Среда выполнения .NET поддерживает таблицу, называемую пулом интернирования, которая содержит одну ссылку на каждую уникальную строку литерала в программе. Если интернированная строка, помеченная <xref:System.Runtime.InteropServices.OutAttribute>, передается по значению в метод P/Invoke, среду выполнения можно дестабилизировать. Дополнительные сведения об интернировании строк см. в разделе примечаний для <xref:System.String.Intern(System.String)?displayProperty=nameWithType>.

## <a name="version-introduced"></a>Представленная версия

5.0

## <a name="recommended-action"></a>Рекомендованное действие

- Если необходимо выполнить маршалирование измененных строковых данных обратно в вызывающий объект, передайте строку по ссылке.

  ```csharp
  [DllImport("MyLibrary")]
  private static extern void PIMethod(out string s);
  ```

- Если вам не нужно маршалировать измененные строковые данные обратно вызывающему объекту, просто удалите <xref:System.Runtime.InteropServices.OutAttribute>.

  ```csharp
  [DllImport("MyLibrary")]
  private static extern void PIMethod(string s);
  ```

  Дополнительные сведения в разделе [CA1417](/visualstudio/code-quality/ca1417).

- Чтобы полностью отключить анализ кода, задайте для параметра `EnableNETAnalyzers` значение `false` в файле проекта. Дополнительные сведения см. в разделе [EnableNETAnalyzers](../../../project-sdk/msbuild-props.md#enablenetanalyzers).

## <a name="affected-apis"></a>Затронутые API

Невозможно обнаружить с помощью анализа API.

<!--

### Affected APIs

Not detectable via API analysis.

### Category

Code analysis

-->
