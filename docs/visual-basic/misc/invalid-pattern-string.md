---
description: 'Дополнительные сведения: недопустимая строка шаблона'
title: Недопустимая строка шаблона
ms.date: 07/20/2015
ms.assetid: ec1aecdb-5339-4a93-be71-eec56b1d7438
ms.openlocfilehash: 4fbf16dd43ac4ae44e1a99d85caae4a7baf99109
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100462065"
---
# <a name="invalid-pattern-string"></a><span data-ttu-id="da9ae-103">Недопустимая строка шаблона</span><span class="sxs-lookup"><span data-stu-id="da9ae-103">Invalid pattern string</span></span>

<span data-ttu-id="da9ae-104">Строка шаблона, указанная в операции поиска `Like` , является недопустимой.</span><span class="sxs-lookup"><span data-stu-id="da9ae-104">The pattern string specified in the `Like` operation of a search is invalid.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="da9ae-105">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="da9ae-105">To correct this error</span></span>  
  
1. <span data-ttu-id="da9ae-106">Просмотрите допустимые символы для выражений списка.</span><span class="sxs-lookup"><span data-stu-id="da9ae-106">Review the valid characters for list expressions.</span></span>  
  
2. <span data-ttu-id="da9ae-107">В диапазоне шаблона убедитесь, что знак в начале диапазона меньше знака в конце диапазона, как в `[a-z]`.</span><span class="sxs-lookup"><span data-stu-id="da9ae-107">In the pattern range, ensure that the start range character is less than the end range character, as in `[a-z]`.</span></span>  
  
3. <span data-ttu-id="da9ae-108">В диапазоне шаблона убедитесь, что не отсутствуют дефисы, указанные рядом друг с другом, как в `[a--z]`.</span><span class="sxs-lookup"><span data-stu-id="da9ae-108">In the pattern range, ensure that there are not multiple hyphens next to each other, as in `[a--z]`.</span></span>  
  
4. <span data-ttu-id="da9ae-109">Завершите диапазон шаблона закрывающей скобкой.</span><span class="sxs-lookup"><span data-stu-id="da9ae-109">End pattern ranges with a closing bracket.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da9ae-110">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="da9ae-110">See also</span></span>

- [<span data-ttu-id="da9ae-111">Оператор Like</span><span class="sxs-lookup"><span data-stu-id="da9ae-111">Like Operator</span></span>](../language-reference/operators/like-operator.md)
