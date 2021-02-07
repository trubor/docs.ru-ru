---
description: Дополнительные сведения см. в описании оператора Option Compare
title: Оператор Option Compare
ms.date: 07/20/2015
f1_keywords:
- vb.Compare
- vb.OptionCompare
helpviewer_keywords:
- case sensitivity, Option Compare statement
- Compare keyword [Visual Basic]
- binary comparison [Visual Basic]
- strings [Visual Basic], returning from functions
- binary comparison [Visual Basic], Option Compare statement
- strings [Visual Basic], comparing
- string comparison [Visual Basic], Option Compare statement
- Text keyword [Visual Basic], Option Compare statement
- Binary keyword [Visual Basic], Option Compare statement
- string comparison [Visual Basic], sorting data
- Option Compare statement [Visual Basic]
- text [Visual Basic], comparing
ms.assetid: 54e8eeeb-3b0d-4fb9-acce-fbfbd5975f6e
ms.openlocfilehash: fba8b207c0077f95540485d79311b47f1b8c209c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99741670"
---
# <a name="option-compare-statement"></a><span data-ttu-id="a46d9-103">Оператор Option Compare</span><span class="sxs-lookup"><span data-stu-id="a46d9-103">Option Compare Statement</span></span>

<span data-ttu-id="a46d9-104">Объявляет метод сравнения по умолчанию для использования при сравнении строковых данных.</span><span class="sxs-lookup"><span data-stu-id="a46d9-104">Declares the default comparison method to use when comparing string data.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a46d9-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a46d9-105">Syntax</span></span>  
  
```vb  
Option Compare { Binary | Text }  
```  
  
## <a name="parts"></a><span data-ttu-id="a46d9-106">Компоненты</span><span class="sxs-lookup"><span data-stu-id="a46d9-106">Parts</span></span>  
  
|<span data-ttu-id="a46d9-107">Термин</span><span class="sxs-lookup"><span data-stu-id="a46d9-107">Term</span></span>|<span data-ttu-id="a46d9-108">Определение</span><span class="sxs-lookup"><span data-stu-id="a46d9-108">Definition</span></span>|  
|---|---|  
|`Binary`|<span data-ttu-id="a46d9-109">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="a46d9-109">Optional.</span></span> <span data-ttu-id="a46d9-110">Сравнения строк основываются на порядке сортировки, производном от внутренних двоичных представлений символов.</span><span class="sxs-lookup"><span data-stu-id="a46d9-110">Results in string comparisons based on a sort order derived from the internal binary representations of the characters.</span></span><br /><br /> <span data-ttu-id="a46d9-111">Такой тип сравнения наиболее часто применяется, если строки могут содержать символы, которые не следует интерпретировать как текст.</span><span class="sxs-lookup"><span data-stu-id="a46d9-111">This type of comparison is useful especially if the strings can contain characters that are not to be interpreted as text.</span></span> <span data-ttu-id="a46d9-112">В этом случае сравнение по алфавитной эквивалентности будет неверным (например, поскольку не будет учитываться регистр).</span><span class="sxs-lookup"><span data-stu-id="a46d9-112">In this case, you do not want to bias comparisons with alphabetical equivalences, such as case insensitivity.</span></span>|  
|`Text`|<span data-ttu-id="a46d9-113">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="a46d9-113">Optional.</span></span> <span data-ttu-id="a46d9-114">Результаты сравнения строк на основе сортировки текста без учета регистра определяются языком вашей системы.</span><span class="sxs-lookup"><span data-stu-id="a46d9-114">Results in string comparisons based on a case-insensitive text sort order determined by your system's locale.</span></span><br /><br /> <span data-ttu-id="a46d9-115">Такой тип сравнения полезен, если строки содержат только текстовые символы, и нужно сравнить их с учетом алфавитной эквивалентности, то есть без учета регистра и  с учетом схожих букв.</span><span class="sxs-lookup"><span data-stu-id="a46d9-115">This type of comparison is useful if your strings contain all text characters, and you want to compare them taking into account alphabetic equivalences such as case insensitivity and closely related letters.</span></span> <span data-ttu-id="a46d9-116">Например, можно считать `A` и `a` равными, а `Ä` и `ä` должны быть до `B` и `b`.</span><span class="sxs-lookup"><span data-stu-id="a46d9-116">For example, you might want to consider `A` and `a` to be equal, and `Ä` and `ä` to come before `B` and `b`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a46d9-117">Remarks</span><span class="sxs-lookup"><span data-stu-id="a46d9-117">Remarks</span></span>  

 <span data-ttu-id="a46d9-118">Если используется оператор `Option Compare`, он должен быть указан в файле до всех прочих операторов.</span><span class="sxs-lookup"><span data-stu-id="a46d9-118">If used, the `Option Compare` statement must appear in a file before any other source code statements.</span></span>  
  
 <span data-ttu-id="a46d9-119">Оператор `Option Compare` указывает метод сравнения строк (`Binary` или `Text`).</span><span class="sxs-lookup"><span data-stu-id="a46d9-119">The `Option Compare` statement specifies the string comparison method (`Binary` or `Text`).</span></span>  <span data-ttu-id="a46d9-120">Метод сравнения текста по умолчанию — `Binary`.</span><span class="sxs-lookup"><span data-stu-id="a46d9-120">The default text comparison method is `Binary`.</span></span>  
  
 <span data-ttu-id="a46d9-121">Сравнение `Binary` сравнивает числовое значение Юникода каждого символа в каждой строке.</span><span class="sxs-lookup"><span data-stu-id="a46d9-121">A `Binary` comparison compares the numeric Unicode value of each character in each string.</span></span> <span data-ttu-id="a46d9-122">Сравнение `Text` сравнивает каждый символ Юникода на основе его лексического значения в текущем языке.</span><span class="sxs-lookup"><span data-stu-id="a46d9-122">A `Text` comparison compares each Unicode character based on its lexical meaning in the current culture.</span></span>  
  
 <span data-ttu-id="a46d9-123">В Microsoft Windows порядок сортировки определяется кодовой страницей.</span><span class="sxs-lookup"><span data-stu-id="a46d9-123">In Microsoft Windows, sort order is determined by the code page.</span></span> <span data-ttu-id="a46d9-124">Дополнительные сведения см. в разделе [Кодовые страницы](/cpp/c-runtime-library/code-pages).</span><span class="sxs-lookup"><span data-stu-id="a46d9-124">For more information, see [Code Pages](/cpp/c-runtime-library/code-pages).</span></span>  
  
 <span data-ttu-id="a46d9-125">В следующем примере символы кодовой страницы ANSI 1252 сортируются с помощью оператора `Option Compare Binary`, создающего двоичный порядок сортировки.</span><span class="sxs-lookup"><span data-stu-id="a46d9-125">In the following example, characters in the English/European code page (ANSI 1252) are sorted by using `Option Compare Binary`, which produces a typical binary sort order.</span></span>  
  
 `A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`  
  
 <span data-ttu-id="a46d9-126">Когда эти же символы этой же кодовой страницы сортируются с помощью `Option Compare Text`, получается следующий порядок сортировки текста.</span><span class="sxs-lookup"><span data-stu-id="a46d9-126">When the same characters in the same code page are sorted by using `Option Compare Text`, the following text sort order is produced.</span></span>  
  
 `(A=a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`  
  
