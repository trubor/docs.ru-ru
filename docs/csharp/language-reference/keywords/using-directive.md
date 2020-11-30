---
description: Справочник по C#. Директива using
title: Справочник по C#. Директива using
ms.date: 07/20/2015
helpviewer_keywords:
- using directive [C#]
ms.assetid: b42b8e61-5e7e-439c-bb71-370094b44ae8
ms.openlocfilehash: f22a67348b19b8c97513ca685b2b10b34b1fd6fd
ms.sourcegitcommit: 0802ac583585110022beb6af8ea0b39188b77c43
ms.translationtype: HT
ms.contentlocale: ru-RU
ms.lasthandoff: 11/26/2020
ms.locfileid: "89141950"
---
# <a name="using-directive-c-reference"></a><span data-ttu-id="50c31-103">Директива using (справочник по C#)</span><span class="sxs-lookup"><span data-stu-id="50c31-103">using directive (C# Reference)</span></span>

<span data-ttu-id="50c31-104">Директива `using` используется в следующих трех целях.</span><span class="sxs-lookup"><span data-stu-id="50c31-104">The `using` directive has three uses:</span></span>

- <span data-ttu-id="50c31-105">Для разрешения использования типов в пространстве имен, чтобы не нужно было квалифицировать использование типа в этом пространстве имен:</span><span class="sxs-lookup"><span data-stu-id="50c31-105">To allow the use of types in a namespace so that you do not have to qualify the use of a type in that namespace:</span></span>

    ```csharp
    using System.Text;
    ```

- <span data-ttu-id="50c31-106">Для разрешения доступа к статическим членам и вложенным типам без необходимости квалифицировать доступ с помощью имени типа.</span><span class="sxs-lookup"><span data-stu-id="50c31-106">To allow you to access static members and nested types of a type without having to qualify the access with the type name.</span></span>

    ```csharp
    using static System.Math;
    ```

    <span data-ttu-id="50c31-107">Дополнительные сведения см. в разделе [Директива using static](using-static.md).</span><span class="sxs-lookup"><span data-stu-id="50c31-107">For more information, see the [using static directive](using-static.md).</span></span>

- <span data-ttu-id="50c31-108">Чтобы создать псевдоним для пространства имен или типа.</span><span class="sxs-lookup"><span data-stu-id="50c31-108">To create an alias for a namespace or a type.</span></span> <span data-ttu-id="50c31-109">Это называется *директивой using static*.</span><span class="sxs-lookup"><span data-stu-id="50c31-109">This is called a *using alias directive*.</span></span>

    ```csharp
    using Project = PC.MyCompany.Project;
    ```

<span data-ttu-id="50c31-110">Ключевое слово `using` также используется для создания *операторов using*, которые помогают обеспечить правильную обработку объектов <xref:System.IDisposable>, таких как файлы и шрифты.</span><span class="sxs-lookup"><span data-stu-id="50c31-110">The `using` keyword is also used to create *using statements*, which help ensure that <xref:System.IDisposable> objects such as files and fonts are handled correctly.</span></span> <span data-ttu-id="50c31-111">Дополнительные сведения см. в разделе [Оператор using](using-statement.md).</span><span class="sxs-lookup"><span data-stu-id="50c31-111">See [using Statement](using-statement.md) for more information.</span></span>

## <a name="using-static-type"></a><span data-ttu-id="50c31-112">Использование статического типа</span><span class="sxs-lookup"><span data-stu-id="50c31-112">Using static type</span></span>

<span data-ttu-id="50c31-113">Вы можете обращаться к статическим членам типа без необходимости квалификации доступа с помощью имени типа:</span><span class="sxs-lookup"><span data-stu-id="50c31-113">You can access static members of a type without having to qualify the access with the type name:</span></span>

```csharp
using static System.Console;
using static System.Math;
class Program
{
    static void Main()
    {
        WriteLine(Sqrt(3*3 + 4*4));
    }
}
```

## <a name="remarks"></a><span data-ttu-id="50c31-114">Комментарии</span><span class="sxs-lookup"><span data-stu-id="50c31-114">Remarks</span></span>

<span data-ttu-id="50c31-115">Область директивы `using` ограничена файлом, в котором она находится.</span><span class="sxs-lookup"><span data-stu-id="50c31-115">The scope of a `using` directive is limited to the file in which it appears.</span></span>

<span data-ttu-id="50c31-116">Директива `using` может отображаться:</span><span class="sxs-lookup"><span data-stu-id="50c31-116">The `using` directive can appear:</span></span>

- <span data-ttu-id="50c31-117">В начале файла исходного кода перед определением пространств имен и типов.</span><span class="sxs-lookup"><span data-stu-id="50c31-117">At the beginning of a source code file, before any namespace or type definitions.</span></span>
- <span data-ttu-id="50c31-118">В пространстве имен перед любыми пространствами имен и типами, объявленными в этом пространстве имен.</span><span class="sxs-lookup"><span data-stu-id="50c31-118">In any namespace, but before any namespace or types declared in this namespace.</span></span>

<span data-ttu-id="50c31-119">В противном случае возникнет ошибка компилятора [CS1529](../../misc/cs1529.md).</span><span class="sxs-lookup"><span data-stu-id="50c31-119">Otherwise, compiler error [CS1529](../../misc/cs1529.md) is generated.</span></span>

<span data-ttu-id="50c31-120">Создайте директиву псевдонима `using`, чтобы упростить квалификацию идентификатора для пространства имен или типа.</span><span class="sxs-lookup"><span data-stu-id="50c31-120">Create a `using` alias directive to make it easier to qualify an identifier to a namespace or type.</span></span> <span data-ttu-id="50c31-121">Во всех директивах `using` следует использовать полное пространство имен или тип независимо от того, какие директивы `using` находятся перед ней.</span><span class="sxs-lookup"><span data-stu-id="50c31-121">In any `using` directive, the fully-qualified namespace or type must be used regardless of the `using` directives that come before it.</span></span> <span data-ttu-id="50c31-122">В объявлении директивы `using` не может использоваться псевдоним `using`.</span><span class="sxs-lookup"><span data-stu-id="50c31-122">No `using` alias can be used in the declaration of a `using` directive.</span></span> <span data-ttu-id="50c31-123">Например, следующий код вызовет ошибку компиляции:</span><span class="sxs-lookup"><span data-stu-id="50c31-123">For example, the following generates a compiler error:</span></span>

```csharp
using s = System.Text;
using s.RegularExpressions; // Generates a compiler error.
```

<span data-ttu-id="50c31-124">Создайте директиву `using`, чтобы использовать типы в пространстве имен без необходимости указания этого пространства имен.</span><span class="sxs-lookup"><span data-stu-id="50c31-124">Create a `using` directive to use the types in a namespace without having to specify the namespace.</span></span> <span data-ttu-id="50c31-125">Директива `using` не предоставляет доступ к пространствам имен, вложенным в указанное пространство имен.</span><span class="sxs-lookup"><span data-stu-id="50c31-125">A `using` directive does not give you access to any namespaces that are nested in the namespace you specify.</span></span>

<span data-ttu-id="50c31-126">Пространства имен делятся на две категории: пользовательские и системные.</span><span class="sxs-lookup"><span data-stu-id="50c31-126">Namespaces come in two categories: user-defined and system-defined.</span></span> <span data-ttu-id="50c31-127">Пользовательские пространства имен задаются в вашем коде.</span><span class="sxs-lookup"><span data-stu-id="50c31-127">User-defined namespaces are namespaces defined in your code.</span></span> <span data-ttu-id="50c31-128">Список системных пространств имен см. в разделе [Браузер API .NET](../../../../api/index.md).</span><span class="sxs-lookup"><span data-stu-id="50c31-128">For a list of the system-defined namespaces, see [.NET API Browser](../../../../api/index.md).</span></span>

## <a name="example-1"></a><span data-ttu-id="50c31-129">Пример 1</span><span class="sxs-lookup"><span data-stu-id="50c31-129">Example 1</span></span>

<span data-ttu-id="50c31-130">В следующем примере показано, как задать и использовать псевдоним `using` для пространства имен.</span><span class="sxs-lookup"><span data-stu-id="50c31-130">The following example shows how to define and use a `using` alias for a namespace:</span></span>

[!code-csharp[csrefKeywordsNamespace#8](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace2.cs#8)]

<span data-ttu-id="50c31-131">Псевдоним using не может иметь открытый универсальный тип с правой стороны.</span><span class="sxs-lookup"><span data-stu-id="50c31-131">A using alias directive cannot have an open generic type on the right hand side.</span></span> <span data-ttu-id="50c31-132">Например, нельзя создать псевдоним using для `List<T>`, но можно создать его для `List<int>`.</span><span class="sxs-lookup"><span data-stu-id="50c31-132">For example, you cannot create a using alias for a `List<T>`, but you can create one for a `List<int>`.</span></span>

## <a name="example-2"></a><span data-ttu-id="50c31-133">Пример 2</span><span class="sxs-lookup"><span data-stu-id="50c31-133">Example 2</span></span>

<span data-ttu-id="50c31-134">В следующем примере показано, как задать директиву `using` и псевдоним `using` для класса.</span><span class="sxs-lookup"><span data-stu-id="50c31-134">The following example shows how to define a `using` directive and a `using` alias for a class:</span></span>

[!code-csharp[csrefKeywordsNamespace#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsNamespace/CS/csrefKeywordsNamespace2.cs#9)]

## <a name="c-language-specification"></a><span data-ttu-id="50c31-135">Спецификация языка C#</span><span class="sxs-lookup"><span data-stu-id="50c31-135">C# language specification</span></span>

<span data-ttu-id="50c31-136">Дополнительные сведения см. в разделе [Директивы using](~/_csharplang/spec/namespaces.md#using-directives) в статье [Спецификация языка C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="50c31-136">For more information, see [Using directives](~/_csharplang/spec/namespaces.md#using-directives) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="50c31-137">Спецификация языка является предписывающим источником информации о синтаксисе и использовании языка C#.</span><span class="sxs-lookup"><span data-stu-id="50c31-137">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="50c31-138">См. также</span><span class="sxs-lookup"><span data-stu-id="50c31-138">See also</span></span>

- [<span data-ttu-id="50c31-139">Справочник по C#</span><span class="sxs-lookup"><span data-stu-id="50c31-139">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="50c31-140">Руководство по программированию на C#</span><span class="sxs-lookup"><span data-stu-id="50c31-140">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="50c31-141">Использование пространств имен</span><span class="sxs-lookup"><span data-stu-id="50c31-141">Using Namespaces</span></span>](../../programming-guide/namespaces/using-namespaces.md)
- [<span data-ttu-id="50c31-142">Ключевые слова в C#</span><span class="sxs-lookup"><span data-stu-id="50c31-142">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="50c31-143">Пространства имен</span><span class="sxs-lookup"><span data-stu-id="50c31-143">Namespaces</span></span>](../../programming-guide/namespaces/index.md)
- [<span data-ttu-id="50c31-144">Оператор using</span><span class="sxs-lookup"><span data-stu-id="50c31-144">using Statement</span></span>](using-statement.md)
