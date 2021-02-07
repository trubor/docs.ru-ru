---
description: 'Дополнительные сведения: список атрибутов (Visual Basic)'
title: Список атрибутов
ms.date: 07/20/2015
helpviewer_keywords:
- attribute list
- attributes [Visual Basic], applying
ms.assetid: 5880073a-68a4-4b6b-8a07-ace32959a4e2
ms.openlocfilehash: bde9387a48001a2696a6f69454edc311e7597bb6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99674042"
---
# <a name="attribute-list-visual-basic"></a><span data-ttu-id="4fa31-103">Список атрибутов (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4fa31-103">Attribute List (Visual Basic)</span></span>

<span data-ttu-id="4fa31-104">Задает атрибуты, применяемые к объявленному программному элементу.</span><span class="sxs-lookup"><span data-stu-id="4fa31-104">Specifies the attributes to be applied to a declared programming element.</span></span> <span data-ttu-id="4fa31-105">Несколько атрибутов разделяются запятыми.</span><span class="sxs-lookup"><span data-stu-id="4fa31-105">Multiple attributes are separated by commas.</span></span> <span data-ttu-id="4fa31-106">Ниже приведен синтаксис для одного атрибута.</span><span class="sxs-lookup"><span data-stu-id="4fa31-106">Following is the syntax for one attribute.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4fa31-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="4fa31-107">Syntax</span></span>  
  
```vb  
[ attributemodifier ] attributename [ ( attributearguments | attributeinitializer ) ]  
```  
  
## <a name="parts"></a><span data-ttu-id="4fa31-108">Компоненты</span><span class="sxs-lookup"><span data-stu-id="4fa31-108">Parts</span></span>  

|||
|---|---|
|`attributemodifier`|<span data-ttu-id="4fa31-109">Требуется для атрибутов, применяемых в начале исходного файла.</span><span class="sxs-lookup"><span data-stu-id="4fa31-109">Required for attributes applied at the beginning of a source file.</span></span> <span data-ttu-id="4fa31-110">Может быть [сборкой](../modifiers/assembly.md) или [модулем](../modifiers/module-keyword.md).</span><span class="sxs-lookup"><span data-stu-id="4fa31-110">Can be [Assembly](../modifiers/assembly.md) or [Module](../modifiers/module-keyword.md).</span></span>|
|`attributename`| <span data-ttu-id="4fa31-111">Обязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="4fa31-111">Required.</span></span> <span data-ttu-id="4fa31-112">Имя атрибута.</span><span class="sxs-lookup"><span data-stu-id="4fa31-112">Name of the attribute.</span></span>|
|`attributearguments`|<span data-ttu-id="4fa31-113">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="4fa31-113">Optional.</span></span> <span data-ttu-id="4fa31-114">Список позиций аргументов для этого атрибута.</span><span class="sxs-lookup"><span data-stu-id="4fa31-114">List of positional arguments for this attribute.</span></span> <span data-ttu-id="4fa31-115">Несколько аргументов разделяются запятыми.</span><span class="sxs-lookup"><span data-stu-id="4fa31-115">Multiple arguments are separated by commas.</span></span>|
|`attributeinitializer`|<span data-ttu-id="4fa31-116">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="4fa31-116">Optional.</span></span> <span data-ttu-id="4fa31-117">Список инициализаторов переменных или свойств для этого атрибута.</span><span class="sxs-lookup"><span data-stu-id="4fa31-117">List of variable or property initializers for this attribute.</span></span> <span data-ttu-id="4fa31-118">Несколько инициализаторов разделяются запятыми.</span><span class="sxs-lookup"><span data-stu-id="4fa31-118">Multiple initializers are separated by commas.</span></span>|
  
