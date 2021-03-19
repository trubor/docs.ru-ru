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
# <a name="bc36647-and-bc36644-data-types-of-the-type-parameters-cannot-be-inferred-from-these-arguments"></a>BC36647 и BC36644: типы данных параметров типа не могут выводиться из этих аргументов

Типы данных параметров типа не могут выводиться из этих аргументов. Эту ошибку может исправить явное указание типов данных.

Эта ошибка возникает при неудачном разрешении перегрузки. Ошибка появляется в виде сообщения, в котором указывается, почему была исключена определенная потенциальная перегрузка. В сообщении об ошибке объясняется, что компилятор не может использовать определение типа для поиска типов данных для параметров типа.

> [!NOTE]
> Когда указание аргументов является обязательным (например, в операторах выражений запросов), это сообщение об ошибке появляется без второй фразы.

Эта ошибка демонстрируется в приведенном ниже коде.

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

**Идентификатор ошибки:** BC36647 и BC36644

## <a name="to-correct-this-error"></a>Исправление ошибки

Попробуйте указать тип данных для параметра или параметров типа, вместо того чтобы полагаться на определение типа.

## <a name="see-also"></a>См. также раздел

- [Неявное преобразование делегата](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
- [Generic Procedures in Visual Basic](../../programming-guide/language-features/data-types/generic-procedures.md)
- [Преобразование типов в Visual Basic](../../programming-guide/language-features/data-types/type-conversions.md)
