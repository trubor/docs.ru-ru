---
description: 'Дополнительные сведения: управляемые классы, производные от класса COM, не могут вызываться с поздним связыванием.'
title: Управляемые классы, производные от класса COM, не могут вызываться с отложенной привязкой.
ms.date: 07/20/2015
f1_keywords:
- vbrLateboundCallToInheritedComClass
ms.assetid: 7bc16e84-8d29-4f8e-bc4f-002c65c71099
ms.openlocfilehash: bde124c3e5c52d4c0dbb0e6e1f7250574c83be8d
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100430044"
---
# <a name="managed-classes-derived-from-a-com-class-cannot-be-called-late-bound"></a><span data-ttu-id="fdb57-103">Управляемые классы, производные от класса COM, не могут вызываться с отложенной привязкой.</span><span class="sxs-lookup"><span data-stu-id="fdb57-103">Managed classes derived from a COM class cannot be called late-bound.</span></span>

<span data-ttu-id="fdb57-104">Предпринята попытка вызова с поздней привязкой управляемого класса, производного от класса COM, однако такие вызовы не поддерживаются.</span><span class="sxs-lookup"><span data-stu-id="fdb57-104">You attempted to make a late-bound call to a managed class derived from a COM Class; such calls are not supported.</span></span>

## <a name="to-correct-the-problem"></a><span data-ttu-id="fdb57-105">Устранение проблемы</span><span class="sxs-lookup"><span data-stu-id="fdb57-105">To correct the problem</span></span>

<span data-ttu-id="fdb57-106">Создайте вызов с ранней привязкой.</span><span class="sxs-lookup"><span data-stu-id="fdb57-106">Make the call early bound.</span></span>

## <a name="see-also"></a><span data-ttu-id="fdb57-107">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="fdb57-107">See also</span></span>

- [<span data-ttu-id="fdb57-108">Типы ошибок</span><span class="sxs-lookup"><span data-stu-id="fdb57-108">Error Types</span></span>](../programming-guide/language-features/error-types.md)
