---
description: 'Дополнительные сведения о: BC36629: определение типа, допускающего значение null, не поддерживается в этом контексте'
title: Выведение типа Nullable не поддерживается в данном контексте
ms.date: 07/20/2015
f1_keywords:
- vbc36629
- bc36629
helpviewer_keywords:
- BC36629
ms.assetid: 0a1e2dbc-d9a4-433d-9306-c5540782b81d
ms.openlocfilehash: 915f964d55068f39b0468e2c47cc6e5538be1a6f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795629"
---
# <a name="bc36629-nullable-type-inference-is-not-supported-in-this-context"></a><span data-ttu-id="0625d-103">BC36629: определение типа, допускающего значение null, не поддерживается в этом контексте</span><span class="sxs-lookup"><span data-stu-id="0625d-103">BC36629: Nullable type inference is not supported in this context</span></span>

<span data-ttu-id="0625d-104">Типы значений и структуры могут быть объявлены как допускающие значение null.</span><span class="sxs-lookup"><span data-stu-id="0625d-104">Value types and structures can be declared nullable.</span></span>

```vb
Dim a? As Integer
Dim b As Integer?
```

 <span data-ttu-id="0625d-105">Однако нельзя использовать объявление Nullable в сочетании с выводом типа.</span><span class="sxs-lookup"><span data-stu-id="0625d-105">However, you cannot use the nullable declaration in combination with type inference.</span></span> <span data-ttu-id="0625d-106">Следующие примеры вызывают эту ошибку.</span><span class="sxs-lookup"><span data-stu-id="0625d-106">The following examples cause this error.</span></span>

```vb
' Not valid.
' Dim c? = 10
' Dim d? = a
```

 <span data-ttu-id="0625d-107">**Идентификатор ошибки:** BC36629</span><span class="sxs-lookup"><span data-stu-id="0625d-107">**Error ID:** BC36629</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="0625d-108">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="0625d-108">To correct this error</span></span>

- <span data-ttu-id="0625d-109">Используйте `As` предложение, чтобы объявить переменную как тип значения, допускающего значение null.</span><span class="sxs-lookup"><span data-stu-id="0625d-109">Use an `As` clause to declare the variable as a nullable value type.</span></span>

## <a name="see-also"></a><span data-ttu-id="0625d-110">См. также</span><span class="sxs-lookup"><span data-stu-id="0625d-110">See also</span></span>

- [<span data-ttu-id="0625d-111">Типы значений, допускающие значение NULL</span><span class="sxs-lookup"><span data-stu-id="0625d-111">Nullable Value Types</span></span>](../../programming-guide/language-features/data-types/nullable-value-types.md)
- [<span data-ttu-id="0625d-112">Вывод локального типа</span><span class="sxs-lookup"><span data-stu-id="0625d-112">Local Type Inference</span></span>](../../programming-guide/language-features/variables/local-type-inference.md)
