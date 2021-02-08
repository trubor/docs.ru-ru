---
description: 'Дополнительные сведения: процедура Let для свойства не определена, а процедура Get свойства не возвращает объект.'
title: Процедура свойства let не определена, а процедура свойства get не вернула объект
ms.date: 07/20/2015
f1_keywords:
- vbrID451
ms.assetid: 8542382a-689f-4e1b-abc0-c1e2dadb92f4
ms.openlocfilehash: 8376a30abb476abb1d45973e36eb086cadad0054
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795369"
---
# <a name="property-let-procedure-not-defined-and-property-get-procedure-did-not-return-an-object"></a><span data-ttu-id="21688-103">Процедура свойства let не определена, а процедура свойства get не вернула объект</span><span class="sxs-lookup"><span data-stu-id="21688-103">Property let procedure not defined and property get procedure did not return an object</span></span>

<span data-ttu-id="21688-104">Определенные свойства, методы и операции могут применяться только к `Collection` объектам.</span><span class="sxs-lookup"><span data-stu-id="21688-104">Certain properties, methods, and operations can only apply to `Collection` objects.</span></span> <span data-ttu-id="21688-105">Вы указали операцию или свойство, которое является эксклюзивным для коллекций, но объект не является коллекцией.</span><span class="sxs-lookup"><span data-stu-id="21688-105">You specified an operation or property that is exclusive to collections, but the object is not a collection.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="21688-106">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="21688-106">To correct this error</span></span>  
  
1. <span data-ttu-id="21688-107">Проверьте правильность написания имени объекта или свойства или убедитесь, что объект является `Collection` объектом.</span><span class="sxs-lookup"><span data-stu-id="21688-107">Check the spelling of the object or property name, or verify that the object is a `Collection` object.</span></span>  
  
2. <span data-ttu-id="21688-108">Взгляните на `Add` метод, используемый для добавления объекта в коллекцию, чтобы убедиться в правильности синтаксиса и правильности написания всех идентификаторов.</span><span class="sxs-lookup"><span data-stu-id="21688-108">Look at the `Add` method used to add the object to the collection to be sure the syntax is correct and that any identifiers were spelled correctly.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21688-109">См. также</span><span class="sxs-lookup"><span data-stu-id="21688-109">See also</span></span>

- <xref:Microsoft.VisualBasic.Collection>
