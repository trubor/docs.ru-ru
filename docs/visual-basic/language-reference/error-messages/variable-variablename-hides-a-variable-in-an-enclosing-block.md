---
description: "Дополнительные сведения о: BC30616: переменная ' <variablename> ' скрывает переменную во внешнем блоке"
title: Переменная <variablename> скрывает содержащуюся в блоке переменную
ms.date: 07/20/2015
f1_keywords:
- vbc30616
- bc30616
helpviewer_keywords:
- BC30616
ms.assetid: e7658ebc-da45-451b-a409-a0f8915f0beb
ms.openlocfilehash: a0b2a4d024ff0409b5617354b5e671ca6dc0305b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99666125"
---
# <a name="bc30616-variable-variablename-hides-a-variable-in-an-enclosing-block"></a><span data-ttu-id="2ec1d-103">BC30616: переменная " \<variablename> " скрывает переменную во внешнем блоке</span><span class="sxs-lookup"><span data-stu-id="2ec1d-103">BC30616: Variable '\<variablename>' hides a variable in an enclosing block</span></span>

<span data-ttu-id="2ec1d-104">Переменная, заключенная в блок, имеет то же имя, что и другая локальная переменная.</span><span class="sxs-lookup"><span data-stu-id="2ec1d-104">A variable enclosed in a block has the same name as another local variable.</span></span>

 <span data-ttu-id="2ec1d-105">**Идентификатор ошибки:** BC30616</span><span class="sxs-lookup"><span data-stu-id="2ec1d-105">**Error ID:** BC30616</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="2ec1d-106">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="2ec1d-106">To correct this error</span></span>

- <span data-ttu-id="2ec1d-107">Переименуйте переменную во вложенном блоке так, чтобы она не совпадала с другими локальными переменными.</span><span class="sxs-lookup"><span data-stu-id="2ec1d-107">Rename the variable in the enclosed block so that it is not the same as any other local variables.</span></span> <span data-ttu-id="2ec1d-108">Пример:</span><span class="sxs-lookup"><span data-stu-id="2ec1d-108">For example:</span></span>

    ```vb
    Dim a, b, x As Integer
    If a = b Then
       Dim y As Integer = 20 ' Uniquely named block variable.
    End If
    ```

- <span data-ttu-id="2ec1d-109">Распространенной причиной этой ошибки является использование `Catch e As Exception` внутри обработчика событий.</span><span class="sxs-lookup"><span data-stu-id="2ec1d-109">A common cause for this error is the use of `Catch e As Exception` inside an event handler.</span></span> <span data-ttu-id="2ec1d-110">Если это так, назовите `Catch` переменную блока, `ex` а не `e` .</span><span class="sxs-lookup"><span data-stu-id="2ec1d-110">If this is the case, name the `Catch` block variable `ex` rather than `e`.</span></span>

- <span data-ttu-id="2ec1d-111">Другой распространенный источник этой ошибки — попытка доступа к локальной переменной, объявленной в `Try` блоке, в отдельном `Catch` блоке.</span><span class="sxs-lookup"><span data-stu-id="2ec1d-111">Another common source of this error is an attempt to access a local variable declared within a `Try` block in a separate `Catch` block.</span></span> <span data-ttu-id="2ec1d-112">Чтобы исправить это, объявите переменную вне `Try...Catch...Finally` структуры.</span><span class="sxs-lookup"><span data-stu-id="2ec1d-112">To correct this, declare the variable outside the `Try...Catch...Finally` structure.</span></span>

## <a name="see-also"></a><span data-ttu-id="2ec1d-113">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="2ec1d-113">See also</span></span>

- [<span data-ttu-id="2ec1d-114">Оператор Try...Catch...Finally</span><span class="sxs-lookup"><span data-stu-id="2ec1d-114">Try...Catch...Finally Statement</span></span>](../statements/try-catch-finally-statement.md)
- [<span data-ttu-id="2ec1d-115">Объявление переменной</span><span class="sxs-lookup"><span data-stu-id="2ec1d-115">Variable Declaration</span></span>](../../programming-guide/language-features/variables/variable-declaration.md)
