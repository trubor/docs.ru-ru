---
title: Правила переносимости и взаимодействия (анализ кода)
description: Сведения о переносимости правил анализа кода и правилах взаимодействия
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- vs.codeanalysis.Portablityrules
- vs.codeanalysis.Interoperabilityrules
helpviewer_keywords:
- managed code analysis rules, interoperability rules, portability rules
- portability rules
- warnings, portability
- interoperability rules
- warnings, interoperability
author: gewarren
ms.author: gewarren
ms.openlocfilehash: a20cd77e13c4a8b95633d129990667f0a8de3ee8
ms.sourcegitcommit: 2e4adc490c1d2a705a0592b295d606b10b9f51f1
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 09/25/2020
ms.locfileid: "96592410"
---
# <a name="portability-and-interoperability-rules"></a><span data-ttu-id="93479-103">Правила переносимости и взаимодействия</span><span class="sxs-lookup"><span data-stu-id="93479-103">Portability and interoperability rules</span></span>

<span data-ttu-id="93479-104">Правила переносимости поддерживают переносимость на разных платформах.</span><span class="sxs-lookup"><span data-stu-id="93479-104">Portability rules support portability across different platforms.</span></span> <span data-ttu-id="93479-105">Правила взаимодействия поддерживают взаимодействие с клиентами COM.</span><span class="sxs-lookup"><span data-stu-id="93479-105">Interoperability rules support interaction with COM clients.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="93479-106">В этом разделе</span><span class="sxs-lookup"><span data-stu-id="93479-106">In this section</span></span>

| <span data-ttu-id="93479-107">Правило</span><span class="sxs-lookup"><span data-stu-id="93479-107">Rule</span></span> | <span data-ttu-id="93479-108">Описание</span><span class="sxs-lookup"><span data-stu-id="93479-108">Description</span></span> |
| - | - |
| [<span data-ttu-id="93479-109">CA1401: методы P/Invoke не должны быть видимыми</span><span class="sxs-lookup"><span data-stu-id="93479-109">CA1401: P/Invokes should not be visible</span></span>](ca1401.md) | <span data-ttu-id="93479-110">Открытый или защищенный метод в открытом типе имеет атрибут System.Runtime.InteropServices.DllImportAttribute (также реализованное ключевым словом Declare в Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="93479-110">A public or protected method in a public type has the System.Runtime.InteropServices.DllImportAttribute attribute (also implemented by the Declare keyword in Visual Basic).</span></span> <span data-ttu-id="93479-111">Такие методы не следует делать видимыми.</span><span class="sxs-lookup"><span data-stu-id="93479-111">Such methods should not be exposed.</span></span> |
| [<span data-ttu-id="93479-112">CA1416. Проверка совместимости платформ</span><span class="sxs-lookup"><span data-stu-id="93479-112">CA1416: Validate platform compatibility</span></span>](ca1416.md) | <span data-ttu-id="93479-113">Использование зависящих от платформы API-интерфейсов в компоненте делает код больше не работает на всех платформах.</span><span class="sxs-lookup"><span data-stu-id="93479-113">Using platform-dependent APIs on a component makes the code no longer work across all platforms.</span></span> |
| [<span data-ttu-id="93479-114">CA1417: не используйте `OutAttribute` в строковых параметрах для P/Invoke</span><span class="sxs-lookup"><span data-stu-id="93479-114">CA1417: Do not use `OutAttribute` on string parameters for P/Invokes</span></span>](ca1417.md) | <span data-ttu-id="93479-115">Строковые параметры, передаваемые по значению, `OutAttribute` могут дестабилизировать среду выполнения, если строка является интернированной строкой.</span><span class="sxs-lookup"><span data-stu-id="93479-115">String parameters passed by value with the `OutAttribute` can destabilize the runtime if the string is an interned string.</span></span> |
