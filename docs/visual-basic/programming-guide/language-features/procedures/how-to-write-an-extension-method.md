---
description: Дополнительные сведения см. в статье как написать метод расширения (Visual Basic).
title: Практическое руководство. Написание метода расширения
ms.date: 07/20/2015
helpviewer_keywords:
- extending data types [Visual Basic]
- writing extension methods [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: fb2739cc-958d-4ef4-a38b-214a74c93413
ms.openlocfilehash: 4c5d88976e55288ccb350ab82d459db0a23f468e
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100476193"
---
# <a name="how-to-write-an-extension-method-visual-basic"></a><span data-ttu-id="3109c-103">Практическое руководство. Написание метода расширения (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3109c-103">How to: Write an Extension Method (Visual Basic)</span></span>

<span data-ttu-id="3109c-104">Методы расширения позволяют добавлять методы в существующий класс.</span><span class="sxs-lookup"><span data-stu-id="3109c-104">Extension methods enable you to add methods to an existing class.</span></span> <span data-ttu-id="3109c-105">Метод расширения можно вызвать так, как если бы он был экземпляром этого класса.</span><span class="sxs-lookup"><span data-stu-id="3109c-105">The extension method can be called as if it were an instance of that class.</span></span>

### <a name="to-define-an-extension-method"></a><span data-ttu-id="3109c-106">Определение метода расширения</span><span class="sxs-lookup"><span data-stu-id="3109c-106">To define an extension method</span></span>

1. <span data-ttu-id="3109c-107">Откройте новое или существующее приложение Visual Basic в Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3109c-107">Open a new or existing Visual Basic application in Visual Studio.</span></span>

2. <span data-ttu-id="3109c-108">В верхней части файла, в котором нужно определить метод расширения, включите следующую инструкцию импорта:</span><span class="sxs-lookup"><span data-stu-id="3109c-108">At the top of the file in which you want to define an extension method, include the following import statement:</span></span>

    ```vb
    Imports System.Runtime.CompilerServices
    ```

3. <span data-ttu-id="3109c-109">В модуле в новом или существующем приложении приступите к определению метода с помощью [`<Extension>`](xref:System.Runtime.CompilerServices.ExtensionAttribute) атрибута:</span><span class="sxs-lookup"><span data-stu-id="3109c-109">Within a module in your new or existing application, begin the method definition with the [`<Extension>`](xref:System.Runtime.CompilerServices.ExtensionAttribute) attribute:</span></span>

    ```vb
    <Extension()>
    ```

    <span data-ttu-id="3109c-110">Обратите внимание, что `Extension` атрибут может применяться только к методу ( `Sub` или `Function` процедуре) в [модуле](../../../language-reference/statements/module-statement.md)Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="3109c-110">Note that the `Extension` attribute can only be applied to a method (a `Sub` or `Function` procedure) in a Visual Basic [Module](../../../language-reference/statements/module-statement.md).</span></span> <span data-ttu-id="3109c-111">Если применить его к методу в `Class` или `Structure` , Visual Basic компилятор создает ошибку [BC36551](../../../misc/bc36551.md), "методы расширения могут быть определены только в модулях".</span><span class="sxs-lookup"><span data-stu-id="3109c-111">If you apply it to a method in a `Class` or a `Structure`, the Visual Basic compiler generates error [BC36551](../../../misc/bc36551.md), "Extension methods can be defined only in modules."</span></span>

4. <span data-ttu-id="3109c-112">Объявите метод обычным способом, за исключением того, что тип первого параметра должен быть типом данных, который требуется расширить.</span><span class="sxs-lookup"><span data-stu-id="3109c-112">Declare your method in the ordinary way, except that the type of the first parameter must be the data type you want to extend.</span></span>

    ```vb
    <Extension()>
    Public Sub SubName(para1 As ExtendedType, <other parameters>)
         ' < Body of the method >
    End Sub
    ```

## <a name="example"></a><span data-ttu-id="3109c-113">Пример</span><span class="sxs-lookup"><span data-stu-id="3109c-113">Example</span></span>

<span data-ttu-id="3109c-114">В следующем примере объявляется метод расширения в модуле `StringExtensions` .</span><span class="sxs-lookup"><span data-stu-id="3109c-114">The following example declares an extension method in module `StringExtensions`.</span></span> <span data-ttu-id="3109c-115">Второй модуль, `Module1` , импортирует `StringExtensions` и вызывает метод.</span><span class="sxs-lookup"><span data-stu-id="3109c-115">A second module, `Module1`, imports `StringExtensions` and calls the method.</span></span> <span data-ttu-id="3109c-116">Метод расширения должен находиться в области видимости при его вызове.</span><span class="sxs-lookup"><span data-stu-id="3109c-116">The extension method must be in scope when it is called.</span></span> <span data-ttu-id="3109c-117">Метод расширения `PrintAndPunctuate` расширяет <xref:System.String> класс с помощью метода, который отображает экземпляр строки, за которым следует строка символов пунктуации, отправленная в в качестве параметра.</span><span class="sxs-lookup"><span data-stu-id="3109c-117">Extension method `PrintAndPunctuate` extends the <xref:System.String> class with a method that displays the string instance followed by a string of punctuation symbols sent in as a parameter.</span></span>

```vb
' Declarations will typically be in a separate module.
Imports System.Runtime.CompilerServices

Module StringExtensions
    <Extension()>
    Public Sub PrintAndPunctuate(aString As String, punc As String)
        Console.WriteLine(aString & punc)
    End Sub

End Module
```

```vb
' Import the module that holds the extension method you want to use,
' and call it.

Imports ConsoleApplication2.StringExtensions

Module Module1

    Sub Main()
        Dim example = "Hello"
        example.PrintAndPunctuate("?")
        example.PrintAndPunctuate("!!!!")
    End Sub

End Module
```

<span data-ttu-id="3109c-118">Обратите внимание, что метод определен с двумя параметрами и вызывается только с одним.</span><span class="sxs-lookup"><span data-stu-id="3109c-118">Notice that the method is defined with two parameters and called with only one.</span></span> <span data-ttu-id="3109c-119">Первый параметр, `aString` , в определении метода, привязан к `example` экземпляру `String` , который вызывает метод.</span><span class="sxs-lookup"><span data-stu-id="3109c-119">The first parameter, `aString`, in the method definition is bound to `example`, the instance of `String` that calls the method.</span></span> <span data-ttu-id="3109c-120">Выходные данные примера могут быть следующими:</span><span class="sxs-lookup"><span data-stu-id="3109c-120">The output of the example is as follows:</span></span>

```console
Hello?
Hello!!!!
```

## <a name="see-also"></a><span data-ttu-id="3109c-121">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="3109c-121">See also</span></span>

- <xref:System.Runtime.CompilerServices.ExtensionAttribute>
- [<span data-ttu-id="3109c-122">Методы расширения</span><span class="sxs-lookup"><span data-stu-id="3109c-122">Extension Methods</span></span>](extension-methods.md)
- [<span data-ttu-id="3109c-123">Оператор Module</span><span class="sxs-lookup"><span data-stu-id="3109c-123">Module Statement</span></span>](../../../language-reference/statements/module-statement.md)
- [<span data-ttu-id="3109c-124">Параметры и аргументы процедуры</span><span class="sxs-lookup"><span data-stu-id="3109c-124">Procedure Parameters and Arguments</span></span>](procedure-parameters-and-arguments.md)
- [<span data-ttu-id="3109c-125">Область видимости в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3109c-125">Scope in Visual Basic</span></span>](../declared-elements/scope.md)
