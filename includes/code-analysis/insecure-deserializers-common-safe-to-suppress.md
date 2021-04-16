---
author: dotpaul
ms.author: paulming
ms.date: 04/17/2019
ms.topic: include
ms.openlocfilehash: 2b60e0e713745b1887ff148c5b3ef151584eb21d
ms.sourcegitcommit: 05d0087dfca85aac9ca2960f86c5efd218bf833f
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/30/2021
ms.locfileid: "96592125"
---
<span data-ttu-id="5037a-101">Можно отключить вывод предупреждений для этого правила в следующих случаях:</span><span class="sxs-lookup"><span data-stu-id="5037a-101">It's safe to suppress a warning from this rule if:</span></span>

- <span data-ttu-id="5037a-102">Вам известно, что входные данные являются доверенными.</span><span class="sxs-lookup"><span data-stu-id="5037a-102">You know the input is trusted.</span></span> <span data-ttu-id="5037a-103">Учитывайте, что со временем могут измениться как границы доверия, так и потоки данных приложения.</span><span class="sxs-lookup"><span data-stu-id="5037a-103">Consider that your application's trust boundary and data flows may change over time.</span></span>
- <span data-ttu-id="5037a-104">Вы выполнили одну из мер предосторожности из раздела [Устранение нарушений](#how-to-fix-violations).</span><span class="sxs-lookup"><span data-stu-id="5037a-104">You've taken one of the precautions in [How to fix violations](#how-to-fix-violations).</span></span>
