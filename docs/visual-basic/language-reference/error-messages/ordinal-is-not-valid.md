---
description: 'Дополнительные сведения о: порядковый номер недопустим'
title: Недопустимый порядковый номер
ms.date: 07/20/2015
f1_keywords:
- vbrID452
ms.assetid: 7459562b-cd4f-4590-95e0-6126ae3589a5
ms.openlocfilehash: 7c58675a08d3821cd05ba0109e5ce0107c68e497
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795525"
---
# <a name="ordinal-is-not-valid"></a><span data-ttu-id="dc844-103">Недопустимый порядковый номер</span><span class="sxs-lookup"><span data-stu-id="dc844-103">Ordinal is not valid</span></span>

<span data-ttu-id="dc844-104">При вызове библиотеки динамической компоновки (DLL) для использования числа вместо имени процедуры используется `#num` синтаксис.</span><span class="sxs-lookup"><span data-stu-id="dc844-104">Your call to a dynamic-link library (DLL) indicated to use a number instead of a procedure name, using the `#num` syntax.</span></span> <span data-ttu-id="dc844-105">Эта ошибка может быть вызвана следующими причинами.</span><span class="sxs-lookup"><span data-stu-id="dc844-105">This error has the following possible causes:</span></span>  
  
- <span data-ttu-id="dc844-106">Сбой при преобразовании `#num` выражения в порядковый номер.</span><span class="sxs-lookup"><span data-stu-id="dc844-106">An attempt to convert the `#num` expression to an ordinal failed.</span></span>  
  
- <span data-ttu-id="dc844-107">В `#num` указанном параметре не указана какая-либо функция в библиотеке DLL.</span><span class="sxs-lookup"><span data-stu-id="dc844-107">The `#num` specified does not specify any function in the DLL.</span></span>  
  
- <span data-ttu-id="dc844-108">Библиотека типов содержит недопустимое объявление, что приводит к внутреннему использованию недопустимого порядкового номера.</span><span class="sxs-lookup"><span data-stu-id="dc844-108">A type library has an invalid declaration resulting in internal use of an invalid ordinal number.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="dc844-109">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="dc844-109">To correct this error</span></span>  
  
1. <span data-ttu-id="dc844-110">Убедитесь, что выражение представляет допустимое число, или вызовите процедуру по имени.</span><span class="sxs-lookup"><span data-stu-id="dc844-110">Make sure the expression represents a valid number, or call the procedure by name.</span></span>  
  
2. <span data-ttu-id="dc844-111">Убедитесь `#num` , что определяет допустимую функцию в библиотеке DLL.</span><span class="sxs-lookup"><span data-stu-id="dc844-111">Make sure `#num` identifies a valid function in the DLL.</span></span>  
  
3. <span data-ttu-id="dc844-112">Изолируйте вызов процедуры, который вызывает проблему, закомментируя код.</span><span class="sxs-lookup"><span data-stu-id="dc844-112">Isolate the procedure call causing the problem by commenting out the code.</span></span> <span data-ttu-id="dc844-113">Напишите `Declare` инструкцию для процедуры и сообщите о проблеме поставщику библиотеки типов.</span><span class="sxs-lookup"><span data-stu-id="dc844-113">Write a `Declare` statement for the procedure, and report the problem to the type library vendor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dc844-114">См. также</span><span class="sxs-lookup"><span data-stu-id="dc844-114">See also</span></span>

- [<span data-ttu-id="dc844-115">Declare Statement</span><span class="sxs-lookup"><span data-stu-id="dc844-115">Declare Statement</span></span>](../statements/declare-statement.md)
