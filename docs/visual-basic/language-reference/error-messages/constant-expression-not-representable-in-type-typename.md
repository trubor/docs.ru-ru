---
description: 'Дополнительные сведения о: BC30439: константное выражение недоступно для представления в типе " <typename> "'
title: Константное выражение не может быть представлено как имеющее тип <typename>
ms.date: 07/20/2015
f1_keywords:
- bc30439
- vbc30439
helpviewer_keywords:
- BC30439
ms.assetid: 0a842906-3bc5-4946-8a37-3e3da883ef63
ms.openlocfilehash: 034278523fc25cea2e8bb6c749d4c6d412620372
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100471374"
---
# <a name="bc30439-constant-expression-not-representable-in-type-typename"></a><span data-ttu-id="a69f6-103">BC30439: константное выражение недоступно для представления в типе " \<typename> "</span><span class="sxs-lookup"><span data-stu-id="a69f6-103">BC30439: Constant expression not representable in type '\<typename>'</span></span>

<span data-ttu-id="a69f6-104">Вы пытаетесь вычислить константу, которая не помещается в целевой тип, обычно потому, что она переполняет диапазон.</span><span class="sxs-lookup"><span data-stu-id="a69f6-104">You are trying to evaluate a constant that will not fit into the target type, usually because it is overflowing the range.</span></span>

 <span data-ttu-id="a69f6-105">**Идентификатор ошибки:** BC30439</span><span class="sxs-lookup"><span data-stu-id="a69f6-105">**Error ID:** BC30439</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="a69f6-106">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="a69f6-106">To correct this error</span></span>

1. <span data-ttu-id="a69f6-107">Измените тип целевого объекта на другой, который может справиться с константой.</span><span class="sxs-lookup"><span data-stu-id="a69f6-107">Change the target type to one that can handle the constant.</span></span>

## <a name="see-also"></a><span data-ttu-id="a69f6-108">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="a69f6-108">See also</span></span>

- [<span data-ttu-id="a69f6-109">Общие сведения о константах</span><span class="sxs-lookup"><span data-stu-id="a69f6-109">Constants Overview</span></span>](../../programming-guide/language-features/constants-enums/constants-overview.md)
- [<span data-ttu-id="a69f6-110">Константы и перечисления</span><span class="sxs-lookup"><span data-stu-id="a69f6-110">Constants and Enumerations</span></span>](../constants-and-enumerations.md)
