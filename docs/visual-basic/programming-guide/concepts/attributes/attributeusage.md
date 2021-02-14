---
description: 'Дополнительные сведения о: AttributeUsage (Visual Basic)'
title: AttributeUsage
ms.date: 07/20/2015
ms.assetid: 48757216-c21d-4051-86d5-8a3e03c39d2c
ms.openlocfilehash: afb043c1b16da3e134888a38ec73f0b6f4ec5f58
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100437817"
---
# <a name="attributeusage-visual-basic"></a><span data-ttu-id="2fdc1-103">AttributeUsage (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2fdc1-103">AttributeUsage (Visual Basic)</span></span>

<span data-ttu-id="2fdc1-104">Определяет, как можно использовать пользовательский класс атрибутов.</span><span class="sxs-lookup"><span data-stu-id="2fdc1-104">Determines how a custom attribute class can be used.</span></span> <span data-ttu-id="2fdc1-105">Атрибут `AttributeUsage` можно применять к пользовательским определениям атрибутов, чтобы контролировать применение нового атрибута.</span><span class="sxs-lookup"><span data-stu-id="2fdc1-105">`AttributeUsage` is an attribute that can be applied to custom attribute definitions to control how the new attribute can be applied.</span></span> <span data-ttu-id="2fdc1-106">При явном применении параметры по умолчанию выглядят следующим образом:</span><span class="sxs-lookup"><span data-stu-id="2fdc1-106">The default settings look like this when applied explicitly:</span></span>

```vb
<System.AttributeUsage(System.AttributeTargets.All,
                   AllowMultiple:=False,
                   Inherited:=True)>
Class NewAttribute
    Inherits System.Attribute
End Class
```

<span data-ttu-id="2fdc1-107">В этом примере класс `NewAttribute` можно применить к любой сущности кода с атрибутами, но только один раз к каждой сущности.</span><span class="sxs-lookup"><span data-stu-id="2fdc1-107">In this example, the `NewAttribute` class can be applied to any attribute-able code entity, but can be applied only once to each entity.</span></span> <span data-ttu-id="2fdc1-108">Он наследуется производными классами при применении к базовому классу.</span><span class="sxs-lookup"><span data-stu-id="2fdc1-108">It is inherited by derived classes when applied to a base class.</span></span>

<span data-ttu-id="2fdc1-109">Аргументы `AllowMultiple` и `Inherited` являются необязательными, так что этот код имеет тот же результат:</span><span class="sxs-lookup"><span data-stu-id="2fdc1-109">The `AllowMultiple` and `Inherited` arguments are optional, so this code has the same effect:</span></span>

```vb
<System.AttributeUsage(System.AttributeTargets.All)>
Class NewAttribute
    Inherits System.Attribute
End Class
```

<span data-ttu-id="2fdc1-110">Первый аргумент `AttributeUsage` должен состоять из одного или нескольких элементов перечисления <xref:System.AttributeTargets>.</span><span class="sxs-lookup"><span data-stu-id="2fdc1-110">The first `AttributeUsage` argument must be one or more elements of the <xref:System.AttributeTargets> enumeration.</span></span> <span data-ttu-id="2fdc1-111">Несколько целевых типов можно связать с помощью оператора OR следующим образом:</span><span class="sxs-lookup"><span data-stu-id="2fdc1-111">Multiple target types can be linked together with the OR operator, like this:</span></span>

```vb
<AttributeUsage(AttributeTargets.Property Or AttributeTargets.Field)>
Class NewPropertyOrFieldAttribute
    Inherits Attribute
End Class
```

<span data-ttu-id="2fdc1-112">Если аргументу `AllowMultiple` присвоено значение `true`, то результирующий атрибут можно применить несколько раз к одной сущности следующим образом:</span><span class="sxs-lookup"><span data-stu-id="2fdc1-112">If the `AllowMultiple` argument is set to `true`, then the resulting attribute can be applied more than once to a single entity, like this:</span></span>

```vb
<AttributeUsage(AttributeTargets.Class, AllowMultiple:=True)>
Class MultiUseAttr
    Inherits Attribute
End Class

<MultiUseAttr(), MultiUseAttr()>
Class Class1
End Class
```

<span data-ttu-id="2fdc1-113">В этом случае `MultiUseAttr` можно применять несколько раз, так как `AllowMultiple` имеет значение `true`.</span><span class="sxs-lookup"><span data-stu-id="2fdc1-113">In this case `MultiUseAttr` can be applied repeatedly because `AllowMultiple` is set to `true`.</span></span> <span data-ttu-id="2fdc1-114">Для применения нескольких атрибутов допускаются оба показанных формата.</span><span class="sxs-lookup"><span data-stu-id="2fdc1-114">Both formats shown for applying multiple attributes are valid.</span></span>

<span data-ttu-id="2fdc1-115">Если `Inherited` имеет значение `false`, то атрибут не наследуется классами, производными от класса с атрибутами.</span><span class="sxs-lookup"><span data-stu-id="2fdc1-115">If `Inherited` is set to `false`, then the attribute is not inherited by classes that are derived from a class that is attributed.</span></span> <span data-ttu-id="2fdc1-116">Пример:</span><span class="sxs-lookup"><span data-stu-id="2fdc1-116">For example:</span></span>

```vb
<AttributeUsage(AttributeTargets.Class, Inherited:=False)>
Class Attr1
    Inherits Attribute
End Class

<Attr1()>
Class BClass

End Class

Class DClass
    Inherits BClass
End Class
```

