---
description: 'Дополнительные сведения: ни один из доступных перегруженных " <methodname> " не может вызываться с этими аргументами без сужения преобразования: <list>'
title: 'Ни один из доступных перегруженных "<methodname>" не может вызываться с этими аргументами без преобразования с сужением:  <list>'
ms.date: 07/20/2015
f1_keywords:
- vbrAmbiguousCall2
ms.assetid: 13b20ffa-9f02-4971-a3cb-e08b402fd971
ms.openlocfilehash: a802b420a01c1894feca2c61c0bfdbb7be5104f5
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100475712"
---
# <a name="no-accessible-overloaded-methodname-can-be-called-with-these-arguments-without-a-narrowing-conversion-list"></a><span data-ttu-id="c6a35-103">Ни один из доступных перегруженных "\<methodname>" не может вызываться с этими аргументами без преобразования с сужением: \<list></span><span class="sxs-lookup"><span data-stu-id="c6a35-103">No accessible overloaded '\<methodname>' can be called with these arguments without a narrowing conversion: \<list></span></span>

<span data-ttu-id="c6a35-104">Вызван перегруженный метод, однако он не может быть сопоставлен со списком указанных аргументов без сужающего преобразования.</span><span class="sxs-lookup"><span data-stu-id="c6a35-104">An overloaded method was called, but the method cannot be matched with the list of provided arguments without a narrowing conversion.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="c6a35-105">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="c6a35-105">To correct this error</span></span>  
  
1. <span data-ttu-id="c6a35-106">Задайте имя `Option Strict Off`.</span><span class="sxs-lookup"><span data-stu-id="c6a35-106">Specify `Option Strict Off`.</span></span>
  
2. <span data-ttu-id="c6a35-107">Измените аргументы таким образом, чтобы они соответствовали сигнатуре перегруженного метода.</span><span class="sxs-lookup"><span data-stu-id="c6a35-107">Change the arguments to match a signature of the overloaded method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6a35-108">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="c6a35-108">See also</span></span>

- [<span data-ttu-id="c6a35-109">Передача аргументов по значению и по ссылке</span><span class="sxs-lookup"><span data-stu-id="c6a35-109">Passing Arguments by Value and by Reference</span></span>](../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="c6a35-110">Widening and Narrowing Conversions</span><span class="sxs-lookup"><span data-stu-id="c6a35-110">Widening and Narrowing Conversions</span></span>](../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