## <a name="when-an-option-compare-statement-is-not-present"></a><span data-ttu-id="a46d9-127">Если оператор Option Compare отсутствует</span><span class="sxs-lookup"><span data-stu-id="a46d9-127">When an Option Compare Statement Is Not Present</span></span>  

 <span data-ttu-id="a46d9-128">Если исходный код не содержит `Option Compare` инструкцию, то используется **параметр Option Compare** на [странице Компиляция, конструктор проектов (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) .</span><span class="sxs-lookup"><span data-stu-id="a46d9-128">If the source code does not contain an `Option Compare` statement, the **Option Compare** setting on the [Compile Page, Project Designer (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic) is used.</span></span> <span data-ttu-id="a46d9-129">При использовании компилятора командной строки используется параметр, заданный параметром компилятора [-оптионкомпаре](../../reference/command-line-compiler/optioncompare.md) .</span><span class="sxs-lookup"><span data-stu-id="a46d9-129">If you use the command-line compiler, the setting specified by the [-optioncompare](../../reference/command-line-compiler/optioncompare.md) compiler option is used.</span></span>  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
#### <a name="to-set-option-compare-in-the-ide"></a><span data-ttu-id="a46d9-130">Чтобы включить Option Compare в среде разработки</span><span class="sxs-lookup"><span data-stu-id="a46d9-130">To set Option Compare in the IDE</span></span>  
  
1. <span data-ttu-id="a46d9-131">Выберите проект в **обозревателе решений**.</span><span class="sxs-lookup"><span data-stu-id="a46d9-131">In **Solution Explorer**, select a project.</span></span> <span data-ttu-id="a46d9-132">В меню **Проект** выберите пункт **Свойства**.</span><span class="sxs-lookup"><span data-stu-id="a46d9-132">On the **Project** menu, click **Properties**.</span></span>  
  
2. <span data-ttu-id="a46d9-133">Откройте вкладку **Компиляция**.</span><span class="sxs-lookup"><span data-stu-id="a46d9-133">Click the **Compile** tab.</span></span>  
  
3. <span data-ttu-id="a46d9-134">Задайте значение в поле **параметр сравнения** .</span><span class="sxs-lookup"><span data-stu-id="a46d9-134">Set the value in the **Option Compare** box.</span></span>  
  
 <span data-ttu-id="a46d9-135">При создании проекта параметр **Option Compare** на вкладке **Компиляция** имеет значение параметр **Option Compare** в диалоговом окне **Параметры** .</span><span class="sxs-lookup"><span data-stu-id="a46d9-135">When you create a project, the **Option Compare** setting on the **Compile** tab is set to the **Option Compare** setting in the **Options** dialog box.</span></span> <span data-ttu-id="a46d9-136">Чтобы изменить этот параметр, в меню **Сервис** выберите пункт **Параметры**.</span><span class="sxs-lookup"><span data-stu-id="a46d9-136">To change this setting, on the **Tools** menu, click **Options**.</span></span> <span data-ttu-id="a46d9-137">В диалоговом окне **Параметры** разверните узел **Проекты и решения** и выберите пункт **Параметры Visual Basic по умолчанию**.</span><span class="sxs-lookup"><span data-stu-id="a46d9-137">In the **Options** dialog box, expand **Projects and Solutions**, and then click **VB Defaults**.</span></span> <span data-ttu-id="a46d9-138">Начальным значением по умолчанию в **VB по умолчанию** является **binary**.</span><span class="sxs-lookup"><span data-stu-id="a46d9-138">The initial default setting in **VB Defaults** is **Binary**.</span></span>  
  
#### <a name="to-set-option-compare-on-the-command-line"></a><span data-ttu-id="a46d9-139">Чтобы включить Option Compare в командной строке</span><span class="sxs-lookup"><span data-stu-id="a46d9-139">To set Option Compare on the command line</span></span>  
  
- <span data-ttu-id="a46d9-140">Включите параметр компилятора [-оптионкомпаре](../../reference/command-line-compiler/optioncompare.md) в команду **vbc** .</span><span class="sxs-lookup"><span data-stu-id="a46d9-140">Include the [-optioncompare](../../reference/command-line-compiler/optioncompare.md) compiler option in the **vbc** command.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a46d9-141">Пример</span><span class="sxs-lookup"><span data-stu-id="a46d9-141">Example</span></span>  

 <span data-ttu-id="a46d9-142">В следующем примере оператор `Option Compare` используется, чтобы задать двоичное сравнение в качестве метода сравнения строк по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="a46d9-142">The following example uses the `Option Compare` statement to set the binary comparison as the default string comparison method.</span></span> <span data-ttu-id="a46d9-143">Чтобы использовать этот код, раскомментируйте оператор `Option Compare Binary` и поместите его в начало файла исходного кода.</span><span class="sxs-lookup"><span data-stu-id="a46d9-143">To use this code, uncomment the `Option Compare Binary` statement, and put it at the top of the source file.</span></span>  
  
 [!code-vb[VbVbalrStatements#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#45)]  
  
## <a name="example"></a><span data-ttu-id="a46d9-144">Пример</span><span class="sxs-lookup"><span data-stu-id="a46d9-144">Example</span></span>  

 <span data-ttu-id="a46d9-145">В следующем примере оператор `Option Compare` используется, чтобы задать сортировку текста без учета регистра в качестве метода сравнения строк по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="a46d9-145">The following example uses the `Option Compare` statement to set the case-insensitive text sort order as the default string comparison method.</span></span> <span data-ttu-id="a46d9-146">Чтобы использовать этот код, раскомментируйте оператор `Option Compare Text` и поместите его в начало файла исходного кода.</span><span class="sxs-lookup"><span data-stu-id="a46d9-146">To use this code, uncomment the `Option Compare Text` statement, and put it at the top of the source file.</span></span>  
  
 [!code-vb[VbVbalrStatements#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class1.vb#46)]  
  
## <a name="see-also"></a><span data-ttu-id="a46d9-147">См. также</span><span class="sxs-lookup"><span data-stu-id="a46d9-147">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.InStr%2A>
- <xref:Microsoft.VisualBasic.Strings.InStrRev%2A>
- <xref:Microsoft.VisualBasic.Strings.Replace%2A>
- <xref:Microsoft.VisualBasic.Strings.Split%2A>
- <xref:Microsoft.VisualBasic.Strings.StrComp%2A>
- [<span data-ttu-id="a46d9-148">-optioncompare</span><span class="sxs-lookup"><span data-stu-id="a46d9-148">-optioncompare</span></span>](../../reference/command-line-compiler/optioncompare.md)
- [<span data-ttu-id="a46d9-149">Операторы сравнения</span><span class="sxs-lookup"><span data-stu-id="a46d9-149">Comparison Operators</span></span>](../operators/comparison-operators.md)
- [<span data-ttu-id="a46d9-150">Comparison Operators in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a46d9-150">Comparison Operators in Visual Basic</span></span>](../../programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [<span data-ttu-id="a46d9-151">Оператор Like</span><span class="sxs-lookup"><span data-stu-id="a46d9-151">Like Operator</span></span>](../operators/like-operator.md)
- [<span data-ttu-id="a46d9-152">Строковые функции</span><span class="sxs-lookup"><span data-stu-id="a46d9-152">String Functions</span></span>](../functions/string-functions.md)
- [<span data-ttu-id="a46d9-153">Оператор Option Explicit</span><span class="sxs-lookup"><span data-stu-id="a46d9-153">Option Explicit Statement</span></span>](option-explicit-statement.md)
- [<span data-ttu-id="a46d9-154">Оператор Option Strict</span><span class="sxs-lookup"><span data-stu-id="a46d9-154">Option Strict Statement</span></span>](option-strict-statement.md)
