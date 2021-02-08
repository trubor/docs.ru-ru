---
description: 'Дополнительные сведения о: BC30812: необязательные параметры должны указывать значение по умолчанию'
title: Для необязательных параметров должно быть задано значение по умолчанию
ms.date: 07/20/2015
f1_keywords:
- vbc30812
- bc30812
helpviewer_keywords:
- BC30812
ms.assetid: 5091a250-be66-413b-98a3-2a9974c4d600
ms.openlocfilehash: 1cbed1c0f1297ecacdae94d9234d18a3d268f487
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99795538"
---
# <a name="bc30812-optional-parameters-must-specify-a-default-value"></a><span data-ttu-id="1ffe5-103">BC30812: необязательные параметры должны указывать значение по умолчанию</span><span class="sxs-lookup"><span data-stu-id="1ffe5-103">BC30812: Optional parameters must specify a default value</span></span>

<span data-ttu-id="1ffe5-104">Необязательные параметры должны предоставлять значения по умолчанию, которые можно использовать, если вызывающая процедура не предоставляет параметр.</span><span class="sxs-lookup"><span data-stu-id="1ffe5-104">Optional parameters must provide default values that can be used if no parameter is supplied by a calling procedure.</span></span>

<span data-ttu-id="1ffe5-105">**Идентификатор ошибки:** BC30812</span><span class="sxs-lookup"><span data-stu-id="1ffe5-105">**Error ID:** BC30812</span></span>

## <a name="example"></a><span data-ttu-id="1ffe5-106">Пример</span><span class="sxs-lookup"><span data-stu-id="1ffe5-106">Example</span></span>

<span data-ttu-id="1ffe5-107">Следующий пример приводит к возникновению ошибки BC30812:</span><span class="sxs-lookup"><span data-stu-id="1ffe5-107">The following example generates BC30812:</span></span>

```vb
Sub Proc1(x As Integer, Optional y As String)
    Console.WriteLine("Default argument is: " & y)
End Sub
```

## <a name="to-correct-this-error"></a><span data-ttu-id="1ffe5-108">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="1ffe5-108">To correct this error</span></span>

<span data-ttu-id="1ffe5-109">Укажите значения по умолчанию для необязательных параметров:</span><span class="sxs-lookup"><span data-stu-id="1ffe5-109">Specify default values for optional parameters:</span></span>

```vb
Sub Proc1(x As Integer, Optional y As String = "Default Value")
    Console.WriteLine("Default argument is: " & y)
End Sub
```

## <a name="see-also"></a><span data-ttu-id="1ffe5-110">См. также</span><span class="sxs-lookup"><span data-stu-id="1ffe5-110">See also</span></span>

- [<span data-ttu-id="1ffe5-111">Необязательно</span><span class="sxs-lookup"><span data-stu-id="1ffe5-111">Optional</span></span>](../modifiers/optional.md)
