---
description: 'Дополнительные сведения: ни один из доступных перегруженных " <methodname> " не может вызываться с этими аргументами без сужения преобразования'
title: Ни один из доступных перегруженных " <methodname> " не может вызываться с этими аргументами без сужения преобразования
ms.date: 07/20/2015
f1_keywords:
- vbrAmbiguousMatch_NarrowingConversion1
ms.assetid: 2fdbadb9-8ef1-404a-a2ed-ce5f5e55cfcb
ms.openlocfilehash: ff70d43e5e5171055f631a6965b81b934bfb0b39
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100479183"
---
# <a name="no-accessible-overloaded-methodname-can-be-called-with-these-arguments-without-a-narrowing-conversion"></a><span data-ttu-id="78ca8-103">Ни один из доступных перегруженных " \<methodname> " не может вызываться с этими аргументами без сужения преобразования</span><span class="sxs-lookup"><span data-stu-id="78ca8-103">No accessible overloaded '\<methodname>' can be called with these arguments without a narrowing conversion</span></span>

<span data-ttu-id="78ca8-104">Вызван перегруженный метод, однако ни один метод не может быть сопоставлен со списком предоставленных аргументов без сужающего преобразования.</span><span class="sxs-lookup"><span data-stu-id="78ca8-104">An overloaded method was called, but no method was matched with the list of provided arguments without a narrowing conversion.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="78ca8-105">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="78ca8-105">To correct this error</span></span>  
  
1. <span data-ttu-id="78ca8-106">Задайте имя `Option Strict Off`.</span><span class="sxs-lookup"><span data-stu-id="78ca8-106">Specify `Option Strict Off`.</span></span>  
  
2. <span data-ttu-id="78ca8-107">Измените аргументы таким образом, чтобы они соответствовали одной из сигнатур перегруженного метода.</span><span class="sxs-lookup"><span data-stu-id="78ca8-107">Change the arguments to match one of the signatures of the overloaded method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78ca8-108">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="78ca8-108">See also</span></span>

- [<span data-ttu-id="78ca8-109">Передача аргументов по значению и по ссылке</span><span class="sxs-lookup"><span data-stu-id="78ca8-109">Passing Arguments by Value and by Reference</span></span>](../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
- [<span data-ttu-id="78ca8-110">Widening and Narrowing Conversions</span><span class="sxs-lookup"><span data-stu-id="78ca8-110">Widening and Narrowing Conversions</span></span>](../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
