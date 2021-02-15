---
description: Дополнительные сведения см. в статье обработка XML-файла (Visual Basic)
title: Обработка XML-файла
ms.date: 07/20/2015
helpviewer_keywords:
- XML comments [Visual Basic], parsing [Visual Basic]
ms.assetid: 78a15cd0-7708-4e79-85d1-c154b7a14a8c
ms.openlocfilehash: 2314e7dafbd747f9a19b73d06d71c73631e53861
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100468399"
---
# <a name="processing-the-xml-file-visual-basic"></a><span data-ttu-id="18616-103">Обработка XML-файла (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="18616-103">Processing the XML File (Visual Basic)</span></span>

<span data-ttu-id="18616-104">Компилятор создает строку идентификатора для каждой конструкции в коде, помеченной для создания документации.</span><span class="sxs-lookup"><span data-stu-id="18616-104">The compiler generates an ID string for each construct in your code that is tagged to generate documentation.</span></span> <span data-ttu-id="18616-105">(Дополнительные сведения о том, как пометить код, см. в разделе [теги XML-комментариев](../../language-reference/xmldoc/index.md).) Строка идентификатора уникально идентифицирует конструкцию.</span><span class="sxs-lookup"><span data-stu-id="18616-105">(For information on how to tag your code, see [XML Comment Tags](../../language-reference/xmldoc/index.md).) The ID string uniquely identifies the construct.</span></span> <span data-ttu-id="18616-106">Программы, обрабатывающие XML-файл, могут использовать строку идентификатора для идентификации соответствующего элемента платформа .NET Framework метаданных или отражения.</span><span class="sxs-lookup"><span data-stu-id="18616-106">Programs that process the XML file can use the ID string to identify the corresponding .NET Framework metadata/reflection item.</span></span>  
  
 <span data-ttu-id="18616-107">XML-файл не является иерархическим представлением кода; Это плоский список с созданным ИДЕНТИФИКАТОРом для каждого элемента.</span><span class="sxs-lookup"><span data-stu-id="18616-107">The XML file is not a hierarchical representation of your code; it is a flat list with a generated ID for each element.</span></span>  
  
 <span data-ttu-id="18616-108">Компилятор соблюдает следующие правила при формировании строк идентификаторов.</span><span class="sxs-lookup"><span data-stu-id="18616-108">The compiler observes the following rules when it generates the ID strings:</span></span>  
  
- <span data-ttu-id="18616-109">Пробелы в строку не вставляются.</span><span class="sxs-lookup"><span data-stu-id="18616-109">No white space is placed in the string.</span></span>  
  
- <span data-ttu-id="18616-110">Первая часть строки идентификатора определяет тип идентифицируемого члена. Это один символ, за которым следует двоеточие.</span><span class="sxs-lookup"><span data-stu-id="18616-110">The first part of the ID string identifies the kind of member being identified, with a single character followed by a colon.</span></span> <span data-ttu-id="18616-111">Используются следующие типы элементов.</span><span class="sxs-lookup"><span data-stu-id="18616-111">The following member types are used.</span></span>  
  
|<span data-ttu-id="18616-112">Символ</span><span class="sxs-lookup"><span data-stu-id="18616-112">Character</span></span>|<span data-ttu-id="18616-113">Описание</span><span class="sxs-lookup"><span data-stu-id="18616-113">Description</span></span>|  
|---|---|  
|<span data-ttu-id="18616-114">Нет</span><span class="sxs-lookup"><span data-stu-id="18616-114">N</span></span>|<span data-ttu-id="18616-115">namespace</span><span class="sxs-lookup"><span data-stu-id="18616-115">namespace</span></span><br /><br /> <span data-ttu-id="18616-116">Нельзя добавлять комментарии к документации в пространство имен, но можно сделать CREF-ссылки на них, где это поддерживается.</span><span class="sxs-lookup"><span data-stu-id="18616-116">You cannot add documentation comments to a namespace, but you can make CREF references to them, where supported.</span></span>|  
|<span data-ttu-id="18616-117">T</span><span class="sxs-lookup"><span data-stu-id="18616-117">T</span></span>|<span data-ttu-id="18616-118">Тип: `Class` , `Module` , `Interface` , `Structure` , `Enum` , `Delegate`</span><span class="sxs-lookup"><span data-stu-id="18616-118">type: `Class`, `Module`, `Interface`, `Structure`, `Enum`, `Delegate`</span></span>|  
|<span data-ttu-id="18616-119">F</span><span class="sxs-lookup"><span data-stu-id="18616-119">F</span></span>|<span data-ttu-id="18616-120">полями `Dim`</span><span class="sxs-lookup"><span data-stu-id="18616-120">field: `Dim`</span></span>|  
|<span data-ttu-id="18616-121">P</span><span class="sxs-lookup"><span data-stu-id="18616-121">P</span></span>|<span data-ttu-id="18616-122">свойство: `Property` (включая свойства по умолчанию)</span><span class="sxs-lookup"><span data-stu-id="18616-122">property: `Property` (including default properties)</span></span>|  
|<span data-ttu-id="18616-123">M</span><span class="sxs-lookup"><span data-stu-id="18616-123">M</span></span>|<span data-ttu-id="18616-124">метод: `Sub` , `Function` , `Declare` , `Operator`</span><span class="sxs-lookup"><span data-stu-id="18616-124">method: `Sub`, `Function`, `Declare`, `Operator`</span></span>|  
|<span data-ttu-id="18616-125">E</span><span class="sxs-lookup"><span data-stu-id="18616-125">E</span></span>|<span data-ttu-id="18616-126">журнале `Event`</span><span class="sxs-lookup"><span data-stu-id="18616-126">event: `Event`</span></span>|  
|<span data-ttu-id="18616-127">!</span><span class="sxs-lookup"><span data-stu-id="18616-127">!</span></span>|<span data-ttu-id="18616-128">текст ошибки</span><span class="sxs-lookup"><span data-stu-id="18616-128">error string</span></span><br /><br /> <span data-ttu-id="18616-129">Остальная часть строки предоставляет сведения об ошибке.</span><span class="sxs-lookup"><span data-stu-id="18616-129">The rest of the string provides information about the error.</span></span> <span data-ttu-id="18616-130">Компилятор Visual Basic создает сведения об ошибках для ссылок, которые не удается разрешить.</span><span class="sxs-lookup"><span data-stu-id="18616-130">The Visual Basic compiler generates error information for links that cannot be resolved.</span></span>|  
  
