---
description: Дополнительные сведения о ковариации и контрвариация (Visual Basic)
title: Ковариация и контрвариация
ms.date: 07/20/2015
ms.assetid: 59224c46-9931-466b-8c6e-3648c3e609c6
ms.openlocfilehash: 6569b2c6c4790a5fcf53a9991543286ad6c4314c
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100485254"
---
# <a name="covariance-and-contravariance-visual-basic"></a><span data-ttu-id="43843-103">Ковариация и контрвариантность (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="43843-103">Covariance and Contravariance (Visual Basic)</span></span>

<span data-ttu-id="43843-104">В Visual Basic ковариация и контрвариантность позволяют использовать неявное преобразование ссылок для типов массивов и делегатов, а также для аргументов универсального типа.</span><span class="sxs-lookup"><span data-stu-id="43843-104">In Visual Basic, covariance and contravariance enable implicit reference conversion for array types, delegate types, and generic type arguments.</span></span> <span data-ttu-id="43843-105">Ковариация сохраняет совместимость присваивания, а при контрвариантности присваивание начинает работать противоположным образом.</span><span class="sxs-lookup"><span data-stu-id="43843-105">Covariance preserves assignment compatibility and contravariance reverses it.</span></span>

<span data-ttu-id="43843-106">Следующий код показывает разницу между совместимостью присваивания, ковариацией и контрвариантностью.</span><span class="sxs-lookup"><span data-stu-id="43843-106">The following code demonstrates the difference between assignment compatibility, covariance, and contravariance.</span></span>

```vb
' Assignment compatibility.
Dim str As String = "test"
' An object of a more derived type is assigned to an object of a less derived type.
Dim obj As Object = str

' Covariance.
Dim strings As IEnumerable(Of String) = New List(Of String)()
' An object that is instantiated with a more derived type argument
' is assigned to an object instantiated with a less derived type argument.
' Assignment compatibility is preserved.
Dim objects As IEnumerable(Of Object) = strings

' Contravariance.
' Assume that there is the following method in the class:
' Shared Sub SetObject(ByVal o As Object)
' End Sub
Dim actObject As Action(Of Object) = AddressOf SetObject

' An object that is instantiated with a less derived type argument
' is assigned to an object instantiated with a more derived type argument.
' Assignment compatibility is reversed.
Dim actString As Action(Of String) = actObject
```

<span data-ttu-id="43843-107">Ковариация для массивов позволяет неявно преобразовать массив более производного типа в массив менее производного типа.</span><span class="sxs-lookup"><span data-stu-id="43843-107">Covariance for arrays enables implicit conversion of an array of a more derived type to an array of a less derived type.</span></span> <span data-ttu-id="43843-108">Но эта операция не является типобезопасной, как показано в следующем примере кода.</span><span class="sxs-lookup"><span data-stu-id="43843-108">But this operation is not type safe, as shown in the following code example.</span></span>

```vb
Dim array() As Object = New String(10) {}
' The following statement produces a run-time exception.
' array(0) = 10
```

