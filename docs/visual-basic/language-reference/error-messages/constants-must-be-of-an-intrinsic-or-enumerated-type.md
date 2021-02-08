---
description: 'Дополнительные сведения о: BC30424: константы должны быть встроенными или перечисляемыми типами, а не классом, структурой, параметром типа или типом массива'
title: Константа должна быть величиной внутреннего или перечислимого типа, а не классом, структурой, параметром типа или массивом
ms.date: 07/20/2015
f1_keywords:
- vbc30424
- bc30424
helpviewer_keywords:
- BC30424
ms.assetid: 2d402c2f-27ad-428b-b699-d45cd62f7196
ms.openlocfilehash: e9765d78ff671d6b99f47242509b1c3b4560c029
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99796734"
---
# <a name="bc30424-constants-must-be-of-an-intrinsic-or-enumerated-type-not-a-class-structure-type-parameter-or-array-type"></a><span data-ttu-id="6f443-103">BC30424: константы должны иметь встроенный или перечислимый тип, а не класс, структуру, параметр типа или тип массива</span><span class="sxs-lookup"><span data-stu-id="6f443-103">BC30424: Constants must be of an intrinsic or enumerated type, not a class, structure, type parameter, or array type</span></span>

<span data-ttu-id="6f443-104">Предпринята попытка объявить константу как класс, структуру или тип массива или как параметр типа, определенный содержащим универсальным типом.</span><span class="sxs-lookup"><span data-stu-id="6f443-104">You have attempted to declare a constant as a class, structure, or array type, or as a type parameter defined by a containing generic type.</span></span>

 <span data-ttu-id="6f443-105">Константы должны иметь встроенный тип ( `Boolean` , `Byte` ,, `Date` , `Decimal` `Double` , `Integer` , `Long` ,,,,,,, `Object` `SByte` `Short` `Single` `String` `UInteger` `ULong` или `UShort` ) или тип, `Enum` основанный на одном из целочисленных типов.</span><span class="sxs-lookup"><span data-stu-id="6f443-105">Constants must be of an intrinsic type (`Boolean`, `Byte`, `Date`, `Decimal`, `Double`, `Integer`, `Long`, `Object`, `SByte`, `Short`, `Single`, `String`, `UInteger`, `ULong`, or `UShort`), or an `Enum` type based on one of the integral types.</span></span>

 <span data-ttu-id="6f443-106">**Идентификатор ошибки:** BC30424</span><span class="sxs-lookup"><span data-stu-id="6f443-106">**Error ID:** BC30424</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="6f443-107">Исправление ошибки</span><span class="sxs-lookup"><span data-stu-id="6f443-107">To correct this error</span></span>

1. <span data-ttu-id="6f443-108">Объявите константу как внутренний или `Enum` тип.</span><span class="sxs-lookup"><span data-stu-id="6f443-108">Declare the constant as an intrinsic or `Enum` type.</span></span>

2. <span data-ttu-id="6f443-109">Константа также может быть специальным значением, таким как `True` , `False` или `Nothing` .</span><span class="sxs-lookup"><span data-stu-id="6f443-109">A constant can also be a special value such as `True`, `False`, or `Nothing`.</span></span> <span data-ttu-id="6f443-110">Компилятор считает эти предопределенные значения соответствующим внутренним типом.</span><span class="sxs-lookup"><span data-stu-id="6f443-110">The compiler considers these predefined values to be of the appropriate intrinsic type.</span></span>

## <a name="see-also"></a><span data-ttu-id="6f443-111">См. также</span><span class="sxs-lookup"><span data-stu-id="6f443-111">See also</span></span>

- [<span data-ttu-id="6f443-112">Константы и перечисления</span><span class="sxs-lookup"><span data-stu-id="6f443-112">Constants and Enumerations</span></span>](../constants-and-enumerations.md)
- [<span data-ttu-id="6f443-113">Типы данных</span><span class="sxs-lookup"><span data-stu-id="6f443-113">Data Types</span></span>](../../programming-guide/language-features/data-types/index.md)
- [<span data-ttu-id="6f443-114">Типы данных</span><span class="sxs-lookup"><span data-stu-id="6f443-114">Data Types</span></span>](../data-types/index.md)
