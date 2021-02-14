---
description: 'Дополнительные сведения: ReDim может изменять только крайнее правое измерение'
title: "\"ReDim\" может изменять только крайнее правое измерение"
ms.date: 07/20/2015
f1_keywords:
- vbrArray_TypeMismatch
ms.assetid: d53cf41b-7a7a-466c-a29a-920d99698fa9
ms.openlocfilehash: 6816e5b2e9c7c079b78ce53e168f46b337831512
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100454694"
---
# <a name="redim-can-only-change-the-right-most-dimension"></a><span data-ttu-id="01244-103">"ReDim" может изменять только крайнее правое измерение</span><span class="sxs-lookup"><span data-stu-id="01244-103">'ReDim' can only change the right-most dimension</span></span>

<span data-ttu-id="01244-104">В операторе `ReDim` ключевое слово `Preserve` используется для изменения измерения массива, которое не является его последним измерением.</span><span class="sxs-lookup"><span data-stu-id="01244-104">A `ReDim` statement attempted to use the `Preserve` keyword to change a dimension of an array that is not the last dimension.</span></span> <span data-ttu-id="01244-105">При использовании `Preserve`можно изменять размер только последнего измерения массива.</span><span class="sxs-lookup"><span data-stu-id="01244-105">When using `Preserve`, you can resize only the last dimension of an array.</span></span> <span data-ttu-id="01244-106">Для всех других измерений необходимо указать тот же размер, что и для существующего массива.</span><span class="sxs-lookup"><span data-stu-id="01244-106">For all other dimensions, you must specify the same size as for the existing array.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="01244-107">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="01244-107">To correct this error</span></span>  
  
- <span data-ttu-id="01244-108">Удалите ключевое слово `Preserve` .</span><span class="sxs-lookup"><span data-stu-id="01244-108">Remove the `Preserve` keyword.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01244-109">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="01244-109">See also</span></span>

- [<span data-ttu-id="01244-110">Массивы в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="01244-110">Arrays in Visual Basic</span></span>](../programming-guide/language-features/arrays/index.md)
- [<span data-ttu-id="01244-111">Размеры массива в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="01244-111">Array dimensions in Visual Basic</span></span>](../programming-guide/language-features/arrays/array-dimensions.md)
- [<span data-ttu-id="01244-112">Оператор reDim</span><span class="sxs-lookup"><span data-stu-id="01244-112">ReDim Statement</span></span>](../language-reference/statements/redim-statement.md)
- [<span data-ttu-id="01244-113">Оператор Dim</span><span class="sxs-lookup"><span data-stu-id="01244-113">Dim Statement</span></span>](../language-reference/statements/dim-statement.md)
