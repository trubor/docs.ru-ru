---
description: 'Дополнительные сведения о: закрыто защищено (Visual Basic)'
title: Частный защищенный
ms.date: 05/10/2018
f1_keywords:
- vb.PrivateProtected
helpviewer_keywords:
- Private Protected keyword [Visual Basic]
- Private Protected keyword [Visual Basic], syntax
ms.openlocfilehash: eb521ace77cd16f4904657cbdc035575e98e98fa
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99700966"
---
# <a name="private-protected-visual-basic"></a><span data-ttu-id="84f44-103">Частный защищенный (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="84f44-103">Private Protected (Visual Basic)</span></span>

<span data-ttu-id="84f44-104">Комбинация ключевых слов `Private Protected` является модификатором доступа к члену.</span><span class="sxs-lookup"><span data-stu-id="84f44-104">The `Private Protected` keyword combination is a member access modifier.</span></span> <span data-ttu-id="84f44-105">`Private Protected`Элемент доступен для всех элементов в содержащем его классе, а также по типам, производным от содержащего класса, но только в том случае, если они находятся в содержащей его сборке.</span><span class="sxs-lookup"><span data-stu-id="84f44-105">A `Private Protected` member is accessible by all members in its containing class, as well as by types derived from the containing class, but only if they are found in its containing assembly.</span></span>

<span data-ttu-id="84f44-106">Можно указать `Private Protected` только для членов классов. нельзя применять `Private Protected` к членам структуры, поскольку структуры не наследуются.</span><span class="sxs-lookup"><span data-stu-id="84f44-106">You can specify `Private Protected` only on members of classes; you cannot apply `Private Protected` to members of a structure because structures cannot be inherited.</span></span>

<span data-ttu-id="84f44-107">`Private Protected`Модификатор доступа поддерживается Visual Basic 15,5 и более поздних версий.</span><span class="sxs-lookup"><span data-stu-id="84f44-107">The `Private Protected` access modifier is supported by Visual Basic 15.5 and later.</span></span> <span data-ttu-id="84f44-108">Чтобы использовать его, можно добавить в файл проекта Visual Basic (VBPROJ) следующий элемент \* .</span><span class="sxs-lookup"><span data-stu-id="84f44-108">To use it, you can add the following element to your Visual Basic project (\*.vbproj) file.</span></span> <span data-ttu-id="84f44-109">Если в системе установлен Visual Basic 15,5 или более поздней версии, он позволяет воспользоваться всеми возможностями языка, поддерживаемыми последней версией компилятора Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="84f44-109">As long as Visual Basic 15.5 or later is installed on your system, it lets you take advantage of all the language features supported by the latest version of the Visual Basic compiler:</span></span>

```xml
<PropertyGroup>
   <LangVersion>latest</LangVersion>
</PropertyGroup>
```

<span data-ttu-id="84f44-110">Дополнительные сведения см. [в разделе Задание языковой версии Visual Basic](../configure-language-version.md).</span><span class="sxs-lookup"><span data-stu-id="84f44-110">For more information see [setting the Visual Basic language version](../configure-language-version.md).</span></span>

> [!NOTE]
> <span data-ttu-id="84f44-111">В Visual Studio выбор справки F1 `private protected` для предоставляет справку как для [частного](private.md) , так и для [защищенного](protected.md).</span><span class="sxs-lookup"><span data-stu-id="84f44-111">In Visual Studio, selecting F1 help on `private protected` provides help for either [private](private.md) or [protected](protected.md).</span></span> <span data-ttu-id="84f44-112">Интегрированная среда разработки выбирает один маркер под курсором, а не составное слово.</span><span class="sxs-lookup"><span data-stu-id="84f44-112">The IDE picks the single token under the cursor rather than the compound word.</span></span>

## <a name="rules"></a><span data-ttu-id="84f44-113">Правила</span><span class="sxs-lookup"><span data-stu-id="84f44-113">Rules</span></span>

- <span data-ttu-id="84f44-114">**Контекст объявления.**</span><span class="sxs-lookup"><span data-stu-id="84f44-114">**Declaration Context.**</span></span> <span data-ttu-id="84f44-115">Можно использовать `Private Protected` только на уровне класса.</span><span class="sxs-lookup"><span data-stu-id="84f44-115">You can use `Private Protected` only at the class level.</span></span> <span data-ttu-id="84f44-116">Это означает, что контекст объявления для `Protected` элемента должен быть классом и не может быть исходным файлом, пространством имен, интерфейсом, модулем, структурой или процедурой.</span><span class="sxs-lookup"><span data-stu-id="84f44-116">This means the declaration context for a `Protected` element must be a class, and cannot be a source file, namespace, interface, module, structure, or procedure.</span></span>

## <a name="behavior"></a><span data-ttu-id="84f44-117">Поведение</span><span class="sxs-lookup"><span data-stu-id="84f44-117">Behavior</span></span>

- <span data-ttu-id="84f44-118">**Уровень доступа.**</span><span class="sxs-lookup"><span data-stu-id="84f44-118">**Access Level.**</span></span> <span data-ttu-id="84f44-119">Весь код в классе может обращаться к его элементам.</span><span class="sxs-lookup"><span data-stu-id="84f44-119">All code in a class can access its elements.</span></span> <span data-ttu-id="84f44-120">Код в любом классе, производном от базового класса и содержащийся в той же сборке, имеет доступ ко всем `Private Protected` элементам базового класса.</span><span class="sxs-lookup"><span data-stu-id="84f44-120">Code in any class that derives from a base class and is contained in the same assembly can access all the `Private Protected` elements of the base class.</span></span> <span data-ttu-id="84f44-121">Однако код в любом классе, производном от базового класса и содержащийся в другой сборке, не может получить доступ к элементам базового класса `Private Protected` .</span><span class="sxs-lookup"><span data-stu-id="84f44-121">However, code in any class that derives from a base class and is contained in a different assembly can't access the base class `Private Protected` elements.</span></span>

