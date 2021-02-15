---
description: 'Дополнительные сведения: использование экземпляра класса по умолчанию в конструкторе класса может привести к бесконечному рекурсивному вызову'
title: Использование экземпляра класса по умолчанию в конструкторе класса может привести к бесконечному рекурсивному вызову
ms.date: 07/20/2015
ms.assetid: 9645b47f-7de5-46d0-bb45-d5fdaa8aaa2a
ms.openlocfilehash: f65956c92f7d391aa77734d7afd5adf3bea1f906
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100475686"
---
# <a name="use-of-default-instance-of-a-class-in-the-class-constructor-could-lead-to-infinite-recursive-call"></a><span data-ttu-id="8219c-103">Использование экземпляра класса по умолчанию в конструкторе класса может привести к бесконечному рекурсивному вызову</span><span class="sxs-lookup"><span data-stu-id="8219c-103">Use of Default Instance of a class in the class constructor could lead to infinite recursive call</span></span>

<span data-ttu-id="8219c-104">В конструкторе класса использован экземпляр класса по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="8219c-104">A default instance of a class has been used in the constructor of the class.</span></span> <span data-ttu-id="8219c-105">Это может привести к бесконечному рекурсивному вызову — бесконечному циклу.</span><span class="sxs-lookup"><span data-stu-id="8219c-105">This can lead to an infinite recursive call, also known as an infinite loop.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="8219c-106">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="8219c-106">To correct this error</span></span>  
  
- <span data-ttu-id="8219c-107">Удалите из конструктора класса экземпляр по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="8219c-107">Remove the default instance from the class constructor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8219c-108">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="8219c-108">See also</span></span>

- [<span data-ttu-id="8219c-109">Конструкторы</span><span class="sxs-lookup"><span data-stu-id="8219c-109">Constructors</span></span>](../programming-guide/concepts/object-oriented-programming.md#constructors)
