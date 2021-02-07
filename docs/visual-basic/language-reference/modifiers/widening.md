---
description: 'Дополнительные сведения: расширение (Visual Basic)'
title: Widening
ms.date: 07/20/2015
f1_keywords:
- vb.widening
helpviewer_keywords:
- conversions [Visual Basic], type
- type conversion [Visual Basic]
- conversions [Visual Basic], data type
- Widening keyword [Visual Basic]
- data type conversion [Visual Basic]
ms.assetid: 646ae263-94d3-40a2-b0cc-64f619292f56
ms.openlocfilehash: de290296ba2b7716ba992c6bed46443053048282
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99700706"
---
# <a name="widening-visual-basic"></a><span data-ttu-id="c520a-103">Widening (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c520a-103">Widening (Visual Basic)</span></span>

<span data-ttu-id="c520a-104">Указывает, что оператор преобразования ( `CType` ) преобразует класс или структуру в тип, который может содержать все возможные значения исходного класса или структуры.</span><span class="sxs-lookup"><span data-stu-id="c520a-104">Indicates that a conversion operator (`CType`) converts a class or structure to a type that can hold all possible values of the original class or structure.</span></span>  
  
## <a name="converting-with-the-widening-keyword"></a><span data-ttu-id="c520a-105">Преобразование с помощью ключевого слова Widening</span><span class="sxs-lookup"><span data-stu-id="c520a-105">Converting with the Widening Keyword</span></span>  

 <span data-ttu-id="c520a-106">Процедура преобразования должна указываться `Public Shared` в дополнение к `Widening` .</span><span class="sxs-lookup"><span data-stu-id="c520a-106">The conversion procedure must specify `Public Shared` in addition to `Widening`.</span></span>  
  
 <span data-ttu-id="c520a-107">Расширяющие преобразования всегда выполняются в период выполнения и никогда не вызывают потери данных.</span><span class="sxs-lookup"><span data-stu-id="c520a-107">Widening conversions always succeed at run time and never incur data loss.</span></span> <span data-ttu-id="c520a-108">Примеры: `Single` `Double` , `Char` до `String` и производный тип в его базовом типе.</span><span class="sxs-lookup"><span data-stu-id="c520a-108">Examples are `Single` to `Double`, `Char` to `String`, and a derived type to its base type.</span></span> <span data-ttu-id="c520a-109">Последнее преобразование является расширяющим, так как производный тип содержит все члены базового типа и, таким же, является экземпляром базового типа.</span><span class="sxs-lookup"><span data-stu-id="c520a-109">This last conversion is widening because the derived type contains all the members of the base type and thus is an instance of the base type.</span></span>  
  
 <span data-ttu-id="c520a-110">Этот код не обязательно должен использоваться `CType` для расширяющих преобразований, даже если `Option Strict` имеет значение `On` .</span><span class="sxs-lookup"><span data-stu-id="c520a-110">The consuming code does not have to use `CType` for widening conversions, even if `Option Strict` is `On`.</span></span>  
  
 <span data-ttu-id="c520a-111">`Widening`Ключевое слово можно использовать в следующем контексте:</span><span class="sxs-lookup"><span data-stu-id="c520a-111">The `Widening` keyword can be used in this context:</span></span>  
  
 [<span data-ttu-id="c520a-112">Operator Statement</span><span class="sxs-lookup"><span data-stu-id="c520a-112">Operator Statement</span></span>](../statements/operator-statement.md)  
  
 <span data-ttu-id="c520a-113">Примеры определений расширяющих и суженных операторов преобразования см. в разделе [руководство. Определение оператора преобразования](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span><span class="sxs-lookup"><span data-stu-id="c520a-113">For example definitions of widening and narrowing conversion operators, see [How to: Define a Conversion Operator](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c520a-114">См. также</span><span class="sxs-lookup"><span data-stu-id="c520a-114">See also</span></span>

- [<span data-ttu-id="c520a-115">Operator Statement</span><span class="sxs-lookup"><span data-stu-id="c520a-115">Operator Statement</span></span>](../statements/operator-statement.md)
- [<span data-ttu-id="c520a-116">Narrowing</span><span class="sxs-lookup"><span data-stu-id="c520a-116">Narrowing</span></span>](narrowing.md)
- [<span data-ttu-id="c520a-117">Widening and Narrowing Conversions</span><span class="sxs-lookup"><span data-stu-id="c520a-117">Widening and Narrowing Conversions</span></span>](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="c520a-118">Практическое руководство. Определение оператора</span><span class="sxs-lookup"><span data-stu-id="c520a-118">How to: Define an Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="c520a-119">CType Function</span><span class="sxs-lookup"><span data-stu-id="c520a-119">CType Function</span></span>](../functions/ctype-function.md)
- [<span data-ttu-id="c520a-120">Оператор Option Strict</span><span class="sxs-lookup"><span data-stu-id="c520a-120">Option Strict Statement</span></span>](../statements/option-strict-statement.md)
- [<span data-ttu-id="c520a-121">Практическое руководство. Определение оператора преобразования</span><span class="sxs-lookup"><span data-stu-id="c520a-121">How to: Define a Conversion Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md)
