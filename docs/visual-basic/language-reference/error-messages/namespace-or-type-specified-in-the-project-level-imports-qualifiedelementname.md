---
description: 'Дополнительные сведения о: BC40057: namespace или Type, указанные в Imports на уровне проекта, <qualifiedelementname> не содержат открытых членов или не могут быть найдены'
title: Пространство имен или тип, указанные в свойстве Imports <qualifiedelementname> для проекта, не содержит никаких общих членов или не может быть найдено
ms.date: 07/20/2015
f1_keywords:
- vbc40057
- bc40057
helpviewer_keywords:
- BC40057
ms.assetid: 4ae3506e-2ebe-4ff3-995d-14ac60db5e9f
ms.openlocfilehash: 66ae40ca6a2feff78f80bdbc8886387e801f7db2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795694"
---
# <a name="bc40057-namespace-or-type-specified-in-the-project-level-imports-qualifiedelementname-doesnt-contain-any-public-member-or-cannot-be-found"></a><span data-ttu-id="eb76c-103">BC40057: пространство имен или тип, указанные в Imports на уровне проекта, \<qualifiedelementname> не содержат открытых членов или не могут быть найдены</span><span class="sxs-lookup"><span data-stu-id="eb76c-103">BC40057: Namespace or type specified in the project-level Imports '\<qualifiedelementname>' doesn't contain any public member or cannot be found</span></span>