## <a name="remarks"></a><span data-ttu-id="4fa31-119">Remarks</span><span class="sxs-lookup"><span data-stu-id="4fa31-119">Remarks</span></span>  

 <span data-ttu-id="4fa31-120">Можно применить один или несколько атрибутов практически к любому элементу программирования (типам, процедурам, свойствам и т. д.).</span><span class="sxs-lookup"><span data-stu-id="4fa31-120">You can apply one or more attributes to nearly any programming element (types, procedures, properties, and so forth).</span></span> <span data-ttu-id="4fa31-121">Атрибуты отображаются в метаданных сборки, и они могут помочь добавить заметки в код или указать способ использования определенного программного элемента.</span><span class="sxs-lookup"><span data-stu-id="4fa31-121">Attributes appear in your assembly's metadata, and they can help you annotate your code or specify how to use a particular programming element.</span></span> <span data-ttu-id="4fa31-122">Можно применять атрибуты, определенные Visual Basic и платформа .NET Framework, а также определять собственные атрибуты.</span><span class="sxs-lookup"><span data-stu-id="4fa31-122">You can apply attributes defined by Visual Basic and the .NET Framework, and you can define your own attributes.</span></span>  

 <span data-ttu-id="4fa31-123">Дополнительные сведения об использовании атрибутов см. в разделе [Общие сведения об атрибутах](../../programming-guide/concepts/attributes/index.md).</span><span class="sxs-lookup"><span data-stu-id="4fa31-123">For more information on when to use attributes, see [Attributes overview](../../programming-guide/concepts/attributes/index.md).</span></span> <span data-ttu-id="4fa31-124">Дополнительные сведения об именах атрибутов см. в разделе [Имена объявленных элементов](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span><span class="sxs-lookup"><span data-stu-id="4fa31-124">For information on attribute names, see [Declared Element Names](../../programming-guide/language-features/declared-elements/declared-element-names.md).</span></span>  
  
## <a name="rules"></a><span data-ttu-id="4fa31-125">Правила</span><span class="sxs-lookup"><span data-stu-id="4fa31-125">Rules</span></span>  
  
- <span data-ttu-id="4fa31-126">**Размещаем.**</span><span class="sxs-lookup"><span data-stu-id="4fa31-126">**Placement.**</span></span> <span data-ttu-id="4fa31-127">К большинству объявленных программных элементов можно применять атрибуты.</span><span class="sxs-lookup"><span data-stu-id="4fa31-127">You can apply attributes to most declared programming elements.</span></span> <span data-ttu-id="4fa31-128">Чтобы применить один или несколько атрибутов, поместите *блок атрибутов* в начало объявления элемента.</span><span class="sxs-lookup"><span data-stu-id="4fa31-128">To apply one or more attributes, you place an *attribute block* at the beginning of the element declaration.</span></span> <span data-ttu-id="4fa31-129">Каждая запись в списке атрибутов указывает атрибут, который вы хотите применить, и модификатор и аргументы, используемые для этого вызова атрибута.</span><span class="sxs-lookup"><span data-stu-id="4fa31-129">Each entry in the attribute list specifies an attribute you wish to apply, and the modifier and arguments you are using for this invocation of the attribute.</span></span>  
  
- <span data-ttu-id="4fa31-130">**Угловые скобки.**</span><span class="sxs-lookup"><span data-stu-id="4fa31-130">**Angle Brackets.**</span></span> <span data-ttu-id="4fa31-131">При указании списка атрибутов необходимо заключить его в угловые скобки (" `<` " и " `>` ").</span><span class="sxs-lookup"><span data-stu-id="4fa31-131">If you supply an attribute list, you must enclose it in angle brackets ("`<`" and "`>`").</span></span>  
  
- <span data-ttu-id="4fa31-132">**Часть объявления.**</span><span class="sxs-lookup"><span data-stu-id="4fa31-132">**Part of the Declaration.**</span></span> <span data-ttu-id="4fa31-133">Атрибут должен быть частью объявления элемента, а не отдельной инструкции.</span><span class="sxs-lookup"><span data-stu-id="4fa31-133">The attribute must be part of the element declaration, not a separate statement.</span></span> <span data-ttu-id="4fa31-134">`_`Для расширения оператора объявления на несколько строк исходного кода можно использовать последовательность продолжения строки ("").</span><span class="sxs-lookup"><span data-stu-id="4fa31-134">You can use the line-continuation sequence (" `_`") to extend the declaration statement onto multiple source-code lines.</span></span>  
  
- <span data-ttu-id="4fa31-135">**Модификаторы.**</span><span class="sxs-lookup"><span data-stu-id="4fa31-135">**Modifiers.**</span></span> <span data-ttu-id="4fa31-136">Модификатор атрибута ( `Assembly` или `Module` ) необходим для каждого атрибута, применяемого к программному элементу в начале исходного файла.</span><span class="sxs-lookup"><span data-stu-id="4fa31-136">An attribute modifier (`Assembly` or `Module`) is required on every attribute applied to a programming element at the beginning of a source file.</span></span> <span data-ttu-id="4fa31-137">Использование модификаторов атрибутов не допускается для атрибутов, применяемых к элементам, которые не находятся в начале исходного файла.</span><span class="sxs-lookup"><span data-stu-id="4fa31-137">Attribute modifiers are not allowed on attributes applied to elements that are not at the beginning of a source file.</span></span>  
  
- <span data-ttu-id="4fa31-138">**Даваемых.**</span><span class="sxs-lookup"><span data-stu-id="4fa31-138">**Arguments.**</span></span> <span data-ttu-id="4fa31-139">Все позиционированные аргументы для атрибута должны предшествовать любым инициализаторам переменных или свойств.</span><span class="sxs-lookup"><span data-stu-id="4fa31-139">All positional arguments for an attribute must precede any variable or property initializers.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4fa31-140">Пример</span><span class="sxs-lookup"><span data-stu-id="4fa31-140">Example</span></span>  

 <span data-ttu-id="4fa31-141">В следующем примере атрибут применяется <xref:System.Runtime.InteropServices.DllImportAttribute> к скелетному определению `Function` процедуры.</span><span class="sxs-lookup"><span data-stu-id="4fa31-141">The following example applies the <xref:System.Runtime.InteropServices.DllImportAttribute> attribute to a skeleton definition of a `Function` procedure.</span></span>  
  
 [!code-vb[VbVbalrStatements#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#1)]  
  
 <span data-ttu-id="4fa31-142"><xref:System.Runtime.InteropServices.DllImportAttribute> Указывает, что процедура с атрибутом представляет точку входа в неуправляемой библиотеке динамической компоновки (DLL).</span><span class="sxs-lookup"><span data-stu-id="4fa31-142"><xref:System.Runtime.InteropServices.DllImportAttribute> indicates that the attributed procedure represents an entry point in an unmanaged dynamic-link library (DLL).</span></span> <span data-ttu-id="4fa31-143">Атрибут предоставляет имя библиотеки DLL в качестве аргумента, а другие сведения — как Инициализаторы переменных.</span><span class="sxs-lookup"><span data-stu-id="4fa31-143">The attribute supplies the DLL name as a positional argument and the other information as variable initializers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4fa31-144">См. также</span><span class="sxs-lookup"><span data-stu-id="4fa31-144">See also</span></span>

- [<span data-ttu-id="4fa31-145">Сборка</span><span class="sxs-lookup"><span data-stu-id="4fa31-145">Assembly</span></span>](../modifiers/assembly.md)
- [<span data-ttu-id="4fa31-146">Модуль \<keyword></span><span class="sxs-lookup"><span data-stu-id="4fa31-146">Module \<keyword></span></span>](../modifiers/module-keyword.md)
- [<span data-ttu-id="4fa31-147">Обзор атрибутов</span><span class="sxs-lookup"><span data-stu-id="4fa31-147">Attributes overview</span></span>](../../programming-guide/concepts/attributes/index.md)
- [<span data-ttu-id="4fa31-148">Практическое руководство. Разбиение и объединение инструкций в коде</span><span class="sxs-lookup"><span data-stu-id="4fa31-148">How to: Break and Combine Statements in Code</span></span>](../../programming-guide/program-structure/how-to-break-and-combine-statements-in-code.md)
