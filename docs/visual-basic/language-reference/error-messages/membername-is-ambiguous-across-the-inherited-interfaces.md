---
description: 'Дополнительные сведения о: BC30685: " <membername> " является неоднозначным по отношению к унаследованным интерфейсам " <interfacename1> " и "<interfacename2>'
title: Член <membername> является неоднозначным в наследуемых интерфейсах <interfacename1> и <interfacename2>
ms.date: 07/20/2015
f1_keywords:
- vbc30685
- bc30685
helpviewer_keywords:
- BC30685
ms.assetid: 756add7a-23d5-4b4f-a48d-8297d6459c73
ms.openlocfilehash: 8d114755c4456c7e846c2e9570481abfd5d13bbf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795837"
---
# <a name="bc30685-membername-is-ambiguous-across-the-inherited-interfaces-interfacename1-and-interfacename2"></a><span data-ttu-id="eee13-103">BC30685: " \<membername> " является неоднозначным по отношению к унаследованным интерфейсам " \<interfacename1> " и " \<interfacename2> "</span><span class="sxs-lookup"><span data-stu-id="eee13-103">BC30685: '\<membername>' is ambiguous across the inherited interfaces '\<interfacename1>' and '\<interfacename2>'</span></span>

<span data-ttu-id="eee13-104">Интерфейс наследует два или более членов с одинаковым именем из нескольких интерфейсов.</span><span class="sxs-lookup"><span data-stu-id="eee13-104">The interface inherits two or more members with the same name from multiple interfaces.</span></span>

 <span data-ttu-id="eee13-105">**Идентификатор ошибки:** BC30685</span><span class="sxs-lookup"><span data-stu-id="eee13-105">**Error ID:** BC30685</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="eee13-106">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="eee13-106">To correct this error</span></span>

- <span data-ttu-id="eee13-107">Приведите значение к базовому интерфейсу, который необходимо использовать; Например:</span><span class="sxs-lookup"><span data-stu-id="eee13-107">Cast the value to the base interface that you want to use; for example:</span></span>

    ```vb
    Interface Left
        Sub MySub()
    End Interface

    Interface Right
        Sub MySub()
    End Interface

    Interface LeftRight
        Inherits Left, Right
    End Interface

    Module test
        Sub Main()
            Dim x As LeftRight
            ' x.MySub()  'x is ambiguous.
            CType(x, Left).MySub() ' Cast to base type.
            CType(x, Right).MySub() ' Call the other base type.
        End Sub
    End Module
    ```

## <a name="see-also"></a><span data-ttu-id="eee13-108">См. также</span><span class="sxs-lookup"><span data-stu-id="eee13-108">See also</span></span>

- [<span data-ttu-id="eee13-109">Интерфейсы</span><span class="sxs-lookup"><span data-stu-id="eee13-109">Interfaces</span></span>](../../programming-guide/language-features/interfaces/index.md)
