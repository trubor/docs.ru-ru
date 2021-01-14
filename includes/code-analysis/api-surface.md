---
ms.openlocfilehash: bf7ea8a36b9c36d82b4c00ada890829bf4c2c024
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 01/14/2021
ms.locfileid: "97700868"
---
### <a name="include-specific-api-surfaces"></a><span data-ttu-id="f321a-101">Включить определенные поверхности API</span><span class="sxs-lookup"><span data-stu-id="f321a-101">Include specific API surfaces</span></span>

<span data-ttu-id="f321a-102">Вы можете настроить, на какие части базы кода следует запускать это правило, в зависимости от их доступности.</span><span class="sxs-lookup"><span data-stu-id="f321a-102">You can configure which parts of your codebase to run this rule on, based on their accessibility.</span></span> <span data-ttu-id="f321a-103">Например, чтобы указать, что правило должно выполняться только для поверхности API, не являющейся общедоступной, добавьте следующую пару "ключ-значение" в файл *. editorconfig* в проекте:</span><span class="sxs-lookup"><span data-stu-id="f321a-103">For example, to specify that the rule should run only against the non-public API surface, add the following key-value pair to an *.editorconfig* file in your project:</span></span>

```ini
dotnet_code_quality.CAXXXX.api_surface = private, internal
```
