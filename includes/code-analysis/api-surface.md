---
ms.openlocfilehash: bf7ea8a36b9c36d82b4c00ada890829bf4c2c024
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2021
ms.locfileid: "97700868"
---
### <a name="include-specific-api-surfaces"></a>Включение определенных контактных зон API

Вы можете настроить, для каких частей базы кода следует выполнять это правило в зависимости от их доступности. Например, чтобы указать, что правило должно выполняться только для закрытой контактной зоны API, добавьте следующую пару "ключ-значение" в файл *EDITORCONFIG* в своем проекте:

```ini
dotnet_code_quality.CAXXXX.api_surface = private, internal
```
