---
description: 'Дополнительные сведения о: BC32025: "#Region" и "#End Region" являются недопустимыми в теле метода или многострочных лямбда-выражениях'
title: 'Операторы #Region и #End Region недопустимы в телах методов/многострочных лямбда-операторах'
ms.date: 07/20/2015
f1_keywords:
- bc32025
- vbc32025
helpviewer_keywords:
- BC32025
ms.assetid: 43707bf1-1c6b-4d82-b081-e5a17dca51c1
ms.openlocfilehash: 0746b9caf677699d6fbbf0c5a7063b1b33d86f3a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792028"
---
# <a name="bc32025-region-and-end-region-statements-are-not-valid-within-method-bodiesmultiline-lambdas"></a><span data-ttu-id="1f3cd-103">BC32025: операторы "#Region" и "#End Region" недопустимы в теле метода/многострочных лямбда-выражений</span><span class="sxs-lookup"><span data-stu-id="1f3cd-103">BC32025: '#Region' and '#End Region' statements are not valid within method bodies/multiline lambdas</span></span>

<span data-ttu-id="1f3cd-104">`#Region`Блок должен быть объявлен на уровне класса, модуля или пространства имен.</span><span class="sxs-lookup"><span data-stu-id="1f3cd-104">The `#Region` block must be declared at a class, module, or namespace level.</span></span> <span data-ttu-id="1f3cd-105">Свертываемая область может включать одну или несколько процедур, но не может начинаться или заканчиваться внутри процедуры.</span><span class="sxs-lookup"><span data-stu-id="1f3cd-105">A collapsible region can include one or more procedures, but it cannot begin or end inside of a procedure.</span></span>

 <span data-ttu-id="1f3cd-106">**Идентификатор ошибки:** BC32025</span><span class="sxs-lookup"><span data-stu-id="1f3cd-106">**Error ID:** BC32025</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="1f3cd-107">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="1f3cd-107">To correct this error</span></span>

1. <span data-ttu-id="1f3cd-108">Убедитесь, что предыдущая процедура правильно завершается `End Function` `End Sub` оператором или.</span><span class="sxs-lookup"><span data-stu-id="1f3cd-108">Ensure that the preceding procedure is properly terminated with an `End Function` or `End Sub` statement.</span></span>

2. <span data-ttu-id="1f3cd-109">Убедитесь, что `#Region` `#End Region` директивы и находятся в одном блоке кода.</span><span class="sxs-lookup"><span data-stu-id="1f3cd-109">Ensure that the `#Region` and `#End Region` directives are in the same code block.</span></span>

## <a name="see-also"></a><span data-ttu-id="1f3cd-110">См. также</span><span class="sxs-lookup"><span data-stu-id="1f3cd-110">See also</span></span>

- [<span data-ttu-id="1f3cd-111">Директива #Region</span><span class="sxs-lookup"><span data-stu-id="1f3cd-111">#Region Directive</span></span>](../directives/region-directive.md)
