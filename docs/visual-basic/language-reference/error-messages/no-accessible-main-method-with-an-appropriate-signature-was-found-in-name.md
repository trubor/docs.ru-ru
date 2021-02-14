---
description: 'Дополнительные сведения о: BC30737: в "" не найден доступный метод "Main" с подходящей сигнатурой. <name>'
title: В <name> не найдено доступного метода Main с подходящей подписью
ms.date: 07/20/2015
f1_keywords:
- bc30737
- vbc30737
helpviewer_keywords:
- BC30737
ms.assetid: 3f40bacd-3fac-4741-b204-852f693d4340
ms.openlocfilehash: 5ff79c1b7589f6b67492ad640179f7a852a2f381
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100483525"
---
# <a name="bc30737-no-accessible-main-method-with-an-appropriate-signature-was-found-in-name"></a><span data-ttu-id="a486d-103">BC30737: в "" не найден доступный метод "Main" с подходящей сигнатурой. \<name></span><span class="sxs-lookup"><span data-stu-id="a486d-103">BC30737: No accessible 'Main' method with an appropriate signature was found in '\<name>'</span></span>

<span data-ttu-id="a486d-104">Приложения командной строки должны иметь `Sub Main` определенные.</span><span class="sxs-lookup"><span data-stu-id="a486d-104">Command-line applications must have a `Sub Main` defined.</span></span> <span data-ttu-id="a486d-105">`Main` должен быть объявлен как `Public Shared` , если он определен в классе, или как, `Public` если он определен в модуле.</span><span class="sxs-lookup"><span data-stu-id="a486d-105">`Main` must be declared as `Public Shared` if it is defined in a class, or as `Public` if defined in a module.</span></span>

 <span data-ttu-id="a486d-106">**Идентификатор ошибки:** BC30737</span><span class="sxs-lookup"><span data-stu-id="a486d-106">**Error ID:** BC30737</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="a486d-107">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="a486d-107">To correct this error</span></span>

- <span data-ttu-id="a486d-108">Определите `Public Sub Main` процедуру для проекта.</span><span class="sxs-lookup"><span data-stu-id="a486d-108">Define a `Public Sub Main` procedure for your project.</span></span> <span data-ttu-id="a486d-109">Объявите его как `Shared` If и только в том случае, если оно определено внутри класса.</span><span class="sxs-lookup"><span data-stu-id="a486d-109">Declare it as `Shared` if and only if you define it inside a class.</span></span>

## <a name="see-also"></a><span data-ttu-id="a486d-110">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="a486d-110">See also</span></span>

- [<span data-ttu-id="a486d-111">Структура программы Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a486d-111">Structure of a Visual Basic Program</span></span>](../../programming-guide/program-structure/structure-of-a-visual-basic-program.md)
- [<span data-ttu-id="a486d-112">Процедуры</span><span class="sxs-lookup"><span data-stu-id="a486d-112">Procedures</span></span>](../../programming-guide/language-features/procedures/index.md)
