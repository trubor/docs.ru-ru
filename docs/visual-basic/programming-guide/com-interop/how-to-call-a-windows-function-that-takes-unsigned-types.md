---
description: Дополнительные сведения см. в статье как вызвать функцию Windows, которая принимает неподписанные типы (Visual Basic)
title: Практическое руководство. Вызов функции Windows, принимающей значение беззнакового типа
ms.date: 07/20/2015
helpviewer_keywords:
- Windows functions [Visual Basic], calling
- unsigned data types [Visual Basic]
- UShort data type [Visual Basic], using
- functions [Visual Basic], calling Windows functions
- ULong data type [Visual Basic], using
- UInteger data type [Visual Basic], using
- data types [Visual Basic], using
- unsigned types [Visual Basic]
- data types [Visual Basic], unsigned
- data types [Visual Basic], numeric
- unsigned types [Visual Basic], using
ms.assetid: c2c0e712-8dc2-43b9-b4c6-345fbb02e7ce
ms.openlocfilehash: 45851e22db88b9d35e5315398fb4cdbc2a7b920c
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100475647"
---
# <a name="how-to-call-a-windows-function-that-takes-unsigned-types-visual-basic"></a><span data-ttu-id="3ae39-103">Практическое руководство. Вызов функции Windows, принимающей значение беззнакового типа (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3ae39-103">How to: Call a Windows Function that Takes Unsigned Types (Visual Basic)</span></span>

<span data-ttu-id="3ae39-104">При использовании класса, модуля или структуры, имеющей члены целочисленных типов без знака, можно получить доступ к этим членам с помощью Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="3ae39-104">If you are consuming a class, module, or structure that has members of unsigned integer types, you can access these members with Visual Basic.</span></span>

## <a name="to-call-a-windows-function-that-takes-an-unsigned-type"></a><span data-ttu-id="3ae39-105">Вызов функции Windows, которая принимает неподписанный тип</span><span class="sxs-lookup"><span data-stu-id="3ae39-105">To call a Windows function that takes an unsigned type</span></span>

1. <span data-ttu-id="3ae39-106">Используйте [инструкцию Declare](../../language-reference/statements/declare-statement.md) , чтобы сообщить Visual Basic, какая библиотека содержит функцию, ее имя в этой библиотеке, последовательность вызова и способ преобразования строк при вызове.</span><span class="sxs-lookup"><span data-stu-id="3ae39-106">Use a [Declare Statement](../../language-reference/statements/declare-statement.md) to tell Visual Basic which library holds the function, what its name is in that library, what its calling sequence is, and how to convert strings when calling it.</span></span>

2. <span data-ttu-id="3ae39-107">В `Declare` инструкции используйте `UInteger` , `ULong` , или в `UShort` `Byte` соответствии с соответствующими параметрами для каждого параметра с типом без знака.</span><span class="sxs-lookup"><span data-stu-id="3ae39-107">In the `Declare` statement, use `UInteger`, `ULong`, `UShort`, or `Byte` as appropriate for each parameter with an unsigned type.</span></span>

3. <span data-ttu-id="3ae39-108">Обратитесь к документации по функции Windows, которую вы вызываете, чтобы найти имена и значения используемых констант.</span><span class="sxs-lookup"><span data-stu-id="3ae39-108">Consult the documentation for the Windows function you are calling to find the names and values of the constants it uses.</span></span> <span data-ttu-id="3ae39-109">Многие из них определены в файле WinUser. h.</span><span class="sxs-lookup"><span data-stu-id="3ae39-109">Many of these are defined in the WinUser.h file.</span></span>

4. <span data-ttu-id="3ae39-110">Объявите необходимые константы в коде.</span><span class="sxs-lookup"><span data-stu-id="3ae39-110">Declare the necessary constants in your code.</span></span> <span data-ttu-id="3ae39-111">Многие константы Windows представляют собой 32-разрядные значения без знака, и их следует объявлять `As UInteger` .</span><span class="sxs-lookup"><span data-stu-id="3ae39-111">Many Windows constants are 32-bit unsigned values, and you should declare these `As UInteger`.</span></span>

