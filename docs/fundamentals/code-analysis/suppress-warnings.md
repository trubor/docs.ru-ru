---
title: Подавление предупреждений анализа кода
description: Узнайте о различных способах подавления нарушений для анализа кода .NET.
ms.date: 01/28/2021
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- code analysis, suppress warnings
- suppress code analysis warnings
ms.openlocfilehash: a8fdfbddd2393f9c6c8cd882a63a9ecc6cb1dc95
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/27/2021
ms.locfileid: "105637043"
---
# <a name="how-to-suppress-code-analysis-warnings"></a><span data-ttu-id="3809e-103">Отключение предупреждений анализа кода</span><span class="sxs-lookup"><span data-stu-id="3809e-103">How to suppress code analysis warnings</span></span>

<span data-ttu-id="3809e-104">В этой статье рассматриваются различные способы подавления предупреждений для анализа кода при сборке приложения .NET.</span><span class="sxs-lookup"><span data-stu-id="3809e-104">This article covers the various ways you can suppress warnings from code analysis when you build your .NET app.</span></span>

> [!TIP]
> <span data-ttu-id="3809e-105">Если вы используете Visual Studio в качестве среды разработки, в меню *лампочки* есть пункты, при выборе которых будет создан код для подавления предупреждений.</span><span class="sxs-lookup"><span data-stu-id="3809e-105">If you're using Visual Studio as your development environment, the *light bulb* menu provides options that generate the code to suppress warnings for you.</span></span> <span data-ttu-id="3809e-106">Дополнительные сведения см. в разделе [Подавление нарушений](/visualstudio/code-quality/use-roslyn-analyzers?#suppress-violations).</span><span class="sxs-lookup"><span data-stu-id="3809e-106">For more information, see [Suppress violations](/visualstudio/code-quality/use-roslyn-analyzers?#suppress-violations).</span></span>

## <a name="disable-the-rule"></a><span data-ttu-id="3809e-107">Отключение правила</span><span class="sxs-lookup"><span data-stu-id="3809e-107">Disable the rule</span></span>

<span data-ttu-id="3809e-108">При отключении правила анализа кода, которое вызывает предупреждение, вы отключаете правило для всего файла или проекта (в зависимости от области используемого [файла конфигурации](configuration-files.md)).</span><span class="sxs-lookup"><span data-stu-id="3809e-108">By disabling the code analysis rule that's causing the warning, you disable the rule for your entire file or project (depending on the scope of the [configuration file](configuration-files.md) that you use).</span></span> <span data-ttu-id="3809e-109">Чтобы отключить правило, установите для него уровень серьезности `none` в файле конфигурации.</span><span class="sxs-lookup"><span data-stu-id="3809e-109">To disable the rule, set its severity to `none` in the configuration file.</span></span>

```ini
[*.{cs,vb}]
dotnet_diagnostic.<rule-ID>.severity = none
```

