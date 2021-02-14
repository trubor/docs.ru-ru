---
description: 'Дополнительные сведения: методы расширения (Visual Basic)'
title: Методы расширения
ms.date: 07/20/2015
f1_keywords:
- vb.ExtensionMethods
helpviewer_keywords:
- extending data types [Visual Basic]
- extension methods [Visual Basic]
ms.assetid: b8020aae-374d-46a9-bcb7-8cc2390b93b6
ms.openlocfilehash: 5a1482502b144524c0be90e1c83a38f49b4a4d26
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100434359"
---
# <a name="extension-methods-visual-basic"></a><span data-ttu-id="05c1c-103">Методы расширения (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="05c1c-103">Extension Methods (Visual Basic)</span></span>

<span data-ttu-id="05c1c-104">Методы расширения позволяют разработчикам добавлять пользовательские функции к типам данных, которые уже определены без создания нового производного типа.</span><span class="sxs-lookup"><span data-stu-id="05c1c-104">Extension methods enable developers to add custom functionality to data types that are already defined without creating a new derived type.</span></span> <span data-ttu-id="05c1c-105">Методы расширения позволяют написать метод, который может вызываться, как если бы он был методом экземпляра существующего типа.</span><span class="sxs-lookup"><span data-stu-id="05c1c-105">Extension methods make it possible to write a method that can be called as if it were an instance method of the existing type.</span></span>

## <a name="remarks"></a><span data-ttu-id="05c1c-106">Remarks</span><span class="sxs-lookup"><span data-stu-id="05c1c-106">Remarks</span></span>

<span data-ttu-id="05c1c-107">Метод расширения может быть только `Sub` процедурой или `Function` процедурой.</span><span class="sxs-lookup"><span data-stu-id="05c1c-107">An extension method can be only a `Sub` procedure or a `Function` procedure.</span></span> <span data-ttu-id="05c1c-108">Невозможно определить свойство, поле или событие расширения.</span><span class="sxs-lookup"><span data-stu-id="05c1c-108">You cannot define an extension property, field, or event.</span></span> <span data-ttu-id="05c1c-109">Все методы расширения должны быть помечены атрибутом расширения `<Extension>` из <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> пространства имен и должны быть определены в [модуле](../../../language-reference/statements/module-statement.md).</span><span class="sxs-lookup"><span data-stu-id="05c1c-109">All extension methods must be marked with the extension attribute `<Extension>` from the <xref:System.Runtime.CompilerServices?displayProperty=nameWithType> namespace and must be defined in a [Module](../../../language-reference/statements/module-statement.md).</span></span> <span data-ttu-id="05c1c-110">Если метод расширения определен за пределами модуля, Visual Basic компилятор создает ошибку [BC36551](../../../misc/bc36551.md), "методы расширения могут быть определены только в модулях".</span><span class="sxs-lookup"><span data-stu-id="05c1c-110">If an extension method is defined outside a module, the Visual Basic compiler generates error [BC36551](../../../misc/bc36551.md), "Extension methods can be defined only in modules".</span></span>

<span data-ttu-id="05c1c-111">Первый параметр в определении метода расширения указывает тип данных, который расширяет метод.</span><span class="sxs-lookup"><span data-stu-id="05c1c-111">The first parameter in an extension method definition specifies which data type the method extends.</span></span> <span data-ttu-id="05c1c-112">При выполнении метода первый параметр привязывается к экземпляру типа данных, который вызывает метод.</span><span class="sxs-lookup"><span data-stu-id="05c1c-112">When the method is run, the first parameter is bound to the instance of the data type that invokes the method.</span></span>

