---
description: 'Дополнительные сведения: ни один из доступных перегруженных " <methodname> " не может вызываться с этими аргументами без расширяющего преобразования: <list>'
title: 'Ни один из доступных перегруженных "<methodname>" не может вызываться с этими аргументами без преобразования с расширением:  <list>'
ms.date: 07/20/2015
f1_keywords:
- vbrAmbiguousCall_WideningConversion2
ms.assetid: 5e74f5cf-80bd-4b48-b58a-465f981ec694
ms.openlocfilehash: 68e3ecf16aac19ef644b0060b49b2b316f72e22e
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100479158"
---
# <a name="no-accessible-overloaded-methodname-can-be-called-with-these-arguments-without-a-widening-conversion-list"></a><span data-ttu-id="a7857-103">Ни один из доступных перегруженных "\<methodname>" не может вызываться с этими аргументами без преобразования с расширением: \<list></span><span class="sxs-lookup"><span data-stu-id="a7857-103">No accessible overloaded '\<methodname>' can be called with these arguments without a widening conversion: \<list></span></span>

<span data-ttu-id="a7857-104">Вызван перегруженный метод, однако метод не может быть сопоставлен со списком указанных аргументов без расширяющего преобразования.</span><span class="sxs-lookup"><span data-stu-id="a7857-104">An overloaded method was called, but no method could be matched with the list of provided arguments without a widening conversion.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="a7857-105">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="a7857-105">To correct this error</span></span>  
  
- <span data-ttu-id="a7857-106">Задайте имя `Option Strict Off`.</span><span class="sxs-lookup"><span data-stu-id="a7857-106">Specify `Option Strict Off`.</span></span>  
  
- <span data-ttu-id="a7857-107">Измените аргументы таким образом, чтобы они соответствовали одной из сигнатур перегруженного метода.</span><span class="sxs-lookup"><span data-stu-id="a7857-107">Change the arguments to match one of the signatures of the overloaded method.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7857-108">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="a7857-108">See also</span></span>

- [<span data-ttu-id="a7857-109">Widening and Narrowing Conversions</span><span class="sxs-lookup"><span data-stu-id="a7857-109">Widening and Narrowing Conversions</span></span>](../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [<span data-ttu-id="a7857-110">Оператор Option Strict</span><span class="sxs-lookup"><span data-stu-id="a7857-110">Option Strict Statement</span></span>](../language-reference/statements/option-strict-statement.md)
