---
description: Дополнительные сведения о главной процедуре см. в Visual Basic
title: Основная процедура
ms.date: 07/20/2015
f1_keywords:
- vb.Main
helpviewer_keywords:
- Main procedure
- Main method [Visual Basic]
- main function
ms.assetid: f0db283e-f283-4464-b521-b90858cc1b44
ms.openlocfilehash: b25190ef216fe4219923a27d6bbe0acff4536685
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100432810"
---
# <a name="main-procedure-in-visual-basic"></a><span data-ttu-id="3a4cb-103">Процедура Main в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3a4cb-103">Main Procedure in Visual Basic</span></span>

<span data-ttu-id="3a4cb-104">Каждое приложение Visual Basic должно содержать процедуру с именем `Main` .</span><span class="sxs-lookup"><span data-stu-id="3a4cb-104">Every Visual Basic application must contain a procedure called `Main`.</span></span> <span data-ttu-id="3a4cb-105">Эта процедура выступает в качестве начальной точки и общего управления для приложения.</span><span class="sxs-lookup"><span data-stu-id="3a4cb-105">This procedure serves as the starting point and overall control for your application.</span></span> <span data-ttu-id="3a4cb-106">Платформа .NET Framework вызывает процедуру, `Main` когда она загрузила приложение и готова передать ему управление.</span><span class="sxs-lookup"><span data-stu-id="3a4cb-106">The .NET Framework calls your `Main` procedure when it has loaded your application and is ready to pass control to it.</span></span> <span data-ttu-id="3a4cb-107">Если вы не создаете Windows Forms приложение, необходимо написать `Main` процедуру для приложений, выполняемых самостоятельно.</span><span class="sxs-lookup"><span data-stu-id="3a4cb-107">Unless you are creating a Windows Forms application, you must write the `Main` procedure for applications that run on their own.</span></span>

 <span data-ttu-id="3a4cb-108">`Main` содержит код, который выполняется в первую очередь.</span><span class="sxs-lookup"><span data-stu-id="3a4cb-108">`Main` contains the code that runs first.</span></span> <span data-ttu-id="3a4cb-109">В `Main` можно определить, какая форма должна загружаться первым при запуске программы, определить, выполняется ли в системе копия приложения, установить набор переменных для приложения или открыть базу данных, требуемую для приложения.</span><span class="sxs-lookup"><span data-stu-id="3a4cb-109">In `Main`, you can determine which form is to be loaded first when the program starts, find out if a copy of your application is already running on the system, establish a set of variables for your application, or open a database that the application requires.</span></span>

## <a name="requirements-for-the-main-procedure"></a><span data-ttu-id="3a4cb-110">Требования для основной процедуры</span><span class="sxs-lookup"><span data-stu-id="3a4cb-110">Requirements for the Main Procedure</span></span>

 <span data-ttu-id="3a4cb-111">Файл, который выполняется самостоятельно (обычно с расширением exe), должен содержать `Main` процедуру.</span><span class="sxs-lookup"><span data-stu-id="3a4cb-111">A file that runs on its own (usually with extension .exe) must contain a `Main` procedure.</span></span> <span data-ttu-id="3a4cb-112">Библиотека (например, с расширением DLL) не запускается самостоятельно и не требует `Main` процедуры.</span><span class="sxs-lookup"><span data-stu-id="3a4cb-112">A library (for example with extension .dll) does not run on its own and does not require a `Main` procedure.</span></span> <span data-ttu-id="3a4cb-113">Ниже приведены требования к различным типам проектов, которые можно создать.</span><span class="sxs-lookup"><span data-stu-id="3a4cb-113">The requirements for the different types of projects you can create are as follows:</span></span>

- <span data-ttu-id="3a4cb-114">Консольные приложения выполняются самостоятельно, и необходимо указать хотя бы одну `Main` процедуру.</span><span class="sxs-lookup"><span data-stu-id="3a4cb-114">Console applications run on their own, and you must supply at least one `Main` procedure.</span></span>

