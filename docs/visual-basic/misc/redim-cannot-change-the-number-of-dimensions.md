---
description: 'Дополнительные сведения: "ReDim" не может изменить число измерений'
title: ReDim не может изменять размерность
ms.date: 07/20/2015
f1_keywords:
- vbrArray_RankMismatch
ms.assetid: 52505298-9985-4682-8f6e-ff7d56077f34
ms.openlocfilehash: 4552dd6b1cce54813b57e5b8c76a3580b81b8def
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100454642"
---
# <a name="redim-cannot-change-the-number-of-dimensions"></a><span data-ttu-id="60f43-103">ReDim не может изменять размерность</span><span class="sxs-lookup"><span data-stu-id="60f43-103">'ReDim' cannot change the number of dimensions</span></span>

<span data-ttu-id="60f43-104">Предпринята попытка использования оператора `ReDim` для изменения ранга (размерности) массива.</span><span class="sxs-lookup"><span data-stu-id="60f43-104">An operation attempts to use the `ReDim` statement to change the rank (number of dimensions) of an array.</span></span> <span data-ttu-id="60f43-105">Оператор`ReDim` может изменять размер одного или нескольких измерений массива, который уже был формально объявлен, но он не может изменить ранг массива.</span><span class="sxs-lookup"><span data-stu-id="60f43-105">`ReDim` can change the size of one or more dimensions of an array that has already been formally declared, but it cannot change an array's rank.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="60f43-106">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="60f43-106">To correct this error</span></span>  
  
- <span data-ttu-id="60f43-107">Убедитесь, что требуется изменить ранг, а не размеры массива, и по возможности используйте `Dim` для объявления нового массива с нужным рангом.</span><span class="sxs-lookup"><span data-stu-id="60f43-107">Ensure that you intend to change the array's rank and not the sizes of its dimensions, and if possible, use `Dim` to declare a new array with the desired rank.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60f43-108">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="60f43-108">See also</span></span>

- [<span data-ttu-id="60f43-109">Массивы в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="60f43-109">Arrays in Visual Basic</span></span>](../programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="60f43-110">Размеры массива в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="60f43-110">Array dimensions in Visual Basic</span></span>](../programming-guide/language-features/arrays/array-dimensions.md)
- [<span data-ttu-id="60f43-111">Оператор reDim</span><span class="sxs-lookup"><span data-stu-id="60f43-111">ReDim Statement</span></span>](../language-reference/statements/redim-statement.md)
- [<span data-ttu-id="60f43-112">Оператор Dim</span><span class="sxs-lookup"><span data-stu-id="60f43-112">Dim Statement</span></span>](../language-reference/statements/dim-statement.md)
