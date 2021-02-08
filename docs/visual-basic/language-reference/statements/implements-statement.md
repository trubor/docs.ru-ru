---
description: 'Дополнительные сведения о инструкции: Implements'
title: Оператор Implements
ms.date: 07/20/2015
f1_keywords:
- vb.Implements
- Implements
helpviewer_keywords:
- Implements statement [Visual Basic], syntax
- Implements statement [Visual Basic]
- interface implementation [Visual Basic], Implements statement
ms.assetid: 1fafb83f-f55a-4215-8ea9-681e8622613d
ms.openlocfilehash: aa53d1f3b4ba9d9111f5ffb09198a11511f8d9e9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99768991"
---
# <a name="implements-statement"></a><span data-ttu-id="8f709-103">Оператор Implements</span><span class="sxs-lookup"><span data-stu-id="8f709-103">Implements Statement</span></span>

<span data-ttu-id="8f709-104">Указывает один или несколько интерфейсов или элементов интерфейса, которые должны быть реализованы в определении класса или структуры, в котором они отображаются.</span><span class="sxs-lookup"><span data-stu-id="8f709-104">Specifies one or more interfaces, or interface members, that must be implemented in the class or structure definition in which it appears.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8f709-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="8f709-105">Syntax</span></span>  
  
```vb  
Implements interfacename [, ...]  
' -or-  
Implements interfacename.interfacemember [, ...]  
```  
  
