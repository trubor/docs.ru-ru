---
description: 'Дополнительные сведения о: BC36599: имя переменной диапазона можно вывести только из простого или полного имени без аргументов'
title: Имя переменной диапазона может быть выведено только из простого или полного имени без аргументов
ms.date: 07/20/2015
f1_keywords:
- vbc36599
- bc36599
helpviewer_keywords:
- BC36599
ms.assetid: 17763dbe-f74f-4ccb-8086-cb7e45ec4d12
ms.openlocfilehash: b729b6786f9b7803a794b9a4e786d94fa41a57ec
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99792067"
---
# <a name="bc36599-range-variable-name-can-be-inferred-only-from-a-simple-or-qualified-name-with-no-arguments"></a><span data-ttu-id="58b60-103">BC36599: имя переменной диапазона может быть выведено только из простого или полного имени без аргументов</span><span class="sxs-lookup"><span data-stu-id="58b60-103">BC36599: Range variable name can be inferred only from a simple or qualified name with no arguments</span></span>

<span data-ttu-id="58b60-104">В запрос LINQ входит программный элемент, который принимает один или несколько аргументов.</span><span class="sxs-lookup"><span data-stu-id="58b60-104">A programming element that takes one or more arguments is included in a LINQ query.</span></span> <span data-ttu-id="58b60-105">Компилятору не удается вывести переменную диапазона из этого программного элемента.</span><span class="sxs-lookup"><span data-stu-id="58b60-105">The compiler is unable to infer a range variable from that programming element.</span></span>

<span data-ttu-id="58b60-106">**Идентификатор ошибки:** BC36599</span><span class="sxs-lookup"><span data-stu-id="58b60-106">**Error ID:** BC36599</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="58b60-107">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="58b60-107">To correct this error</span></span>

<span data-ttu-id="58b60-108">Укажите явное имя переменной для программного элемента, как показано в следующем коде:</span><span class="sxs-lookup"><span data-stu-id="58b60-108">Supply an explicit variable name for the programming element, as shown in the following code:</span></span>

```vb
Dim query = From var1 In collection1
            Select VariableAlias= SampleFunction(var1), var1
```

## <a name="see-also"></a><span data-ttu-id="58b60-109">См. также</span><span class="sxs-lookup"><span data-stu-id="58b60-109">See also</span></span>

- <span data-ttu-id="58b60-110">[Introduction to LINQ in Visual Basic](../../programming-guide/language-features/linq/introduction-to-linq.md) (Знакомство с LINQ в Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="58b60-110">[Introduction to LINQ in Visual Basic](../../programming-guide/language-features/linq/introduction-to-linq.md)</span></span>
- [<span data-ttu-id="58b60-111">Предложение SELECT</span><span class="sxs-lookup"><span data-stu-id="58b60-111">Select Clause</span></span>](../queries/select-clause.md)
