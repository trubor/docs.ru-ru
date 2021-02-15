---
description: Дополнительные сведения см. в статье как создать метод расширения, используемый инициализатором коллекции (Visual Basic)
title: Практическое руководство. Создание метода добавления расширения, используемого инициализатором коллекции
ms.date: 07/20/2015
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: f64b52c7-8b11-4410-93a6-cb3aeebcc772
ms.openlocfilehash: 1fbe6f438c4761ae668a6bd6a0a2c38c8efdb439
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100475478"
---
# <a name="how-to-create-an-add-extension-method-used-by-a-collection-initializer-visual-basic"></a><span data-ttu-id="7f6cd-103">Практическое руководство. Создание метода расширения Add, используемого инициализатором набора (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7f6cd-103">How to: Create an Add Extension Method Used by a Collection Initializer (Visual Basic)</span></span>

<span data-ttu-id="7f6cd-104">При использовании инициализатора коллекции для создания коллекции компилятор Visual Basic выполняет поиск `Add` метода типа коллекции, для которого параметры `Add` метода соответствуют типам значений в инициализаторе коллекции.</span><span class="sxs-lookup"><span data-stu-id="7f6cd-104">When you use a collection initializer to create a collection, the Visual Basic compiler searches for an `Add` method of the collection type for which the parameters for the `Add` method match the types of the values in the collection initializer.</span></span> <span data-ttu-id="7f6cd-105">Этот `Add` метод используется для заполнения коллекции значениями из инициализатора коллекции.</span><span class="sxs-lookup"><span data-stu-id="7f6cd-105">This `Add` method is used to populate the collection with the values from the collection initializer.</span></span>  
  
 <span data-ttu-id="7f6cd-106">Если соответствующий `Add` метод не существует и вы не можете изменить код для коллекции, можно добавить метод расширения `Add` с именем, принимающий параметры, необходимые инициализатору коллекции.</span><span class="sxs-lookup"><span data-stu-id="7f6cd-106">If no matching `Add` method exists and you cannot modify the code for the collection, you can add an extension method called `Add` that takes the parameters that are required by the collection initializer.</span></span> <span data-ttu-id="7f6cd-107">Обычно это необходимо сделать при использовании инициализаторов коллекций для универсальных коллекций.</span><span class="sxs-lookup"><span data-stu-id="7f6cd-107">This is typically what you need to do when you use collection initializers for generic collections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7f6cd-108">Пример</span><span class="sxs-lookup"><span data-stu-id="7f6cd-108">Example</span></span>  

 <span data-ttu-id="7f6cd-109">В следующем примере показано, как добавить метод расширения в универсальный тип, <xref:System.Collections.Generic.List%601> чтобы инициализатор коллекции можно было использовать для добавления объектов типа `Employee` .</span><span class="sxs-lookup"><span data-stu-id="7f6cd-109">The following example shows how to add an extension method to the generic <xref:System.Collections.Generic.List%601> type so that a collection initializer can be used to add objects of type `Employee`.</span></span> <span data-ttu-id="7f6cd-110">Метод расширения позволяет использовать сокращенный синтаксис инициализатора коллекции.</span><span class="sxs-lookup"><span data-stu-id="7f6cd-110">The extension method enables you to use the shortened collection initializer syntax.</span></span>  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#1)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#2)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="7f6cd-111">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="7f6cd-111">See also</span></span>

- [<span data-ttu-id="7f6cd-112">Инициализаторы коллекций</span><span class="sxs-lookup"><span data-stu-id="7f6cd-112">Collection Initializers</span></span>](index.md)
- [<span data-ttu-id="7f6cd-113">Практическое руководство. Создание коллекции с помощью инициализатора набора</span><span class="sxs-lookup"><span data-stu-id="7f6cd-113">How to: Create a Collection Used by a Collection Initializer</span></span>](how-to-create-a-collection-used-by-a-collection-initializer.md)
