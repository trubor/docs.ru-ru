---
description: 'Дополнительные сведения: -define (Visual Basic)'
title: -define
ms.date: 03/10/2018
helpviewer_keywords:
- -d compiler option [Visual Basic]
- /d compiler option [Visual Basic]
- -define compiler option [Visual Basic]
- d compiler option [Visual Basic]
- /define compiler option [Visual Basic]
- define compiler option [Visual Basic]
ms.assetid: f735c57d-1cf9-4f2f-a26f-0de630fd4077
ms.openlocfilehash: 9d6394ecad8e59d64ef3c51312ac85562ba3ec2c
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100466982"
---
# <a name="-define-visual-basic"></a><span data-ttu-id="83292-103">-define (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="83292-103">-define (Visual Basic)</span></span>

<span data-ttu-id="83292-104">Задает константы условной компиляции.</span><span class="sxs-lookup"><span data-stu-id="83292-104">Defines conditional compiler constants.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83292-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="83292-105">Syntax</span></span>  
  
```console  
-define:["]symbol[=value][,symbol[=value]]["]  
```

<span data-ttu-id="83292-106">or</span><span class="sxs-lookup"><span data-stu-id="83292-106">or</span></span>

```console  
-d:["]symbol[=value][,symbol[=value]]["]  
```  
  
## <a name="arguments"></a><span data-ttu-id="83292-107">Аргументы</span><span class="sxs-lookup"><span data-stu-id="83292-107">Arguments</span></span>  
  
|<span data-ttu-id="83292-108">Термин</span><span class="sxs-lookup"><span data-stu-id="83292-108">Term</span></span>|<span data-ttu-id="83292-109">Определение</span><span class="sxs-lookup"><span data-stu-id="83292-109">Definition</span></span>|  
|---|---|  
|`symbol`|<span data-ttu-id="83292-110">Обязательный.</span><span class="sxs-lookup"><span data-stu-id="83292-110">Required.</span></span> <span data-ttu-id="83292-111">Определяемый символ.</span><span class="sxs-lookup"><span data-stu-id="83292-111">The symbol to define.</span></span>|  
|`value`|<span data-ttu-id="83292-112">Необязательный элемент.</span><span class="sxs-lookup"><span data-stu-id="83292-112">Optional.</span></span> <span data-ttu-id="83292-113">Значение, которому назначается `symbol`.</span><span class="sxs-lookup"><span data-stu-id="83292-113">The value to assign `symbol`.</span></span> <span data-ttu-id="83292-114">Если `value` является строкой, его необходимо заключить в последовательности из обратной косой черты и кавычки (\\"), а не просто в кавычки.</span><span class="sxs-lookup"><span data-stu-id="83292-114">If `value` is a string, it must be surrounded by backslash/quotation-mark sequences (\\") instead of quotation marks.</span></span> <span data-ttu-id="83292-115">Если значение не задано, считается, что используется значение True.</span><span class="sxs-lookup"><span data-stu-id="83292-115">If no value is specified, then it is taken to be True.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="83292-116">Примечания</span><span class="sxs-lookup"><span data-stu-id="83292-116">Remarks</span></span>  

 <span data-ttu-id="83292-117">Влияние параметра `-define` похоже на использование директивы препроцессора `#Const` в исходном файле, за исключением того, что определенные с помощью `-define` константы являются общими и применяются ко всем файлам в проекте.</span><span class="sxs-lookup"><span data-stu-id="83292-117">The `-define` option has an effect similar to using a `#Const` preprocessor directive in your source file, except that constants defined with `-define` are public and apply to all files in the project.</span></span>  
  
 <span data-ttu-id="83292-118">Вы можете использовать символы, созданные этим параметром с помощью директивы `#If`...`Then`...`#Else`, для условной компиляции исходных файлов.</span><span class="sxs-lookup"><span data-stu-id="83292-118">You can use symbols created by this option with the `#If`...`Then`...`#Else` directive to compile source files conditionally.</span></span>  
  
 <span data-ttu-id="83292-119">`-d` является краткой формой `-define`.</span><span class="sxs-lookup"><span data-stu-id="83292-119">`-d` is the short form of `-define`.</span></span>  
  
 <span data-ttu-id="83292-120">Вы можете определить несколько символов с помощью `-define`, разделяя их определения запятой.</span><span class="sxs-lookup"><span data-stu-id="83292-120">You can define multiple symbols with `-define` by using a comma to separate symbol definitions.</span></span>  
  
|<span data-ttu-id="83292-121">Задание параметра -define в интегрированной среде разработки Visual Studio</span><span class="sxs-lookup"><span data-stu-id="83292-121">To set -define in the Visual Studio integrated development environment</span></span>|  
|---|  
|<span data-ttu-id="83292-122">1.  Выберите проект в **Обозревателе решений**.</span><span class="sxs-lookup"><span data-stu-id="83292-122">1.  Have a project selected in **Solution Explorer**.</span></span> <span data-ttu-id="83292-123">В меню **Проект** выберите пункт **Свойства**.</span><span class="sxs-lookup"><span data-stu-id="83292-123">On the **Project** menu, click **Properties**.</span></span> <br /><span data-ttu-id="83292-124">2.  Откройте вкладку **Компиляция**.</span><span class="sxs-lookup"><span data-stu-id="83292-124">2.  Click the **Compile** tab.</span></span><br /><span data-ttu-id="83292-125">3.  Нажмите кнопку **Дополнительно**.</span><span class="sxs-lookup"><span data-stu-id="83292-125">3.  Click **Advanced**.</span></span><br /><span data-ttu-id="83292-126">4.  Измените значение в поле **Настраиваемые константы**.</span><span class="sxs-lookup"><span data-stu-id="83292-126">4.  Modify the value in the **Custom Constants** box.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="83292-127">Пример</span><span class="sxs-lookup"><span data-stu-id="83292-127">Example</span></span>  

 <span data-ttu-id="83292-128">В следующем примере кода определяются и используются две константы условной компиляции.</span><span class="sxs-lookup"><span data-stu-id="83292-128">The following code defines and then uses two conditional compiler constants.</span></span>  
  
 [!code-vb[VbVbalrCompiler#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/Class1.vb#45)]  
  
## <a name="see-also"></a><span data-ttu-id="83292-129">См. также</span><span class="sxs-lookup"><span data-stu-id="83292-129">See also</span></span>

- [<span data-ttu-id="83292-130">Компилятор Visual Basic с интерфейсом командной строки</span><span class="sxs-lookup"><span data-stu-id="83292-130">Visual Basic Command-Line Compiler</span></span>](index.md)
- [<span data-ttu-id="83292-131">Директивы #If...Then...#Else</span><span class="sxs-lookup"><span data-stu-id="83292-131">#If...Then...#Else Directives</span></span>](../../language-reference/directives/if-then-else-directives.md)
- [<span data-ttu-id="83292-132">Директива #Const</span><span class="sxs-lookup"><span data-stu-id="83292-132">#Const Directive</span></span>](../../language-reference/directives/const-directive.md)
- [<span data-ttu-id="83292-133">Примеры командных строк компиляции</span><span class="sxs-lookup"><span data-stu-id="83292-133">Sample Compilation Command Lines</span></span>](sample-compilation-command-lines.md)