<span data-ttu-id="3809e-110">Дополнительные сведения об уровнях серьезности правил см. в разделе [Настройка уровня серьезности правила](~/docs/fundamentals/code-analysis/configuration-options.md#severity-level).</span><span class="sxs-lookup"><span data-stu-id="3809e-110">For more information about rule severities, see [Configure rule severity](~/docs/fundamentals/code-analysis/configuration-options.md#severity-level).</span></span>

## <a name="use-a-preprocessor-directive"></a><span data-ttu-id="3809e-111">Использование директивы препроцессора</span><span class="sxs-lookup"><span data-stu-id="3809e-111">Use a preprocessor directive</span></span>

<span data-ttu-id="3809e-112">Используйте директиву [#pragma warning (C#)](../../csharp/language-reference/preprocessor-directives.md#pragma-warning) или [Disable (Visual Basic)](../../visual-basic/language-reference/directives/disable-enable.md), чтобы подавить предупреждение только для определенной строки кода.</span><span class="sxs-lookup"><span data-stu-id="3809e-112">Use a [#pragma warning (C#)](../../csharp/language-reference/preprocessor-directives.md#pragma-warning) or [Disable (Visual Basic)](../../visual-basic/language-reference/directives/disable-enable.md) directive to suppress the warning for only a specific line of code.</span></span>

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

## <a name="use-the-suppressmessageattribute"></a><span data-ttu-id="3809e-113">Использование атрибута SuppressMessageAttribute</span><span class="sxs-lookup"><span data-stu-id="3809e-113">Use the SuppressMessageAttribute</span></span>

<span data-ttu-id="3809e-114">Вы можете использовать <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute>, чтобы подавить предупреждение либо в исходном файле, либо в глобальном файле подавлений для проекта (*GlobalSuppressions.cs* или *GlobalSuppressions.vb*).</span><span class="sxs-lookup"><span data-stu-id="3809e-114">You can use a <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> to suppress a warning either in the source file or in a global suppressions file for the project (*GlobalSuppressions.cs* or *GlobalSuppressions.vb*).</span></span> <span data-ttu-id="3809e-115">Этот атрибут позволяет подавлять предупреждения только в определенных частях проекта или файла.</span><span class="sxs-lookup"><span data-stu-id="3809e-115">This attribute provides a way to suppress a warning in only certain parts of your project or file.</span></span>

<span data-ttu-id="3809e-116">Два обязательных позиционных параметра для атрибута <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> — это *категория* правила и *идентификатор правила*.</span><span class="sxs-lookup"><span data-stu-id="3809e-116">The two required, positional parameters for the <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute> attribute are the *category* of the rule and the *rule ID*.</span></span> <span data-ttu-id="3809e-117">В следующем фрагменте кода передаются значения `"Usage"` и `"CA2200:Rethrow to preserve stack details"` для этих параметров.</span><span class="sxs-lookup"><span data-stu-id="3809e-117">The following code snippet passes `"Usage"` and `"CA2200:Rethrow to preserve stack details"` for these parameters.</span></span>

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

<span data-ttu-id="3809e-118">При добавлении атрибута в глобальный файл подавлений вы указываете желаемый уровень для [области](xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Scope) подавления, например, `"member"`.</span><span class="sxs-lookup"><span data-stu-id="3809e-118">If you add the attribute to the global suppressions file, you [scope](xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Scope) the suppression to the desired level, for example `"member"`.</span></span> <span data-ttu-id="3809e-119">API, в котором следует подавлять предупреждение, указывается с помощью свойства <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Target>.</span><span class="sxs-lookup"><span data-stu-id="3809e-119">You specify the API where the warning should be suppressed using the <xref:System.Diagnostics.CodeAnalysis.SuppressMessageAttribute.Target> property.</span></span>

```csharp
[assembly: SuppressMessage("Usage", "CA2200:Rethrow to preserve stack details", Justification = "Not production code.", Scope = "member", Target = "~M:MyApp.Program.IngorableCharacters")]
```

<span data-ttu-id="3809e-120">Чтобы подавить предупреждения для кода, созданного компилятором, который не соответствует предоставленному явным образом исходному файлу пользователя, необходимо добавить атрибут подавления в глобальный файл подавлений.</span><span class="sxs-lookup"><span data-stu-id="3809e-120">To suppress warnings for compiler-generated code that doesn't map to explicitly provided user source, you must put the suppression attribute in a global suppressions file.</span></span> <span data-ttu-id="3809e-121">Например, следующий код подавляет нарушение в конструкторе, созданном компилятором:</span><span class="sxs-lookup"><span data-stu-id="3809e-121">For example, the following code suppresses a violation against a compiler-emitted constructor:</span></span>

```csharp
[module: SuppressMessage("Microsoft.Design", "CA1055:AbstractTypesDoNotHavePublicConstructors", Scope="member", Target="MyTools.Type..ctor()")]
```

## <a name="see-also"></a><span data-ttu-id="3809e-122">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="3809e-122">See also</span></span>

- [<span data-ttu-id="3809e-123">Подавление нарушений (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="3809e-123">Suppress violations (Visual Studio)</span></span>](/visualstudio/code-quality/use-roslyn-analyzers?#suppress-violations)
