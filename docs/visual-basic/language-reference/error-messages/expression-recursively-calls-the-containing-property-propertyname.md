---
description: 'Дополнительные сведения о: BC42026: Expression рекурсивно вызывает содержащееся свойство " <propertyname> "'
title: Выражение рекурсивно вызывает содержащее свойство <propertyname>
ms.date: 07/20/2015
f1_keywords:
- vbc42026
- BC42026
helpviewer_keywords:
- BC42026
ms.assetid: 4fde9db6-3bf3-48dc-8e05-981bf08969da
ms.openlocfilehash: e9e8a39458fe930eb77c548866e62c1c32b4ed16
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100437674"
---
# <a name="bc42026-expression-recursively-calls-the-containing-property-propertyname"></a><span data-ttu-id="c4c02-103">BC42026: выражение рекурсивно вызывает содержащееся свойство " \<propertyname> "</span><span class="sxs-lookup"><span data-stu-id="c4c02-103">BC42026: Expression recursively calls the containing property '\<propertyname>'</span></span>

<span data-ttu-id="c4c02-104">Оператор в `Set` процедуре определения свойства сохраняет значение в имени свойства.</span><span class="sxs-lookup"><span data-stu-id="c4c02-104">A statement in the `Set` procedure of a property definition stores a value into the name of the property.</span></span>

 <span data-ttu-id="c4c02-105">Рекомендуемый подход к удержанию значения свойства — определить `Private` переменную в контейнере свойства и использовать ее в `Get` `Set` процедурах и.</span><span class="sxs-lookup"><span data-stu-id="c4c02-105">The recommended approach to holding the value of a property is to define a `Private` variable in the property's container and use it in both the `Get` and `Set` procedures.</span></span> <span data-ttu-id="c4c02-106">`Set`Процедура должна сохранить входящее значение в этой `Private` переменной.</span><span class="sxs-lookup"><span data-stu-id="c4c02-106">The `Set` procedure should then store the incoming value in this `Private` variable.</span></span>

 <span data-ttu-id="c4c02-107">`Get`Процедура ведет себя как `Function` процедура, поэтому ей можно присвоить значение имени свойства и вернуть управление, выполнив `End Get` инструкцию.</span><span class="sxs-lookup"><span data-stu-id="c4c02-107">The `Get` procedure behaves like a `Function` procedure, so it can assign a value to the property name and return control by encountering the `End Get` statement.</span></span> <span data-ttu-id="c4c02-108">Однако рекомендуемый подход заключается в включении `Private` переменной в качестве значения в [операторе return](../statements/return-statement.md).</span><span class="sxs-lookup"><span data-stu-id="c4c02-108">The recommended approach, however, is to include the `Private` variable as the value in a [Return Statement](../statements/return-statement.md).</span></span>

 <span data-ttu-id="c4c02-109">`Set`Процедура ведет себя как `Sub` процедура, которая не возвращает значение.</span><span class="sxs-lookup"><span data-stu-id="c4c02-109">The `Set` procedure behaves like a `Sub` procedure, which does not return a value.</span></span> <span data-ttu-id="c4c02-110">Следовательно, имя процедуры или свойства не имеет особого смысла в `Set` процедуре, и в ней нельзя хранить значение.</span><span class="sxs-lookup"><span data-stu-id="c4c02-110">Therefore, the procedure or property name has no special meaning within a `Set` procedure, and you cannot store a value into it.</span></span>

 <span data-ttu-id="c4c02-111">В следующем примере показан подход, который может вызвать эту ошибку, за которым следует рекомендуемый подход.</span><span class="sxs-lookup"><span data-stu-id="c4c02-111">The following example illustrates the approach that can cause this error, followed by the recommended approach.</span></span>

```vb
Public Class illustrateProperties
' The code in the following property causes this error.
    Public Property badProp() As Char
        Get
            Dim charValue As Char
            ' Insert code to update charValue.
            badProp = charValue
        End Get
        Set(ByVal Value As Char)
            ' The following statement causes this error.
            badProp = Value
            ' The value stored in the local variable badProp
            ' is not used by the Get procedure in this property.
        End Set
    End Property
' The following code uses the recommended approach.
    Private propValue As Char
    Public Property goodProp() As Char
        Get
            ' Insert code to update propValue.
            Return propValue
        End Get
        Set(ByVal Value As Char)
            propValue = Value
        End Set
    End Property
End Class
```

 <span data-ttu-id="c4c02-112">По умолчанию данное сообщение является предупреждением.</span><span class="sxs-lookup"><span data-stu-id="c4c02-112">By default, this message is a warning.</span></span> <span data-ttu-id="c4c02-113">Дополнительные сведения о скрытии предупреждений или обработке предупреждений как ошибок см. [в разделе Настройка предупреждений в Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="c4c02-113">For more information about hiding warnings or treating warnings as errors, please see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>

 <span data-ttu-id="c4c02-114">**Идентификатор ошибки:** BC42026</span><span class="sxs-lookup"><span data-stu-id="c4c02-114">**Error ID:** BC42026</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="c4c02-115">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="c4c02-115">To correct this error</span></span>

- <span data-ttu-id="c4c02-116">Перепишите определение свойства, чтобы использовать рекомендуемый подход, как показано в предыдущем примере.</span><span class="sxs-lookup"><span data-stu-id="c4c02-116">Rewrite the property definition to use the recommended approach as illustrated in the preceding example.</span></span>

## <a name="see-also"></a><span data-ttu-id="c4c02-117">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="c4c02-117">See also</span></span>

- [<span data-ttu-id="c4c02-118">Процедуры свойств</span><span class="sxs-lookup"><span data-stu-id="c4c02-118">Property Procedures</span></span>](../../programming-guide/language-features/procedures/property-procedures.md)
- [<span data-ttu-id="c4c02-119">Property Statement</span><span class="sxs-lookup"><span data-stu-id="c4c02-119">Property Statement</span></span>](../statements/property-statement.md)
- [<span data-ttu-id="c4c02-120">Инструкция SET</span><span class="sxs-lookup"><span data-stu-id="c4c02-120">Set Statement</span></span>](../statements/set-statement.md)
