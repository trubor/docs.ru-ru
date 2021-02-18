---
description: 'Дополнительные сведения: -doc'
title: -doc
ms.date: 03/10/2018
helpviewer_keywords:
- doc compiler option [Visual Basic]
- -doc compiler option [Visual Basic]
- /doc compiler option [Visual Basic]
ms.assetid: 5fc32ec9-a149-4648-994c-a8d0cccd0a65
ms.openlocfilehash: da1ff6ad133dd2f46484b61ff73e1c6159eae557
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100461428"
---
# <a name="-doc"></a><span data-ttu-id="860dc-103">-doc</span><span class="sxs-lookup"><span data-stu-id="860dc-103">-doc</span></span>

<span data-ttu-id="860dc-104">Обрабатывает комментарии к документации в XML-файл.</span><span class="sxs-lookup"><span data-stu-id="860dc-104">Processes documentation comments to an XML file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="860dc-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="860dc-105">Syntax</span></span>  
  
```console  
-doc[+ | -]  
```

<span data-ttu-id="860dc-106">or</span><span class="sxs-lookup"><span data-stu-id="860dc-106">or</span></span>  

```console
-doc:file  
```  
  
## <a name="arguments"></a><span data-ttu-id="860dc-107">Аргументы</span><span class="sxs-lookup"><span data-stu-id="860dc-107">Arguments</span></span>  
  
|<span data-ttu-id="860dc-108">Термин</span><span class="sxs-lookup"><span data-stu-id="860dc-108">Term</span></span>|<span data-ttu-id="860dc-109">Определение</span><span class="sxs-lookup"><span data-stu-id="860dc-109">Definition</span></span>|  
|---|---|  
|<span data-ttu-id="860dc-110">`+` &#124; `-`</span><span class="sxs-lookup"><span data-stu-id="860dc-110">`+` &#124; `-`</span></span>|<span data-ttu-id="860dc-111">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="860dc-111">Optional.</span></span> <span data-ttu-id="860dc-112">Если задать + или `-doc`, компилятор создаст документацию и поместит ее в XML-файл.</span><span class="sxs-lookup"><span data-stu-id="860dc-112">Specifying +, or just `-doc`, causes the compiler to generate documentation information and place it in an XML file.</span></span> <span data-ttu-id="860dc-113">Если задать `-`, что эквивалентно отсутствию `-doc`, компилятор не будет создавать документацию.</span><span class="sxs-lookup"><span data-stu-id="860dc-113">Specifying `-` is the equivalent of not specifying `-doc`, causing no documentation information to be created.</span></span>|  
|`file`|<span data-ttu-id="860dc-114">Является обязательным, если используется параметр `-doc:`.</span><span class="sxs-lookup"><span data-stu-id="860dc-114">Required if `-doc:` is used.</span></span> <span data-ttu-id="860dc-115">Определяет выходной XML-файл, который заполняется комментариями из файлов исходного кода, участвующих в компиляции.</span><span class="sxs-lookup"><span data-stu-id="860dc-115">Specifies the output XML file, which is populated with the comments from the source-code files of the compilation.</span></span> <span data-ttu-id="860dc-116">Если имя файла содержит пробел, заключите его в кавычки (" ").</span><span class="sxs-lookup"><span data-stu-id="860dc-116">If the file name contains a space, surround the name with quotation marks (" ").</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="860dc-117">Примечания</span><span class="sxs-lookup"><span data-stu-id="860dc-117">Remarks</span></span>  

 <span data-ttu-id="860dc-118">Параметр `-doc` определяет, будет ли компилятор создавать XML-файл, содержащий комментарии.</span><span class="sxs-lookup"><span data-stu-id="860dc-118">The `-doc` option controls whether the compiler generates an XML file containing the documentation comments.</span></span> <span data-ttu-id="860dc-119">Если вы используете синтаксис `-doc:file`, параметр `file` определяет имя XML-файла.</span><span class="sxs-lookup"><span data-stu-id="860dc-119">If you use the `-doc:file` syntax, the `file` parameter specifies the name of the XML file.</span></span> <span data-ttu-id="860dc-120">Если вы используете `-doc` или `-doc+`, компилятор использует имя XML-файла из исполняемого файла или библиотеки, создаваемой компилятором.</span><span class="sxs-lookup"><span data-stu-id="860dc-120">If you use `-doc` or `-doc+`, the compiler takes the XML file name from the executable file or library that the compiler is creating.</span></span> <span data-ttu-id="860dc-121">Если вы используете `-doc-` или не задаете параметр `-doc`, компилятор не создает XML-файл.</span><span class="sxs-lookup"><span data-stu-id="860dc-121">If you use `-doc-` or do not specify the `-doc` option, the compiler does not create an XML file.</span></span>  
  
 <span data-ttu-id="860dc-122">В файлах исходного кода комментарии к документации могут предшествовать таким определениям:</span><span class="sxs-lookup"><span data-stu-id="860dc-122">In source-code files, documentation comments can precede the following definitions:</span></span>  
  
