---
title: Руководство по программированию на C#. Отображение аргументов командной строки
description: Узнайте, как отобразить аргументы командной строки. Изучите пример кода и ознакомьтесь с дополнительными ресурсами.
ms.date: 03/08/2021
helpviewer_keywords:
- command-line arguments [C#], displaying
ms.assetid: b8479f2d-9e05-4d38-82da-2e61246e5437
ms.openlocfilehash: 7c3e8d7f6ad2a599308057e996808509e70b7508
ms.sourcegitcommit: 0bb8074d524e0dcf165430b744bb143461f17026
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/15/2021
ms.locfileid: "103480272"
---
# <a name="how-to-display-command-line-arguments-c-programming-guide"></a><span data-ttu-id="ab963-104">Руководство по программированию на C#. Отображение аргументов командной строки</span><span class="sxs-lookup"><span data-stu-id="ab963-104">How to display command-line arguments (C# Programming Guide)</span></span>

<span data-ttu-id="ab963-105">Аргументы, предоставляемые исполняемому файлу в командной строке, доступны через [инструкции верхнего уровня](top-level-statements.md) или через необязательный параметр для метода `Main`.</span><span class="sxs-lookup"><span data-stu-id="ab963-105">Arguments provided to an executable on the command line are accessible in [top-level statements](top-level-statements.md) or through an optional parameter to `Main`.</span></span> <span data-ttu-id="ab963-106">Аргументы предоставляются в форме массива строк.</span><span class="sxs-lookup"><span data-stu-id="ab963-106">The arguments are provided in the form of an array of strings.</span></span> <span data-ttu-id="ab963-107">Каждый элемент массива содержит один аргумент.</span><span class="sxs-lookup"><span data-stu-id="ab963-107">Each element of the array contains one argument.</span></span> <span data-ttu-id="ab963-108">Пробелы между аргументами удаляются.</span><span class="sxs-lookup"><span data-stu-id="ab963-108">White-space between arguments is removed.</span></span> <span data-ttu-id="ab963-109">Например, рассмотрим следующие вызовы из командной строки вымышленного исполняемого файла:</span><span class="sxs-lookup"><span data-stu-id="ab963-109">For example, consider these command-line invocations of a fictitious executable:</span></span>  
  
|<span data-ttu-id="ab963-110">Входные данные в командной строке</span><span class="sxs-lookup"><span data-stu-id="ab963-110">Input on command line</span></span>|<span data-ttu-id="ab963-111">Массив строк, передаваемых в метод Main</span><span class="sxs-lookup"><span data-stu-id="ab963-111">Array of strings passed to Main</span></span>|  
|----------------------------|-------------------------------------|  
|<span data-ttu-id="ab963-112">**executable.exe a b c**</span><span class="sxs-lookup"><span data-stu-id="ab963-112">**executable.exe a b c**</span></span>|<span data-ttu-id="ab963-113">"a"</span><span class="sxs-lookup"><span data-stu-id="ab963-113">"a"</span></span><br /><br /> <span data-ttu-id="ab963-114">"b"</span><span class="sxs-lookup"><span data-stu-id="ab963-114">"b"</span></span><br /><br /> <span data-ttu-id="ab963-115">"c"</span><span class="sxs-lookup"><span data-stu-id="ab963-115">"c"</span></span>|  
|<span data-ttu-id="ab963-116">**executable.exe one two**</span><span class="sxs-lookup"><span data-stu-id="ab963-116">**executable.exe one two**</span></span>|<span data-ttu-id="ab963-117">"one"</span><span class="sxs-lookup"><span data-stu-id="ab963-117">"one"</span></span><br /><br /> <span data-ttu-id="ab963-118">"two"</span><span class="sxs-lookup"><span data-stu-id="ab963-118">"two"</span></span>|  
|<span data-ttu-id="ab963-119">**executable.exe "one two" three**</span><span class="sxs-lookup"><span data-stu-id="ab963-119">**executable.exe "one two" three**</span></span>|<span data-ttu-id="ab963-120">"один два"</span><span class="sxs-lookup"><span data-stu-id="ab963-120">"one two"</span></span><br /><br /> <span data-ttu-id="ab963-121">"три"</span><span class="sxs-lookup"><span data-stu-id="ab963-121">"three"</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="ab963-122">При выполнении приложения в Visual Studio аргументы командной строки можно указать на [странице "Отладка" в конструкторе проектов](/visualstudio/ide/reference/debug-page-project-designer).</span><span class="sxs-lookup"><span data-stu-id="ab963-122">When you are running an application in Visual Studio, you can specify command-line arguments in the [Debug Page, Project Designer](/visualstudio/ide/reference/debug-page-project-designer).</span></span>  
  
## <a name="example"></a><span data-ttu-id="ab963-123">Пример</span><span class="sxs-lookup"><span data-stu-id="ab963-123">Example</span></span>  

 <span data-ttu-id="ab963-124">Этот пример отображает аргументы командной строки, передаваемые в приложение командной строки.</span><span class="sxs-lookup"><span data-stu-id="ab963-124">This example displays the command-line arguments passed to a command-line application.</span></span> <span data-ttu-id="ab963-125">Показанные выходные данные — первая запись в таблице выше.</span><span class="sxs-lookup"><span data-stu-id="ab963-125">The output shown is for the first entry in the table above.</span></span>  
  
 [!code-csharp[csProgGuideMain#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideMain/CS/Class1.cs#9)]  
  
## <a name="see-also"></a><span data-ttu-id="ab963-126">См. также</span><span class="sxs-lookup"><span data-stu-id="ab963-126">See also</span></span>

- [<span data-ttu-id="ab963-127">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="ab963-127">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="ab963-128">Main() и аргументы командной строки</span><span class="sxs-lookup"><span data-stu-id="ab963-128">Main() and Command-Line Arguments</span></span>](./index.md)
- [<span data-ttu-id="ab963-129">Значения, возвращаемые методом main()</span><span class="sxs-lookup"><span data-stu-id="ab963-129">Main() Return Values</span></span>](./main-return-values.md)