- <span data-ttu-id="84f44-122">**Модификаторы доступа.**</span><span class="sxs-lookup"><span data-stu-id="84f44-122">**Access Modifiers.**</span></span> <span data-ttu-id="84f44-123">Ключевые слова, определяющие уровень доступа, называются *модификаторами доступа*.</span><span class="sxs-lookup"><span data-stu-id="84f44-123">The keywords that specify access level are called *access modifiers*.</span></span> <span data-ttu-id="84f44-124">Сравнение модификаторов доступа см. [в разделе уровни доступа в Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span><span class="sxs-lookup"><span data-stu-id="84f44-124">For a comparison of the access modifiers, see [Access levels in Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).</span></span>

<span data-ttu-id="84f44-125">Модификатор `Private Protected` можно использовать в следующих контекстах:</span><span class="sxs-lookup"><span data-stu-id="84f44-125">The `Private Protected` modifier can be used in these contexts:</span></span>

- <span data-ttu-id="84f44-126">[Оператор Class](../statements/class-statement.md) вложенного класса</span><span class="sxs-lookup"><span data-stu-id="84f44-126">[Class Statement](../statements/class-statement.md) of a nested class</span></span>

- [<span data-ttu-id="84f44-127">Оператор Const</span><span class="sxs-lookup"><span data-stu-id="84f44-127">Const Statement</span></span>](../statements/const-statement.md)

- [<span data-ttu-id="84f44-128">Declare Statement</span><span class="sxs-lookup"><span data-stu-id="84f44-128">Declare Statement</span></span>](../statements/declare-statement.md)

- <span data-ttu-id="84f44-129">[Оператор Delegate](../statements/delegate-statement.md) делегата, вложенного в класс</span><span class="sxs-lookup"><span data-stu-id="84f44-129">[Delegate Statement](../statements/delegate-statement.md) of a delegate nested in a class</span></span>

- [<span data-ttu-id="84f44-130">Оператор Dim</span><span class="sxs-lookup"><span data-stu-id="84f44-130">Dim Statement</span></span>](../statements/dim-statement.md)

- <span data-ttu-id="84f44-131">[Оператор Enum](../statements/enum-statement.md) перечисления, вложенного в класс</span><span class="sxs-lookup"><span data-stu-id="84f44-131">[Enum Statement](../statements/enum-statement.md) of an enumeration nested in a class</span></span>

- [<span data-ttu-id="84f44-132">Оператор Event</span><span class="sxs-lookup"><span data-stu-id="84f44-132">Event Statement</span></span>](../statements/event-statement.md)

- [<span data-ttu-id="84f44-133">Оператор Function</span><span class="sxs-lookup"><span data-stu-id="84f44-133">Function Statement</span></span>](../statements/function-statement.md)

- <span data-ttu-id="84f44-134">[Оператор Interface](../statements/interface-statement.md) интерфейса, вложенного в класс</span><span class="sxs-lookup"><span data-stu-id="84f44-134">[Interface Statement](../statements/interface-statement.md) of an interface nested in a class</span></span>

- [<span data-ttu-id="84f44-135">Property Statement</span><span class="sxs-lookup"><span data-stu-id="84f44-135">Property Statement</span></span>](../statements/property-statement.md)

- <span data-ttu-id="84f44-136">[Оператор Structure](../statements/structure-statement.md) структуры, вложенной в класс</span><span class="sxs-lookup"><span data-stu-id="84f44-136">[Structure Statement](../statements/structure-statement.md) of a structure nested in a class</span></span>

- [<span data-ttu-id="84f44-137">Оператор Sub</span><span class="sxs-lookup"><span data-stu-id="84f44-137">Sub Statement</span></span>](../statements/sub-statement.md)

## <a name="see-also"></a><span data-ttu-id="84f44-138">См. также</span><span class="sxs-lookup"><span data-stu-id="84f44-138">See also</span></span>

- [<span data-ttu-id="84f44-139">Общедоступная</span><span class="sxs-lookup"><span data-stu-id="84f44-139">Public</span></span>](public.md)
- [<span data-ttu-id="84f44-140">Защищенный</span><span class="sxs-lookup"><span data-stu-id="84f44-140">Protected</span></span>](protected.md)
- [<span data-ttu-id="84f44-141">Friend</span><span class="sxs-lookup"><span data-stu-id="84f44-141">Friend</span></span>](friend.md)
- [<span data-ttu-id="84f44-142">Частная</span><span class="sxs-lookup"><span data-stu-id="84f44-142">Private</span></span>](private.md)
- [<span data-ttu-id="84f44-143">Protected Friend</span><span class="sxs-lookup"><span data-stu-id="84f44-143">Protected Friend</span></span>](./protected-friend.md)
- [<span data-ttu-id="84f44-144">Уровни доступа в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="84f44-144">Access levels in Visual Basic</span></span>](../../programming-guide/language-features/declared-elements/access-levels.md)
- [<span data-ttu-id="84f44-145">Процедуры</span><span class="sxs-lookup"><span data-stu-id="84f44-145">Procedures</span></span>](../../programming-guide/language-features/procedures/index.md)
- [<span data-ttu-id="84f44-146">Структуры</span><span class="sxs-lookup"><span data-stu-id="84f44-146">Structures</span></span>](../../programming-guide/language-features/data-types/structures.md)
- [<span data-ttu-id="84f44-147">Объекты и классы</span><span class="sxs-lookup"><span data-stu-id="84f44-147">Objects and Classes</span></span>](../../programming-guide/language-features/objects-and-classes/index.md)