- <span data-ttu-id="860dc-123">определяемые пользователем типы, такие как [class](../../language-reference/statements/class-statement.md) или [interface](../../language-reference/statements/interface-statement.md);</span><span class="sxs-lookup"><span data-stu-id="860dc-123">User-defined types, such as a [class](../../language-reference/statements/class-statement.md) or [interface](../../language-reference/statements/interface-statement.md)</span></span>  
  
- <span data-ttu-id="860dc-124">члены, такие как field, [event](../../language-reference/statements/event-statement.md), [property](../../language-reference/statements/property-statement.md), [function](../../language-reference/statements/function-statement.md) или [subroutine](../../language-reference/statements/sub-statement.md).</span><span class="sxs-lookup"><span data-stu-id="860dc-124">Members, such as a field, [event](../../language-reference/statements/event-statement.md), [property](../../language-reference/statements/property-statement.md), [function](../../language-reference/statements/function-statement.md), or [subroutine](../../language-reference/statements/sub-statement.md).</span></span>  
  
 <span data-ttu-id="860dc-125">Чтобы использовать созданный XML-файл с помощью такой функции Visual Studio, как [IntelliSense](/visualstudio/ide/using-intellisense), имя XML-файла должно совпадать с именем сборки.</span><span class="sxs-lookup"><span data-stu-id="860dc-125">To use the generated XML file with the Visual Studio [IntelliSense](/visualstudio/ide/using-intellisense) feature, let the file name of the XML file be the same as the assembly you want to support.</span></span> <span data-ttu-id="860dc-126">Убедитесь, что XML-файл находится в том же каталоге, что и сборка, чтобы при обращении к сборке в проекте Visual Studio XML-файл мог бы также быть найден.</span><span class="sxs-lookup"><span data-stu-id="860dc-126">Make sure the XML file is in the same directory as the assembly so that when the assembly is referenced in the Visual Studio project, the .xml file is found as well.</span></span> <span data-ttu-id="860dc-127">XML-файлы документации не являются обязательными для работы IntelliSense с кодом в рамках одного или нескольких проектов, на которые ссылается проект.</span><span class="sxs-lookup"><span data-stu-id="860dc-127">XML documentation files are not required for IntelliSense to work for code within a project or within projects referenced by a project.</span></span>  
  
 <span data-ttu-id="860dc-128">XML-файл содержит теги `<assembly></assembly>`, если сборка не выполняется с помощью `-target:module`.</span><span class="sxs-lookup"><span data-stu-id="860dc-128">Unless you compile with `-target:module`, the XML file contains the tags `<assembly></assembly>`.</span></span> <span data-ttu-id="860dc-129">Эти теги указывают имя файла, содержащего манифест сборки для выходного файла компиляции.</span><span class="sxs-lookup"><span data-stu-id="860dc-129">These tags specify the name of the file containing the assembly manifest for the output file of the compilation.</span></span>  
  
 <span data-ttu-id="860dc-130">Способы создания документации из комментариев в коде описаны в разделе об [XML-тегах комментариев](../../language-reference/xmldoc/index.md).</span><span class="sxs-lookup"><span data-stu-id="860dc-130">See [XML Comment Tags](../../language-reference/xmldoc/index.md) for ways to generate documentation from comments in your code.</span></span>  
  
|<span data-ttu-id="860dc-131">Настройка параметра -doc в интегрированной среде разработки Visual Studio</span><span class="sxs-lookup"><span data-stu-id="860dc-131">To set -doc in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="860dc-132">1.  Выберите проект в **Обозревателе решений**.</span><span class="sxs-lookup"><span data-stu-id="860dc-132">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="860dc-133">В меню **Проект** выберите пункт **Свойства**.</span><span class="sxs-lookup"><span data-stu-id="860dc-133">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="860dc-134">2.  Откройте вкладку **Компиляция**.</span><span class="sxs-lookup"><span data-stu-id="860dc-134">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="860dc-135">3.  Задайте значение в поле **Создать XML-файл документации**.</span><span class="sxs-lookup"><span data-stu-id="860dc-135">3.  Set the value in the **Generate XML documentation file** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="860dc-136">Пример</span><span class="sxs-lookup"><span data-stu-id="860dc-136">Example</span></span>  

 <span data-ttu-id="860dc-137">Пример см. в статье [Документирование кода с помощью XML-комментариев](../../programming-guide/program-structure/documenting-your-code-with-xml.md).</span><span class="sxs-lookup"><span data-stu-id="860dc-137">See [Documenting Your Code with XML](../../programming-guide/program-structure/documenting-your-code-with-xml.md) for a sample.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="860dc-138">См. также</span><span class="sxs-lookup"><span data-stu-id="860dc-138">See also</span></span>

- [<span data-ttu-id="860dc-139">Компилятор Visual Basic с интерфейсом командной строки</span><span class="sxs-lookup"><span data-stu-id="860dc-139">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="860dc-140">Документирование кода с помощью XML</span><span class="sxs-lookup"><span data-stu-id="860dc-140">Documenting Your Code with XML</span></span>](../../programming-guide/program-structure/documenting-your-code-with-xml.md)