## <a name="parts"></a><span data-ttu-id="8f709-106">Компоненты</span><span class="sxs-lookup"><span data-stu-id="8f709-106">Parts</span></span>  

 `interfacename`  
 <span data-ttu-id="8f709-107">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="8f709-107">Required.</span></span> <span data-ttu-id="8f709-108">Интерфейс, свойства, процедуры и события которого должны быть реализованы соответствующими элементами в классе или структуре.</span><span class="sxs-lookup"><span data-stu-id="8f709-108">An interface whose properties, procedures, and events are to be implemented by corresponding members in the class or structure.</span></span>  
  
 `interfacemember`  
 <span data-ttu-id="8f709-109">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="8f709-109">Required.</span></span> <span data-ttu-id="8f709-110">Член реализуемого интерфейса.</span><span class="sxs-lookup"><span data-stu-id="8f709-110">The member of an interface that is being implemented.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8f709-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="8f709-111">Remarks</span></span>  

 <span data-ttu-id="8f709-112">Интерфейс — это коллекция прототипов, представляющих члены (свойства, процедуры и события), которые инкапсулирует интерфейс.</span><span class="sxs-lookup"><span data-stu-id="8f709-112">An interface is a collection of prototypes representing the members (properties, procedures, and events) the interface encapsulates.</span></span> <span data-ttu-id="8f709-113">Интерфейсы содержат только объявления для членов; классы и структуры реализуют эти члены.</span><span class="sxs-lookup"><span data-stu-id="8f709-113">Interfaces contain only the declarations for members; classes and structures implement these members.</span></span> <span data-ttu-id="8f709-114">Дополнительные сведения см. в разделе [Интерфейсы](../../programming-guide/language-features/interfaces/index.md).</span><span class="sxs-lookup"><span data-stu-id="8f709-114">For more information, see [Interfaces](../../programming-guide/language-features/interfaces/index.md).</span></span>  
  
 <span data-ttu-id="8f709-115">`Implements`Оператор должен следовать непосредственно за `Class` `Structure` оператором или.</span><span class="sxs-lookup"><span data-stu-id="8f709-115">The `Implements` statement must immediately follow the `Class` or `Structure` statement.</span></span>  
  
 <span data-ttu-id="8f709-116">При реализации интерфейса необходимо реализовать все члены, объявленные в интерфейсе.</span><span class="sxs-lookup"><span data-stu-id="8f709-116">When you implement an interface, you must implement all the members declared in the interface.</span></span> <span data-ttu-id="8f709-117">Пропуск любого члена считается синтаксической ошибкой.</span><span class="sxs-lookup"><span data-stu-id="8f709-117">Omitting any member is considered to be a syntax error.</span></span> <span data-ttu-id="8f709-118">Для реализации отдельного элемента необходимо указать ключевое слово [Implements](implements-clause.md) (отдельно от `Implements` оператора) при объявлении члена в классе или структуре.</span><span class="sxs-lookup"><span data-stu-id="8f709-118">To implement an individual member, you specify the [Implements](implements-clause.md) keyword (which is separate from the `Implements` statement) when you declare the member in the class or structure.</span></span> <span data-ttu-id="8f709-119">Дополнительные сведения см. в разделе [Интерфейсы](../../programming-guide/language-features/interfaces/index.md).</span><span class="sxs-lookup"><span data-stu-id="8f709-119">For more information, see [Interfaces](../../programming-guide/language-features/interfaces/index.md).</span></span>  
  
 <span data-ttu-id="8f709-120">Классы могут использовать [закрытые](../modifiers/private.md) реализации свойств и процедур, но эти члены доступны только путем приведения экземпляра реализующего класса к переменной, объявленной как тип интерфейса.</span><span class="sxs-lookup"><span data-stu-id="8f709-120">Classes can use [Private](../modifiers/private.md) implementations of properties and procedures, but these members are accessible only by casting an instance of the implementing class into a variable declared to be of the type of the interface.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8f709-121">Пример</span><span class="sxs-lookup"><span data-stu-id="8f709-121">Example</span></span>  

 <span data-ttu-id="8f709-122">В следующем примере показано, как использовать `Implements` инструкцию для реализации членов интерфейса.</span><span class="sxs-lookup"><span data-stu-id="8f709-122">The following example shows how to use the `Implements` statement to implement members of an interface.</span></span> <span data-ttu-id="8f709-123">Он определяет интерфейс с именем `ICustomerInfo` с событием, свойством и процедурой.</span><span class="sxs-lookup"><span data-stu-id="8f709-123">It defines an interface named `ICustomerInfo` with an event, a property, and a procedure.</span></span> <span data-ttu-id="8f709-124">Класс `customerInfo` реализует все члены, определенные в интерфейсе.</span><span class="sxs-lookup"><span data-stu-id="8f709-124">The class `customerInfo` implements all the members defined in the interface.</span></span>  
  
 [!code-vb[VbVbalrStatements#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#33)]  
  
 <span data-ttu-id="8f709-125">Обратите внимание, что класс `customerInfo` использует `Implements` оператор в отдельной строке исходного кода, чтобы указать, что класс реализует все члены `ICustomerInfo` интерфейса.</span><span class="sxs-lookup"><span data-stu-id="8f709-125">Note that the class `customerInfo` uses the `Implements` statement on a separate source code line to indicate that the class implements all the members of the `ICustomerInfo` interface.</span></span> <span data-ttu-id="8f709-126">Затем каждый член класса использует `Implements` ключевое слово как часть его объявления члена, чтобы указать, что он реализует этот член интерфейса.</span><span class="sxs-lookup"><span data-stu-id="8f709-126">Then each member in the class uses the `Implements` keyword as part of its member declaration to indicate that it implements that interface member.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8f709-127">Пример</span><span class="sxs-lookup"><span data-stu-id="8f709-127">Example</span></span>  

 <span data-ttu-id="8f709-128">В следующих двух процедурах показано, как можно использовать интерфейс, реализованный в предыдущем примере.</span><span class="sxs-lookup"><span data-stu-id="8f709-128">The following two procedures show how you could use the interface implemented in the preceding example.</span></span> <span data-ttu-id="8f709-129">Чтобы протестировать реализацию, добавьте эти процедуры в проект и вызовите `testImplements` процедуру.</span><span class="sxs-lookup"><span data-stu-id="8f709-129">To test the implementation, add these procedures to your project and call the `testImplements` procedure.</span></span>  
  
 [!code-vb[VbVbalrStatements#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#34)]  
  
## <a name="see-also"></a><span data-ttu-id="8f709-130">См. также</span><span class="sxs-lookup"><span data-stu-id="8f709-130">See also</span></span>

- [<span data-ttu-id="8f709-131">Реализации</span><span class="sxs-lookup"><span data-stu-id="8f709-131">Implements</span></span>](implements-clause.md)
- [<span data-ttu-id="8f709-132">Оператор Interface</span><span class="sxs-lookup"><span data-stu-id="8f709-132">Interface Statement</span></span>](interface-statement.md)
- [<span data-ttu-id="8f709-133">Интерфейсы</span><span class="sxs-lookup"><span data-stu-id="8f709-133">Interfaces</span></span>](../../programming-guide/language-features/interfaces/index.md)