<span data-ttu-id="2fdc1-117">В этом случае `Attr1` не применяется к `DClass` путем наследования.</span><span class="sxs-lookup"><span data-stu-id="2fdc1-117">In this case `Attr1` is not applied to `DClass` via inheritance.</span></span>

## <a name="remarks"></a><span data-ttu-id="2fdc1-118">Remarks</span><span class="sxs-lookup"><span data-stu-id="2fdc1-118">Remarks</span></span>

<span data-ttu-id="2fdc1-119">Атрибут `AttributeUsage` можно использовать только один раз — его нельзя повторно применять к одному и тому же классу.</span><span class="sxs-lookup"><span data-stu-id="2fdc1-119">The `AttributeUsage` attribute is a single-use attribute--it cannot be applied more than once to the same class.</span></span> <span data-ttu-id="2fdc1-120">`AttributeUsage` является псевдонимом для <xref:System.AttributeUsageAttribute>.</span><span class="sxs-lookup"><span data-stu-id="2fdc1-120">`AttributeUsage` is an alias for <xref:System.AttributeUsageAttribute>.</span></span>

<span data-ttu-id="2fdc1-121">Дополнительные сведения см. в статье [Accessing Attributes by Using Reflection (Visual Basic)](accessing-attributes-by-using-reflection.md) (Обращение к атрибутам с помощью отражения (Visual Basic)).</span><span class="sxs-lookup"><span data-stu-id="2fdc1-121">For more information, see [Accessing Attributes by Using Reflection (Visual Basic)](accessing-attributes-by-using-reflection.md).</span></span>

## <a name="example"></a><span data-ttu-id="2fdc1-122">Пример</span><span class="sxs-lookup"><span data-stu-id="2fdc1-122">Example</span></span>

<span data-ttu-id="2fdc1-123">В приведенном ниже примере демонстрируется действие аргументов `Inherited` и `AllowMultiple` по отношению к атрибуту `AttributeUsage`, а также способ перечисления настраиваемых атрибутов, примененных к классу.</span><span class="sxs-lookup"><span data-stu-id="2fdc1-123">The following example demonstrates the effect of the `Inherited` and `AllowMultiple` arguments to the `AttributeUsage` attribute, and how the custom attributes applied to a class can be enumerated.</span></span>

```vb
' Create some custom attributes:
<AttributeUsage(System.AttributeTargets.Class, Inherited:=False)>
Class A1
    Inherits System.Attribute
End Class

<AttributeUsage(System.AttributeTargets.Class)>
Class A2
    Inherits System.Attribute
End Class

<AttributeUsage(System.AttributeTargets.Class, AllowMultiple:=True)>
Class A3
    Inherits System.Attribute
End Class

' Apply custom attributes to classes:
<A1(), A2()>
Class BaseClass

End Class

<A3(), A3()>
Class DerivedClass
    Inherits BaseClass
End Class

Public Class TestAttributeUsage
    Sub Main()
        Dim b As New BaseClass
        Dim d As New DerivedClass
        ' Display custom attributes for each class.
        Console.WriteLine("Attributes on Base Class:")
        Dim attrs() As Object = b.GetType().GetCustomAttributes(True)

        For Each attr In attrs
            Console.WriteLine(attr)
        Next

        Console.WriteLine("Attributes on Derived Class:")
        attrs = d.GetType().GetCustomAttributes(True)
        For Each attr In attrs
            Console.WriteLine(attr)
        Next
    End Sub
End Class
```

## <a name="sample-output"></a><span data-ttu-id="2fdc1-124">Пример выходных данных</span><span class="sxs-lookup"><span data-stu-id="2fdc1-124">Sample Output</span></span>

```console
Attributes on Base Class:
A1
A2
Attributes on Derived Class:
A3
A3
A2
```

## <a name="see-also"></a><span data-ttu-id="2fdc1-125">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="2fdc1-125">See also</span></span>

- <xref:System.Attribute>
- <xref:System.Reflection>
- [<span data-ttu-id="2fdc1-126">Руководство по программированию на Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2fdc1-126">Visual Basic Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="2fdc1-127">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="2fdc1-127">Attributes</span></span>](../../../../standard/attributes/index.md)
- <span data-ttu-id="2fdc1-128">[Reflection (Visual Basic)](../reflection.md) (Отражение (Visual Basic))</span><span class="sxs-lookup"><span data-stu-id="2fdc1-128">[Reflection (Visual Basic)](../reflection.md)</span></span>
- [<span data-ttu-id="2fdc1-129">Атрибуты (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2fdc1-129">Attributes (Visual Basic)</span></span>](../../../language-reference/attributes.md)
- <span data-ttu-id="2fdc1-130">[Creating Custom Attributes (Visual Basic)](creating-custom-attributes.md) (Создание настраиваемых атрибутов (Visual Basic))</span><span class="sxs-lookup"><span data-stu-id="2fdc1-130">[Creating Custom Attributes (Visual Basic)](creating-custom-attributes.md)</span></span>
- <span data-ttu-id="2fdc1-131">[Accessing Attributes by Using Reflection (Visual Basic)](accessing-attributes-by-using-reflection.md) (Обращение к атрибутам с помощью отражения (Visual Basic))</span><span class="sxs-lookup"><span data-stu-id="2fdc1-131">[Accessing Attributes by Using Reflection (Visual Basic)](accessing-attributes-by-using-reflection.md)</span></span>
