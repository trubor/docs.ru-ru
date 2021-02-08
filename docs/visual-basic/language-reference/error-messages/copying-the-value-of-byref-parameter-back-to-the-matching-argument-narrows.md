---
description: 'Дополнительные сведения о: BC32053: копирование значения параметра "ByRef" " <parametername> " обратно в соответствующий аргумент сводит тип " <typename1> " к типу "<typename2>'
title: При копировании значения ByRef параметра <parametername> обратно в соответствующий аргумент тип <typename1> сужается в тип <typename2>
ms.date: 07/20/2015
f1_keywords:
- bc32053
- vbc32053
helpviewer_keywords:
- BC32053
ms.assetid: 281564b7-99f7-451f-b10d-f985e831bb25
ms.openlocfilehash: a90e64cd81443831a7b8f934fea646411eb5a220
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796708"
---
# <a name="bc32053-copying-the-value-of-byref-parameter-parametername-back-to-the-matching-argument-narrows-from-type-typename1-to-type-typename2"></a><span data-ttu-id="c2558-103">BC32053: копирование значения параметра "ByRef" " \<parametername> " обратно в соответствующий аргумент сводит тип "" \<typename1> к типу " \<typename2> "</span><span class="sxs-lookup"><span data-stu-id="c2558-103">BC32053: Copying the value of 'ByRef' parameter '\<parametername>' back to the matching argument narrows from type '\<typename1>' to type '\<typename2>'</span></span>

<span data-ttu-id="c2558-104">Процедура вызывается с аргументом, который расширяется до соответствующего типа параметра, а преобразование из параметра в аргумент является сужением.</span><span class="sxs-lookup"><span data-stu-id="c2558-104">A procedure is called with an argument that widens to the corresponding parameter type, and the conversion from the parameter to the argument is narrowing.</span></span>

 <span data-ttu-id="c2558-105">При определении класса или структуры можно определить один или несколько операторов преобразования для преобразования типа класса или структуры в другие типы.</span><span class="sxs-lookup"><span data-stu-id="c2558-105">When you define a class or structure, you can define one or more conversion operators to convert that class or structure type to other types.</span></span> <span data-ttu-id="c2558-106">Можно также определить операторы обратного преобразования для преобразования других типов обратно в тип класса или структуры.</span><span class="sxs-lookup"><span data-stu-id="c2558-106">You can also define reverse conversion operators to convert those other types back to your class or structure type.</span></span> <span data-ttu-id="c2558-107">При использовании типа класса или структуры в вызове процедуры Visual Basic могут использовать эти операторы преобразования для преобразования типа аргумента в тип соответствующего параметра.</span><span class="sxs-lookup"><span data-stu-id="c2558-107">When you use your class or structure type in a procedure call, Visual Basic can use these conversion operators to convert the type of an argument to the type of its corresponding parameter.</span></span>

 <span data-ttu-id="c2558-108">При передаче аргумента [ByRef](../modifiers/byref.md)Visual Basic иногда копирует значение аргумента в локальную переменную в процедуре вместо передачи ссылки.</span><span class="sxs-lookup"><span data-stu-id="c2558-108">If you pass the argument [ByRef](../modifiers/byref.md), Visual Basic sometimes copies the argument value into a local variable in the procedure instead of passing a reference.</span></span> <span data-ttu-id="c2558-109">В этом случае, когда процедура возвращает, Visual Basic необходимо скопировать значение локальной переменной обратно в аргумент в вызывающем коде.</span><span class="sxs-lookup"><span data-stu-id="c2558-109">In such a case, when the procedure returns, Visual Basic must then copy the local variable value back into the argument in the calling code.</span></span>

 <span data-ttu-id="c2558-110">Если значение аргумента `ByRef` копируется в процедуру, а аргумент и параметр имеют один и тот же тип, то преобразование не требуется.</span><span class="sxs-lookup"><span data-stu-id="c2558-110">If a `ByRef` argument value is copied into the procedure and the argument and parameter are of the same type, no conversion is necessary.</span></span> <span data-ttu-id="c2558-111">Но если типы различаются, Visual Basic должны быть преобразованы в обоих направлениях.</span><span class="sxs-lookup"><span data-stu-id="c2558-111">But if the types are different, Visual Basic must convert in both directions.</span></span> <span data-ttu-id="c2558-112">Если один из типов является типом класса или структуры, Visual Basic должен преобразовать его в другой тип и из него.</span><span class="sxs-lookup"><span data-stu-id="c2558-112">If one of the types is your class or structure type, Visual Basic must convert it both to and from the other type.</span></span> <span data-ttu-id="c2558-113">Если одно из этих преобразований является расширяющим, то обратным преобразованием может быть сужение.</span><span class="sxs-lookup"><span data-stu-id="c2558-113">If one of these conversions is widening, the reverse conversion might be narrowing.</span></span>

 <span data-ttu-id="c2558-114">**Идентификатор ошибки:** BC32053</span><span class="sxs-lookup"><span data-stu-id="c2558-114">**Error ID:** BC32053</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="c2558-115">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="c2558-115">To correct this error</span></span>

