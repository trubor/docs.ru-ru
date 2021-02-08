---
description: 'Дополнительные сведения о: BC30996: требуется инициализатор'
title: Ожидается инициализатор
ms.date: 07/20/2015
f1_keywords:
- vbc30996
- bc30996
helpviewer_keywords:
- BC30996
ms.assetid: 6e183fe0-8888-43ed-a062-01571079455f
ms.openlocfilehash: a9859dc319ec53cb42785d71b21447a097ce30f6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796058"
---
# <a name="bc30996-initializer-expected"></a><span data-ttu-id="d4deb-103">BC30996: требуется инициализатор</span><span class="sxs-lookup"><span data-stu-id="d4deb-103">BC30996: Initializer expected</span></span>

<span data-ttu-id="d4deb-104">Предпринята попытка объявить экземпляр класса с помощью инициализатора объекта, в котором список инициализации пуст, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="d4deb-104">You have tried to declare an instance of a class by using an object initializer in which the initialization list is empty, as shown in the following example.</span></span>

 `' Not valid.`

 `' Dim aStudent As New Student With {}`

 <span data-ttu-id="d4deb-105">В списке инициализаторов должно быть инициализировано по крайней мере одно поле или свойство, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="d4deb-105">At least one field or property must be initialized in the initializer list, as shown in the following example.</span></span>

 `Dim aStudent As New Student With {.year = "Senior"}`

 <span data-ttu-id="d4deb-106">**Идентификатор ошибки:** BC30996</span><span class="sxs-lookup"><span data-stu-id="d4deb-106">**Error ID:** BC30996</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="d4deb-107">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="d4deb-107">To correct this error</span></span>

- <span data-ttu-id="d4deb-108">Инициализируйте по крайней мере одно поле или свойство в инициализаторе или не используйте инициализатор объекта.</span><span class="sxs-lookup"><span data-stu-id="d4deb-108">Initialize at least one field or property in the initializer, or do not use an object initializer.</span></span>

## <a name="see-also"></a><span data-ttu-id="d4deb-109">См. также</span><span class="sxs-lookup"><span data-stu-id="d4deb-109">See also</span></span>

- [<span data-ttu-id="d4deb-110">Инициализаторы объектов: именованные и анонимные типы</span><span class="sxs-lookup"><span data-stu-id="d4deb-110">Object Initializers: Named and Anonymous Types</span></span>](../../programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [<span data-ttu-id="d4deb-111">Практическое руководство. Объявление объекта с помощью инициализатора объектов</span><span class="sxs-lookup"><span data-stu-id="d4deb-111">How to: Declare an Object by Using an Object Initializer</span></span>](../../programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)