<span data-ttu-id="43843-109">Поддержка ковариации и контрвариантности для групп методов позволяет сопоставить сигнатуры методов с типами делегатов.</span><span class="sxs-lookup"><span data-stu-id="43843-109">Covariance and contravariance support for method groups allows for matching method signatures with delegate types.</span></span> <span data-ttu-id="43843-110">За счет этого вы можете назначать делегатам не только методы с совпадающими сигнатурами, но и методы, которые возвращают более производные типы (ковариация) или принимают параметры с менее производными типами (контрвариантность), чем задает тип делегата.</span><span class="sxs-lookup"><span data-stu-id="43843-110">This enables you to assign to delegates not only methods that have matching signatures, but also methods that return more derived types (covariance) or that accept parameters that have less derived types (contravariance) than that specified by the delegate type.</span></span> <span data-ttu-id="43843-111">Дополнительные сведения см. в разделах [Вариативность в делегатах (Visual Basic)](variance-in-delegates.md) и [Использование вариативности в делегатах (Visual Basic)](using-variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="43843-111">For more information, see [Variance in Delegates (Visual Basic)](variance-in-delegates.md) and [Using Variance in Delegates (Visual Basic)](using-variance-in-delegates.md).</span></span>

<span data-ttu-id="43843-112">В следующем примере кода демонстрируется поддержка ковариации и контрвариантности для групп методов.</span><span class="sxs-lookup"><span data-stu-id="43843-112">The following code example shows covariance and contravariance support for method groups.</span></span>

```vb
Shared Function GetObject() As Object
    Return Nothing
End Function

Shared Sub SetObject(ByVal obj As Object)
End Sub

Shared Function GetString() As String
    Return ""
End Function

Shared Sub SetString(ByVal str As String)

End Sub

Shared Sub Test()
    ' Covariance. A delegate specifies a return type as object,
    ' but you can assign a method that returns a string.
    Dim del As Func(Of Object) = AddressOf GetString

    ' Contravariance. A delegate specifies a parameter type as string,
    ' but you can assign a method that takes an object.
    Dim del2 As Action(Of String) = AddressOf SetObject
End Sub
```

<span data-ttu-id="43843-113">В платформа .NET Framework 4 или более поздней версии Visual Basic поддерживает ковариации и контрвариация в универсальных интерфейсах и делегатах и позволяет неявное преобразование параметров универсального типа.</span><span class="sxs-lookup"><span data-stu-id="43843-113">In .NET Framework 4 or later, Visual Basic supports covariance and contravariance in generic interfaces and delegates and allows for implicit conversion of generic type parameters.</span></span> <span data-ttu-id="43843-114">Дополнительные сведения см. в разделах [Вариативность в универсальных интерфейсах (Visual Basic)](variance-in-generic-interfaces.md) и [Вариативность в делегатах (Visual Basic)](variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="43843-114">For more information, see [Variance in Generic Interfaces (Visual Basic)](variance-in-generic-interfaces.md) and [Variance in Delegates (Visual Basic)](variance-in-delegates.md).</span></span>

<span data-ttu-id="43843-115">В следующем примере кода показано неявное преобразование ссылок для универсальных интерфейсов.</span><span class="sxs-lookup"><span data-stu-id="43843-115">The following code example shows implicit reference conversion for generic interfaces.</span></span>

```vb
Dim strings As IEnumerable(Of String) = New List(Of String)
Dim objects As IEnumerable(Of Object) = strings
```

<span data-ttu-id="43843-116">Универсальный интерфейс или делегат называется *вариантным*, если его универсальные параметры объявлены ковариантными или контрвариантными.</span><span class="sxs-lookup"><span data-stu-id="43843-116">A generic interface or delegate is called *variant* if its generic parameters are declared covariant or contravariant.</span></span> <span data-ttu-id="43843-117">Visual Basic позволяет вам создавать свои собственные вариантные интерфейсы и делегаты.</span><span class="sxs-lookup"><span data-stu-id="43843-117">Visual Basic enables you to create your own variant interfaces and delegates.</span></span> <span data-ttu-id="43843-118">Дополнительные сведения см. в разделах [Создание вариативных универсальных интерфейсов (Visual Basic)](creating-variant-generic-interfaces.md) и [Вариативность в делегатах (Visual Basic)](variance-in-delegates.md).</span><span class="sxs-lookup"><span data-stu-id="43843-118">For more information, see [Creating Variant Generic Interfaces (Visual Basic)](creating-variant-generic-interfaces.md) and [Variance in Delegates (Visual Basic)](variance-in-delegates.md).</span></span>

## <a name="related-topics"></a><span data-ttu-id="43843-119">См. также</span><span class="sxs-lookup"><span data-stu-id="43843-119">Related Topics</span></span>

|<span data-ttu-id="43843-120">Заголовок</span><span class="sxs-lookup"><span data-stu-id="43843-120">Title</span></span>|<span data-ttu-id="43843-121">Описание</span><span class="sxs-lookup"><span data-stu-id="43843-121">Description</span></span>|
|-----------|-----------------|
|[<span data-ttu-id="43843-122">Вариативность в универсальных интерфейсах (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="43843-122">Variance in Generic Interfaces (Visual Basic)</span></span>](variance-in-generic-interfaces.md)|<span data-ttu-id="43843-123">В этом разделе описываются ковариация и контрвариация в универсальных интерфейсах, а также представлен список вариативных универсальных интерфейсов платформы .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="43843-123">Discusses covariance and contravariance in generic interfaces and provides a list of variant generic interfaces in the .NET Framework.</span></span>|
|[<span data-ttu-id="43843-124">Создание вариативных универсальных интерфейсов (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="43843-124">Creating Variant Generic Interfaces (Visual Basic)</span></span>](creating-variant-generic-interfaces.md)|<span data-ttu-id="43843-125">Узнайте, как создавать ваши собственные вариантные интерфейсы.</span><span class="sxs-lookup"><span data-stu-id="43843-125">Shows how to create custom variant interfaces.</span></span>|
|[<span data-ttu-id="43843-126">Использование вариативности в интерфейсах для универсальных коллекций (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="43843-126">Using Variance in Interfaces for Generic Collections (Visual Basic)</span></span>](using-variance-in-interfaces-for-generic-collections.md)|<span data-ttu-id="43843-127">Узнайте, как использовать поддержку ковариации и контрвариантности в интерфейсах <xref:System.Collections.Generic.IEnumerable%601> и <xref:System.IComparable%601> для многократного использования кода.</span><span class="sxs-lookup"><span data-stu-id="43843-127">Shows how covariance and contravariance support in the <xref:System.Collections.Generic.IEnumerable%601> and <xref:System.IComparable%601> interfaces can help you reuse code.</span></span>|
|[<span data-ttu-id="43843-128">Вариативность в делегатах (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="43843-128">Variance in Delegates (Visual Basic)</span></span>](variance-in-delegates.md)|<span data-ttu-id="43843-129">Раздел описывает ковариацию и контрвариантность в универсальных и неуниверсальных делегатах, а также приводит список вариантных универсальных делегатов в платформе .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="43843-129">Discusses covariance and contravariance in generic and non-generic delegates and provides a list of variant generic delegates in the .NET Framework.</span></span>|
|[<span data-ttu-id="43843-130">Использование вариативности в делегатах (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="43843-130">Using Variance in Delegates (Visual Basic)</span></span>](using-variance-in-delegates.md)|<span data-ttu-id="43843-131">Узнайте, как использовать поддержку ковариации и контрвариантности в неуниверсальных делегатах для сопоставления сигнатур методов с типами делегатов.</span><span class="sxs-lookup"><span data-stu-id="43843-131">Shows how to use covariance and contravariance support in non-generic delegates to match method signatures with delegate types.</span></span>|
|[<span data-ttu-id="43843-132">Использование вариативности в универсальных методах-делегатах Func и Action (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="43843-132">Using Variance for Func and Action Generic Delegates (Visual Basic)</span></span>](using-variance-for-func-and-action-generic-delegates.md)|<span data-ttu-id="43843-133">Узнайте, как использовать поддержку ковариации и контрвариантности в делегатах `Func` и `Action` для многократного использования кода.</span><span class="sxs-lookup"><span data-stu-id="43843-133">Shows how covariance and contravariance support in the `Func` and `Action` delegates can help you reuse code.</span></span>|
