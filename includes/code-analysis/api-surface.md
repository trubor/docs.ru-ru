---
ms.openlocfilehash: bf7ea8a36b9c36d82b4c00ada890829bf4c2c024
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2021
ms.locfileid: "97700868"
---
### <a name="include-specific-api-surfaces"></a><span data-ttu-id="3257d-101">Включение определенных контактных зон API</span><span class="sxs-lookup"><span data-stu-id="3257d-101">Include specific API surfaces</span></span>

<span data-ttu-id="3257d-102">Вы можете настроить, для каких частей базы кода следует выполнять это правило в зависимости от их доступности.</span><span class="sxs-lookup"><span data-stu-id="3257d-102">You can configure which parts of your codebase to run this rule on, based on their accessibility.</span></span> <span data-ttu-id="3257d-103">Например, чтобы указать, что правило должно выполняться только для закрытой контактной зоны API, добавьте следующую пару "ключ-значение" в файл *EDITORCONFIG* в своем проекте:</span><span class="sxs-lookup"><span data-stu-id="3257d-103">For example, to specify that the rule should run only against the non-public API surface, add the following key-value pair to an *.editorconfig* file in your project:</span></span>

```ini
dotnet_code_quality.CAXXXX.api_surface = private, internal
```
