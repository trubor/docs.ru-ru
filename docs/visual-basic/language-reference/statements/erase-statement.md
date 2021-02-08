---
description: 'Дополнительные сведения об инструкции: Erase (Visual Basic)'
title: Оператор Erase
ms.date: 07/20/2015
f1_keywords:
- vb.Erase
helpviewer_keywords:
- Erase keyword [Visual Basic]
- Erase statement [Visual Basic]
ms.assetid: 7a8133d7-b750-4d74-8b66-ba1dd9778d4b
ms.openlocfilehash: 295abec89f3d69f8f2641a5a3d574a2d10f98474
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99769160"
---
# <a name="erase-statement-visual-basic"></a><span data-ttu-id="9981d-103">Оператор Erase (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9981d-103">Erase Statement (Visual Basic)</span></span>

<span data-ttu-id="9981d-104">Используется для высвобождения переменных массива и освобождения памяти, используемой для их элементов.</span><span class="sxs-lookup"><span data-stu-id="9981d-104">Used to release array variables and deallocate the memory used for their elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9981d-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="9981d-105">Syntax</span></span>  
  
```vb  
Erase arraylist  
```  
  
## <a name="parts"></a><span data-ttu-id="9981d-106">Компоненты</span><span class="sxs-lookup"><span data-stu-id="9981d-106">Parts</span></span>  

 `arraylist`  
 <span data-ttu-id="9981d-107">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="9981d-107">Required.</span></span> <span data-ttu-id="9981d-108">Список переменных массива для удаления.</span><span class="sxs-lookup"><span data-stu-id="9981d-108">List of array variables to be erased.</span></span> <span data-ttu-id="9981d-109">Переменные разделяются запятыми.</span><span class="sxs-lookup"><span data-stu-id="9981d-109">Multiple variables are separated by commas.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9981d-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="9981d-110">Remarks</span></span>  

 <span data-ttu-id="9981d-111">`Erase`Инструкция может использоваться только на уровне процедуры.</span><span class="sxs-lookup"><span data-stu-id="9981d-111">The `Erase` statement can appear only at procedure level.</span></span> <span data-ttu-id="9981d-112">Это означает, что массивы можно освобождать внутри процедуры, но не на уровне класса или модуля.</span><span class="sxs-lookup"><span data-stu-id="9981d-112">This means you can release arrays inside a procedure but not at class or module level.</span></span>  
  
 <span data-ttu-id="9981d-113">`Erase`Оператор эквивалентен присвоению `Nothing` каждой переменной массива.</span><span class="sxs-lookup"><span data-stu-id="9981d-113">The `Erase` statement is equivalent to assigning `Nothing` to each array variable.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9981d-114">Пример</span><span class="sxs-lookup"><span data-stu-id="9981d-114">Example</span></span>  

 <span data-ttu-id="9981d-115">В следующем примере инструкция используется `Erase` для очистки двух массивов и освобождения памяти (1000 и 100, соответственно).</span><span class="sxs-lookup"><span data-stu-id="9981d-115">The following example uses the `Erase` statement to clear two arrays and free their memory (1000 and 100 storage elements, respectively).</span></span> <span data-ttu-id="9981d-116">`ReDim`Затем оператор присваивает новый экземпляр массива трехмерному массиву.</span><span class="sxs-lookup"><span data-stu-id="9981d-116">The `ReDim` statement then assigns a new array instance to the three-dimensional array.</span></span>  
  
 [!code-vb[VbVbalrStatements#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#19)]  
  
## <a name="see-also"></a><span data-ttu-id="9981d-117">См. также</span><span class="sxs-lookup"><span data-stu-id="9981d-117">See also</span></span>

- [<span data-ttu-id="9981d-118">Nothing</span><span class="sxs-lookup"><span data-stu-id="9981d-118">Nothing</span></span>](../nothing.md)
- [<span data-ttu-id="9981d-119">Оператор reDim</span><span class="sxs-lookup"><span data-stu-id="9981d-119">ReDim Statement</span></span>](redim-statement.md)