- <span data-ttu-id="3a4cb-115">Windows Forms приложения выполняются самостоятельно.</span><span class="sxs-lookup"><span data-stu-id="3a4cb-115">Windows Forms applications run on their own.</span></span> <span data-ttu-id="3a4cb-116">Однако компилятор Visual Basic автоматически создает `Main` процедуру в таком приложении, и вам не нужно писать его.</span><span class="sxs-lookup"><span data-stu-id="3a4cb-116">However, the Visual Basic compiler automatically generates a `Main` procedure in such an application, and you do not need to write one.</span></span>

- <span data-ttu-id="3a4cb-117">Библиотеки классов не нуждаются в `Main` процедуре.</span><span class="sxs-lookup"><span data-stu-id="3a4cb-117">Class libraries do not require a `Main` procedure.</span></span> <span data-ttu-id="3a4cb-118">К ним относятся библиотеки элементов управления Windows и библиотеки веб-элементов управления.</span><span class="sxs-lookup"><span data-stu-id="3a4cb-118">These include Windows Control Libraries and Web Control Libraries.</span></span> <span data-ttu-id="3a4cb-119">Веб-приложения развертываются в виде библиотек классов.</span><span class="sxs-lookup"><span data-stu-id="3a4cb-119">Web applications are deployed as class libraries.</span></span>

## <a name="declaring-the-main-procedure"></a><span data-ttu-id="3a4cb-120">Объявление основной процедуры</span><span class="sxs-lookup"><span data-stu-id="3a4cb-120">Declaring the Main Procedure</span></span>

 <span data-ttu-id="3a4cb-121">Существует четыре способа объявления `Main` процедуры.</span><span class="sxs-lookup"><span data-stu-id="3a4cb-121">There are four ways to declare the `Main` procedure.</span></span> <span data-ttu-id="3a4cb-122">Он может принимать аргументы, а также не может возвращать значение.</span><span class="sxs-lookup"><span data-stu-id="3a4cb-122">It can take arguments or not, and it can return a value or not.</span></span>

> [!NOTE]
> <span data-ttu-id="3a4cb-123">При объявлении `Main` в классе необходимо использовать `Shared` ключевое слово.</span><span class="sxs-lookup"><span data-stu-id="3a4cb-123">If you declare `Main` in a class, you must use the `Shared` keyword.</span></span> <span data-ttu-id="3a4cb-124">В модуле не `Main` обязательно должен быть `Shared` .</span><span class="sxs-lookup"><span data-stu-id="3a4cb-124">In a module, `Main` does not need to be `Shared`.</span></span>

- <span data-ttu-id="3a4cb-125">Самый простой способ — объявить `Sub` процедуру, которая не принимает аргументы или не возвращает значение.</span><span class="sxs-lookup"><span data-stu-id="3a4cb-125">The simplest way is to declare a `Sub` procedure that does not take arguments or return a value.</span></span>

    ```vb
    Module mainModule
        Sub Main()
            MsgBox("The Main procedure is starting the application.")
            ' Insert call to appropriate starting place in your code.
            MsgBox("The application is terminating.")
        End Sub
    End Module
    ```

- <span data-ttu-id="3a4cb-126">`Main` также может возвращать `Integer` значение, которое операционная система использует в качестве кода выхода для программы.</span><span class="sxs-lookup"><span data-stu-id="3a4cb-126">`Main` can also return an `Integer` value, which the operating system uses as the exit code for your program.</span></span> <span data-ttu-id="3a4cb-127">Другие программы могут протестировать этот код, изучая значение ERRORLEVEL Windows.</span><span class="sxs-lookup"><span data-stu-id="3a4cb-127">Other programs can test this code by examining the Windows ERRORLEVEL value.</span></span> <span data-ttu-id="3a4cb-128">Чтобы вернуть код выхода, вместо процедуры необходимо объявить `Main` `Function` процедуру `Sub` .</span><span class="sxs-lookup"><span data-stu-id="3a4cb-128">To return an exit code, you must declare `Main` as a `Function` procedure instead of a `Sub` procedure.</span></span>

    ```vb
    Module mainModule
        Function Main() As Integer
            MsgBox("The Main procedure is starting the application.")
            Dim returnValue As Integer = 0
            ' Insert call to appropriate starting place in your code.
            ' On return, assign appropriate value to returnValue.
            ' 0 usually means successful completion.
            MsgBox("The application is terminating with error level " &
                 CStr(returnValue) & ".")
            Return returnValue
        End Function
    End Module
    ```

