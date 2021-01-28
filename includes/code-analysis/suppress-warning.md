---
ms.openlocfilehash: b26e346f7076a57aef8ae7587ab1222b4100a323
ms.sourcegitcommit: 7e42488c2f8f63f6d499b5f8fb1dec5bac9ad254
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/28/2021
ms.locfileid: "98957940"
---
## <a name="suppress-a-warning"></a><span data-ttu-id="f529f-101">Подавлять предупреждение</span><span class="sxs-lookup"><span data-stu-id="f529f-101">Suppress a warning</span></span>

<span data-ttu-id="f529f-102">Чтобы отключить нарушение правил, установите параметр серьезности для конкретного идентификатора правила `none` в файл EditorConfig.</span><span class="sxs-lookup"><span data-stu-id="f529f-102">To suppress a rule violation, set the severity option for the specific rule ID to `none` in an EditorConfig file.</span></span> <span data-ttu-id="f529f-103">Пример:</span><span class="sxs-lookup"><span data-stu-id="f529f-103">For example:</span></span>

```ini
[*.{cs,vb}]
dotnet_diagnostic.CA1822.severity = none
```

<span data-ttu-id="f529f-104">Visual Studio предоставляет дополнительные способы отключения предупреждений из правил анализа кода.</span><span class="sxs-lookup"><span data-stu-id="f529f-104">Visual Studio provides additional ways to suppress warnings from code analysis rules.</span></span> <span data-ttu-id="f529f-105">Дополнительные сведения см. в разделе [подавлять нарушения](/visualstudio/code-quality/use-roslyn-analyzers#suppress-violations).</span><span class="sxs-lookup"><span data-stu-id="f529f-105">For more information, see [Suppress violations](/visualstudio/code-quality/use-roslyn-analyzers#suppress-violations).</span></span>

<span data-ttu-id="f529f-106">Дополнительные сведения о серьезности правил см. в разделе [Настройка серьезности правила](~/docs/fundamentals/code-analysis/configuration-options.md#severity-level).</span><span class="sxs-lookup"><span data-stu-id="f529f-106">For more information about rule severities, see [Configure rule severity](~/docs/fundamentals/code-analysis/configuration-options.md#severity-level).</span></span>