5. <span data-ttu-id="3ae39-112">Вызовите функцию обычным образом.</span><span class="sxs-lookup"><span data-stu-id="3ae39-112">Call the function in the normal way.</span></span> <span data-ttu-id="3ae39-113">В следующем примере вызывается функция Windows `MessageBox` , которая принимает беззнаковый целочисленный аргумент.</span><span class="sxs-lookup"><span data-stu-id="3ae39-113">The following example calls the Windows function `MessageBox`, which takes an unsigned integer argument.</span></span>

    ```vb
    Public Class windowsMessage
        Private Declare Auto Function mb Lib "user32.dll" Alias "MessageBox" (
            ByVal hWnd As Integer,
            ByVal lpText As String,
            ByVal lpCaption As String,
            ByVal uType As UInteger) As Integer
        Private Const MB_OK As UInteger = 0
        Private Const MB_ICONEXCLAMATION As UInteger = &H30
        Private Const IDOK As UInteger = 1
        Private Const IDCLOSE As UInteger = 8
        Private Const c As UInteger = MB_OK Or MB_ICONEXCLAMATION
        Public Function messageThroughWindows() As String
            Dim r As Integer = mb(0, "Click OK if you see this!",
                "Windows API call", c)
            Dim s As String = "Windows API MessageBox returned " &
                 CStr(r)& vbCrLf & "(IDOK = " & CStr(IDOK) &
                 ", IDCLOSE = " & CStr(IDCLOSE) & ")"
            Return s
        End Function
    End Class
    ```

     <span data-ttu-id="3ae39-114">Функцию можно проверить `messageThroughWindows` с помощью следующего кода.</span><span class="sxs-lookup"><span data-stu-id="3ae39-114">You can test the function `messageThroughWindows` with the following code.</span></span>

    ```vb
    Public Sub consumeWindowsMessage()
        Dim w As New windowsMessage
        w.messageThroughWindows()
    End Sub
    ```

    > [!CAUTION]
    > <span data-ttu-id="3ae39-115">`UInteger` `ULong` `UShort` Типы данных,, и `SByte` не являются частью [независимость от языка и Language-Independent компонентов](../../../standard/language-independence-and-language-independent-components.md) (CLS), поэтому CLS-совместимый код не может использовать компонент, который их использует.</span><span class="sxs-lookup"><span data-stu-id="3ae39-115">The `UInteger`, `ULong`, `UShort`, and `SByte` data types are not part of the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), so CLS-compliant code cannot consume a component that uses them.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="3ae39-116">Вызов неуправляемого кода, например программного интерфейса Windows (API), предоставляет ваш код потенциальным угрозам безопасности.</span><span class="sxs-lookup"><span data-stu-id="3ae39-116">Making a call to unmanaged code, such as the Windows application programming interface (API), exposes your code to potential security risks.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="3ae39-117">Для вызова API Windows требуется разрешение неуправляемого кода, которое может повлиять на его выполнение в ситуациях частичного доверия.</span><span class="sxs-lookup"><span data-stu-id="3ae39-117">Calling the Windows API requires unmanaged code permission, which might affect its execution in partial-trust situations.</span></span> <span data-ttu-id="3ae39-118">Дополнительные сведения см. в разделе <xref:System.Security.Permissions.SecurityPermission> и [разрешения на доступ к коду](/previous-versions/dotnet/netframework-4.0/h846e9b3(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="3ae39-118">For more information, see <xref:System.Security.Permissions.SecurityPermission> and [Code Access Permissions](/previous-versions/dotnet/netframework-4.0/h846e9b3(v=vs.100)).</span></span>

## <a name="see-also"></a><span data-ttu-id="3ae39-119">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="3ae39-119">See also</span></span>

- [<span data-ttu-id="3ae39-120">Типы данных</span><span class="sxs-lookup"><span data-stu-id="3ae39-120">Data Types</span></span>](../../language-reference/data-types/index.md)
- [<span data-ttu-id="3ae39-121">Тип данных Integer</span><span class="sxs-lookup"><span data-stu-id="3ae39-121">Integer Data Type</span></span>](../../language-reference/data-types/integer-data-type.md)
- [<span data-ttu-id="3ae39-122">Тип данных UInteger</span><span class="sxs-lookup"><span data-stu-id="3ae39-122">UInteger Data Type</span></span>](../../language-reference/data-types/uinteger-data-type.md)
- [<span data-ttu-id="3ae39-123">Declare Statement</span><span class="sxs-lookup"><span data-stu-id="3ae39-123">Declare Statement</span></span>](../../language-reference/statements/declare-statement.md)
- [<span data-ttu-id="3ae39-124">Пошаговое руководство. Вызов API Windows</span><span class="sxs-lookup"><span data-stu-id="3ae39-124">Walkthrough: Calling Windows APIs</span></span>](walkthrough-calling-windows-apis.md)
