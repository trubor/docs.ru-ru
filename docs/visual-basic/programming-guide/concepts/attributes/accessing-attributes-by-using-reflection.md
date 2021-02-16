---
description: 'Дополнительные сведения: доступ к атрибутам с помощью отражения (Visual Basic)'
title: Обращение к атрибутам с помощью отражения
ms.date: 07/20/2015
ms.assetid: c56e41da-5433-464f-a7bf-2a722e78bc9f
ms.openlocfilehash: e585bb427456f1187eaf8c39937eaa67651d9309
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100437869"
---
# <a name="accessing-attributes-by-using-reflection-visual-basic"></a><span data-ttu-id="5fb7c-103">Accessing Attributes by Using Reflection (Visual Basic) (Обращение к атрибутам с помощью отражения (Visual Basic))</span><span class="sxs-lookup"><span data-stu-id="5fb7c-103">Accessing Attributes by Using Reflection (Visual Basic)</span></span>

<span data-ttu-id="5fb7c-104">Возможность определения настраиваемых атрибутов и их помещения в собственный исходный код не будет настолько значимой без наличия способа извлечения этих сведений и работы с ними.</span><span class="sxs-lookup"><span data-stu-id="5fb7c-104">The fact that you can define custom attributes and place them in your source code would be of little value without some way of retrieving that information and acting on it.</span></span> <span data-ttu-id="5fb7c-105">Отражение позволяет извлекать сведения, определенные с настраиваемыми атрибутами.</span><span class="sxs-lookup"><span data-stu-id="5fb7c-105">By using reflection, you can retrieve the information that was defined with custom attributes.</span></span> <span data-ttu-id="5fb7c-106">Основным методом выступает `GetCustomAttributes`, который возвращает массив объектов, являющихся эквивалентами времени выполнения атрибутов исходного кода.</span><span class="sxs-lookup"><span data-stu-id="5fb7c-106">The key method is `GetCustomAttributes`, which returns an array of objects that are the run-time equivalents of the source code attributes.</span></span> <span data-ttu-id="5fb7c-107">Для этого метода существует несколько перегруженных версий.</span><span class="sxs-lookup"><span data-stu-id="5fb7c-107">This method has several overloaded versions.</span></span> <span data-ttu-id="5fb7c-108">Для получения дополнительной информации см. <xref:System.Attribute>.</span><span class="sxs-lookup"><span data-stu-id="5fb7c-108">For more information, see <xref:System.Attribute>.</span></span>

<span data-ttu-id="5fb7c-109">Спецификация атрибута, например:</span><span class="sxs-lookup"><span data-stu-id="5fb7c-109">An attribute specification such as:</span></span>

```vb
<Author("P. Ackerman", Version:=1.1)>
Class SampleClass
    ' P. Ackerman's code goes here...
End Class
```

 <span data-ttu-id="5fb7c-110">концептуально эквивалентна следующему коду:</span><span class="sxs-lookup"><span data-stu-id="5fb7c-110">is conceptually equivalent to this:</span></span>

```vb
Dim anonymousAuthorObject As Author = New Author("P. Ackerman")
anonymousAuthorObject.version = 1.1
```

<span data-ttu-id="5fb7c-111">Однако код не выполняется до тех пор, пока у `SampleClass` не будут запрошены атрибуты.</span><span class="sxs-lookup"><span data-stu-id="5fb7c-111">However, the code is not executed until `SampleClass` is queried for attributes.</span></span> <span data-ttu-id="5fb7c-112">Вызов `GetCustomAttributes` в `SampleClass` приведет к тому, что объект `Author` будет создан и инициализирован так, как показано выше.</span><span class="sxs-lookup"><span data-stu-id="5fb7c-112">Calling `GetCustomAttributes` on `SampleClass` causes an `Author` object to be constructed and initialized as above.</span></span> <span data-ttu-id="5fb7c-113">Если класс имеет другие атрибуты, другие объекты атрибутов создаются аналогично.</span><span class="sxs-lookup"><span data-stu-id="5fb7c-113">If the class has other attributes, other attribute objects are constructed similarly.</span></span> <span data-ttu-id="5fb7c-114">`GetCustomAttributes` затем возвращает объект `Author` и все другие объекты атрибутов в массиве.</span><span class="sxs-lookup"><span data-stu-id="5fb7c-114">`GetCustomAttributes` then returns the `Author` object and any other attribute objects in an array.</span></span> <span data-ttu-id="5fb7c-115">Потом можно пройти по этому массиву, определить в зависимости от типа каждого элемента массива какие атрибуты были применены и извлечь сведения из объектов атрибутов.</span><span class="sxs-lookup"><span data-stu-id="5fb7c-115">You can then iterate over this array, determine what attributes were applied based on the type of each array element, and extract information from the attribute objects.</span></span>

