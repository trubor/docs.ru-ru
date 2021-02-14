---
description: 'Дополнительные сведения: Определение анонимного типа (Visual Basic)'
title: Определение анонимного типа
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous types [Visual Basic], type definition
ms.assetid: 7a8a0ddc-55ba-4d67-869e-87a84d938bac
ms.openlocfilehash: 2e3f847f5f844e3ed6e036c26efc330a237d193f
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100436920"
---
# <a name="anonymous-type-definition-visual-basic"></a><span data-ttu-id="92468-103">Определение анонимного типа (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="92468-103">Anonymous Type Definition (Visual Basic)</span></span>

<span data-ttu-id="92468-104">В ответ на объявление экземпляра анонимного типа компилятор создает новое определение класса, которое содержит указанные свойства для типа.</span><span class="sxs-lookup"><span data-stu-id="92468-104">In response to the declaration of an instance of an anonymous type, the compiler creates a new class definition that contains the specified properties for the type.</span></span>

## <a name="compiler-generated-code"></a><span data-ttu-id="92468-105">Код Compiler-Generated</span><span class="sxs-lookup"><span data-stu-id="92468-105">Compiler-Generated Code</span></span>

<span data-ttu-id="92468-106">Для следующего определения `product` компилятор создает новое определение класса, которое содержит свойства `Name` , `Price` и `OnHand` .</span><span class="sxs-lookup"><span data-stu-id="92468-106">For the following definition of `product`, the compiler creates a new class definition that contains properties `Name`, `Price`, and `OnHand`.</span></span>

