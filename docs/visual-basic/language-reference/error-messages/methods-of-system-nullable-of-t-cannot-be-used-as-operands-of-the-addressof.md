---
description: 'Дополнительные сведения о: BC32126: методы "System. Nullable (Of T)" не могут использоваться в качестве операндов оператора "AddressOf".'
title: Методы System.Nullable(Of T) нельзя использовать в качестве операндов оператора AddressOf
ms.date: 07/20/2015
f1_keywords:
- vbc32126
- bc32126
helpviewer_keywords:
- BC32126
ms.assetid: 2325668b-e2ad-40ee-a1ec-30450236c20d
ms.openlocfilehash: 5ddf2f11bab3193423a3294a7f96afe68f0e5dce
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795798"
---
# <a name="bc32126-methods-of-systemnullableof-t-cannot-be-used-as-operands-of-the-addressof-operator"></a><span data-ttu-id="7207b-103">BC32126: методы "System. Nullable (Of T)" не могут использоваться в качестве операндов оператора "AddressOf"</span><span class="sxs-lookup"><span data-stu-id="7207b-103">BC32126: Methods of 'System.Nullable(Of T)' cannot be used as operands of the 'AddressOf' operator</span></span>

<span data-ttu-id="7207b-104">Оператор использует `AddressOf` оператор с операндом, представляющим процедуру <xref:System.Nullable%601> структуры.</span><span class="sxs-lookup"><span data-stu-id="7207b-104">A statement uses the `AddressOf` operator with an operand that represents a procedure of the <xref:System.Nullable%601> structure.</span></span>

 <span data-ttu-id="7207b-105">**Идентификатор ошибки:** BC32126</span><span class="sxs-lookup"><span data-stu-id="7207b-105">**Error ID:** BC32126</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="7207b-106">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="7207b-106">To correct this error</span></span>

- <span data-ttu-id="7207b-107">Замените имя процедуры в `AddressOf` предложении операндом, который не является членом <xref:System.Nullable%601> .</span><span class="sxs-lookup"><span data-stu-id="7207b-107">Replace the procedure name in the `AddressOf` clause with an operand that is not a member of <xref:System.Nullable%601>.</span></span>

- <span data-ttu-id="7207b-108">Напишите класс, который заключает в оболочку метод <xref:System.Nullable%601> , который требуется использовать.</span><span class="sxs-lookup"><span data-stu-id="7207b-108">Write a class that wraps the method of <xref:System.Nullable%601> that you want to use.</span></span> <span data-ttu-id="7207b-109">В следующем примере `NullableWrapper` класс определяет новый метод с именем `GetValueOrDefault` .</span><span class="sxs-lookup"><span data-stu-id="7207b-109">In the following example, the `NullableWrapper` class defines a new method named `GetValueOrDefault`.</span></span> <span data-ttu-id="7207b-110">Поскольку этот новый метод не является членом <xref:System.Nullable%601> , он может быть применен к `nullInstance` экземпляру типа, допускающему значение null, для формирования аргумента для `AddressOf` .</span><span class="sxs-lookup"><span data-stu-id="7207b-110">Because this new method is not a member of <xref:System.Nullable%601>, it can be applied to `nullInstance`, an instance of a nullable type, to form an argument for `AddressOf`.</span></span>

```vb
Module Module1

    Delegate Function Deleg() As Integer

    Sub Main()
        Dim nullInstance As New Nullable(Of Integer)(1)

        Dim del As Deleg

        ' GetValueOrDefault is a method of the Nullable generic
        ' type. It cannot be used as an operand of AddressOf.
        ' del = AddressOf nullInstance.GetValueOrDefault

        ' The following line uses the GetValueOrDefault method
        ' defined in the NullableWrapper class.
        del = AddressOf (New NullableWrapper(
            Of Integer)(nullInstance)).GetValueOrDefault

        Console.WriteLine(del.Invoke())
    End Sub

    Class NullableWrapper(Of T As Structure)
        Private m_Value As Nullable(Of T)

        Sub New(ByVal Value As Nullable(Of T))
            m_Value = Value
        End Sub

        Public Function GetValueOrDefault() As T
            Return m_Value.Value
        End Function
    End Class
End Module
```

## <a name="see-also"></a><span data-ttu-id="7207b-111">См. также</span><span class="sxs-lookup"><span data-stu-id="7207b-111">See also</span></span>

- <xref:System.Nullable%601>
- [<span data-ttu-id="7207b-112">Оператор AddressOf</span><span class="sxs-lookup"><span data-stu-id="7207b-112">AddressOf Operator</span></span>](../operators/addressof-operator.md)
- [<span data-ttu-id="7207b-113">Типы значений, допускающие значение NULL</span><span class="sxs-lookup"><span data-stu-id="7207b-113">Nullable Value Types</span></span>](../../programming-guide/language-features/data-types/nullable-value-types.md)
- [<span data-ttu-id="7207b-114">Generic Types in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7207b-114">Generic Types in Visual Basic</span></span>](../../programming-guide/language-features/data-types/generic-types.md)