- <span data-ttu-id="3a4cb-129">`Main` также может принимать `String` массив в качестве аргумента.</span><span class="sxs-lookup"><span data-stu-id="3a4cb-129">`Main` can also take a `String` array as an argument.</span></span> <span data-ttu-id="3a4cb-130">Каждая строка в массиве содержит один из аргументов командной строки, используемых для вызова программы.</span><span class="sxs-lookup"><span data-stu-id="3a4cb-130">Each string in the array contains one of the command-line arguments used to invoke your program.</span></span> <span data-ttu-id="3a4cb-131">В зависимости от их значений можно выполнять различные действия.</span><span class="sxs-lookup"><span data-stu-id="3a4cb-131">You can take different actions depending on their values.</span></span>

    ```vb
    Module mainModule
        Function Main(ByVal cmdArgs() As String) As Integer
            MsgBox("The Main procedure is starting the application.")
            Dim returnValue As Integer = 0
            ' See if there are any arguments.
            If cmdArgs.Length > 0 Then
                For argNum As Integer = 0 To UBound(cmdArgs, 1)
                    ' Insert code to examine cmdArgs(argNum) and take
                    ' appropriate action based on its value.
                Next
            End If
            ' Insert call to appropriate starting place in your code.
            ' On return, assign appropriate value to returnValue.
            ' 0 usually means successful completion.
            MsgBox("The application is terminating with error level " &
                 CStr(returnValue) & ".")
            Return returnValue
        End Function
    End Module
    ```

- <span data-ttu-id="3a4cb-132">Можно объявить `Main` , чтобы проверить аргументы командной строки, но не вернуть код выхода, как показано ниже.</span><span class="sxs-lookup"><span data-stu-id="3a4cb-132">You can declare `Main` to examine the command-line arguments but not return an exit code, as follows.</span></span>

    ```vb
    Module mainModule
        Sub Main(ByVal cmdArgs() As String)
            MsgBox("The Main procedure is starting the application.")
            Dim returnValue As Integer = 0
            ' See if there are any arguments.
            If cmdArgs.Length > 0 Then
                For argNum As Integer = 0 To UBound(cmdArgs, 1)
                    ' Insert code to examine cmdArgs(argNum) and take
                    ' appropriate action based on its value.
                Next
            End If
            ' Insert call to appropriate starting place in your code.
            MsgBox("The application is terminating.")
        End Sub
    End Module
    ```
  
## <a name="see-also"></a><span data-ttu-id="3a4cb-133">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="3a4cb-133">See also</span></span>

- <xref:Microsoft.VisualBasic.Interaction.MsgBox%2A>
- <xref:System.Array.Length%2A>
- <xref:Microsoft.VisualBasic.Information.UBound%2A>
- [<span data-ttu-id="3a4cb-134">Структура программы Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3a4cb-134">Structure of a Visual Basic Program</span></span>](structure-of-a-visual-basic-program.md)
- [<span data-ttu-id="3a4cb-135">-main</span><span class="sxs-lookup"><span data-stu-id="3a4cb-135">-main</span></span>](../../reference/command-line-compiler/main.md)
- [<span data-ttu-id="3a4cb-136">Общий</span><span class="sxs-lookup"><span data-stu-id="3a4cb-136">Shared</span></span>](../../language-reference/modifiers/shared.md)
- [<span data-ttu-id="3a4cb-137">Оператор Sub</span><span class="sxs-lookup"><span data-stu-id="3a4cb-137">Sub Statement</span></span>](../../language-reference/statements/sub-statement.md)
- [<span data-ttu-id="3a4cb-138">Оператор Function</span><span class="sxs-lookup"><span data-stu-id="3a4cb-138">Function Statement</span></span>](../../language-reference/statements/function-statement.md)
- [<span data-ttu-id="3a4cb-139">Тип данных Integer</span><span class="sxs-lookup"><span data-stu-id="3a4cb-139">Integer Data Type</span></span>](../../language-reference/data-types/integer-data-type.md)
- [<span data-ttu-id="3a4cb-140">Тип данных String</span><span class="sxs-lookup"><span data-stu-id="3a4cb-140">String Data Type</span></span>](../../language-reference/data-types/string-data-type.md)
