---
title: Подавление предупреждений анализа кода
description: Узнайте о различных способах подавления нарушений для анализа кода .NET.
ms.date: 01/28/2021
ms-topic: how-to
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- code analysis, suppress warnings
- suppress code analysis warnings
ms.openlocfilehash: a2c85a032c8754be2a1c5c6c8cee06754b3231f2
ms.sourcegitcommit: 8f71a6c655a9c39d5223401aed76c02ba00e03ee
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 04/20/2021
ms.locfileid: "107740557"
---
# <a name="how-to-suppress-code-analysis-warnings"></a>Отключение предупреждений анализа кода

В этой статье рассматриваются различные способы подавления предупреждений для анализа кода при сборке приложения .NET.

> [!TIP]
> Если вы используете Visual Studio в качестве среды разработки, в меню *лампочки* есть пункты, при выборе которых будет создан код для подавления предупреждений. Дополнительные сведения см. в разделе [Подавление нарушений](/visualstudio/code-quality/use-roslyn-analyzers?#suppress-violations).

## <a name="disable-the-rule"></a>Отключение правила

При отключении правила анализа кода, которое вызывает предупреждение, вы отключаете правило для всего файла или проекта (в зависимости от области используемого [файла конфигурации](configuration-files.md)). Чтобы отключить правило, установите для него уровень серьезности `none` в файле конфигурации.

```ini
[*.{cs,vb}]
dotnet_diagnostic.<rule-ID>.severity = none
```

Дополнительные сведения об уровнях серьезности правил см. в разделе [Настройка уровня серьезности правила](~/docs/fundamentals/code-analysis/configuration-options.md#severity-level).

## <a name="use-a-preprocessor-directive"></a>Использование директивы препроцессора

Используйте директиву [#pragma warning (C#)](../../csharp/language-reference/preprocessor-directives.md#pragma-warning) или [Disable (Visual Basic)](../../visual-basic/language-reference/directives/disable-enable.md), чтобы подавить предупреждение только для определенной строки кода.

```csharp
    try { ... }
    catch (Exception e)
    {
#pragma warning disable CA2200 // Rethrow to preserve stack details
        throw e;
#pragma warning restore CA2200 // Rethrow to preserve stack details
    }
```

```vb
    Try
        ...
    Catch e As Exception
#Disable Warning CA2200 ' Rethrow to preserve stack details
        Throw e
#Enable Warning CA2200 ' Rethrow to preserve stack details
    End Try
```

## <a name="use-the-suppressmessageattribute"></a>Использование атрибута SuppressMessageAttribute

Вы можете использовать <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute>, чтобы подавить предупреждение либо в исходном файле, либо в глобальном файле подавлений для проекта (*GlobalSuppressions.cs* или *GlobalSuppressions.vb*). Этот атрибут позволяет подавлять предупреждения только в определенных частях проекта или файла.

Два обязательных позиционных параметра для атрибута <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> — это *категория* правила и *идентификатор правила*. В следующем фрагменте кода передаются значения `"Usage"` и `"CA2200:Rethrow to preserve stack details"` для этих параметров.

```csharp
[System.Diagnostics.CodeAnalysis.SuppressMessage("Usage", "CA2200:Rethrow to preserve stack details", Justification = "Not production code.")]
private static void IngorableCharacters()
{
    try
    {
        ...
    }
    catch (Exception e)
    {
        throw e;
    }
}
```

При добавлении атрибута в глобальный файл подавлений вы указываете желаемый уровень для [области](xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Scope) подавления, например, `"member"`. API, в котором следует подавлять предупреждение, указывается с помощью свойства <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Target>.

```csharp
[assembly: SuppressMessage("Usage", "CA2200:Rethrow to preserve stack details", Justification = "Not production code.", Scope = "member", Target = "~M:MyApp.Program.IngorableCharacters")]
```

Чтобы подавить предупреждения для кода, созданного компилятором, который не соответствует предоставленному явным образом исходному файлу пользователя, необходимо добавить атрибут подавления в глобальный файл подавлений. Например, следующий код подавляет нарушение в конструкторе, созданном компилятором:

```csharp
[module: SuppressMessage("Microsoft.Design", "CA1055:AbstractTypesDoNotHavePublicConstructors", Scope="member", Target="MyTools.Type..ctor()")]
```

## <a name="see-also"></a>См. также раздел

- [Подавление нарушений (Visual Studio)](/visualstudio/code-quality/use-roslyn-analyzers?#suppress-violations)