- <span data-ttu-id="18616-131">Вторая часть `String` представляет собой полное имя элемента, начиная с корня пространства имен.</span><span class="sxs-lookup"><span data-stu-id="18616-131">The second part of the `String` is the fully qualified name of the item, starting at the root of the namespace.</span></span> <span data-ttu-id="18616-132">Имя элемента, включающий его тип (s) и пространство имен разделяются точками.</span><span class="sxs-lookup"><span data-stu-id="18616-132">The name of the item, its enclosing type(s), and the namespace are separated by periods.</span></span> <span data-ttu-id="18616-133">Если имя элемента содержит точки, они заменяются знаком номера (#).</span><span class="sxs-lookup"><span data-stu-id="18616-133">If the name of the item itself contains periods, they are replaced by the number sign (#).</span></span> <span data-ttu-id="18616-134">Предполагается, что ни один элемент не имеет знака номера непосредственно в имени.</span><span class="sxs-lookup"><span data-stu-id="18616-134">It is assumed that no item has a number sign directly in its name.</span></span> <span data-ttu-id="18616-135">Например, полное имя `String` конструктора — `System.String.#ctor` .</span><span class="sxs-lookup"><span data-stu-id="18616-135">For example, the fully qualified name of the `String` constructor would be `System.String.#ctor`.</span></span>  
  
- <span data-ttu-id="18616-136">Для свойств и методов, имеющих аргументы, список этих аргументов заключается в круглые скобки и указывается в конце.</span><span class="sxs-lookup"><span data-stu-id="18616-136">For properties and methods, if there are arguments to the method, the argument list enclosed in parentheses follows.</span></span> <span data-ttu-id="18616-137">Если аргументы не используются, скобки отсутствуют.</span><span class="sxs-lookup"><span data-stu-id="18616-137">If there are no arguments, no parentheses are present.</span></span> <span data-ttu-id="18616-138">Аргументы разделяются запятыми.</span><span class="sxs-lookup"><span data-stu-id="18616-138">The arguments are separated by commas.</span></span> <span data-ttu-id="18616-139">Кодировка каждого аргумента соответствует непосредственно их кодированию в сигнатуре платформа .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="18616-139">The encoding of each argument follows directly how it is encoded in a .NET Framework signature.</span></span>  
  
## <a name="example"></a><span data-ttu-id="18616-140">Пример</span><span class="sxs-lookup"><span data-stu-id="18616-140">Example</span></span>  

 <span data-ttu-id="18616-141">В следующем коде показано, как создаются строки идентификатора для класса и его членов.</span><span class="sxs-lookup"><span data-stu-id="18616-141">The following code shows how the ID strings for a class and its members are generated.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#10)]  
  
## <a name="see-also"></a><span data-ttu-id="18616-142">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="18616-142">See also</span></span>

- [<span data-ttu-id="18616-143">-doc</span><span class="sxs-lookup"><span data-stu-id="18616-143">-doc</span></span>](../../reference/command-line-compiler/doc.md)
- [<span data-ttu-id="18616-144">Практическое руководство. Создание XML-документации</span><span class="sxs-lookup"><span data-stu-id="18616-144">How to: Create XML Documentation</span></span>](how-to-create-xml-documentation.md)