<span data-ttu-id="05c1c-113">`Extension`Атрибут можно применить только к Visual Basic [`Module`](../../../language-reference/statements/module-statement.md) , [`Sub`](../../../language-reference/statements/sub-statement.md) или [`Function`](../../../language-reference/statements/function-statement.md) .</span><span class="sxs-lookup"><span data-stu-id="05c1c-113">The `Extension` attribute can only be applied to a Visual Basic [`Module`](../../../language-reference/statements/module-statement.md), [`Sub`](../../../language-reference/statements/sub-statement.md), or [`Function`](../../../language-reference/statements/function-statement.md).</span></span> <span data-ttu-id="05c1c-114">Если применить его к `Class` или `Structure` , Visual Basic компилятор создает ошибку [BC36550](../../../language-reference/error-messages/extension-attribute-can-be-applied-only-to-module-sub-or-function-declarations.md), атрибут "Extension" можно применить только к объявлениям "Module", "" или "Function".</span><span class="sxs-lookup"><span data-stu-id="05c1c-114">If you apply it to a `Class` or a `Structure`, the Visual Basic compiler generates error [BC36550](../../../language-reference/error-messages/extension-attribute-can-be-applied-only-to-module-sub-or-function-declarations.md), "'Extension' attribute can be applied only to 'Module', 'Sub', or 'Function' declarations".</span></span>

## <a name="example"></a><span data-ttu-id="05c1c-115">Пример</span><span class="sxs-lookup"><span data-stu-id="05c1c-115">Example</span></span>

<span data-ttu-id="05c1c-116">В следующем примере определяется `Print` расширение для <xref:System.String> типа данных.</span><span class="sxs-lookup"><span data-stu-id="05c1c-116">The following example defines a `Print` extension to the <xref:System.String> data type.</span></span> <span data-ttu-id="05c1c-117">Метод использует `Console.WriteLine` для вывода строки.</span><span class="sxs-lookup"><span data-stu-id="05c1c-117">The method uses `Console.WriteLine` to display a string.</span></span> <span data-ttu-id="05c1c-118">Параметр `Print` метода `aString` определяет, что метод расширяет <xref:System.String> класс.</span><span class="sxs-lookup"><span data-stu-id="05c1c-118">The parameter of the `Print` method, `aString`, establishes that the method extends the <xref:System.String> class.</span></span>

