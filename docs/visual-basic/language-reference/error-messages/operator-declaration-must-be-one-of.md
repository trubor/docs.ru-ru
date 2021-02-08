---
description: 'Дополнительные сведения о: BC33000: объявление оператора должно быть одним из следующих: +,-, *,,/, ^, &amp; , Like, mod, and или, XOR, not,  <<,  >>...'
title: 'Объявление оператора должно быть одним из следующих: +,-, *,-,-, ^, &amp; , Like, mod, and, или, XOR, not,  <<,  >>, =,  <>, <, <=, >, >=, CType, IsTrue, IsFalse'
ms.date: 07/20/2015
f1_keywords:
- bc33000
- vbc33000
helpviewer_keywords:
- BC33000
ms.assetid: 15c5d8eb-3a8c-4141-8f41-33151afabf97
ms.openlocfilehash: 0ad82a6414387278622a10624952ebc35e7e9b83
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795564"
---
# <a name="bc33000-operator-declaration-must-be-one-of----amp-like-mod-and-or-xor-not--"></a><span data-ttu-id="21d33-103">BC33000: объявление оператора должно быть одним из следующих: +,-, \*, \, /, ^, &amp; , Like, mod, and или, XOR, not, \<\<, >>...</span><span class="sxs-lookup"><span data-stu-id="21d33-103">BC33000: Operator declaration must be one of:  +,-,\*,\,/,^, &amp;, Like, Mod, And, Or, Xor, Not, \<\<, >>...</span></span>

<span data-ttu-id="21d33-104">Можно объявить только оператор, пригодный для перегрузки.</span><span class="sxs-lookup"><span data-stu-id="21d33-104">You can declare only an operator that is eligible for overloading.</span></span> <span data-ttu-id="21d33-105">В следующей таблице перечислены операторы, которые можно объявить.</span><span class="sxs-lookup"><span data-stu-id="21d33-105">The following table lists the operators you can declare.</span></span>

|<span data-ttu-id="21d33-106">Тип</span><span class="sxs-lookup"><span data-stu-id="21d33-106">Type</span></span>|<span data-ttu-id="21d33-107">Операторы</span><span class="sxs-lookup"><span data-stu-id="21d33-107">Operators</span></span>|
|----------|---------------|
|<span data-ttu-id="21d33-108">Унарный</span><span class="sxs-lookup"><span data-stu-id="21d33-108">Unary</span></span>|<span data-ttu-id="21d33-109">`+`, `-`, `IsFalse`, `IsTrue`, `Not`</span><span class="sxs-lookup"><span data-stu-id="21d33-109">`+`, `-`, `IsFalse`, `IsTrue`, `Not`</span></span>|
|<span data-ttu-id="21d33-110">Двоичные данные</span><span class="sxs-lookup"><span data-stu-id="21d33-110">Binary</span></span>|<span data-ttu-id="21d33-111">`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`</span><span class="sxs-lookup"><span data-stu-id="21d33-111">`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`</span></span>|
|<span data-ttu-id="21d33-112">Преобразование (унарный)</span><span class="sxs-lookup"><span data-stu-id="21d33-112">Conversion (unary)</span></span>|`CType`|

 <span data-ttu-id="21d33-113">Обратите внимание, что `=` оператор в списке binary является оператором сравнения, а не оператором присваивания.</span><span class="sxs-lookup"><span data-stu-id="21d33-113">Note that the `=` operator in the binary list is the comparison operator, not the assignment operator.</span></span>

 <span data-ttu-id="21d33-114">**Идентификатор ошибки:** BC33000</span><span class="sxs-lookup"><span data-stu-id="21d33-114">**Error ID:** BC33000</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="21d33-115">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="21d33-115">To correct this error</span></span>

- <span data-ttu-id="21d33-116">Выберите оператор из набора перегружаемых операторов.</span><span class="sxs-lookup"><span data-stu-id="21d33-116">Select an operator from the set of overloadable operators.</span></span>

- <span data-ttu-id="21d33-117">Если требуется возможность перегрузки оператора, который нельзя перегрузить непосредственно, создайте процедуру `Function` , которая принимает соответствующие параметры и возвращает соответствующее значение.</span><span class="sxs-lookup"><span data-stu-id="21d33-117">If you need the functionality of overloading an operator that you cannot overload directly, create a `Function` procedure that takes the appropriate parameters and returns the appropriate value.</span></span>

## <a name="see-also"></a><span data-ttu-id="21d33-118">См. также</span><span class="sxs-lookup"><span data-stu-id="21d33-118">See also</span></span>

- [<span data-ttu-id="21d33-119">Operator Statement</span><span class="sxs-lookup"><span data-stu-id="21d33-119">Operator Statement</span></span>](../statements/operator-statement.md)
- [<span data-ttu-id="21d33-120">Процедуры операторов</span><span class="sxs-lookup"><span data-stu-id="21d33-120">Operator Procedures</span></span>](../../programming-guide/language-features/procedures/operator-procedures.md)
- [<span data-ttu-id="21d33-121">Практическое руководство. Определение оператора</span><span class="sxs-lookup"><span data-stu-id="21d33-121">How to: Define an Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="21d33-122">Практическое руководство. Определение оператора преобразования</span><span class="sxs-lookup"><span data-stu-id="21d33-122">How to: Define a Conversion Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="21d33-123">Оператор Function</span><span class="sxs-lookup"><span data-stu-id="21d33-123">Function Statement</span></span>](../statements/function-statement.md)
