---
description: 'Дополнительные сведения об инструкции: Imports (пространство имен .NET и тип)'
title: Оператор Imports — пространство имен и тип .NET
ms.date: 07/20/2015
f1_keywords:
- vb.Imports
- imports
helpviewer_keywords:
- declared element names [Visual Basic], qualification
- imports [Visual Basic]
- Imports statement [Visual Basic]
- aliases [Visual Basic], Imports statement
- container elements [Visual Basic]
- namespaces [Visual Basic], importing
- Imports statement [Visual Basic], syntax
- import aliases [Visual Basic]
- aliases [Visual Basic], import
- declared elements [Visual Basic], container elements
ms.assetid: 7062f8aa-d890-4232-9eed-92836e13fb6e
ms.openlocfilehash: 28b7608e250fdba9c39f0209154d5a3d8f725eea
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99768978"
---
# <a name="imports-statement-net-namespace-and-type"></a><span data-ttu-id="59fbb-103">Оператор Imports (пространство имен .NET и тип)</span><span class="sxs-lookup"><span data-stu-id="59fbb-103">Imports Statement (.NET Namespace and Type)</span></span>

<span data-ttu-id="59fbb-104">Позволяет ссылаться на имена типов без уточнения пространства имен.</span><span class="sxs-lookup"><span data-stu-id="59fbb-104">Enables type names to be referenced without namespace qualification.</span></span>

## <a name="syntax"></a><span data-ttu-id="59fbb-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="59fbb-105">Syntax</span></span>

```vb
Imports [ aliasname = ] namespace
' -or-
Imports [ aliasname = ] namespace.element
```

## <a name="parts"></a><span data-ttu-id="59fbb-106">Компоненты</span><span class="sxs-lookup"><span data-stu-id="59fbb-106">Parts</span></span>

