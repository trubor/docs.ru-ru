---
description: 'Дополнительные сведения о: BC30020: "is" требует операндов, имеющих ссылочные типы, но этот операнд имеет тип значения "<typename>'
title: При использовании оператора сравнения Is требуются операнды со ссылочным типом, однако данный операнд имеет тип значения <typename>
ms.date: 07/20/2015
f1_keywords:
- bc30020
- vbc30020
helpviewer_keywords:
- BC30020
ms.assetid: 228afebd-1203-4bd3-8d7a-c5c56f3cedc4
ms.openlocfilehash: f12d4bb4787c3d003c9afc6a0367f7f9e9248f15
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796006"
---
# <a name="bc30020-is-requires-operands-that-have-reference-types-but-this-operand-has-the-value-type-typename"></a><span data-ttu-id="420f2-103">BC30020: для "is" требуются операнды, имеющие ссылочные типы, но этот операнд имеет тип значения " \<typename> "</span><span class="sxs-lookup"><span data-stu-id="420f2-103">BC30020: 'Is' requires operands that have reference types, but this operand has the value type '\<typename>'</span></span>

<span data-ttu-id="420f2-104">`Is`Оператор сравнения определяет, ссылаются ли две объектные переменные на один и тот же экземпляр.</span><span class="sxs-lookup"><span data-stu-id="420f2-104">The `Is` comparison operator determines whether two object variables refer to the same instance.</span></span> <span data-ttu-id="420f2-105">Это сравнение не определено для типов значений.</span><span class="sxs-lookup"><span data-stu-id="420f2-105">This comparison is not defined for value types.</span></span>

 <span data-ttu-id="420f2-106">**Идентификатор ошибки:** BC30020</span><span class="sxs-lookup"><span data-stu-id="420f2-106">**Error ID:** BC30020</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="420f2-107">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="420f2-107">To correct this error</span></span>

- <span data-ttu-id="420f2-108">Используйте соответствующий оператор арифметического сравнения или `Like` оператор для сравнения двух типов значений.</span><span class="sxs-lookup"><span data-stu-id="420f2-108">Use the appropriate arithmetic comparison operator or the `Like` operator to compare two value types.</span></span>

## <a name="see-also"></a><span data-ttu-id="420f2-109">См. также</span><span class="sxs-lookup"><span data-stu-id="420f2-109">See also</span></span>

- [<span data-ttu-id="420f2-110">Оператор Is</span><span class="sxs-lookup"><span data-stu-id="420f2-110">Is Operator</span></span>](../operators/is-operator.md)
- [<span data-ttu-id="420f2-111">Оператор Like</span><span class="sxs-lookup"><span data-stu-id="420f2-111">Like Operator</span></span>](../operators/like-operator.md)
- [<span data-ttu-id="420f2-112">Операторы сравнения</span><span class="sxs-lookup"><span data-stu-id="420f2-112">Comparison Operators</span></span>](../operators/comparison-operators.md)
