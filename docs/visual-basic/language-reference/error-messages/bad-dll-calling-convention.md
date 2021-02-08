---
description: 'Дополнительные сведения: недопустимое соглашение о вызовах DLL'
title: Недопустимое соглашение о вызовах DLL
ms.date: 07/20/2015
f1_keywords:
- vbrID49
ms.assetid: 7c7def45-b0ab-450f-ad3f-4383dfd9aed7
ms.openlocfilehash: 7e98ce5131d440a12bff4a4630da087102bdc4da
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99797098"
---
# <a name="bad-dll-calling-convention"></a><span data-ttu-id="4672a-103">Недопустимое соглашение о вызовах DLL</span><span class="sxs-lookup"><span data-stu-id="4672a-103">Bad DLL calling convention</span></span>

<span data-ttu-id="4672a-104">Аргументы, передаваемые в библиотеку динамической компоновки (DLL), должны точно совпадать с параметрами, ожидаемыми подпрограммыми.</span><span class="sxs-lookup"><span data-stu-id="4672a-104">Arguments passed to a dynamic-link library (DLL) must exactly match those expected by the routine.</span></span> <span data-ttu-id="4672a-105">Соглашения о вызовах имеют дело с числом, типом и порядком аргументов.</span><span class="sxs-lookup"><span data-stu-id="4672a-105">Calling conventions deal with number, type, and order of arguments.</span></span> <span data-ttu-id="4672a-106">Программа может вызвать подпрограмму в библиотеке DLL, которая передает неверный тип или число аргументов.</span><span class="sxs-lookup"><span data-stu-id="4672a-106">Your program may be calling a routine in a DLL that is being passed the wrong type or number of arguments.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="4672a-107">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="4672a-107">To correct this error</span></span>  
  
1. <span data-ttu-id="4672a-108">Убедитесь, что все типы аргументов согласуются с указанными в объявлении подпрограммы, которую вы вызываете.</span><span class="sxs-lookup"><span data-stu-id="4672a-108">Make sure all argument types agree with those specified in the declaration of the routine that you are calling.</span></span>  
  
2. <span data-ttu-id="4672a-109">Убедитесь, что вы передаете то же количество аргументов, которое указано в объявлении вызываемой подпрограммы.</span><span class="sxs-lookup"><span data-stu-id="4672a-109">Make sure you are passing the same number of arguments indicated in the declaration of the routine that you are calling.</span></span>  
  
3. <span data-ttu-id="4672a-110">Если подпрограммы DLL ожидает аргументы по значению, убедитесь, что `ByVal` для этих аргументов в объявлении подпрограммы задано значение.</span><span class="sxs-lookup"><span data-stu-id="4672a-110">If the DLL routine expects arguments by value, make sure `ByVal` is specified for those arguments in the declaration for the routine.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4672a-111">См. также</span><span class="sxs-lookup"><span data-stu-id="4672a-111">See also</span></span>

- [<span data-ttu-id="4672a-112">Типы ошибок</span><span class="sxs-lookup"><span data-stu-id="4672a-112">Error Types</span></span>](../../programming-guide/language-features/error-types.md)
- [<span data-ttu-id="4672a-113">Оператор Call</span><span class="sxs-lookup"><span data-stu-id="4672a-113">Call Statement</span></span>](../statements/call-statement.md)
- [<span data-ttu-id="4672a-114">Declare Statement</span><span class="sxs-lookup"><span data-stu-id="4672a-114">Declare Statement</span></span>](../statements/declare-statement.md)