|<span data-ttu-id="59fbb-107">Термин</span><span class="sxs-lookup"><span data-stu-id="59fbb-107">Term</span></span>|<span data-ttu-id="59fbb-108">Определение</span><span class="sxs-lookup"><span data-stu-id="59fbb-108">Definition</span></span>|
|---|---|
|`aliasname`|<span data-ttu-id="59fbb-109">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="59fbb-109">Optional.</span></span> <span data-ttu-id="59fbb-110">Псевдоним или имя *импорта* , по которому может ссылаться код `namespace` вместо полной уточняющей строки.</span><span class="sxs-lookup"><span data-stu-id="59fbb-110">An *import alias* or name by which code can refer to `namespace` instead of the full qualification string.</span></span> <span data-ttu-id="59fbb-111">См. раздел [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="59fbb-111">See [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>|
|`namespace`|<span data-ttu-id="59fbb-112">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="59fbb-112">Required.</span></span> <span data-ttu-id="59fbb-113">Полное имя импортируемого пространства имен.</span><span class="sxs-lookup"><span data-stu-id="59fbb-113">The fully qualified name of the namespace being imported.</span></span> <span data-ttu-id="59fbb-114">Может быть строкой пространств имен, вложенных в любой уровень.</span><span class="sxs-lookup"><span data-stu-id="59fbb-114">Can be a string of namespaces nested to any level.</span></span>|
|`element`|<span data-ttu-id="59fbb-115">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="59fbb-115">Optional.</span></span> <span data-ttu-id="59fbb-116">Имя программного элемента, объявленного в пространстве имен.</span><span class="sxs-lookup"><span data-stu-id="59fbb-116">The name of a programming element declared in the namespace.</span></span> <span data-ttu-id="59fbb-117">Может быть любым элементом контейнера.</span><span class="sxs-lookup"><span data-stu-id="59fbb-117">Can be any container element.</span></span>|

## <a name="remarks"></a><span data-ttu-id="59fbb-118">Remarks</span><span class="sxs-lookup"><span data-stu-id="59fbb-118">Remarks</span></span>

<span data-ttu-id="59fbb-119">`Imports`Оператор позволяет напрямую ссылаться на типы, содержащиеся в данном пространстве имен.</span><span class="sxs-lookup"><span data-stu-id="59fbb-119">The `Imports` statement enables types that are contained in a given namespace to be referenced directly.</span></span>

<span data-ttu-id="59fbb-120">Можно указать одно имя пространства имен или строку вложенных пространств имен.</span><span class="sxs-lookup"><span data-stu-id="59fbb-120">You can supply a single namespace name or a string of nested namespaces.</span></span> <span data-ttu-id="59fbb-121">Каждое вложенное пространство имен отделяется от следующего пространства имен более высокого уровня точкой ( `.` ), как показано в следующем примере:</span><span class="sxs-lookup"><span data-stu-id="59fbb-121">Each nested namespace is separated from the next higher level namespace by a period (`.`), as the following example illustrates:</span></span>

```vb
Imports System.Collections.Generic
```

<span data-ttu-id="59fbb-122">Каждый исходный файл может содержать любое количество `Imports` инструкций.</span><span class="sxs-lookup"><span data-stu-id="59fbb-122">Each source file can contain any number of `Imports` statements.</span></span> <span data-ttu-id="59fbb-123">Они должны следовать любым объявлениям параметров, таким как `Option Strict` оператор, и должны предшествовать любым объявлениям элементов программирования, таким как `Module` операторы или `Class` .</span><span class="sxs-lookup"><span data-stu-id="59fbb-123">These must follow any option declarations, such as the `Option Strict` statement, and they must precede any programming element declarations, such as `Module` or `Class` statements.</span></span>

<span data-ttu-id="59fbb-124">Можно использовать `Imports` только на уровне файлов.</span><span class="sxs-lookup"><span data-stu-id="59fbb-124">You can use `Imports` only at file level.</span></span> <span data-ttu-id="59fbb-125">Это означает, что контекст объявления для импорта должен быть исходным файлом и не может быть пространством имен, классом, структурой, модулем, интерфейсом, процедурой или блоком.</span><span class="sxs-lookup"><span data-stu-id="59fbb-125">This means the declaration context for importation must be a source file, and cannot be a namespace, class, structure, module, interface, procedure, or block.</span></span>

<span data-ttu-id="59fbb-126">Обратите внимание, что `Imports` инструкция не делает элементы из других проектов и сборок доступными для проекта.</span><span class="sxs-lookup"><span data-stu-id="59fbb-126">Note that the `Imports` statement does not make elements from other projects and assemblies available to your project.</span></span> <span data-ttu-id="59fbb-127">Импорт не является местом установки ссылки.</span><span class="sxs-lookup"><span data-stu-id="59fbb-127">Importing does not take the place of setting a reference.</span></span> <span data-ttu-id="59fbb-128">Он только устраняет необходимость уточнять имена, которые уже доступны для проекта.</span><span class="sxs-lookup"><span data-stu-id="59fbb-128">It only removes the need to qualify names that are already available to your project.</span></span> <span data-ttu-id="59fbb-129">Дополнительные сведения см. в разделе "Импорт содержащихся элементов" в [ссылках на объявленные элементы](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span><span class="sxs-lookup"><span data-stu-id="59fbb-129">For more information, see "Importing Containing Elements" in [References to Declared Elements](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>

> [!NOTE]
> <span data-ttu-id="59fbb-130">Неявные инструкции можно определить `Imports` с помощью [страницы ссылки в конструкторе проектов (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="59fbb-130">You can define implicit `Imports` statements by using the [References Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/references-page-project-designer-visual-basic).</span></span> <span data-ttu-id="59fbb-131">Дополнительные сведения см. [в разделе инструкции. Добавление или удаление импортированных пространств имен (Visual Basic)](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="59fbb-131">For more information, see [How to: Add or Remove Imported Namespaces (Visual Basic)](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic).</span></span>

## <a name="import-aliases"></a><span data-ttu-id="59fbb-132">Импорт псевдонимов</span><span class="sxs-lookup"><span data-stu-id="59fbb-132">Import Aliases</span></span>

<span data-ttu-id="59fbb-133">*Псевдоним импорта* определяет псевдоним для пространства имен или типа.</span><span class="sxs-lookup"><span data-stu-id="59fbb-133">An *import alias* defines the alias for a namespace or type.</span></span> <span data-ttu-id="59fbb-134">Псевдонимы импорта полезны, когда необходимо использовать элементы с одинаковыми именами, объявленными в одном или нескольких пространствах имен.</span><span class="sxs-lookup"><span data-stu-id="59fbb-134">Import aliases are useful when you need to use items with the same name that are declared in one or more namespaces.</span></span> <span data-ttu-id="59fbb-135">Дополнительные сведения и пример см. в разделе "уточнение имени элемента в [ссылках на объявленные элементы](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)".</span><span class="sxs-lookup"><span data-stu-id="59fbb-135">For more information and an example, see "Qualifying an Element Name" in [References to Declared Elements](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md).</span></span>

<span data-ttu-id="59fbb-136">Не следует объявлять элемент на уровне модуля с тем же именем, что и `aliasname` .</span><span class="sxs-lookup"><span data-stu-id="59fbb-136">You should not declare a member at module level with the same name as `aliasname`.</span></span> <span data-ttu-id="59fbb-137">В этом случае компилятор Visual Basic использует `aliasname` только для объявленного элемента и больше не распознает его как псевдоним импорта.</span><span class="sxs-lookup"><span data-stu-id="59fbb-137">If you do, the Visual Basic compiler uses `aliasname` only for the declared member and no longer recognizes it as an import alias.</span></span>

<span data-ttu-id="59fbb-138">Хотя синтаксис, используемый для объявления псевдонима импорта, похож на тот, который используется для импорта префикса пространства имен XML, результаты различаются.</span><span class="sxs-lookup"><span data-stu-id="59fbb-138">Although the syntax used for declaring an import alias is like that used for importing an XML namespace prefix, the results are different.</span></span> <span data-ttu-id="59fbb-139">Псевдоним импорта можно использовать как выражение в коде, тогда как префикс пространства имен XML можно использовать только в литералах XML или свойствах оси XML в качестве префикса для полного имени элемента или атрибута.</span><span class="sxs-lookup"><span data-stu-id="59fbb-139">An import alias can be used as an expression in your code, whereas an XML namespace prefix can be used only in XML literals or XML axis properties as the prefix for a qualified element or attribute name.</span></span>

### <a name="element-names"></a><span data-ttu-id="59fbb-140">Имена элементов</span><span class="sxs-lookup"><span data-stu-id="59fbb-140">Element Names</span></span>

<span data-ttu-id="59fbb-141">При указании `element` он должен представлять элемент- *контейнер*, то есть программный элемент, который может содержать другие элементы.</span><span class="sxs-lookup"><span data-stu-id="59fbb-141">If you supply `element`, it must represent a *container element*, that is, a programming element that can contain other elements.</span></span> <span data-ttu-id="59fbb-142">Контейнерные элементы включают классы, структуры, модули, интерфейсы и перечисления.</span><span class="sxs-lookup"><span data-stu-id="59fbb-142">Container elements include classes, structures, modules, interfaces, and enumerations.</span></span>

<span data-ttu-id="59fbb-143">Область действия элементов, доступных для `Imports` инструкции, зависит от того, указан ли параметр `element` .</span><span class="sxs-lookup"><span data-stu-id="59fbb-143">The scope of the elements made available by an `Imports` statement depends on whether you specify `element`.</span></span> <span data-ttu-id="59fbb-144">Если указать только `namespace` , то все члены этого пространства имен с уникальными именами и элементы контейнеров внутри этого пространства имен будут доступны без квалификации.</span><span class="sxs-lookup"><span data-stu-id="59fbb-144">If you specify only `namespace`, all uniquely named members of that namespace, and members of container elements within that namespace, are available without qualification.</span></span> <span data-ttu-id="59fbb-145">Если указать `namespace` и, и `element` , то только элементы этого элемента будут доступны без квалификации.</span><span class="sxs-lookup"><span data-stu-id="59fbb-145">If you specify both `namespace` and `element`, only the members of that element are available without qualification.</span></span>

## <a name="example"></a><span data-ttu-id="59fbb-146">Пример</span><span class="sxs-lookup"><span data-stu-id="59fbb-146">Example</span></span>

<span data-ttu-id="59fbb-147">В следующем примере возвращаются все папки в каталоге *C: \\* с помощью <xref:System.IO.DirectoryInfo> класса:</span><span class="sxs-lookup"><span data-stu-id="59fbb-147">The following example returns all the folders in the *C:\\* directory by using the <xref:System.IO.DirectoryInfo> class:</span></span>

<span data-ttu-id="59fbb-148">Код не содержит `Imports` операторов в верхней части файла.</span><span class="sxs-lookup"><span data-stu-id="59fbb-148">The code has no `Imports` statements at the top of the file.</span></span> <span data-ttu-id="59fbb-149">Таким образом, <xref:System.IO.DirectoryInfo> <xref:System.Text.StringBuilder> ссылки, и <xref:Microsoft.VisualBasic.ControlChars.CrLf> полностью определены с помощью пространств имен.</span><span class="sxs-lookup"><span data-stu-id="59fbb-149">Therefore, the <xref:System.IO.DirectoryInfo>, <xref:System.Text.StringBuilder>, and <xref:Microsoft.VisualBasic.ControlChars.CrLf> references are all fully qualified with the namespaces.</span></span>

[!code-vb[VbVbalrStatements#152](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#152)]

## <a name="example"></a><span data-ttu-id="59fbb-150">Пример</span><span class="sxs-lookup"><span data-stu-id="59fbb-150">Example</span></span>

<span data-ttu-id="59fbb-151">В следующем примере содержатся `Imports` инструкции для пространств имен, на которые имеются ссылки.</span><span class="sxs-lookup"><span data-stu-id="59fbb-151">The following example includes `Imports` statements for the referenced namespaces.</span></span> <span data-ttu-id="59fbb-152">Поэтому типы не обязательно должны быть полными с помощью пространств имен.</span><span class="sxs-lookup"><span data-stu-id="59fbb-152">Therefore, the types do not have to be fully qualified with the namespaces.</span></span>

[!code-vb[VbVbalrStatements#153](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#153)]

[!code-vb[VbVbalrStatements#154](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#154)]
  
## <a name="example"></a><span data-ttu-id="59fbb-153">Пример</span><span class="sxs-lookup"><span data-stu-id="59fbb-153">Example</span></span>

<span data-ttu-id="59fbb-154">В следующем примере содержатся `Imports` инструкции, создающие псевдонимы для упоминаемых пространств имен.</span><span class="sxs-lookup"><span data-stu-id="59fbb-154">The following example includes `Imports` statements that create aliases for the referenced namespaces.</span></span> <span data-ttu-id="59fbb-155">Типы дополнены псевдонимами.</span><span class="sxs-lookup"><span data-stu-id="59fbb-155">The types are qualified with the aliases.</span></span>

[!code-vb[VbVbalrStatements#155](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#155)]

[!code-vb[VbVbalrStatements#156](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#156)]

## <a name="example"></a><span data-ttu-id="59fbb-156">Пример</span><span class="sxs-lookup"><span data-stu-id="59fbb-156">Example</span></span>

<span data-ttu-id="59fbb-157">В следующем примере содержатся `Imports` инструкции, создающие псевдонимы для ссылочных типов.</span><span class="sxs-lookup"><span data-stu-id="59fbb-157">The following example includes `Imports` statements that create aliases for the referenced types.</span></span> <span data-ttu-id="59fbb-158">Для указания типов используются псевдонимы.</span><span class="sxs-lookup"><span data-stu-id="59fbb-158">Aliases are used to specify the types.</span></span>

[!code-vb[VbVbalrStatements#157](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#157)]

[!code-vb[VbVbalrStatements#158](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/class12.vb#158)]
  
## <a name="see-also"></a><span data-ttu-id="59fbb-159">См. также</span><span class="sxs-lookup"><span data-stu-id="59fbb-159">See also</span></span>

- [<span data-ttu-id="59fbb-160">Оператор Namespace</span><span class="sxs-lookup"><span data-stu-id="59fbb-160">Namespace Statement</span></span>](namespace-statement.md)
- [<span data-ttu-id="59fbb-161">Пространства имен в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="59fbb-161">Namespaces in Visual Basic</span></span>](../../programming-guide/program-structure/namespaces.md)
- [<span data-ttu-id="59fbb-162">Ссылки и оператор Imports</span><span class="sxs-lookup"><span data-stu-id="59fbb-162">References and the Imports Statement</span></span>](../../programming-guide/program-structure/references-and-the-imports-statement.md)
- [<span data-ttu-id="59fbb-163">Оператор Imports (пространство имен XML)</span><span class="sxs-lookup"><span data-stu-id="59fbb-163">Imports Statement (XML Namespace)</span></span>](imports-statement-xml-namespace.md)
- [<span data-ttu-id="59fbb-164">References to Declared Elements</span><span class="sxs-lookup"><span data-stu-id="59fbb-164">References to Declared Elements</span></span>](../../programming-guide/language-features/declared-elements/references-to-declared-elements.md)