[!code-vb[VbVbalrExtensionMethods#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/StringExtensions.vb#1)]

<span data-ttu-id="05c1c-119">Обратите внимание, что определение метода расширения помечено атрибутом Extension `<Extension()>` .</span><span class="sxs-lookup"><span data-stu-id="05c1c-119">Notice that the extension method definition is marked with the extension attribute `<Extension()>`.</span></span> <span data-ttu-id="05c1c-120">Маркировка модуля, в котором определен метод, является необязательной, но каждый метод расширения должен быть помечен.</span><span class="sxs-lookup"><span data-stu-id="05c1c-120">Marking the module in which the method is defined is optional, but each extension method must be marked.</span></span> <span data-ttu-id="05c1c-121"><xref:System.Runtime.CompilerServices> необходимо импортировать, чтобы получить доступ к атрибуту расширения.</span><span class="sxs-lookup"><span data-stu-id="05c1c-121"><xref:System.Runtime.CompilerServices> must be imported in order to access the extension attribute.</span></span>

<span data-ttu-id="05c1c-122">Методы расширения могут объявляться только внутри модулей.</span><span class="sxs-lookup"><span data-stu-id="05c1c-122">Extension methods can be declared only within modules.</span></span> <span data-ttu-id="05c1c-123">Как правило, модуль, в котором определен метод расширения, не совпадает с модулем, в котором он вызывается.</span><span class="sxs-lookup"><span data-stu-id="05c1c-123">Typically, the module in which an extension method is defined is not the same module as the one in which it is called.</span></span> <span data-ttu-id="05c1c-124">Вместо этого модуль, содержащий метод расширения, импортируется, если требуется, чтобы перевести его в область.</span><span class="sxs-lookup"><span data-stu-id="05c1c-124">Instead, the module that contains the extension method is imported, if it needs to be, to bring it into scope.</span></span> <span data-ttu-id="05c1c-125">После того, как модуль, содержащий, `Print` находится в области, метод можно вызвать так, как если бы он был обычным методом экземпляра, не принимающим аргументы, например `ToUpper` :</span><span class="sxs-lookup"><span data-stu-id="05c1c-125">After the module that contains `Print` is in scope, the method can be called as if it were an ordinary instance method that takes no arguments, such as `ToUpper`:</span></span>

[!code-vb[VbVbalrExtensionMethods#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class1.vb#2)]

<span data-ttu-id="05c1c-126">Следующий пример, `PrintAndPunctuate` , также является расширением для, на <xref:System.String> этот раз определен с двумя параметрами.</span><span class="sxs-lookup"><span data-stu-id="05c1c-126">The next example, `PrintAndPunctuate`, is also an extension to <xref:System.String>, this time defined with two parameters.</span></span> <span data-ttu-id="05c1c-127">Первый параметр, `aString` задает расширение метода расширения <xref:System.String> .</span><span class="sxs-lookup"><span data-stu-id="05c1c-127">The first parameter, `aString`, establishes that the extension method extends <xref:System.String>.</span></span> <span data-ttu-id="05c1c-128">Второй параметр, `punc` , — это строка знаков препинания, которая передается в качестве аргумента при вызове метода.</span><span class="sxs-lookup"><span data-stu-id="05c1c-128">The second parameter, `punc`, is intended to be a string of punctuation marks that is passed in as an argument when the method is called.</span></span> <span data-ttu-id="05c1c-129">Метод отображает строку, за которой следуют знаки пунктуации.</span><span class="sxs-lookup"><span data-stu-id="05c1c-129">The method displays the string followed by the punctuation marks.</span></span>

[!code-vb[VbVbalrExtensionMethods#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class2.vb#3)]

<span data-ttu-id="05c1c-130">Метод вызывается путем отправки в строковый аргумент для `punc` : `example.PrintAndPunctuate(".")`</span><span class="sxs-lookup"><span data-stu-id="05c1c-130">The method is called by sending in a string argument for `punc`: `example.PrintAndPunctuate(".")`</span></span>

<span data-ttu-id="05c1c-131">В следующем примере показаны `Print` и `PrintAndPunctuate` определяются и вызываются.</span><span class="sxs-lookup"><span data-stu-id="05c1c-131">The following example shows `Print` and `PrintAndPunctuate` defined and called.</span></span> <span data-ttu-id="05c1c-132"><xref:System.Runtime.CompilerServices> импортируется в модуль определения, чтобы обеспечить доступ к атрибуту расширения.</span><span class="sxs-lookup"><span data-stu-id="05c1c-132"><xref:System.Runtime.CompilerServices> is imported in the definition module in order to enable access to the extension attribute.</span></span>

```vb
Imports System.Runtime.CompilerServices

Module StringExtensions

    <Extension()>
    Public Sub Print(aString As String)
        Console.WriteLine(aString)
    End Sub

    <Extension()>
    Public Sub PrintAndPunctuate(aString As String, punc As String)
        Console.WriteLine(aString & punc)
    End Sub
End Module
```

<span data-ttu-id="05c1c-133">Далее методы расширения переносятся в область и называются:</span><span class="sxs-lookup"><span data-stu-id="05c1c-133">Next, the extension methods are brought into scope and called:</span></span>

```vb
Imports ConsoleApplication2.StringExtensions

Module Module1

    Sub Main()
        Dim example As String = "Example string"
        example.Print()

        example = "Hello"
        example.PrintAndPunctuate(".")
        example.PrintAndPunctuate("!!!!")
    End Sub
End Module
```

<span data-ttu-id="05c1c-134">Все, что необходимо для выполнения этих или аналогичных методов расширения, заключается в том, что они находятся в области.</span><span class="sxs-lookup"><span data-stu-id="05c1c-134">All that is required to be able to run these or similar extension methods is that they be in scope.</span></span> <span data-ttu-id="05c1c-135">Если модуль, содержащий метод расширения, находится в области видимости, он отображается в IntelliSense и может быть вызван как обычный метод экземпляра.</span><span class="sxs-lookup"><span data-stu-id="05c1c-135">If the module that contains an extension method is in scope, it is visible in IntelliSense and can be called as if it were an ordinary instance method.</span></span>

<span data-ttu-id="05c1c-136">Обратите внимание, что при вызове методов для первого параметра не отправляется ни один аргумент.</span><span class="sxs-lookup"><span data-stu-id="05c1c-136">Notice that when the methods are invoked, no argument is sent in for the first parameter.</span></span> <span data-ttu-id="05c1c-137">Параметр `aString` в предыдущих определениях метода привязан к `example` экземпляру `String` , который вызывает их.</span><span class="sxs-lookup"><span data-stu-id="05c1c-137">Parameter `aString` in the previous method definitions is bound to `example`, the instance of `String` that calls them.</span></span> <span data-ttu-id="05c1c-138">Компилятор будет использовать `example` в качестве аргумента, отправляемого в первый параметр.</span><span class="sxs-lookup"><span data-stu-id="05c1c-138">The compiler will use `example` as the argument sent to the first parameter.</span></span>

<span data-ttu-id="05c1c-139">Если метод расширения вызывается для объекта, для которого задано значение `Nothing` , метод расширения выполняется.</span><span class="sxs-lookup"><span data-stu-id="05c1c-139">If an extension method is called for an object that is set to `Nothing`, the extension method executes.</span></span> <span data-ttu-id="05c1c-140">Это не относится к обычным методам экземпляра.</span><span class="sxs-lookup"><span data-stu-id="05c1c-140">This does not apply to ordinary instance methods.</span></span> <span data-ttu-id="05c1c-141">Можно выполнить явную проверку `Nothing` в методе расширения.</span><span class="sxs-lookup"><span data-stu-id="05c1c-141">You can explicitly check for `Nothing` in the extension method.</span></span>

## <a name="types-that-can-be-extended"></a><span data-ttu-id="05c1c-142">Типы, которые могут быть расширены</span><span class="sxs-lookup"><span data-stu-id="05c1c-142">Types that can be extended</span></span>

<span data-ttu-id="05c1c-143">Можно определить метод расширения для большинства типов, которые могут быть представлены в списке параметров Visual Basic, включая следующие:</span><span class="sxs-lookup"><span data-stu-id="05c1c-143">You can define an extension method on most types that can be represented in a Visual Basic parameter list, including the following:</span></span>

- <span data-ttu-id="05c1c-144">Классы (ссылочные типы)</span><span class="sxs-lookup"><span data-stu-id="05c1c-144">Classes (reference types)</span></span>
- <span data-ttu-id="05c1c-145">Структуры (типы значений)</span><span class="sxs-lookup"><span data-stu-id="05c1c-145">Structures (value types)</span></span>
- <span data-ttu-id="05c1c-146">Интерфейсы</span><span class="sxs-lookup"><span data-stu-id="05c1c-146">Interfaces</span></span>
- <span data-ttu-id="05c1c-147">Делегаты</span><span class="sxs-lookup"><span data-stu-id="05c1c-147">Delegates</span></span>
- <span data-ttu-id="05c1c-148">Аргументы ByRef и ByVal</span><span class="sxs-lookup"><span data-stu-id="05c1c-148">ByRef and ByVal arguments</span></span>
- <span data-ttu-id="05c1c-149">Параметры универсального метода</span><span class="sxs-lookup"><span data-stu-id="05c1c-149">Generic method parameters</span></span>
- <span data-ttu-id="05c1c-150">Массивы</span><span class="sxs-lookup"><span data-stu-id="05c1c-150">Arrays</span></span>

<span data-ttu-id="05c1c-151">Поскольку первый параметр указывает тип данных, который расширяет метод расширения, он является обязательным и не может быть необязательным.</span><span class="sxs-lookup"><span data-stu-id="05c1c-151">Because the first parameter specifies the data type that the extension method extends, it is required and cannot be optional.</span></span> <span data-ttu-id="05c1c-152">По этой причине `Optional` Параметры и `ParamArray` параметры не могут быть первыми параметрами в списке параметров.</span><span class="sxs-lookup"><span data-stu-id="05c1c-152">For that reason, `Optional` parameters and `ParamArray` parameters cannot be the first parameter in the parameter list.</span></span>

<span data-ttu-id="05c1c-153">Методы расширения не рассматриваются в позднем связывании.</span><span class="sxs-lookup"><span data-stu-id="05c1c-153">Extension methods are not considered in late binding.</span></span> <span data-ttu-id="05c1c-154">В следующем примере инструкция `anObject.PrintMe()` вызывает <xref:System.MissingMemberException> исключение, то же самое исключение отображается, если `PrintMe` было удалено определение второго метода расширения.</span><span class="sxs-lookup"><span data-stu-id="05c1c-154">In the following example, the statement `anObject.PrintMe()` raises a <xref:System.MissingMemberException> exception, the same exception you would see if the second `PrintMe` extension method definition were deleted.</span></span>

[!code-vb[VbVbalrExtensionMethods#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class6.vb#9)]

## <a name="best-practices"></a><span data-ttu-id="05c1c-155">Рекомендации</span><span class="sxs-lookup"><span data-stu-id="05c1c-155">Best practices</span></span>

<span data-ttu-id="05c1c-156">Методы расширения предоставляют удобный и мощный способ расширения существующего типа.</span><span class="sxs-lookup"><span data-stu-id="05c1c-156">Extension methods provide a convenient and powerful way to extend an existing type.</span></span> <span data-ttu-id="05c1c-157">Тем не менее, чтобы использовать их успешно, необходимо учитывать некоторые моменты.</span><span class="sxs-lookup"><span data-stu-id="05c1c-157">However, to use them successfully, there are some points to consider.</span></span> <span data-ttu-id="05c1c-158">Эти рекомендации относятся главным образом к авторам библиотек классов, но они могут повлиять на любое приложение, использующее методы расширения.</span><span class="sxs-lookup"><span data-stu-id="05c1c-158">These considerations apply mainly to authors of class libraries, but they might affect any application that uses extension methods.</span></span>

<span data-ttu-id="05c1c-159">Чаще всего методы расширения, добавляемые к несобственным типам, более уязвимы, чем методы расширения, добавляемые к управляемым типам.</span><span class="sxs-lookup"><span data-stu-id="05c1c-159">Most generally, extension methods that you add to types that you do not own are more vulnerable than extension methods added to types that you control.</span></span> <span data-ttu-id="05c1c-160">В несобственных классах могут возникать некоторые вещи, которые могут повлиять на методы расширения.</span><span class="sxs-lookup"><span data-stu-id="05c1c-160">A number of things can occur in classes you do not own that can interfere with your extension methods.</span></span>

- <span data-ttu-id="05c1c-161">Если существует любой доступный член экземпляра, имеющий сигнатуру, совместимую с аргументами в вызывающей инструкции, без сужающих преобразований из аргумента в параметр, метод экземпляра будет использоваться в качестве предпочтений любому методу расширения.</span><span class="sxs-lookup"><span data-stu-id="05c1c-161">If any accessible instance member exists that has a signature that is compatible with the arguments in the calling statement, with no narrowing conversions required from argument to parameter, the instance method will be used in preference to any extension method.</span></span> <span data-ttu-id="05c1c-162">Таким образом, если в какой-то момент в классе добавляется соответствующий метод экземпляра, существующий член расширения, который вы используете, может стать недоступным.</span><span class="sxs-lookup"><span data-stu-id="05c1c-162">Therefore, if an appropriate instance method is added to a class at some point, an existing extension member that you rely on may become inaccessible.</span></span>

- <span data-ttu-id="05c1c-163">Автор метода расширения не может препятствовать написанию другими программистами конфликтующих методов расширения, которые могут иметь приоритет над исходным расширением.</span><span class="sxs-lookup"><span data-stu-id="05c1c-163">The author of an extension method cannot prevent other programmers from writing conflicting extension methods that may have precedence over the original extension.</span></span>

- <span data-ttu-id="05c1c-164">Надежность можно повысить, поместив методы расширения в собственное пространство имен.</span><span class="sxs-lookup"><span data-stu-id="05c1c-164">You can improve robustness by putting extension methods in their own namespace.</span></span> <span data-ttu-id="05c1c-165">Потребители библиотеки могут добавить пространство имен или исключить ее, или выбрать пространства имен отдельно от остальной части библиотеки.</span><span class="sxs-lookup"><span data-stu-id="05c1c-165">Consumers of your library can then include a namespace or exclude it, or select among namespaces, separately from the rest of the library.</span></span>

- <span data-ttu-id="05c1c-166">Расширение интерфейсов может быть более безопасным, чем расширение классов, особенно если вы не владеете интерфейсом или классом.</span><span class="sxs-lookup"><span data-stu-id="05c1c-166">It may be safer to extend interfaces than it is to extend classes, especially if you do not own the interface or class.</span></span> <span data-ttu-id="05c1c-167">Изменение интерфейса влияет на каждый класс, реализующий его.</span><span class="sxs-lookup"><span data-stu-id="05c1c-167">A change in an interface affects every class that implements it.</span></span> <span data-ttu-id="05c1c-168">Таким образом, автор может снизить вероятность добавления или изменения методов в интерфейсе.</span><span class="sxs-lookup"><span data-stu-id="05c1c-168">Therefore, the author may be less likely to add or change methods in an interface.</span></span> <span data-ttu-id="05c1c-169">Однако если класс реализует два интерфейса, у которых есть методы расширения с одинаковой сигнатурой, то ни один из методов расширения не виден.</span><span class="sxs-lookup"><span data-stu-id="05c1c-169">However, if a class implements two interfaces that have extension methods with the same signature, neither extension method is visible.</span></span>

- <span data-ttu-id="05c1c-170">Расширьте наиболее конкретный тип, который можно.</span><span class="sxs-lookup"><span data-stu-id="05c1c-170">Extend the most specific type you can.</span></span> <span data-ttu-id="05c1c-171">В иерархии типов при выборе типа, от которого наследуются многие другие типы, существуют уровни возможностей для введения методов экземпляра или других методов расширения, которые могут мешать работе.</span><span class="sxs-lookup"><span data-stu-id="05c1c-171">In a hierarchy of types, if you select a type from which many other types are derived, there are layers of possibilities for the introduction of instance methods or other extension methods that might interfere with yours.</span></span>

## <a name="extension-methods-instance-methods-and-properties"></a><span data-ttu-id="05c1c-172">Методы расширения, методы экземпляров и свойства</span><span class="sxs-lookup"><span data-stu-id="05c1c-172">Extension methods, instance methods, and properties</span></span>

<span data-ttu-id="05c1c-173">Если метод экземпляра в области имеет сигнатуру, совместимую с аргументами вызывающей инструкции, метод экземпляра выбирается в качестве предпочтений любому методу расширения.</span><span class="sxs-lookup"><span data-stu-id="05c1c-173">When an in-scope instance method has a signature that is compatible with the arguments of a calling statement, the instance method is chosen in preference to any extension method.</span></span> <span data-ttu-id="05c1c-174">Метод экземпляра имеет приоритет, даже если метод расширения лучше соответствует.</span><span class="sxs-lookup"><span data-stu-id="05c1c-174">The instance method has precedence even if the extension method is a better match.</span></span> <span data-ttu-id="05c1c-175">В следующем примере `ExampleClass` содержит метод экземпляра с именем `ExampleMethod` , имеющий один параметр типа `Integer` .</span><span class="sxs-lookup"><span data-stu-id="05c1c-175">In the following example, `ExampleClass` contains an instance method named `ExampleMethod` that has one parameter of type `Integer`.</span></span> <span data-ttu-id="05c1c-176">Метод расширения `ExampleMethod` расширяет `ExampleClass` и имеет один параметр типа `Long` .</span><span class="sxs-lookup"><span data-stu-id="05c1c-176">Extension method `ExampleMethod` extends `ExampleClass`, and has one parameter of type `Long`.</span></span>

[!code-vb[VbVbalrExtensionMethods#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class4.vb#4)]

<span data-ttu-id="05c1c-177">Первый вызов `ExampleMethod` в следующем коде вызывает метод расширения, поскольку `arg1` имеет значение `Long` и совместимо только с `Long` параметром в методе расширения.</span><span class="sxs-lookup"><span data-stu-id="05c1c-177">The first call to `ExampleMethod` in the following code calls the extension method, because `arg1` is `Long` and is compatible only with the `Long` parameter in the extension method.</span></span> <span data-ttu-id="05c1c-178">Второй вызов `ExampleMethod` `Integer` метода содержит аргумент, `arg2` и вызывает метод экземпляра.</span><span class="sxs-lookup"><span data-stu-id="05c1c-178">The second call to `ExampleMethod` has an `Integer` argument, `arg2`, and it calls the instance method.</span></span>

[!code-vb[VbVbalrExtensionMethods#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class4.vb#5)]

<span data-ttu-id="05c1c-179">Теперь измените типы данных параметров в двух методах:</span><span class="sxs-lookup"><span data-stu-id="05c1c-179">Now reverse the data types of the parameters in the two methods:</span></span>

[!code-vb[VbVbalrExtensionMethods#6](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class5.vb#6)]

<span data-ttu-id="05c1c-180">В этот раз код `Main` вызывает метод экземпляра в обоих случаях.</span><span class="sxs-lookup"><span data-stu-id="05c1c-180">This time the code in `Main` calls the instance method both times.</span></span> <span data-ttu-id="05c1c-181">Это происходит потому `arg1` , что и, и `arg2` имеют расширяющее преобразование в `Long` , а метод экземпляра имеет приоритет над методом расширения в обоих случаях.</span><span class="sxs-lookup"><span data-stu-id="05c1c-181">This is because both `arg1` and `arg2` have a widening conversion to `Long`, and the instance method takes precedence over the extension method in both cases.</span></span>

[!code-vb[VbVbalrExtensionMethods#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Class5.vb#7)]

<span data-ttu-id="05c1c-182">Поэтому метод расширения не может заменить существующий метод экземпляра.</span><span class="sxs-lookup"><span data-stu-id="05c1c-182">Therefore, an extension method cannot replace an existing instance method.</span></span> <span data-ttu-id="05c1c-183">Однако, если метод расширения имеет то же имя, что и метод экземпляра, но подписи не конфликтуют, доступ к обоим методам возможен.</span><span class="sxs-lookup"><span data-stu-id="05c1c-183">However, when an extension method has the same name as an instance method but the signatures do not conflict, both methods can be accessed.</span></span> <span data-ttu-id="05c1c-184">Например, если класс `ExampleClass` содержит метод с именем `ExampleMethod` , который не принимает аргументы, методы расширения с тем же именем, но с разными сигнатурами разрешены, как показано в следующем коде.</span><span class="sxs-lookup"><span data-stu-id="05c1c-184">For example, if class `ExampleClass` contains a method named `ExampleMethod` that takes no arguments, extension methods with the same name but different signatures are permitted, as shown in the following code.</span></span>

[!code-vb[VbVbalrExtensionMethods#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrExtensionMethods/VB/Module3.vb#8)]

<span data-ttu-id="05c1c-185">Результат выполнения этого кода выглядит следующим образом:</span><span class="sxs-lookup"><span data-stu-id="05c1c-185">The output from this code is as follows:</span></span>

```console
Extension method
Instance method
```

<span data-ttu-id="05c1c-186">Ситуация упрощается с помощью свойств: Если метод расширения имеет то же имя, что и свойство класса, который он расширяет, метод расширения не будет виден и к нему нельзя получить доступ.</span><span class="sxs-lookup"><span data-stu-id="05c1c-186">The situation is simpler with properties: if an extension method has the same name as a property of the class it extends, the extension method is not visible and cannot be accessed.</span></span>

## <a name="extension-method-precedence"></a><span data-ttu-id="05c1c-187">Приоритет метода расширения</span><span class="sxs-lookup"><span data-stu-id="05c1c-187">Extension method precedence</span></span>

<span data-ttu-id="05c1c-188">Если два метода расширения, имеющие идентичные сигнатуры, находятся в области видимости и доступны, будет вызван один из них с более высоким приоритетом.</span><span class="sxs-lookup"><span data-stu-id="05c1c-188">When two extension methods that have identical signatures are in scope and accessible, the one with higher precedence will be invoked.</span></span> <span data-ttu-id="05c1c-189">Приоритет метода расширения основан на механизме, который используется для приведения метода в область.</span><span class="sxs-lookup"><span data-stu-id="05c1c-189">An extension method's precedence is based on the mechanism used to bring the method into scope.</span></span> <span data-ttu-id="05c1c-190">В следующем списке показана иерархия очередностью, от самого высокого до самого низкого.</span><span class="sxs-lookup"><span data-stu-id="05c1c-190">The following list shows the precedence hierarchy, from highest to lowest.</span></span>

1. <span data-ttu-id="05c1c-191">Методы расширения, определенные в текущем модуле.</span><span class="sxs-lookup"><span data-stu-id="05c1c-191">Extension methods defined inside the current module.</span></span>

2. <span data-ttu-id="05c1c-192">Методы расширения, определенные внутри типов данных в текущем пространстве имен или на любом из его родителей, с дочерними пространствами имен с более высоким приоритетом, чем у родительских пространств имен.</span><span class="sxs-lookup"><span data-stu-id="05c1c-192">Extension methods defined inside data types in the current namespace or any one of its parents, with child namespaces having higher precedence than parent namespaces.</span></span>

3. <span data-ttu-id="05c1c-193">Методы расширения, определенные внутри любых импортов типов в текущем файле.</span><span class="sxs-lookup"><span data-stu-id="05c1c-193">Extension methods defined inside any type imports in the current file.</span></span>

4. <span data-ttu-id="05c1c-194">Методы расширения, определенные в любом импорте пространства имен в текущем файле.</span><span class="sxs-lookup"><span data-stu-id="05c1c-194">Extension methods defined inside any namespace imports in the current file.</span></span>

5. <span data-ttu-id="05c1c-195">Методы расширения, определенные внутри любых импортов типа на уровне проекта.</span><span class="sxs-lookup"><span data-stu-id="05c1c-195">Extension methods defined inside any project-level type imports.</span></span>

6. <span data-ttu-id="05c1c-196">Методы расширения, определенные внутри любых импортов пространства имен на уровне проекта.</span><span class="sxs-lookup"><span data-stu-id="05c1c-196">Extension methods defined inside any project-level namespace imports.</span></span>

<span data-ttu-id="05c1c-197">Если приоритет не позволяет устранить неоднозначность, можно использовать полное имя, чтобы указать вызываемый метод.</span><span class="sxs-lookup"><span data-stu-id="05c1c-197">If precedence does not resolve the ambiguity, you can use the fully qualified name to specify the method that you are calling.</span></span> <span data-ttu-id="05c1c-198">Если `Print` метод в предыдущем примере определен в модуле с именем `StringExtensions` , полное имя `StringExtensions.Print(example)` вместо `example.Print()` .</span><span class="sxs-lookup"><span data-stu-id="05c1c-198">If the `Print` method in the earlier example is defined in a module named `StringExtensions`, the fully qualified name is `StringExtensions.Print(example)` instead of `example.Print()`.</span></span>

## <a name="see-also"></a><span data-ttu-id="05c1c-199">См. также</span><span class="sxs-lookup"><span data-stu-id="05c1c-199">See also</span></span>

- <xref:System.Runtime.CompilerServices>
- <xref:System.Runtime.CompilerServices.ExtensionAttribute>
- [<span data-ttu-id="05c1c-200">Методы расширения</span><span class="sxs-lookup"><span data-stu-id="05c1c-200">Extension Methods</span></span>](../../../../csharp/programming-guide/classes-and-structs/extension-methods.md)
- [<span data-ttu-id="05c1c-201">Оператор Module</span><span class="sxs-lookup"><span data-stu-id="05c1c-201">Module Statement</span></span>](../../../language-reference/statements/module-statement.md)
- [<span data-ttu-id="05c1c-202">Параметры и аргументы процедуры</span><span class="sxs-lookup"><span data-stu-id="05c1c-202">Procedure Parameters and Arguments</span></span>](procedure-parameters-and-arguments.md)
- [<span data-ttu-id="05c1c-203">Необязательные параметры</span><span class="sxs-lookup"><span data-stu-id="05c1c-203">Optional Parameters</span></span>](optional-parameters.md)
- [<span data-ttu-id="05c1c-204">Массивы параметров</span><span class="sxs-lookup"><span data-stu-id="05c1c-204">Parameter Arrays</span></span>](parameter-arrays.md)
- [<span data-ttu-id="05c1c-205">Обзор атрибутов</span><span class="sxs-lookup"><span data-stu-id="05c1c-205">Attributes overview</span></span>](../../concepts/attributes/index.md)
- [<span data-ttu-id="05c1c-206">Область видимости в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="05c1c-206">Scope in Visual Basic</span></span>](../declared-elements/scope.md)
