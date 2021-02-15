---
description: Дополнительные сведения см. в статье как создать коллекцию, используемую инициализатором коллекции (Visual Basic)
title: Практическое руководство. Создание коллекции с помощью инициализатора набора
ms.date: 07/20/2015
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: c858db10-424d-47e0-92cd-e08087cc5ebc
ms.openlocfilehash: 09928cb0fbeb0346fd0e1148ffcd6ddce54279c0
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100460024"
---
# <a name="how-to-create-a-collection-used-by-a-collection-initializer-visual-basic"></a><span data-ttu-id="6153a-103">Практическое руководство. Создание коллекции, используемой инициализатором набора (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6153a-103">How to: Create a Collection Used by a Collection Initializer (Visual Basic)</span></span>

<span data-ttu-id="6153a-104">При использовании инициализатора коллекции для создания коллекции компилятор Visual Basic выполняет поиск `Add` метода типа коллекции, для которого параметры `Add` метода соответствуют типам значений в инициализаторе коллекции.</span><span class="sxs-lookup"><span data-stu-id="6153a-104">When you use a collection initializer to create a collection, the Visual Basic compiler searches for an `Add` method of the collection type for which the parameters for the `Add` method match the types of the values in the collection initializer.</span></span> <span data-ttu-id="6153a-105">Этот `Add` метод используется для заполнения коллекции значениями из инициализатора коллекции.</span><span class="sxs-lookup"><span data-stu-id="6153a-105">This `Add` method is used to populate the collection with the values from the collection initializer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6153a-106">Пример</span><span class="sxs-lookup"><span data-stu-id="6153a-106">Example</span></span>  

 <span data-ttu-id="6153a-107">В следующем примере показана `OrderCollection` коллекция, содержащая открытый `Add` метод, который инициализатор коллекции может использовать для добавления объектов типа `Order` .</span><span class="sxs-lookup"><span data-stu-id="6153a-107">The following example shows an `OrderCollection` collection that contains a public `Add` method that a collection initializer can use to add objects of type `Order`.</span></span> <span data-ttu-id="6153a-108">`Add`Метод позволяет использовать сокращенный синтаксис инициализатора коллекции.</span><span class="sxs-lookup"><span data-stu-id="6153a-108">The `Add` method enables you to use the shortened collection initializer syntax.</span></span>  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#4)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#1)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#2)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="6153a-109">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="6153a-109">See also</span></span>

- [<span data-ttu-id="6153a-110">Инициализаторы коллекций</span><span class="sxs-lookup"><span data-stu-id="6153a-110">Collection Initializers</span></span>](index.md)
- [<span data-ttu-id="6153a-111">Практическое руководство. Создание метода добавления расширения, используемого инициализатором коллекции</span><span class="sxs-lookup"><span data-stu-id="6153a-111">How to: Create an Add Extension Method Used by a Collection Initializer</span></span>](how-to-create-an-add-extension-method-used-by-a-collection-initializer.md)
