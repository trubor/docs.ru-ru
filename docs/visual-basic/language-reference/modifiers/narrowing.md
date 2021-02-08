---
description: 'Дополнительные сведения: понижающие (Visual Basic)'
title: Narrowing
ms.date: 07/20/2015
f1_keywords:
- vb.narrowing
helpviewer_keywords:
- conversions [Visual Basic], type
- type conversion [Visual Basic]
- conversions [Visual Basic], data type
- Narrowing keyword [Visual Basic]
- data type conversion [Visual Basic]
ms.assetid: a207ee91-aca4-4771-b4e2-713f029bf2bb
ms.openlocfilehash: 1dd9185ccf30fb6f9dc9360f75450c2533ab90e5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795356"
---
# <a name="narrowing-visual-basic"></a><span data-ttu-id="7bcf1-103">Narrowing (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7bcf1-103">Narrowing (Visual Basic)</span></span>

<span data-ttu-id="7bcf1-104">Указывает, что оператор преобразования ( `CType` ) преобразует класс или структуру в тип, который не может содержать некоторые из возможных значений исходного класса или структуры.</span><span class="sxs-lookup"><span data-stu-id="7bcf1-104">Indicates that a conversion operator (`CType`) converts a class or structure to a type that might not be able to hold some of the possible values of the original class or structure.</span></span>  
  
## <a name="converting-with-the-narrowing-keyword"></a><span data-ttu-id="7bcf1-105">Преобразование с помощью ключевого слова "Narrow"</span><span class="sxs-lookup"><span data-stu-id="7bcf1-105">Converting with the Narrowing Keyword</span></span>  

 <span data-ttu-id="7bcf1-106">Процедура преобразования должна указываться `Public Shared` в дополнение к `Narrowing` .</span><span class="sxs-lookup"><span data-stu-id="7bcf1-106">The conversion procedure must specify `Public Shared` in addition to `Narrowing`.</span></span>  
  
 <span data-ttu-id="7bcf1-107">Сужающие преобразования не всегда выполняются успешно во время выполнения и могут привести к сбою или потери данных.</span><span class="sxs-lookup"><span data-stu-id="7bcf1-107">Narrowing conversions do not always succeed at run time, and can fail or incur data loss.</span></span> <span data-ttu-id="7bcf1-108">Примерами `Long` являются `Integer` , `String` to `Date` и базовый тип для производного типа.</span><span class="sxs-lookup"><span data-stu-id="7bcf1-108">Examples are `Long` to `Integer`, `String` to `Date`, and a base type to a derived type.</span></span> <span data-ttu-id="7bcf1-109">Последнее преобразование является сужением, так как базовый тип может не содержать все члены производного типа и поэтому не является экземпляром производного типа.</span><span class="sxs-lookup"><span data-stu-id="7bcf1-109">This last conversion is narrowing because the base type might not contain all the members of the derived type and thus is not an instance of the derived type.</span></span>  
  
 <span data-ttu-id="7bcf1-110">Если `Option Strict` имеет значение `On` , то `CType` для всех сужающих преобразований код должен использовать.</span><span class="sxs-lookup"><span data-stu-id="7bcf1-110">If `Option Strict` is `On`, the consuming code must use `CType` for all narrowing conversions.</span></span>  
  
 <span data-ttu-id="7bcf1-111">`Narrowing`Ключевое слово можно использовать в следующем контексте:</span><span class="sxs-lookup"><span data-stu-id="7bcf1-111">The `Narrowing` keyword can be used in this context:</span></span>  
  
 [<span data-ttu-id="7bcf1-112">Operator Statement</span><span class="sxs-lookup"><span data-stu-id="7bcf1-112">Operator Statement</span></span>](../statements/operator-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="7bcf1-113">См. также</span><span class="sxs-lookup"><span data-stu-id="7bcf1-113">See also</span></span>

- [<span data-ttu-id="7bcf1-114">Operator Statement</span><span class="sxs-lookup"><span data-stu-id="7bcf1-114">Operator Statement</span></span>](../statements/operator-statement.md)
- [<span data-ttu-id="7bcf1-115">Widening</span><span class="sxs-lookup"><span data-stu-id="7bcf1-115">Widening</span></span>](widening.md)
- [<span data-ttu-id="7bcf1-116">Widening and Narrowing Conversions</span><span class="sxs-lookup"><span data-stu-id="7bcf1-116">Widening and Narrowing Conversions</span></span>](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="7bcf1-117">Практическое руководство. Определение оператора</span><span class="sxs-lookup"><span data-stu-id="7bcf1-117">How to: Define an Operator</span></span>](../../programming-guide/language-features/procedures/how-to-define-an-operator.md)
- [<span data-ttu-id="7bcf1-118">CType Function</span><span class="sxs-lookup"><span data-stu-id="7bcf1-118">CType Function</span></span>](../functions/ctype-function.md)
- [<span data-ttu-id="7bcf1-119">Оператор Option Strict</span><span class="sxs-lookup"><span data-stu-id="7bcf1-119">Option Strict Statement</span></span>](../statements/option-strict-statement.md)
