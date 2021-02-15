---
description: 'Дополнительные сведения о: неправильный номер записи'
title: Неверный номер записи
ms.date: 07/20/2015
f1_keywords:
- vbrID63
ms.assetid: 1fcc33f8-822a-4de9-a6e3-228ddb5824a6
ms.openlocfilehash: a250419c131f75381426705d52563732322631cb
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100460999"
---
# <a name="bad-record-number"></a><span data-ttu-id="ab35d-103">Неверный номер записи</span><span class="sxs-lookup"><span data-stu-id="ab35d-103">Bad record number</span></span>

<span data-ttu-id="ab35d-104">Номер записи в операторе `a FileGet`, `FilePut`, `FileGetObject`или `FilePutObject` меньше или равен нулю.</span><span class="sxs-lookup"><span data-stu-id="ab35d-104">The record number in `a FileGet`, `FilePut`, `FileGetObject`, or `FilePutObject` statement is less than or equal to zero.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ab35d-105">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="ab35d-105">To correct this error</span></span>  
  
1. <span data-ttu-id="ab35d-106">Проверьте вычисления, используемые при формировании номера записи.</span><span class="sxs-lookup"><span data-stu-id="ab35d-106">Check the calculations used in generating the record number.</span></span> <span data-ttu-id="ab35d-107">Проверьте правильность написания переменных, содержащих номер записи или используемых при вычислении номеров записей.</span><span class="sxs-lookup"><span data-stu-id="ab35d-107">Verify spelling of the variables containing the record number or used in calculating record numbers.</span></span> <span data-ttu-id="ab35d-108">Неправильно написанное имя переменной неявно объявляется и приравнивается к нулю, если вы не использовали `Option Explicit On` в модуле.</span><span class="sxs-lookup"><span data-stu-id="ab35d-108">A misspelled variable name is implicitly declared and initialized to zero, unless you used `Option Explicit On` in the module.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab35d-109">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="ab35d-109">See also</span></span>

- [<span data-ttu-id="ab35d-110">Оператор Option Explicit</span><span class="sxs-lookup"><span data-stu-id="ab35d-110">Option Explicit Statement</span></span>](../language-reference/statements/option-explicit-statement.md)