[!code-vb[VbVbalrAnonymousTypes#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#25)]

<span data-ttu-id="92468-107">Определение класса содержит определения свойств, аналогичные приведенным ниже.</span><span class="sxs-lookup"><span data-stu-id="92468-107">The class definition contains property definitions similar to the following.</span></span> <span data-ttu-id="92468-108">Обратите внимание, что `Set` для ключевых свойств отсутствует метод.</span><span class="sxs-lookup"><span data-stu-id="92468-108">Notice that there is no `Set` method for the key properties.</span></span> <span data-ttu-id="92468-109">Значения ключевых свойств доступны только для чтения.</span><span class="sxs-lookup"><span data-stu-id="92468-109">The values of key properties are read-only.</span></span>

```vb
Public Class $Anonymous1
    Private _name As String
    Private _price As Double
    Private _onHand As Integer
     Public ReadOnly Property Name() As String
        Get
            Return _name
        End Get
    End Property

    Public ReadOnly Property Price() As Double
        Get
            Return _price
        End Get
    End Property

    Public Property OnHand() As Integer
        Get
            Return _onHand
        End Get
        Set(ByVal Value As Integer)
            _onHand = Value
        End Set
    End Property

End Class
```

<span data-ttu-id="92468-110">Кроме того, анонимные определения типов содержат конструктор без параметров.</span><span class="sxs-lookup"><span data-stu-id="92468-110">In addition, anonymous type definitions contain a parameterless constructor.</span></span> <span data-ttu-id="92468-111">Конструкторы, требующие параметров, не разрешены.</span><span class="sxs-lookup"><span data-stu-id="92468-111">Constructors that require parameters are not permitted.</span></span>

<span data-ttu-id="92468-112">Если объявление анонимного типа содержит по крайней мере одно ключевое свойство, определение типа переопределяет три члена, наследуемые от <xref:System.Object> : <xref:System.Object.Equals%2A> , <xref:System.Object.GetHashCode%2A> и <xref:System.Object.ToString%2A> .</span><span class="sxs-lookup"><span data-stu-id="92468-112">If an anonymous type declaration contains at least one key property, the type definition overrides three members inherited from <xref:System.Object>: <xref:System.Object.Equals%2A>, <xref:System.Object.GetHashCode%2A>, and <xref:System.Object.ToString%2A>.</span></span> <span data-ttu-id="92468-113">Если ключевые свойства не объявлены, <xref:System.Object.ToString%2A> то переопределяется только.</span><span class="sxs-lookup"><span data-stu-id="92468-113">If no key properties are declared, only <xref:System.Object.ToString%2A> is overridden.</span></span> <span data-ttu-id="92468-114">Переопределения предоставляют следующие функциональные возможности:</span><span class="sxs-lookup"><span data-stu-id="92468-114">The overrides provide the following functionality:</span></span>

- <span data-ttu-id="92468-115">`Equals` Возвращает `True` значение, если два экземпляра анонимных типов являются одним и тем же экземпляром, или если они отвечают следующим условиям:</span><span class="sxs-lookup"><span data-stu-id="92468-115">`Equals` returns `True` if two anonymous type instances are the same instance, or if they meet the following conditions:</span></span>

  - <span data-ttu-id="92468-116">Они имеют одинаковое число свойств.</span><span class="sxs-lookup"><span data-stu-id="92468-116">They have the same number of properties.</span></span>

  - <span data-ttu-id="92468-117">Свойства объявляются в том же порядке с одинаковыми именами и теми же выводимыми типами.</span><span class="sxs-lookup"><span data-stu-id="92468-117">The properties are declared in the same order, with the same names and the same inferred types.</span></span> <span data-ttu-id="92468-118">При сравнении имен регистр не учитывается.</span><span class="sxs-lookup"><span data-stu-id="92468-118">Name comparisons are not case-sensitive.</span></span>

  - <span data-ttu-id="92468-119">По крайней мере одно из свойств является ключевым свойством, а `Key` ключевое слово применяется к тем же свойствам.</span><span class="sxs-lookup"><span data-stu-id="92468-119">At least one of the properties is a key property, and the `Key` keyword is applied to the same properties.</span></span>

  - <span data-ttu-id="92468-120">Сравнение каждой соответствующей пары ключевых свойств возвращает `True` .</span><span class="sxs-lookup"><span data-stu-id="92468-120">Comparison of each corresponding pair of key properties returns `True`.</span></span>

    <span data-ttu-id="92468-121">Например, в следующих примерах функция `Equals` возвращает `True` только для `employee01` и `employee08` .</span><span class="sxs-lookup"><span data-stu-id="92468-121">For example, in the following examples, `Equals` returns `True` only for `employee01` and `employee08`.</span></span> <span data-ttu-id="92468-122">Комментарий перед каждой строкой указывает причину, по которой новый экземпляр не соответствует `employee01` .</span><span class="sxs-lookup"><span data-stu-id="92468-122">The comment before each line specifies the reason why the new instance does not match `employee01`.</span></span>

    [!code-vb[VbVbalrAnonymousTypes#24](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#24)]

- <span data-ttu-id="92468-123">`GetHashcode` предоставляет соответствующим образом уникальный алгоритм GetHashCode.</span><span class="sxs-lookup"><span data-stu-id="92468-123">`GetHashcode` provides an appropriately unique GetHashCode algorithm.</span></span> <span data-ttu-id="92468-124">Алгоритм использует только ключевые свойства для вычисления хэш-кода.</span><span class="sxs-lookup"><span data-stu-id="92468-124">The algorithm uses only the key properties to compute the hash code.</span></span>

- <span data-ttu-id="92468-125">`ToString` Возвращает строку сцепленных значений свойств, как показано в следующем примере.</span><span class="sxs-lookup"><span data-stu-id="92468-125">`ToString` returns a string of concatenated property values, as shown in the following example.</span></span> <span data-ttu-id="92468-126">Включены ключевые и неключевые свойства.</span><span class="sxs-lookup"><span data-stu-id="92468-126">Both key and non-key properties are included.</span></span>

  [!code-vb[VbVbalrAnonymousTypes#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrAnonymousTypes/VB/Class2.vb#29)]

<span data-ttu-id="92468-127">Явно именованные свойства анонимного типа не могут конфликтовать с этими созданными методами.</span><span class="sxs-lookup"><span data-stu-id="92468-127">Explicitly named properties of an anonymous type cannot conflict with these generated methods.</span></span> <span data-ttu-id="92468-128">То есть нельзя использовать `.Equals` , `.GetHashCode` или `.ToString` для именования свойства.</span><span class="sxs-lookup"><span data-stu-id="92468-128">That is, you cannot use `.Equals`, `.GetHashCode`, or `.ToString` to name a property.</span></span>

<span data-ttu-id="92468-129">Определения анонимных типов, включающие по крайней мере одно ключевое свойство, также реализуют <xref:System.IEquatable%601?displayProperty=nameWithType> интерфейс, где `T` — это тип анонимного типа.</span><span class="sxs-lookup"><span data-stu-id="92468-129">Anonymous type definitions that include at least one key property also implement the <xref:System.IEquatable%601?displayProperty=nameWithType> interface, where `T` is the type of the anonymous type.</span></span>

> [!NOTE]
> <span data-ttu-id="92468-130">Объявления анонимного типа создают один и тот же анонимный тип только в том случае, если они встречаются в одной сборке, их свойства имеют одинаковые имена и те же выводимые типы, свойства объявляются в том же порядке, а те же свойства помечаются как ключевые свойства.</span><span class="sxs-lookup"><span data-stu-id="92468-130">Anonymous type declarations create the same anonymous type only if they occur in the same assembly, their properties have the same names and the same inferred types, the properties are declared in the same order, and the same properties are marked as key properties.</span></span>

## <a name="see-also"></a><span data-ttu-id="92468-131">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="92468-131">See also</span></span>

- [<span data-ttu-id="92468-132">Анонимные типы</span><span class="sxs-lookup"><span data-stu-id="92468-132">Anonymous Types</span></span>](anonymous-types.md)
- [<span data-ttu-id="92468-133">Практическое руководство. Выведение имен свойств и типов в объявлениях анонимных типов</span><span class="sxs-lookup"><span data-stu-id="92468-133">How to: Infer Property Names and Types in Anonymous Type Declarations</span></span>](how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)
