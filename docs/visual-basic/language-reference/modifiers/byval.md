---
description: 'Дополнительные сведения: ByVal (Visual Basic)'
title: ByVal
ms.date: 07/20/2015
f1_keywords:
- vb.ByVal
- ByVal
helpviewer_keywords:
- ByVal keyword [Visual Basic], contexts
- ByVal keyword [Visual Basic]
ms.assetid: 1eaf4e58-b305-4785-9e3d-e416b9c75598
ms.openlocfilehash: cd7116c0bcc3d263cc2bb6a9b95e46e8ff0cc116
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99774620"
---
# <a name="byval-visual-basic"></a><span data-ttu-id="a9eea-103">ByVal (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a9eea-103">ByVal (Visual Basic)</span></span>

<span data-ttu-id="a9eea-104">Указывает, что аргумент передается [по значению](../../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md), поэтому вызываемая процедура или свойство не может изменить значение переменной, которая является базовым аргументом в вызывающем коде.</span><span class="sxs-lookup"><span data-stu-id="a9eea-104">Specifies that an argument is passed [by value](../../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md), so that the called procedure or property cannot change the value of a variable underlying the argument in the calling code.</span></span> <span data-ttu-id="a9eea-105">Если модификатор не указан, по умолчанию используется значение ByVal.</span><span class="sxs-lookup"><span data-stu-id="a9eea-105">If no modifier is specified, ByVal is the default.</span></span>

> [!NOTE]
> <span data-ttu-id="a9eea-106">Поскольку это значение по умолчанию, нет необходимости явно указывать `ByVal` ключевое слово в сигнатурах метода.</span><span class="sxs-lookup"><span data-stu-id="a9eea-106">Because it is the default, you do not have to explicitly specify the `ByVal` keyword in method signatures.</span></span> <span data-ttu-id="a9eea-107">Он, как правило, создает шум и часто ведет к нестандартному `ByRef` ключевому слову.</span><span class="sxs-lookup"><span data-stu-id="a9eea-107">It tends to produce noisy code and often leads to the non-default `ByRef` keyword being overlooked.</span></span>

## <a name="remarks"></a><span data-ttu-id="a9eea-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="a9eea-108">Remarks</span></span>

 <span data-ttu-id="a9eea-109">Модификатор `ByVal` можно использовать в следующих контекстах:</span><span class="sxs-lookup"><span data-stu-id="a9eea-109">The `ByVal` modifier can be used in these contexts:</span></span>

 [<span data-ttu-id="a9eea-110">Declare Statement</span><span class="sxs-lookup"><span data-stu-id="a9eea-110">Declare Statement</span></span>](../statements/declare-statement.md)

 [<span data-ttu-id="a9eea-111">Оператор Function</span><span class="sxs-lookup"><span data-stu-id="a9eea-111">Function Statement</span></span>](../statements/function-statement.md)
  
 [<span data-ttu-id="a9eea-112">Operator Statement</span><span class="sxs-lookup"><span data-stu-id="a9eea-112">Operator Statement</span></span>](../statements/operator-statement.md)
  
 [<span data-ttu-id="a9eea-113">Property Statement</span><span class="sxs-lookup"><span data-stu-id="a9eea-113">Property Statement</span></span>](../statements/property-statement.md)
  
 [<span data-ttu-id="a9eea-114">Оператор Sub</span><span class="sxs-lookup"><span data-stu-id="a9eea-114">Sub Statement</span></span>](../statements/sub-statement.md)

## <a name="example"></a><span data-ttu-id="a9eea-115">Пример</span><span class="sxs-lookup"><span data-stu-id="a9eea-115">Example</span></span>

 <span data-ttu-id="a9eea-116">В следующем примере демонстрируется использование `ByVal` механизма передачи параметров с аргументом ссылочного типа.</span><span class="sxs-lookup"><span data-stu-id="a9eea-116">The following example demonstrates the use of the `ByVal` parameter passing mechanism with a reference type argument.</span></span> <span data-ttu-id="a9eea-117">В примере аргумент — это `c1` экземпляр класса `Class1` .</span><span class="sxs-lookup"><span data-stu-id="a9eea-117">In the example, the argument is `c1`, an instance of class `Class1`.</span></span> <span data-ttu-id="a9eea-118">`ByVal` запрещает коду в процедурах изменять базовое значение ссылочного аргумента, `c1` , но не защищает доступные поля и свойства `c1` .</span><span class="sxs-lookup"><span data-stu-id="a9eea-118">`ByVal` prevents the code in the procedures from changing the underlying value of the reference argument, `c1`, but does not protect the accessible fields and properties of `c1`.</span></span>

 [!code-vb[VbVbalrKeywords#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class5.vb#10)]

## <a name="see-also"></a><span data-ttu-id="a9eea-119">См. также</span><span class="sxs-lookup"><span data-stu-id="a9eea-119">See also</span></span>

- [<span data-ttu-id="a9eea-120">Ключевые слова</span><span class="sxs-lookup"><span data-stu-id="a9eea-120">Keywords</span></span>](../keywords/index.md)
- [<span data-ttu-id="a9eea-121">Передача аргументов по значению и по ссылке</span><span class="sxs-lookup"><span data-stu-id="a9eea-121">Passing Arguments by Value and by Reference</span></span>](../../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
