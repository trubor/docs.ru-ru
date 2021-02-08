---
description: 'Дополнительные сведения о: BC30439: константное выражение недоступно для представления в типе "<typename>'
title: Константное выражение не может быть представлено как имеющее тип <typename>
ms.date: 07/20/2015
f1_keywords:
- bc30439
- vbc30439
helpviewer_keywords:
- BC30439
ms.assetid: 0a842906-3bc5-4946-8a37-3e3da883ef63
ms.openlocfilehash: 763ed8a414d8dda3e950ae85a4b1152a459518a5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796747"
---
# <a name="bc30439-constant-expression-not-representable-in-type-typename"></a><span data-ttu-id="cb95d-103">BC30439: константное выражение недоступно для представления в типе " \<typename> "</span><span class="sxs-lookup"><span data-stu-id="cb95d-103">BC30439: Constant expression not representable in type '\<typename>'</span></span>

<span data-ttu-id="cb95d-104">Вы пытаетесь вычислить константу, которая не помещается в целевой тип, обычно потому, что она переполняет диапазон.</span><span class="sxs-lookup"><span data-stu-id="cb95d-104">You are trying to evaluate a constant that will not fit into the target type, usually because it is overflowing the range.</span></span>

 <span data-ttu-id="cb95d-105">**Идентификатор ошибки:** BC30439</span><span class="sxs-lookup"><span data-stu-id="cb95d-105">**Error ID:** BC30439</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="cb95d-106">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="cb95d-106">To correct this error</span></span>

1. <span data-ttu-id="cb95d-107">Измените тип целевого объекта на другой, который может справиться с константой.</span><span class="sxs-lookup"><span data-stu-id="cb95d-107">Change the target type to one that can handle the constant.</span></span>

## <a name="see-also"></a><span data-ttu-id="cb95d-108">См. также</span><span class="sxs-lookup"><span data-stu-id="cb95d-108">See also</span></span>

- [<span data-ttu-id="cb95d-109">Общие сведения о константах</span><span class="sxs-lookup"><span data-stu-id="cb95d-109">Constants Overview</span></span>](../../programming-guide/language-features/constants-enums/constants-overview.md)
- [<span data-ttu-id="cb95d-110">Константы и перечисления</span><span class="sxs-lookup"><span data-stu-id="cb95d-110">Constants and Enumerations</span></span>](../constants-and-enumerations.md)
