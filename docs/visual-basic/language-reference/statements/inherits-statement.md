---
description: 'Дополнительные сведения о: Inherits, инструкция'
title: Inherits Statement
ms.date: 07/20/2015
f1_keywords:
- vb.Inherits
- Inherits
helpviewer_keywords:
- Inherits statement [Visual Basic]
- Inherits statement [Visual Basic], syntax
ms.assetid: 9e6fe042-9af3-4341-8093-fc3537770cf2
ms.openlocfilehash: fba574ec207b384c1e7219341526a4a89c8a619c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99768926"
---
# <a name="inherits-statement"></a><span data-ttu-id="a8559-103">Inherits Statement</span><span class="sxs-lookup"><span data-stu-id="a8559-103">Inherits Statement</span></span>

<span data-ttu-id="a8559-104">Заставляет текущий класс или интерфейс наследовать атрибуты, переменные, свойства, процедуры и события из другого класса или набора интерфейсов.</span><span class="sxs-lookup"><span data-stu-id="a8559-104">Causes the current class or interface to inherit the attributes, variables, properties, procedures, and events from another class or set of interfaces.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8559-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a8559-105">Syntax</span></span>  
  
```vb  
Inherits basetypenames  
```  
  
## <a name="parts"></a><span data-ttu-id="a8559-106">Компоненты</span><span class="sxs-lookup"><span data-stu-id="a8559-106">Parts</span></span>  
  
|<span data-ttu-id="a8559-107">Термин</span><span class="sxs-lookup"><span data-stu-id="a8559-107">Term</span></span>|<span data-ttu-id="a8559-108">Определение</span><span class="sxs-lookup"><span data-stu-id="a8559-108">Definition</span></span>|  
|---|---|  
|`basetypenames`|<span data-ttu-id="a8559-109">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="a8559-109">Required.</span></span> <span data-ttu-id="a8559-110">Имя класса, от которого наследует этот класс.</span><span class="sxs-lookup"><span data-stu-id="a8559-110">The name of the class from which this class derives.</span></span><br /><br /> <span data-ttu-id="a8559-111">-или-</span><span class="sxs-lookup"><span data-stu-id="a8559-111">-or-</span></span><br /><br /> <span data-ttu-id="a8559-112">Имена интерфейсов, из которых наследуется этот интерфейс.</span><span class="sxs-lookup"><span data-stu-id="a8559-112">The names of the interfaces from which this interface derives.</span></span> <span data-ttu-id="a8559-113">Используйте запятые для разделения нескольких имен.</span><span class="sxs-lookup"><span data-stu-id="a8559-113">Use commas to separate multiple names.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a8559-114">Remarks</span><span class="sxs-lookup"><span data-stu-id="a8559-114">Remarks</span></span>  

 <span data-ttu-id="a8559-115">При использовании `Inherits` инструкция должна быть первой непустой строкой, не являющейся комментарием, в определении класса или интерфейса.</span><span class="sxs-lookup"><span data-stu-id="a8559-115">If used, the `Inherits` statement must be the first non-blank, non-comment line in a class or interface definition.</span></span> <span data-ttu-id="a8559-116">Он должен следовать сразу за `Class` `Interface` оператором или.</span><span class="sxs-lookup"><span data-stu-id="a8559-116">It should immediately follow the `Class` or `Interface` statement.</span></span>  
  
 <span data-ttu-id="a8559-117">Можно использовать `Inherits` только в классе или интерфейсе.</span><span class="sxs-lookup"><span data-stu-id="a8559-117">You can use `Inherits` only in a class or interface.</span></span> <span data-ttu-id="a8559-118">Это означает, что контекст объявления для наследования не может быть исходным файлом, пространством имен, структурой, модулем, процедурой или блоком.</span><span class="sxs-lookup"><span data-stu-id="a8559-118">This means the declaration context for an inheritance cannot be a source file, namespace, structure, module, procedure, or block.</span></span>  
  
## <a name="rules"></a><span data-ttu-id="a8559-119">Правила</span><span class="sxs-lookup"><span data-stu-id="a8559-119">Rules</span></span>  
  
- <span data-ttu-id="a8559-120">**Наследование класса.**</span><span class="sxs-lookup"><span data-stu-id="a8559-120">**Class Inheritance.**</span></span> <span data-ttu-id="a8559-121">Если класс использует `Inherits` инструкцию, можно указать только один базовый класс.</span><span class="sxs-lookup"><span data-stu-id="a8559-121">If a class uses the `Inherits` statement, you can specify only one base class.</span></span>  
  
     <span data-ttu-id="a8559-122">Класс не может наследовать от класса, вложенного в него.</span><span class="sxs-lookup"><span data-stu-id="a8559-122">A class cannot inherit from a class nested within it.</span></span>  
  
