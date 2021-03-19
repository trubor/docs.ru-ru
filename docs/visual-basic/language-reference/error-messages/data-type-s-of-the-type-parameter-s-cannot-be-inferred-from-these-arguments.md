---
title: Типы данных параметров-типов не могут быть определены из этих аргументов
description: 'Дополнительные сведения: BC36647 и BC36644: типы данных параметров типа не могут выводиться из этих аргументов'
ms.date: 07/20/2015
f1_keywords:
- bc36644
- bc36647
- vbc36647
- vbc36644
helpviewer_keywords:
- BC36644
- BC36647
ms.assetid: 0e0050f2-2039-4311-b260-f0ebfde84189
ms.openlocfilehash: 26b4358dc2059aaff0a6a72d1489216c854f79a6
ms.sourcegitcommit: 1dbe25ff484a02025d5c34146e517c236f7161fb
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 03/19/2021
ms.locfileid: "104653677"
---
# <a name="bc36647-and-bc36644-data-types-of-the-type-parameters-cannot-be-inferred-from-these-arguments"></a><span data-ttu-id="afad5-103">BC36647 и BC36644: типы данных параметров типа не могут выводиться из этих аргументов</span><span class="sxs-lookup"><span data-stu-id="afad5-103">BC36647 and BC36644: Data type(s) of the type parameter(s) cannot be inferred from these arguments</span></span>

<span data-ttu-id="afad5-104">Типы данных параметров типа не могут выводиться из этих аргументов.</span><span class="sxs-lookup"><span data-stu-id="afad5-104">Data type(s) of the type parameter(s) cannot be inferred from these arguments.</span></span> <span data-ttu-id="afad5-105">Эту ошибку может исправить явное указание типов данных.</span><span class="sxs-lookup"><span data-stu-id="afad5-105">Specifying the data type(s) explicitly might correct this error.</span></span>

<span data-ttu-id="afad5-106">Эта ошибка возникает при неудачном разрешении перегрузки.</span><span class="sxs-lookup"><span data-stu-id="afad5-106">This error occurs when overload resolution has failed.</span></span> <span data-ttu-id="afad5-107">Ошибка появляется в виде сообщения, в котором указывается, почему была исключена определенная потенциальная перегрузка.</span><span class="sxs-lookup"><span data-stu-id="afad5-107">It occurs as a subordinate message that states why a particular overload candidate has been eliminated.</span></span> <span data-ttu-id="afad5-108">В сообщении об ошибке объясняется, что компилятор не может использовать определение типа для поиска типов данных для параметров типа.</span><span class="sxs-lookup"><span data-stu-id="afad5-108">The error message explains that the compiler cannot use type inference to find data types for the type parameters.</span></span>

> [!NOTE]
> <span data-ttu-id="afad5-109">Когда указание аргументов является обязательным (например, в операторах выражений запросов), это сообщение об ошибке появляется без второй фразы.</span><span class="sxs-lookup"><span data-stu-id="afad5-109">When specifying arguments is not an option (for example, for query operators in query expressions), the error message appears without the second sentence.</span></span>

<span data-ttu-id="afad5-110">Эта ошибка демонстрируется в приведенном ниже коде.</span><span class="sxs-lookup"><span data-stu-id="afad5-110">The following code demonstrates the error.</span></span>

```vb
Module Module1

    Sub Main()

        '' Not Valid.
        'OverloadedGenericMethod("Hello", "World")

    End Sub

    Sub OverloadedGenericMethod(Of T)(ByVal x As String,
                                      ByVal y As InterfaceExample(Of T))
    End Sub

    Sub OverloadedGenericMethod(Of T, R)(ByVal x As T,
                                         ByVal y As InterfaceExample(Of R))
    End Sub

End Module

Interface InterfaceExample(Of T)
End Interface
```

<span data-ttu-id="afad5-111">**Идентификатор ошибки:** BC36647 и BC36644</span><span class="sxs-lookup"><span data-stu-id="afad5-111">**Error ID:** BC36647 and BC36644</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="afad5-112">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="afad5-112">To correct this error</span></span>

<span data-ttu-id="afad5-113">Попробуйте указать тип данных для параметра или параметров типа, вместо того чтобы полагаться на определение типа.</span><span class="sxs-lookup"><span data-stu-id="afad5-113">You may be able to specify a data type for the type parameter or parameters instead of relying on type inference.</span></span>

## <a name="see-also"></a><span data-ttu-id="afad5-114">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="afad5-114">See also</span></span>

- [<span data-ttu-id="afad5-115">Неявное преобразование делегата</span><span class="sxs-lookup"><span data-stu-id="afad5-115">Relaxed Delegate Conversion</span></span>](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
- [<span data-ttu-id="afad5-116">Generic Procedures in Visual Basic</span><span class="sxs-lookup"><span data-stu-id="afad5-116">Generic Procedures in Visual Basic</span></span>](../../programming-guide/language-features/data-types/generic-procedures.md)
- [<span data-ttu-id="afad5-117">Преобразование типов в Visual Basic</span><span class="sxs-lookup"><span data-stu-id="afad5-117">Type Conversions in Visual Basic</span></span>](../../programming-guide/language-features/data-types/type-conversions.md)
