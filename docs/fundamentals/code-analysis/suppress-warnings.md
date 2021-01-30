---
title: Подавлять предупреждения анализа кода
description: Узнайте о различных способах отключения нарушений анализа кода .NET.
ms.date: 01/28/2021
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- code analysis, suppress warnings
- suppress code analysis warnings
ms.openlocfilehash: b08e93089975a59fabfeb0daaf6a2a6454b2c7e8
ms.sourcegitcommit: 68c9d9d9a97aab3b59d388914004b5474cf1dbd7
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/30/2021
ms.locfileid: "99217267"
---
# <a name="how-to-suppress-code-analysis-warnings"></a><span data-ttu-id="c0f2f-103">Отключение предупреждений анализа кода</span><span class="sxs-lookup"><span data-stu-id="c0f2f-103">How to suppress code analysis warnings</span></span>

<span data-ttu-id="c0f2f-104">В этой статье рассматриваются различные способы отключения предупреждений из анализа кода при сборке приложения .NET.</span><span class="sxs-lookup"><span data-stu-id="c0f2f-104">This article covers the various ways you can suppress warnings from code analysis when you build your .NET app.</span></span>

> [!TIP]
> <span data-ttu-id="c0f2f-105">Если вы используете Visual Studio в качестве среды разработки, меню *лампочки* содержит параметры, создающие код для подавления предупреждений.</span><span class="sxs-lookup"><span data-stu-id="c0f2f-105">If you're using Visual Studio as your development environment, the *light bulb* menu provides options that generate the code to suppress warnings for you.</span></span> <span data-ttu-id="c0f2f-106">Дополнительные сведения см. в разделе [подавлять нарушения](/visualstudio/code-quality/use-roslyn-analyzers?#suppress-violations).</span><span class="sxs-lookup"><span data-stu-id="c0f2f-106">For more information, see [Suppress violations](/visualstudio/code-quality/use-roslyn-analyzers?#suppress-violations).</span></span>

## <a name="disable-the-rule"></a><span data-ttu-id="c0f2f-107">Отключение правила</span><span class="sxs-lookup"><span data-stu-id="c0f2f-107">Disable the rule</span></span>

<span data-ttu-id="c0f2f-108">При отключении правила анализа кода, которое вызывает предупреждение, вы отключаете правило для всего файла или проекта (в зависимости от используемой области [файла конфигурации](configuration-files.md) ).</span><span class="sxs-lookup"><span data-stu-id="c0f2f-108">By disabling the code analysis rule that's causing the warning, you disable the rule for your entire file or project (depending on the scope of the [configuration file](configuration-files.md) that you use).</span></span> <span data-ttu-id="c0f2f-109">Чтобы отключить правило, установите его серьезность в `none` файле конфигурации.</span><span class="sxs-lookup"><span data-stu-id="c0f2f-109">To disable the rule, set its severity to `none` in the configuration file.</span></span>

```ini
[*.{cs,vb}]
dotnet_diagnostic.<rule-ID>.severity = none
```

