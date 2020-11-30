---
description: Справочник по C#. Модификатор extern
title: Справочник по C#. Модификатор extern
ms.date: 07/20/2015
f1_keywords:
- extern_CSharpKeyword
- extern
helpviewer_keywords:
- DllImport attribute
- extern keyword [C#]
ms.assetid: 9c3f02c4-51b8-4d80-9cb2-f2b6e1ae15c7
ms.openlocfilehash: 25eb5e6642d8b608bedcb4e9adadde4d84c2bae9
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "89138973"
---
# <a name="extern-c-reference"></a><span data-ttu-id="6beb4-103">extern (справочник по C#)</span><span class="sxs-lookup"><span data-stu-id="6beb4-103">extern (C# Reference)</span></span>

<span data-ttu-id="6beb4-104">Модификатор `extern` используется для объявления метода с внешней реализацией.</span><span class="sxs-lookup"><span data-stu-id="6beb4-104">The `extern` modifier is used to declare a method that is implemented externally.</span></span> <span data-ttu-id="6beb4-105">При применении служб взаимодействия для вызова неуправляемого кода модификатор `extern` обычно используется с атрибутом `DllImport`.</span><span class="sxs-lookup"><span data-stu-id="6beb4-105">A common use of the `extern` modifier is with the `DllImport` attribute when you are using Interop services to call into unmanaged code.</span></span> <span data-ttu-id="6beb4-106">В этом случае также необходимо объявить метод как `static` в соответствии со следующим примером:</span><span class="sxs-lookup"><span data-stu-id="6beb4-106">In this case, the method must also be declared as `static`, as shown in the following example:</span></span>

```csharp
[DllImport("avifil32.dll")]
private static extern void AVIFileInit();
```

<span data-ttu-id="6beb4-107">Ключевое слово `extern` может также определять внешний псевдоним сборки, который позволяет ссылаться на разные версии одного компонента из одной сборки.</span><span class="sxs-lookup"><span data-stu-id="6beb4-107">The `extern` keyword can also define an external assembly alias, which makes it possible to reference different versions of the same component from within a single assembly.</span></span> <span data-ttu-id="6beb4-108">Дополнительные сведения см. в разделе [Псевдоним extern](extern-alias.md).</span><span class="sxs-lookup"><span data-stu-id="6beb4-108">For more information, see [extern alias](extern-alias.md).</span></span>

<span data-ttu-id="6beb4-109">Совместное использование модификаторов [abstract](abstract.md) и `extern` для изменения одного члена недопустимо.</span><span class="sxs-lookup"><span data-stu-id="6beb4-109">It is an error to use the [abstract](abstract.md) and `extern` modifiers together to modify the same member.</span></span> <span data-ttu-id="6beb4-110">Использование модификатора `extern` означает, что метод реализуется вне кода C#, а применение модификатора `abstract` указывает на то, что в данном классе реализация метода не обеспечивается.</span><span class="sxs-lookup"><span data-stu-id="6beb4-110">Using the `extern` modifier means that the method is implemented outside the C# code, whereas using the `abstract` modifier means that the method implementation is not provided in the class.</span></span>

<span data-ttu-id="6beb4-111">В C# ключевое слово extern имеет более ограниченное применение, чем в C++.</span><span class="sxs-lookup"><span data-stu-id="6beb4-111">The extern keyword has more limited uses in C# than in C++.</span></span> <span data-ttu-id="6beb4-112">Сравнительные характеристики использования этого ключевого слова в C# и в C++ см. в разделе "Использование extern для указания компоновки" Справочника по языку C++.</span><span class="sxs-lookup"><span data-stu-id="6beb4-112">To compare the C# keyword with the C++ keyword, see Using extern to Specify Linkage in the C++ Language Reference.</span></span>

## <a name="example-1"></a><span data-ttu-id="6beb4-113">Пример 1</span><span class="sxs-lookup"><span data-stu-id="6beb4-113">Example 1</span></span>

<span data-ttu-id="6beb4-114">В этом примере программа получает от пользователя строку и отображает ее в окне сообщения.</span><span class="sxs-lookup"><span data-stu-id="6beb4-114">In this example, the program receives a string from the user and displays it inside a message box.</span></span> <span data-ttu-id="6beb4-115">В этой программе используется метод `MessageBox`, импортированный из библиотеки User32.dll.</span><span class="sxs-lookup"><span data-stu-id="6beb4-115">The program uses the `MessageBox` method imported from the User32.dll library.</span></span>

[!code-csharp[csrefKeywordsModifiers#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#8)]

## <a name="example-2"></a><span data-ttu-id="6beb4-116">Пример 2</span><span class="sxs-lookup"><span data-stu-id="6beb4-116">Example 2</span></span>

<span data-ttu-id="6beb4-117">В этом примере показана программа C#, в которой вызывается библиотека C (собственная библиотека DLL).</span><span class="sxs-lookup"><span data-stu-id="6beb4-117">This example illustrates a C# program that calls into a C library (a native DLL).</span></span>

1. <span data-ttu-id="6beb4-118">Создайте следующий файл C и назовите его `cmdll.c`.</span><span class="sxs-lookup"><span data-stu-id="6beb4-118">Create the following C file and name it `cmdll.c`:</span></span>

    ```c
    // cmdll.c
    // Compile with: -LD
    int __declspec(dllexport) SampleMethod(int i)
    {
      return i*10;
    }
    ```

2. <span data-ttu-id="6beb4-119">Откройте из каталога установки Visual Studio окно командной строки Visual Studio x64 (или x32) Native Tools и скомпилируйте файл `cmdll.c`, введя в командной строке **cl -LD cmdll.c**.</span><span class="sxs-lookup"><span data-stu-id="6beb4-119">Open a Visual Studio x64 (or x32) Native Tools Command Prompt window from the Visual Studio installation directory and compile the `cmdll.c` file by typing **cl -LD cmdll.c** at the command prompt.</span></span>

3. <span data-ttu-id="6beb4-120">В том же каталоге создайте следующий файл C# и назовите его `cm.cs`.</span><span class="sxs-lookup"><span data-stu-id="6beb4-120">In the same directory, create the following C# file and name it `cm.cs`:</span></span>

    ```csharp
    // cm.cs
    using System;
    using System.Runtime.InteropServices;
    public class MainClass
    {
        [DllImport("Cmdll.dll")]
          public static extern int SampleMethod(int x);

        static void Main()
        {
            Console.WriteLine("SampleMethod() returns {0}.", SampleMethod(5));
        }
    }
    ```

4. <span data-ttu-id="6beb4-121">Откройте из каталога установки Visual Studio окно командной строки Visual Studio x64 (или x32) Native Tools и скомпилируйте файл `cm.cs`, введя:</span><span class="sxs-lookup"><span data-stu-id="6beb4-121">Open a Visual Studio x64 (or x32) Native Tools Command Prompt window from the Visual Studio installation directory and compile the `cm.cs` file by typing:</span></span>

    > <span data-ttu-id="6beb4-122">**csc cm.cs** (для командной строки x64) — или — **csc -platform:x86 cm.cs** (для командной строки x32)</span><span class="sxs-lookup"><span data-stu-id="6beb4-122">**csc cm.cs** (for the x64 command prompt) —or— **csc -platform:x86 cm.cs** (for the x32 command prompt)</span></span>

    <span data-ttu-id="6beb4-123">При этом будет создан исполняемый файл `cm.exe`.</span><span class="sxs-lookup"><span data-stu-id="6beb4-123">This will create the executable file `cm.exe`.</span></span>

5. <span data-ttu-id="6beb4-124">Выполните `cm.exe`.</span><span class="sxs-lookup"><span data-stu-id="6beb4-124">Run `cm.exe`.</span></span> <span data-ttu-id="6beb4-125">Метод `SampleMethod` передает значение 5 в файл DLL, который возвращает значение, умноженное на 10.</span><span class="sxs-lookup"><span data-stu-id="6beb4-125">The `SampleMethod` method passes the value 5 to the DLL file, which returns the value multiplied by 10.</span></span>  <span data-ttu-id="6beb4-126">Программа выдает следующие результаты.</span><span class="sxs-lookup"><span data-stu-id="6beb4-126">The program produces the following output:</span></span>

    ```output
    SampleMethod() returns 50.
    ```

## <a name="c-language-specification"></a><span data-ttu-id="6beb4-127">Спецификация языка C#</span><span class="sxs-lookup"><span data-stu-id="6beb4-127">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="6beb4-128">См. также</span><span class="sxs-lookup"><span data-stu-id="6beb4-128">See also</span></span>

- <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=nameWithType>
- [<span data-ttu-id="6beb4-129">Справочник по C#</span><span class="sxs-lookup"><span data-stu-id="6beb4-129">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="6beb4-130">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="6beb4-130">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="6beb4-131">Ключевые слова в C#</span><span class="sxs-lookup"><span data-stu-id="6beb4-131">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="6beb4-132">Модификаторы</span><span class="sxs-lookup"><span data-stu-id="6beb4-132">Modifiers</span></span>](index.md)