<span data-ttu-id="eb76c-104">Пространство имен или тип, указанные в Imports на уровне проекта, \<qualifiedelementname> не содержат открытых членов или не могут быть найдены.</span><span class="sxs-lookup"><span data-stu-id="eb76c-104">Namespace or type specified in the project-level Imports '\<qualifiedelementname>' doesn't contain any public member or cannot be found.</span></span> <span data-ttu-id="eb76c-105">Убедитесь, что пространство имен или тип определены и содержат по крайней мере один открытый член.</span><span class="sxs-lookup"><span data-stu-id="eb76c-105">Make sure the namespace or the type is defined and contains at least one public member.</span></span> <span data-ttu-id="eb76c-106">Убедитесь, что имя псевдонима не содержит других псевдонимов.</span><span class="sxs-lookup"><span data-stu-id="eb76c-106">Make sure the alias name doesn't contain other aliases.</span></span>

 <span data-ttu-id="eb76c-107">Свойство импорта проекта указывает содержащий элемент, который не может быть найден или не определяет какие-либо `Public` элементы.</span><span class="sxs-lookup"><span data-stu-id="eb76c-107">An import property of a project specifies a containing element that either cannot be found or does not define any `Public` members.</span></span>

 <span data-ttu-id="eb76c-108">*Содержащий элемент* может быть пространством имен, классом, структурой, модулем, интерфейсом или перечислением.</span><span class="sxs-lookup"><span data-stu-id="eb76c-108">A *containing element* can be a namespace, class, structure, module, interface, or enumeration.</span></span> <span data-ttu-id="eb76c-109">Содержащий элемент содержит такие элементы, как переменные, процедуры или другие элементы, содержащие.</span><span class="sxs-lookup"><span data-stu-id="eb76c-109">The containing element contains members, such as variables, procedures, or other containing elements.</span></span>

 <span data-ttu-id="eb76c-110">Цель импорта заключается в том, чтобы предоставить коду доступ к пространству имен или членам типа без необходимости уточнять их.</span><span class="sxs-lookup"><span data-stu-id="eb76c-110">The purpose of importing is to allow your code to access namespace or type members without having to qualify them.</span></span> <span data-ttu-id="eb76c-111">В проекте также может потребоваться добавить ссылку на пространство имен или тип.</span><span class="sxs-lookup"><span data-stu-id="eb76c-111">Your project might also need to add a reference to the namespace or type.</span></span> <span data-ttu-id="eb76c-112">Дополнительные сведения см. в разделе "Импорт содержащихся элементов" в [ссылках на объявленные элементы](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="eb76c-112">For more information, see "Importing Containing Elements" in [References to Declared Elements](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>

 <span data-ttu-id="eb76c-113">Если компилятор не может найти указанный содержащий элемент, он не сможет разрешить ссылки, которые его используют.</span><span class="sxs-lookup"><span data-stu-id="eb76c-113">If the compiler cannot find the specified containing element, then it cannot resolve references that use it.</span></span> <span data-ttu-id="eb76c-114">Если он находит элемент, но элемент не предоставляет никаких `Public` членов, ссылка не может быть успешной.</span><span class="sxs-lookup"><span data-stu-id="eb76c-114">If it finds the element but the element does not expose any `Public` members, then no reference can be successful.</span></span> <span data-ttu-id="eb76c-115">В любом случае нет смысла импортировать элемент.</span><span class="sxs-lookup"><span data-stu-id="eb76c-115">In either case it is meaningless to import the element.</span></span>

 <span data-ttu-id="eb76c-116">Для указания элементов для импорта используется **Конструктор проектов** .</span><span class="sxs-lookup"><span data-stu-id="eb76c-116">You use the **Project Designer** to specify elements to import.</span></span> <span data-ttu-id="eb76c-117">Используйте раздел **Импортированные пространства имен** на странице **ссылки** .</span><span class="sxs-lookup"><span data-stu-id="eb76c-117">Use the **Imported namespaces** section of the **References** page.</span></span> <span data-ttu-id="eb76c-118">Чтобы открыть **Конструктор проектов** , дважды щелкните значок " **Мой проект** " в **Обозреватель решений**.</span><span class="sxs-lookup"><span data-stu-id="eb76c-118">You can get to the **Project Designer** by double-clicking the **My Project** icon in **Solution Explorer**.</span></span>

 <span data-ttu-id="eb76c-119">**Идентификатор ошибки:** BC40057</span><span class="sxs-lookup"><span data-stu-id="eb76c-119">**Error ID:** BC40057</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="eb76c-120">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="eb76c-120">To correct this error</span></span>

1. <span data-ttu-id="eb76c-121">Откройте **Конструктор проектов** и перейдите на страницу **ссылки** .</span><span class="sxs-lookup"><span data-stu-id="eb76c-121">Open the **Project Designer** and switch to the **Reference** page.</span></span>

2. <span data-ttu-id="eb76c-122">В разделе **Импортированные пространства имен** убедитесь, что содержащий элемент доступен из проекта.</span><span class="sxs-lookup"><span data-stu-id="eb76c-122">In the **Imported namespaces** section, verify that the containing element is accessible from your project.</span></span>

3. <span data-ttu-id="eb76c-123">Убедитесь, что содержащий элемент предоставляет по крайней мере один `Public` элемент.</span><span class="sxs-lookup"><span data-stu-id="eb76c-123">Verify that the containing element exposes at least one `Public` member.</span></span>

## <a name="see-also"></a><span data-ttu-id="eb76c-124">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="eb76c-124">See also</span></span>

- [<span data-ttu-id="eb76c-125">Страница "Ссылки" в конструкторе проектов (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="eb76c-125">References Page, Project Designer (Visual Basic)</span></span>](/visualstudio/ide/reference/references-page-project-designer-visual-basic)
- [<span data-ttu-id="eb76c-126">Управление свойствами проектов и решений</span><span class="sxs-lookup"><span data-stu-id="eb76c-126">Managing Project and Solution Properties</span></span>](/visualstudio/ide/managing-project-and-solution-properties)
- [<span data-ttu-id="eb76c-127">Общедоступная</span><span class="sxs-lookup"><span data-stu-id="eb76c-127">Public</span></span>](../modifiers/public.md)
- [<span data-ttu-id="eb76c-128">Пространства имен в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="eb76c-128">Namespaces in Visual Basic</span></span>](../../programming-guide/program-structure/namespaces.md)
- [<span data-ttu-id="eb76c-129">References to Declared Elements</span><span class="sxs-lookup"><span data-stu-id="eb76c-129">References to Declared Elements</span></span>](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)
