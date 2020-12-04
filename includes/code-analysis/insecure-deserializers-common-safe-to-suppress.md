---
author: dotpaul
ms.author: paulming
ms.date: 04/17/2019
ms.topic: include
ms.openlocfilehash: 2b60e0e713745b1887ff148c5b3ef151584eb21d
ms.sourcegitcommit: c04535ad05e374fb269fcfc6509217755fbc0d54
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/25/2020
ms.locfileid: "96592125"
---
<span data-ttu-id="b1fc4-101">Предупреждение из этого правила можно отключить, если:</span><span class="sxs-lookup"><span data-stu-id="b1fc4-101">It's safe to suppress a warning from this rule if:</span></span>

- <span data-ttu-id="b1fc4-102">Известно, что входные данные являются доверенными.</span><span class="sxs-lookup"><span data-stu-id="b1fc4-102">You know the input is trusted.</span></span> <span data-ttu-id="b1fc4-103">Учтите, что границы доверия и потоки данных приложения могут меняться со временем.</span><span class="sxs-lookup"><span data-stu-id="b1fc4-103">Consider that your application's trust boundary and data flows may change over time.</span></span>
- <span data-ttu-id="b1fc4-104">Вы предоставили одно из предосторожностей по [устранению нарушений](#how-to-fix-violations).</span><span class="sxs-lookup"><span data-stu-id="b1fc4-104">You've taken one of the precautions in [How to fix violations](#how-to-fix-violations).</span></span>