- <span data-ttu-id="c2558-116">По возможности используйте аргумент вызова того же типа, что и параметр процедуры, поэтому Visual Basic не требуется выполнять преобразование.</span><span class="sxs-lookup"><span data-stu-id="c2558-116">If possible, use a calling argument of the same type as the procedure parameter, so Visual Basic does not need to do any conversion.</span></span>

- <span data-ttu-id="c2558-117">Если необходимо вызвать процедуру с аргументом, тип которого отличается от типа параметра, но не требуется возвращать значение в аргумент вызова, то определите параметр как [ByVal](../modifiers/byval.md) , а не `ByRef`.</span><span class="sxs-lookup"><span data-stu-id="c2558-117">If you need to call the procedure with an argument type different from the parameter type but do not need to return a value into the calling argument, define the parameter to be [ByVal](../modifiers/byval.md) instead of `ByRef`.</span></span>

- <span data-ttu-id="c2558-118">Если необходимо вернуть значение в аргумент вызова, определите оператор обратного преобразования в качестве [расширяющего](../modifiers/widening.md), если это возможно.</span><span class="sxs-lookup"><span data-stu-id="c2558-118">If you need to return a value into the calling argument, define the reverse conversion operator as [Widening](../modifiers/widening.md), if possible.</span></span>

## <a name="see-also"></a><span data-ttu-id="c2558-119">См. также</span><span class="sxs-lookup"><span data-stu-id="c2558-119">See also</span></span>

- [<span data-ttu-id="c2558-120">Процедуры</span><span class="sxs-lookup"><span data-stu-id="c2558-120">Procedures</span></span>](../../programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="c2558-121">Параметры и аргументы процедуры</span><span class="sxs-lookup"><span data-stu-id="c2558-121">Procedure Parameters and Arguments</span></span>](../../programming-guide/language-features/procedures/procedure-parameters-and-arguments.md)
- [<span data-ttu-id="c2558-122">Передача аргументов по значению и по ссылке</span><span class="sxs-lookup"><span data-stu-id="c2558-122">Passing Arguments by Value and by Reference</span></span>](../../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="c2558-123">Процедуры операторов</span><span class="sxs-lookup"><span data-stu-id="c2558-123">Operator Procedures</span></span>](../../programming-guide/language-features/procedures/operator-procedures.md)
- [<span data-ttu-id="c2558-124">Operator Statement</span><span class="sxs-lookup"><span data-stu-id="c2558-124">Operator Statement</span></span>](../statements/operator-statement.md)
- [<span data-ttu-id="c2558-125">Практическое руководство. Определение оператора</span><span class="sxs-lookup"><span data-stu-id="c2558-125">How to: Define an Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="c2558-126">Практическое руководство. Определение оператора преобразования</span><span class="sxs-lookup"><span data-stu-id="c2558-126">How to: Define a Conversion Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
- [<span data-ttu-id="c2558-127">Преобразование типов в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c2558-127">Type Conversions in Visual Basic</span></span>](../../programming-guide/language-features/data-types/type-conversions.md)
- [<span data-ttu-id="c2558-128">Widening and Narrowing Conversions</span><span class="sxs-lookup"><span data-stu-id="c2558-128">Widening and Narrowing Conversions</span></span>](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
