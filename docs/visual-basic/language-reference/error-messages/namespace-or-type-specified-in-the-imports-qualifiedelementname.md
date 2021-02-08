---
description: 'Дополнительные сведения о: BC40056: namespace или Type, указанные в Imports " <qualifiedelementname> ", не содержат открытых членов или не могут быть найдены'
title: Пространство имен или тип, указанный в Imports <qualifiedelementname>, не содержит общих членов или не найден
ms.date: 07/20/2015
f1_keywords:
- bc40056
- vbc40056
helpviewer_keywords:
- BC40056
ms.assetid: b59f5754-444f-4378-9272-9678b437e84a
ms.openlocfilehash: e98ba70660823196e763300cd33ec1ba9a9db3b4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795707"
---
# <a name="bc40056-namespace-or-type-specified-in-the-imports-qualifiedelementname-doesnt-contain-any-public-member-or-cannot-be-found"></a><span data-ttu-id="487e7-103">BC40056: пространство имен или тип, указанные в Imports " \<qualifiedelementname> ", не содержат открытых членов или не могут быть найдены</span><span class="sxs-lookup"><span data-stu-id="487e7-103">BC40056: Namespace or type specified in the Imports '\<qualifiedelementname>' doesn't contain any public member or cannot be found</span></span>

<span data-ttu-id="487e7-104">Пространство имен или тип, указанные в Imports " \<qualifiedelementname> ", не содержат открытых членов или не могут быть найдены.</span><span class="sxs-lookup"><span data-stu-id="487e7-104">Namespace or type specified in the Imports '\<qualifiedelementname>' doesn't contain any public member or cannot be found.</span></span> <span data-ttu-id="487e7-105">Убедитесь, что пространство имен или тип определены и содержат по крайней мере один открытый член.</span><span class="sxs-lookup"><span data-stu-id="487e7-105">Make sure the namespace or the type is defined and contains at least one public member.</span></span> <span data-ttu-id="487e7-106">Убедитесь, что имя псевдонима не содержит других псевдонимов.</span><span class="sxs-lookup"><span data-stu-id="487e7-106">Make sure the alias name doesn't contain other aliases.</span></span>

<span data-ttu-id="487e7-107">`Imports`Оператор указывает содержащий элемент, который либо не может быть найден, либо не определяет какие-либо `Public` элементы.</span><span class="sxs-lookup"><span data-stu-id="487e7-107">An `Imports` statement specifies a containing element that either cannot be found or does not define any `Public` members.</span></span>

<span data-ttu-id="487e7-108">*Содержащий элемент* может быть пространством имен, классом, структурой, модулем, интерфейсом или перечислением.</span><span class="sxs-lookup"><span data-stu-id="487e7-108">A *containing element* can be a namespace, class, structure, module, interface, or enumeration.</span></span> <span data-ttu-id="487e7-109">Содержащий элемент содержит такие элементы, как переменные, процедуры или другие элементы, содержащие.</span><span class="sxs-lookup"><span data-stu-id="487e7-109">The containing element contains members, such as variables, procedures, or other containing elements.</span></span>

<span data-ttu-id="487e7-110">Цель импорта заключается в том, чтобы предоставить коду доступ к пространству имен или членам типа без необходимости уточнять их.</span><span class="sxs-lookup"><span data-stu-id="487e7-110">The purpose of importing is to allow your code to access namespace or type members without having to qualify them.</span></span> <span data-ttu-id="487e7-111">В проекте также может потребоваться добавить ссылку на пространство имен или тип.</span><span class="sxs-lookup"><span data-stu-id="487e7-111">Your project might also need to add a reference to the namespace or type.</span></span> <span data-ttu-id="487e7-112">Дополнительные сведения см. в разделе "Импорт содержащихся элементов" в [ссылках на объявленные элементы](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="487e7-112">For more information, see "Importing Containing Elements" in [References to Declared Elements](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>

<span data-ttu-id="487e7-113">Если компилятор не может найти указанный содержащий элемент, он не сможет разрешить ссылки, которые его используют.</span><span class="sxs-lookup"><span data-stu-id="487e7-113">If the compiler cannot find the specified containing element, then it cannot resolve references that use it.</span></span> <span data-ttu-id="487e7-114">Если он находит элемент, но элемент не предоставляет никаких `Public` членов, ссылка не может быть успешной.</span><span class="sxs-lookup"><span data-stu-id="487e7-114">If it finds the element but the element does not expose any `Public` members, then no reference can be successful.</span></span> <span data-ttu-id="487e7-115">В любом случае нет смысла импортировать элемент.</span><span class="sxs-lookup"><span data-stu-id="487e7-115">In either case it is meaningless to import the element.</span></span>

<span data-ttu-id="487e7-116">Помните, что при импорте содержащего элемента и присвоении ему псевдонима импорта нельзя использовать этот псевдоним импорта для импорта другого элемента.</span><span class="sxs-lookup"><span data-stu-id="487e7-116">Keep in mind that if you import a containing element and assign an import alias to it, then you cannot use that import alias to import another element.</span></span> <span data-ttu-id="487e7-117">Следующий код приводит к ошибке компилятора.</span><span class="sxs-lookup"><span data-stu-id="487e7-117">The following code generates a compiler error.</span></span>

```vb
Imports winfrm = System.Windows.Forms

' The following statement is INVALID  because it reuses an import alias.

Imports behave = winfrm.Design.Behavior`
```

<span data-ttu-id="487e7-118">**Идентификатор ошибки:** BC40056</span><span class="sxs-lookup"><span data-stu-id="487e7-118">**Error ID:** BC40056</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="487e7-119">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="487e7-119">To correct this error</span></span>

1. <span data-ttu-id="487e7-120">Убедитесь, что содержащий элемент доступен из проекта.</span><span class="sxs-lookup"><span data-stu-id="487e7-120">Verify that the containing element is accessible from your project.</span></span>

2. <span data-ttu-id="487e7-121">Убедитесь, что спецификация содержащего элемента не содержит псевдоним импорта из другого импорта.</span><span class="sxs-lookup"><span data-stu-id="487e7-121">Verify that the specification of the containing element does not include any import alias from another import.</span></span>

3. <span data-ttu-id="487e7-122">Убедитесь, что содержащий элемент предоставляет по крайней мере один `Public` элемент.</span><span class="sxs-lookup"><span data-stu-id="487e7-122">Verify that the containing element exposes at least one `Public` member.</span></span>

## <a name="see-also"></a><span data-ttu-id="487e7-123">См. также</span><span class="sxs-lookup"><span data-stu-id="487e7-123">See also</span></span>

- [<span data-ttu-id="487e7-124">Оператор Imports (пространство имен .NET и тип)</span><span class="sxs-lookup"><span data-stu-id="487e7-124">Imports Statement (.NET Namespace and Type)</span></span>](../statements/imports-statement-net-namespace-and-type.md)
- [<span data-ttu-id="487e7-125">Оператор Namespace</span><span class="sxs-lookup"><span data-stu-id="487e7-125">Namespace Statement</span></span>](../statements/namespace-statement.md)
- [<span data-ttu-id="487e7-126">Общедоступная</span><span class="sxs-lookup"><span data-stu-id="487e7-126">Public</span></span>](../modifiers/public.md)
- [<span data-ttu-id="487e7-127">Пространства имен в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="487e7-127">Namespaces in Visual Basic</span></span>](../../programming-guide/program-structure/namespaces.md)
- [<span data-ttu-id="487e7-128">References to Declared Elements</span><span class="sxs-lookup"><span data-stu-id="487e7-128">References to Declared Elements</span></span>](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)