<span data-ttu-id="c0f2f-110">Дополнительные сведения о серьезности правил см. в разделе [Настройка серьезности правила](~/docs/fundamentals/code-analysis/configuration-options.md#severity-level).</span><span class="sxs-lookup"><span data-stu-id="c0f2f-110">For more information about rule severities, see [Configure rule severity](~/docs/fundamentals/code-analysis/configuration-options.md#severity-level).</span></span>

## <a name="use-a-preprocessor-directive"></a><span data-ttu-id="c0f2f-111">Использование директивы препроцессора</span><span class="sxs-lookup"><span data-stu-id="c0f2f-111">Use a preprocessor directive</span></span>

<span data-ttu-id="c0f2f-112">Используйте директиву [#pragma warning (C#)](../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md) или [Disable (Visual Basic)](../../visual-basic/language-reference/directives/disable-enable.md) , чтобы отключить предупреждение только для определенной строки кода.</span><span class="sxs-lookup"><span data-stu-id="c0f2f-112">Use a [#pragma warning (C#)](../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md) or [Disable (Visual Basic)](../../visual-basic/language-reference/directives/disable-enable.md) directive to suppress the warning for only a specific line of code.</span></span>

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

## <a name="use-the-suppressmessageattribute"></a><span data-ttu-id="c0f2f-113">Использование Суппрессмессажеаттрибуте</span><span class="sxs-lookup"><span data-stu-id="c0f2f-113">Use the SuppressMessageAttribute</span></span>

<span data-ttu-id="c0f2f-114">Можно использовать, <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> чтобы отключить предупреждение либо в исходном файле, либо в глобальном файле подавления для проекта (*GlobalSuppressions.CS* или *глобалсуппрессионс. vb*).</span><span class="sxs-lookup"><span data-stu-id="c0f2f-114">You can use a <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> to suppress a warning either in the source file or in a global suppressions file for the project (*GlobalSuppressions.cs* or *GlobalSuppressions.vb*).</span></span> <span data-ttu-id="c0f2f-115">Этот атрибут позволяет подавлять предупреждения только в определенных частях проекта или файла.</span><span class="sxs-lookup"><span data-stu-id="c0f2f-115">This attribute provides a way to suppress a warning in only certain parts of your project or file.</span></span>

<span data-ttu-id="c0f2f-116">Два обязательных, позиционированных параметра для <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> атрибута являются *категорией* правила и *идентификатором правила*.</span><span class="sxs-lookup"><span data-stu-id="c0f2f-116">The two required, positional parameters for the <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> attribute are the *category* of the rule and the *rule ID*.</span></span> <span data-ttu-id="c0f2f-117">Следующий фрагмент кода передает `"Usage"` и `"CA2200:Rethrow to preserve stack details"` для этих параметров.</span><span class="sxs-lookup"><span data-stu-id="c0f2f-117">The following code snippet passes `"Usage"` and `"CA2200:Rethrow to preserve stack details"` for these parameters.</span></span>

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

<span data-ttu-id="c0f2f-118">При добавлении атрибута в глобальный файл подавления, например, [область](xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Scope) подавляется до нужного уровня `"member"` .</span><span class="sxs-lookup"><span data-stu-id="c0f2f-118">If you add the attribute to the global suppressions file, you [scope](xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Scope) the suppression to the desired level, for example `"member"`.</span></span> <span data-ttu-id="c0f2f-119">Вы указываете API, где предупреждение следует подавлять с помощью <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Target> Свойства.</span><span class="sxs-lookup"><span data-stu-id="c0f2f-119">You specify the API where the warning should be suppressed using the <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Target> property.</span></span>

```csharp
[assembly: SuppressMessage("Usage", "CA2200:Rethrow to preserve stack details", Justification = "Not production code.", Scope = "member", Target = "~M:MyApp.Program.IngorableCharacters")]
```

<span data-ttu-id="c0f2f-120">Чтобы отключить предупреждения для кода, созданного компилятором, который не соответствует явно предоставленному источнику пользователя, необходимо добавить атрибут подавления в глобальный файл подавления.</span><span class="sxs-lookup"><span data-stu-id="c0f2f-120">To suppress warnings for compiler-generated code that doesn't map to explicitly provided user source, you must put the suppression attribute in a global suppressions file.</span></span> <span data-ttu-id="c0f2f-121">Например, следующий код подавляет нарушение в конструкторе, созданном компилятором:</span><span class="sxs-lookup"><span data-stu-id="c0f2f-121">For example, the following code suppresses a violation against a compiler-emitted constructor:</span></span>

```csharp
[module: SuppressMessage("Microsoft.Design", "CA1055:AbstractTypesDoNotHavePublicConstructors", Scope="member", Target="MyTools.Type..ctor()")]
```

## <a name="see-also"></a><span data-ttu-id="c0f2f-122">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="c0f2f-122">See also</span></span>

- [<span data-ttu-id="c0f2f-123">Подавлять нарушения (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="c0f2f-123">Suppress violations (Visual Studio)</span></span>](/visualstudio/code-quality/use-roslyn-analyzers?#suppress-violations)
