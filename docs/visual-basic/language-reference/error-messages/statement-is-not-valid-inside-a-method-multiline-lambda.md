---
description: 'Дополнительные сведения о: BC30024: оператор недопустим в методе или многострочной лямбда-выражении'
title: Оператор недопустим в теле метода/многострочного лямбда-оператора
ms.date: 07/20/2015
f1_keywords:
- vbc30024
- bc30024
helpviewer_keywords:
- BC30024
ms.assetid: 758e7a8f-429b-42c1-9a78-778e5b480e04
ms.openlocfilehash: c70e5563ab8c161966cd9790ae1f192fa5d50b17
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99731179"
---
# <a name="bc30024-statement-is-not-valid-inside-a-methodmultiline-lambda"></a><span data-ttu-id="2210a-103">BC30024: недопустимая инструкция в методе или многострочной лямбда-выражении</span><span class="sxs-lookup"><span data-stu-id="2210a-103">BC30024: Statement is not valid inside a method/multiline lambda</span></span>

<span data-ttu-id="2210a-104">Оператор недопустим в `Sub` `Function` процедуре свойства,, свойства `Get` или `Set` .</span><span class="sxs-lookup"><span data-stu-id="2210a-104">The statement is not valid within a `Sub`, `Function`, property `Get`, or property `Set` procedure.</span></span> <span data-ttu-id="2210a-105">Некоторые инструкции можно разместить на уровне модуля или класса.</span><span class="sxs-lookup"><span data-stu-id="2210a-105">Some statements can be placed at the module or class level.</span></span> <span data-ttu-id="2210a-106">Другие, такие как `Option Strict` , должны находиться на уровне пространства имен и предшествовать всем остальным объявлениям.</span><span class="sxs-lookup"><span data-stu-id="2210a-106">Others, such as `Option Strict`, must be at namespace level and precede all other declarations.</span></span>

 <span data-ttu-id="2210a-107">**Идентификатор ошибки:** BC30024</span><span class="sxs-lookup"><span data-stu-id="2210a-107">**Error ID:** BC30024</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="2210a-108">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="2210a-108">To correct this error</span></span>

- <span data-ttu-id="2210a-109">Удалите инструкцию из процедуры.</span><span class="sxs-lookup"><span data-stu-id="2210a-109">Remove the statement from the procedure.</span></span>

## <a name="see-also"></a><span data-ttu-id="2210a-110">См. также</span><span class="sxs-lookup"><span data-stu-id="2210a-110">See also</span></span>

- [<span data-ttu-id="2210a-111">Оператор Sub</span><span class="sxs-lookup"><span data-stu-id="2210a-111">Sub Statement</span></span>](../statements/sub-statement.md)
- [<span data-ttu-id="2210a-112">Оператор Function</span><span class="sxs-lookup"><span data-stu-id="2210a-112">Function Statement</span></span>](../statements/function-statement.md)
- [<span data-ttu-id="2210a-113">Оператор Get</span><span class="sxs-lookup"><span data-stu-id="2210a-113">Get Statement</span></span>](../statements/get-statement.md)
- [<span data-ttu-id="2210a-114">Инструкция SET</span><span class="sxs-lookup"><span data-stu-id="2210a-114">Set Statement</span></span>](../statements/set-statement.md)