- <span data-ttu-id="a8559-123">**Наследование интерфейса.**</span><span class="sxs-lookup"><span data-stu-id="a8559-123">**Interface Inheritance.**</span></span> <span data-ttu-id="a8559-124">Если интерфейс использует `Inherits` инструкцию, можно указать один или несколько базовых интерфейсов.</span><span class="sxs-lookup"><span data-stu-id="a8559-124">If an interface uses the `Inherits` statement, you can specify one or more base interfaces.</span></span> <span data-ttu-id="a8559-125">Можно наследовать от двух интерфейсов, даже если каждый из них определяет член с тем же именем.</span><span class="sxs-lookup"><span data-stu-id="a8559-125">You can inherit from two interfaces even if they each define a member with the same name.</span></span> <span data-ttu-id="a8559-126">В этом случае реализующий код должен использовать уточнение имени, чтобы указать, какой член он реализует.</span><span class="sxs-lookup"><span data-stu-id="a8559-126">If you do so, the implementing code must use name qualification to specify which member it is implementing.</span></span>  
  
     <span data-ttu-id="a8559-127">Интерфейс не может наследовать от другого интерфейса с более узким уровнем доступа.</span><span class="sxs-lookup"><span data-stu-id="a8559-127">An interface cannot inherit from another interface with a more restrictive access level.</span></span> <span data-ttu-id="a8559-128">Например, `Public` интерфейс не может наследовать от `Friend` интерфейса.</span><span class="sxs-lookup"><span data-stu-id="a8559-128">For example, a `Public` interface cannot inherit from a `Friend` interface.</span></span>  
  
     <span data-ttu-id="a8559-129">Интерфейс не может наследовать от вложенного в него интерфейса.</span><span class="sxs-lookup"><span data-stu-id="a8559-129">An interface cannot inherit from an interface nested within it.</span></span>  
  
 <span data-ttu-id="a8559-130">Примером наследования класса в платформа .NET Framework является <xref:System.ArgumentException> класс, который наследует от <xref:System.SystemException> класса.</span><span class="sxs-lookup"><span data-stu-id="a8559-130">An example of class inheritance in the .NET Framework is the <xref:System.ArgumentException> class, which inherits from the <xref:System.SystemException> class.</span></span> <span data-ttu-id="a8559-131">Это обеспечивает <xref:System.ArgumentException> все предопределенные свойства и процедуры, необходимые системным исключениям, таким как <xref:System.Exception.Message%2A> свойство и <xref:System.Exception.ToString%2A> метод.</span><span class="sxs-lookup"><span data-stu-id="a8559-131">This provides to <xref:System.ArgumentException> all the predefined properties and procedures required by system exceptions, such as the <xref:System.Exception.Message%2A> property and the <xref:System.Exception.ToString%2A> method.</span></span>  
  
 <span data-ttu-id="a8559-132">Примером наследования интерфейса в платформа .NET Framework является <xref:System.Collections.ICollection> интерфейс, который наследует от <xref:System.Collections.IEnumerable> интерфейса.</span><span class="sxs-lookup"><span data-stu-id="a8559-132">An example of interface inheritance in the .NET Framework is the <xref:System.Collections.ICollection> interface, which inherits from the <xref:System.Collections.IEnumerable> interface.</span></span> <span data-ttu-id="a8559-133">Это приводит <xref:System.Collections.ICollection> к наследованию определения перечислителя, необходимого для прохода по коллекции.</span><span class="sxs-lookup"><span data-stu-id="a8559-133">This causes <xref:System.Collections.ICollection> to inherit the definition of the enumerator required to traverse a collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a8559-134">Пример</span><span class="sxs-lookup"><span data-stu-id="a8559-134">Example</span></span>  

 <span data-ttu-id="a8559-135">В следующем примере оператор используется `Inherits` для демонстрации того, как класс с именем `thisClass` может наследовать все члены базового класса с именем `anotherClass` .</span><span class="sxs-lookup"><span data-stu-id="a8559-135">The following example uses the `Inherits` statement to show how a class named `thisClass` can inherit all the members of a base class named `anotherClass`.</span></span>  
  
 [!code-vb[VbVbalrStatements#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#37)]  
  
## <a name="example"></a><span data-ttu-id="a8559-136">Пример</span><span class="sxs-lookup"><span data-stu-id="a8559-136">Example</span></span>  

 <span data-ttu-id="a8559-137">В следующем примере показано наследование нескольких интерфейсов.</span><span class="sxs-lookup"><span data-stu-id="a8559-137">The following example shows inheritance of multiple interfaces.</span></span>  
  
 [!code-vb[VbVbalrStatements#38](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#38)]  
  
 <span data-ttu-id="a8559-138">Интерфейс с именем `thisInterface` теперь включает все определения в <xref:System.IComparable> <xref:System.IDisposable> интерфейсах, и, <xref:System.IFormattable> унаследованные члены предоставляют соответствующие типы для сравнения двух объектов, высвобождения выделенных ресурсов и выражения значения объекта как `String` .</span><span class="sxs-lookup"><span data-stu-id="a8559-138">The interface named `thisInterface` now includes all the definitions in the <xref:System.IComparable>, <xref:System.IDisposable>, and <xref:System.IFormattable> interfaces The inherited members provide respectively for type-specific comparison of two objects, releasing allocated resources, and expressing the value of an object as a `String`.</span></span> <span data-ttu-id="a8559-139">Класс, реализующий, `thisInterface` должен реализовывать каждый член каждого базового интерфейса.</span><span class="sxs-lookup"><span data-stu-id="a8559-139">A class that implements `thisInterface` must implement every member of every base interface.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8559-140">См. также</span><span class="sxs-lookup"><span data-stu-id="a8559-140">See also</span></span>

- [<span data-ttu-id="a8559-141">MustInherit</span><span class="sxs-lookup"><span data-stu-id="a8559-141">MustInherit</span></span>](../modifiers/mustinherit.md)
- [<span data-ttu-id="a8559-142">NotInheritable</span><span class="sxs-lookup"><span data-stu-id="a8559-142">NotInheritable</span></span>](../modifiers/notinheritable.md)
- [<span data-ttu-id="a8559-143">Объекты и классы</span><span class="sxs-lookup"><span data-stu-id="a8559-143">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
- [<span data-ttu-id="a8559-144">Основы наследования</span><span class="sxs-lookup"><span data-stu-id="a8559-144">Inheritance Basics</span></span>](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [<span data-ttu-id="a8559-145">Интерфейсы</span><span class="sxs-lookup"><span data-stu-id="a8559-145">Interfaces</span></span>](../../programming-guide/language-features/interfaces/index.md)
