---
title: Базовые типы
description: 'Изучите основные основные типы, используемые в языке F #.'
ms.date: 08/15/2020
ms.openlocfilehash: 2bfc9ba9370cb8ba1fcc1d42369c2551cbb57623
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100456917"
---
# <a name="basic-types"></a><span data-ttu-id="a1d9e-103">Базовые типы</span><span class="sxs-lookup"><span data-stu-id="a1d9e-103">Basic types</span></span>

<span data-ttu-id="a1d9e-104">В этом разделе перечислены базовые типы, определенные в языке F #.</span><span class="sxs-lookup"><span data-stu-id="a1d9e-104">This topic lists the basic types that are defined in the F# language.</span></span> <span data-ttu-id="a1d9e-105">Эти типы являются наиболее фундаментальными в F #, образуя основы практически каждой программы F #.</span><span class="sxs-lookup"><span data-stu-id="a1d9e-105">These types are the most fundamental in F#, forming the basis of nearly every F# program.</span></span> <span data-ttu-id="a1d9e-106">Они являются надмножеством типов-примитивов .NET.</span><span class="sxs-lookup"><span data-stu-id="a1d9e-106">They are a superset of .NET primitive types.</span></span>

|<span data-ttu-id="a1d9e-107">Тип</span><span class="sxs-lookup"><span data-stu-id="a1d9e-107">Type</span></span>|<span data-ttu-id="a1d9e-108">Тип .NET</span><span class="sxs-lookup"><span data-stu-id="a1d9e-108">.NET type</span></span>|<span data-ttu-id="a1d9e-109">Описание</span><span class="sxs-lookup"><span data-stu-id="a1d9e-109">Description</span></span>|<span data-ttu-id="a1d9e-110">Пример</span><span class="sxs-lookup"><span data-stu-id="a1d9e-110">Example</span></span>|
|----|---------|-----------|-------|
|`bool`|<xref:System.Boolean>|<span data-ttu-id="a1d9e-111">Возможные значения: `true` и `false`.</span><span class="sxs-lookup"><span data-stu-id="a1d9e-111">Possible values are `true` and `false`.</span></span>|`true`/`false`|
|`byte`|<xref:System.Byte>|<span data-ttu-id="a1d9e-112">Значения от 0 до 255.</span><span class="sxs-lookup"><span data-stu-id="a1d9e-112">Values from 0 to 255.</span></span>|`1uy`|
|`sbyte`|<xref:System.SByte>|<span data-ttu-id="a1d9e-113">Значения от-128 до 127.</span><span class="sxs-lookup"><span data-stu-id="a1d9e-113">Values from -128 to 127.</span></span>|`1y`|
|`int16`|<xref:System.Int16>|<span data-ttu-id="a1d9e-114">Значения от-32768 до 32767.</span><span class="sxs-lookup"><span data-stu-id="a1d9e-114">Values from -32768 to 32767.</span></span>|`1s`|
|`uint16`|<xref:System.UInt16>|<span data-ttu-id="a1d9e-115">Значения от 0 до 65535.</span><span class="sxs-lookup"><span data-stu-id="a1d9e-115">Values from 0 to 65535.</span></span>|`1us`|
|`int`|<xref:System.Int32>|<span data-ttu-id="a1d9e-116">Значения от-2 147 483 648 до 2 147 483 647.</span><span class="sxs-lookup"><span data-stu-id="a1d9e-116">Values from -2,147,483,648 to 2,147,483,647.</span></span>|`1`|
|`uint`|<xref:System.UInt32>|<span data-ttu-id="a1d9e-117">Значения от 0 до 4 294 967 295.</span><span class="sxs-lookup"><span data-stu-id="a1d9e-117">Values from 0 to 4,294,967,295.</span></span>|`1u`|
|`int64`|<xref:System.Int64>|<span data-ttu-id="a1d9e-118">Значения от-9223372036854775808 до 9 223 372 036 854 775 807.</span><span class="sxs-lookup"><span data-stu-id="a1d9e-118">Values from -9,223,372,036,854,775,808 to 9,223,372,036,854,775,807.</span></span>|`1L`|
|`uint64`|<xref:System.UInt64>|<span data-ttu-id="a1d9e-119">Значения от 0 до 18446744073709551615.</span><span class="sxs-lookup"><span data-stu-id="a1d9e-119">Values from 0 to 18,446,744,073,709,551,615.</span></span>|`1UL`|
|`nativeint`|<xref:System.IntPtr>|<span data-ttu-id="a1d9e-120">Собственный указатель в виде целого числа со знаком.</span><span class="sxs-lookup"><span data-stu-id="a1d9e-120">A native pointer as a signed integer.</span></span>|`nativeint 1`|
|`unativeint`|<xref:System.UIntPtr>|<span data-ttu-id="a1d9e-121">Собственный указатель в виде целого числа без знака.</span><span class="sxs-lookup"><span data-stu-id="a1d9e-121">A native pointer as an unsigned integer.</span></span>|`unativeint 1`|
|`decimal`|<xref:System.Decimal>|<span data-ttu-id="a1d9e-122">Тип данных с плавающей запятой, содержащий не менее 28 значащих цифр.</span><span class="sxs-lookup"><span data-stu-id="a1d9e-122">A floating point data type that has at least 28 significant digits.</span></span>|`1.0`|
|<span data-ttu-id="a1d9e-123">`float`, `double`</span><span class="sxs-lookup"><span data-stu-id="a1d9e-123">`float`, `double`</span></span>|<xref:System.Double>|<span data-ttu-id="a1d9e-124">64-разрядный тип с плавающей точкой.</span><span class="sxs-lookup"><span data-stu-id="a1d9e-124">A 64-bit floating point type.</span></span>|`1.0`|
|<span data-ttu-id="a1d9e-125">`float32`, `single`</span><span class="sxs-lookup"><span data-stu-id="a1d9e-125">`float32`, `single`</span></span>|<xref:System.Single>|<span data-ttu-id="a1d9e-126">32-разрядный тип с плавающей точкой.</span><span class="sxs-lookup"><span data-stu-id="a1d9e-126">A 32-bit floating point type.</span></span>|`1.0f`|
|`char`|<xref:System.Char>|<span data-ttu-id="a1d9e-127">Значения символов Юникода.</span><span class="sxs-lookup"><span data-stu-id="a1d9e-127">Unicode character values.</span></span>|`'c'`|
|`string`|<xref:System.String>|<span data-ttu-id="a1d9e-128">Текст в Юникоде.</span><span class="sxs-lookup"><span data-stu-id="a1d9e-128">Unicode text.</span></span>|`"str"`|
|`unit`|<span data-ttu-id="a1d9e-129">Неприменимо</span><span class="sxs-lookup"><span data-stu-id="a1d9e-129">not applicable</span></span>|<span data-ttu-id="a1d9e-130">Указывает на отсутствие фактического значения.</span><span class="sxs-lookup"><span data-stu-id="a1d9e-130">Indicates the absence of an actual value.</span></span> <span data-ttu-id="a1d9e-131">Тип имеет только одно формальное значение, которое обозначается `()` .</span><span class="sxs-lookup"><span data-stu-id="a1d9e-131">The type has only one formal value, which is denoted `()`.</span></span> <span data-ttu-id="a1d9e-132">Значение единицы, `()` , часто используется в качестве заполнителя, где требуется значение, но реальное значение недоступно или имеет смысл.</span><span class="sxs-lookup"><span data-stu-id="a1d9e-132">The unit value, `()`, is often used as a placeholder where a value is needed but no real value is available or makes sense.</span></span>|`()`|

> [!NOTE]
> <span data-ttu-id="a1d9e-133">С помощью типа можно выполнять вычисления с целыми числами слишком большими для 64-разрядного целочисленного типа `bigint` .</span><span class="sxs-lookup"><span data-stu-id="a1d9e-133">You can perform computations with integers too big for the 64-bit integer type by using the `bigint` type.</span></span> <span data-ttu-id="a1d9e-134">`bigint` не считается базовым типом; это аббревиатура для `System.Numerics.BigInteger` .</span><span class="sxs-lookup"><span data-stu-id="a1d9e-134">`bigint` is not considered a basic type; it is an abbreviation for `System.Numerics.BigInteger`.</span></span>

## <a name="see-also"></a><span data-ttu-id="a1d9e-135">См. также</span><span class="sxs-lookup"><span data-stu-id="a1d9e-135">See also</span></span>

- [<span data-ttu-id="a1d9e-136">Справочник по языку F#</span><span class="sxs-lookup"><span data-stu-id="a1d9e-136">F# Language Reference</span></span>](index.md)