## <a name="example"></a><span data-ttu-id="5fb7c-116">Пример</span><span class="sxs-lookup"><span data-stu-id="5fb7c-116">Example</span></span>

<span data-ttu-id="5fb7c-117">Ниже приведен полный пример.</span><span class="sxs-lookup"><span data-stu-id="5fb7c-117">Here is a complete example.</span></span> <span data-ttu-id="5fb7c-118">Определяется настраиваемый атрибут, который применяется к нескольким сущностям и извлекается через отражение.</span><span class="sxs-lookup"><span data-stu-id="5fb7c-118">A custom attribute is defined, applied to several entities, and retrieved via reflection.</span></span>

```vb
' Multiuse attribute
<System.AttributeUsage(System.AttributeTargets.Class Or
                       System.AttributeTargets.Struct,
                       AllowMultiple:=True)>
Public Class Author
    Inherits System.Attribute
    Private name As String
    Public version As Double
    Sub New(ByVal authorName As String)
        name = authorName

        ' Default value
        version = 1.0
    End Sub

    Function GetName() As String
        Return name
    End Function
End Class

' Class with the Author attribute
<Author("P. Ackerman")>
Public Class FirstClass
End Class

' Class without the Author attribute
Public Class SecondClass
End Class

' Class with multiple Author attributes.
<Author("P. Ackerman"), Author("R. Koch", Version:=2.0)>
Public Class ThirdClass
End Class

Class TestAuthorAttribute
    Sub Main()
        PrintAuthorInfo(GetType(FirstClass))
        PrintAuthorInfo(GetType(SecondClass))
        PrintAuthorInfo(GetType(ThirdClass))
    End Sub

    Private Shared Sub PrintAuthorInfo(ByVal t As System.Type)
        System.Console.WriteLine("Author information for {0}", t)

        ' Using reflection
        Dim attrs() As System.Attribute = System.Attribute.GetCustomAttributes(t)

        ' Displaying output
        For Each attr In attrs
            Dim a As Author = CType(attr, Author)
            System.Console.WriteLine("   {0}, version {1:f}", a.GetName(), a.version)
        Next
    End Sub

    ' Output:
    '   Author information for FirstClass
    '     P. Ackerman, version 1.00
    ' Author information for SecondClass
    ' Author information for ThirdClass
    '  R. Koch, version 2.00
    '  P. Ackerman, version 1.00

End Class
```

## <a name="see-also"></a><span data-ttu-id="5fb7c-119">См. также</span><span class="sxs-lookup"><span data-stu-id="5fb7c-119">See also</span></span>

- <xref:System.Reflection>
- <xref:System.Attribute>
- [<span data-ttu-id="5fb7c-120">Руководство по программированию на Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5fb7c-120">Visual Basic Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="5fb7c-121">Извлечение информации, сохраненной в атрибуте</span><span class="sxs-lookup"><span data-stu-id="5fb7c-121">Retrieving Information Stored in Attributes</span></span>](../../../../standard/attributes/retrieving-information-stored-in-attributes.md)
- <span data-ttu-id="5fb7c-122">[Reflection (Visual Basic)](../reflection.md) (Отражение (Visual Basic))</span><span class="sxs-lookup"><span data-stu-id="5fb7c-122">[Reflection (Visual Basic)](../reflection.md)</span></span>
- [<span data-ttu-id="5fb7c-123">Атрибуты (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5fb7c-123">Attributes (Visual Basic)</span></span>](../../../language-reference/attributes.md)
- <span data-ttu-id="5fb7c-124">[Creating Custom Attributes (Visual Basic)](creating-custom-attributes.md) (Создание настраиваемых атрибутов (Visual Basic))</span><span class="sxs-lookup"><span data-stu-id="5fb7c-124">[Creating Custom Attributes (Visual Basic)](creating-custom-attributes.md)</span></span>
