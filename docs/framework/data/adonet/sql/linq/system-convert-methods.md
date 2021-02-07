---
description: Дополнительные сведения о методах System. Convert
title: Методы System.Convert
ms.date: 03/30/2017
ms.assetid: 3ca6c5b6-ea5d-4ab0-b675-f082135b342c
ms.openlocfilehash: a323f8d0c3c4a8d1248409d2ec27565acdc58222
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99681413"
---
# <a name="systemconvert-methods"></a><span data-ttu-id="3e896-103">Методы System.Convert</span><span class="sxs-lookup"><span data-stu-id="3e896-103">System.Convert Methods</span></span>

[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <span data-ttu-id="3e896-104">не поддерживает следующие методы <xref:System.Convert>.</span><span class="sxs-lookup"><span data-stu-id="3e896-104">does not support the following <xref:System.Convert> methods.</span></span>

- <span data-ttu-id="3e896-105">Версии с параметром <xref:System.IFormatProvider>.</span><span class="sxs-lookup"><span data-stu-id="3e896-105">Versions with an <xref:System.IFormatProvider> parameter.</span></span>

- <span data-ttu-id="3e896-106">Методы, включающие символьные и байтовые массивы.</span><span class="sxs-lookup"><span data-stu-id="3e896-106">Methods that involve char arrays or byte arrays:</span></span>

  - <xref:System.Convert.FromBase64CharArray%2A>

  - <xref:System.Convert.ToBase64CharArray%2A>

  - <xref:System.Convert.FromBase64String%2A>

  - <xref:System.Convert.ToBase64String%2A>

- <span data-ttu-id="3e896-107">Следующие методы:</span><span class="sxs-lookup"><span data-stu-id="3e896-107">The following methods:</span></span>

  - <span data-ttu-id="3e896-108">`public static <Type2> To<Type2>(<Type1> value);`, где:</span><span class="sxs-lookup"><span data-stu-id="3e896-108">`public static <Type2> To<Type2>(<Type1> value);` where</span></span>

    <span data-ttu-id="3e896-109">`Type1` и `Type2` имеют тип `sbyte`, `uint`, `ulong` или `ushort`.</span><span class="sxs-lookup"><span data-stu-id="3e896-109">`Type1` and `Type2` are each one of `sbyte`, `uint`, `ulong`, or `ushort`.</span></span>

  - <span data-ttu-id="3e896-110">C#:</span><span class="sxs-lookup"><span data-stu-id="3e896-110">C#:</span></span>

    `int To<int type>(string value, int fromBase),`

    `ToString(... value, int toBase)`

  - <span data-ttu-id="3e896-111">Visual Basic:</span><span class="sxs-lookup"><span data-stu-id="3e896-111">Visual Basic:</span></span>

    `Function To(Of [Numeric])(value as String, fromBase As Integer)`

    `As [Numeric], ToString( value As …, toBase As Integer)`

  - <xref:System.Convert.IsDBNull%2A>

  - <xref:System.Convert.GetTypeCode%2A>

  - <xref:System.Convert.ChangeType%2A>

## <a name="see-also"></a><span data-ttu-id="3e896-112">См. также</span><span class="sxs-lookup"><span data-stu-id="3e896-112">See also</span></span>

- [<span data-ttu-id="3e896-113">Типы данных и функции</span><span class="sxs-lookup"><span data-stu-id="3e896-113">Data Types and Functions</span></span>](data-types-and-functions.md)
