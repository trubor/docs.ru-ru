---
description: Дополнительные сведения см. в статье как создать объединение C/C++ с помощью атрибутов (Visual Basic).
title: Инструкции. Создание объединения C-C + + с помощью атрибутов
ms.date: 07/20/2015
ms.assetid: 9352a7e4-c0da-4d07-aa14-55ed43736fcb
ms.openlocfilehash: 10717ec97efe866f4c3993cc26789f29d97b148a
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100437752"
---
# <a name="how-to-create-a-cc-union-by-using-attributes-visual-basic"></a><span data-ttu-id="e8762-103">How to: Create a C/C++ Union by Using Attributes (Visual Basic) (Практическое руководство. Создание объединения C/C++ с помощью атрибутов (Visual Basic))</span><span class="sxs-lookup"><span data-stu-id="e8762-103">How to: Create a C/C++ Union by Using Attributes (Visual Basic)</span></span>

<span data-ttu-id="e8762-104">С помощью атрибутов можно настраивать расположение структур в памяти.</span><span class="sxs-lookup"><span data-stu-id="e8762-104">By using attributes you can customize how structs are laid out in memory.</span></span> <span data-ttu-id="e8762-105">Например, можно создать так называемое объединение в C/C++ с помощью атрибутов `StructLayout(LayoutKind.Explicit)` и `FieldOffset`.</span><span class="sxs-lookup"><span data-stu-id="e8762-105">For example, you can create what is known as a union in C/C++ by using the `StructLayout(LayoutKind.Explicit)` and `FieldOffset` attributes.</span></span>

## <a name="example"></a><span data-ttu-id="e8762-106">Пример</span><span class="sxs-lookup"><span data-stu-id="e8762-106">Example</span></span>

<span data-ttu-id="e8762-107">В этом сегменте кода все поля объединения `TestUnion` начинаются с одного адреса в памяти.</span><span class="sxs-lookup"><span data-stu-id="e8762-107">In this code segment, all of the fields of `TestUnion` start at the same location in memory.</span></span>

```vb
' Add an Imports statement for System.Runtime.InteropServices.

<System.Runtime.InteropServices.StructLayout(
      System.Runtime.InteropServices.LayoutKind.Explicit)>
Structure TestUnion
    <System.Runtime.InteropServices.FieldOffset(0)>
    Public i As Integer

    <System.Runtime.InteropServices.FieldOffset(0)>
    Public d As Double

    <System.Runtime.InteropServices.FieldOffset(0)>
    Public c As Char

    <System.Runtime.InteropServices.FieldOffset(0)>
    Public b As Byte
End Structure
```

## <a name="example"></a><span data-ttu-id="e8762-108">Пример</span><span class="sxs-lookup"><span data-stu-id="e8762-108">Example</span></span>

<span data-ttu-id="e8762-109">Ниже приведен еще один пример, в котором поля начинаются с разных явно заданных адресов.</span><span class="sxs-lookup"><span data-stu-id="e8762-109">The following is another example where fields start at different explicitly set locations.</span></span>

```vb
' Add an Imports statement for System.Runtime.InteropServices.

 <System.Runtime.InteropServices.StructLayout(
      System.Runtime.InteropServices.LayoutKind.Explicit)>
Structure TestExplicit
     <System.Runtime.InteropServices.FieldOffset(0)>
     Public lg As Long

     <System.Runtime.InteropServices.FieldOffset(0)>
     Public i1 As Integer

     <System.Runtime.InteropServices.FieldOffset(4)>
     Public i2 As Integer

     <System.Runtime.InteropServices.FieldOffset(8)>
     Public d As Double

     <System.Runtime.InteropServices.FieldOffset(12)>
     Public c As Char

     <System.Runtime.InteropServices.FieldOffset(14)>
     Public b As Byte
 End Structure
```

<span data-ttu-id="e8762-110">Два целочисленных поля `i1` и `i2` используют те же адреса памяти, что и `lg`.</span><span class="sxs-lookup"><span data-stu-id="e8762-110">The two integer fields, `i1` and `i2`, share the same memory locations as `lg`.</span></span> <span data-ttu-id="e8762-111">Такое управление расположением структуры полезно при использовании вызова неуправляемого кода.</span><span class="sxs-lookup"><span data-stu-id="e8762-111">This sort of control over struct layout is useful when using platform invocation.</span></span>

## <a name="see-also"></a><span data-ttu-id="e8762-112">См. также</span><span class="sxs-lookup"><span data-stu-id="e8762-112">See also</span></span>

- <xref:System.Reflection>
- <xref:System.Attribute>
- [<span data-ttu-id="e8762-113">Руководство по программированию на Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e8762-113">Visual Basic Programming Guide</span></span>](../../index.md)
- [<span data-ttu-id="e8762-114">Атрибуты</span><span class="sxs-lookup"><span data-stu-id="e8762-114">Attributes</span></span>](../../../../standard/attributes/index.md)
- <span data-ttu-id="e8762-115">[Reflection (Visual Basic)](../reflection.md) (Отражение (Visual Basic))</span><span class="sxs-lookup"><span data-stu-id="e8762-115">[Reflection (Visual Basic)](../reflection.md)</span></span>
- [<span data-ttu-id="e8762-116">Атрибуты (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e8762-116">Attributes (Visual Basic)</span></span>](../../../language-reference/attributes.md)
- <span data-ttu-id="e8762-117">[Creating Custom Attributes (Visual Basic)](creating-custom-attributes.md) (Создание настраиваемых атрибутов (Visual Basic))</span><span class="sxs-lookup"><span data-stu-id="e8762-117">[Creating Custom Attributes (Visual Basic)](creating-custom-attributes.md)</span></span>
- <span data-ttu-id="e8762-118">[Accessing Attributes by Using Reflection (Visual Basic)](accessing-attributes-by-using-reflection.md) (Обращение к атрибутам с помощью отражения (Visual Basic))</span><span class="sxs-lookup"><span data-stu-id="e8762-118">[Accessing Attributes by Using Reflection (Visual Basic)](accessing-attributes-by-using-reflection.md)</span></span>
