---
description: Дополнительные сведения о перечислении Корелементтипе
title: Перечисление CorElementType
ms.date: 03/30/2017
api_name:
- CorElementType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorElementType
helpviewer_keywords:
- CorElementType enumeration [.NET Framework metadata]
ms.assetid: c3809c8f-1737-4f0f-9442-0c01ee689871
topic_type:
- apiref
ms.openlocfilehash: 3eaf75a6d2094ec875ab1861aac49e4382e65801
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784539"
---
# <a name="corelementtype-enumeration"></a><span data-ttu-id="7f146-103">Перечисление CorElementType</span><span class="sxs-lookup"><span data-stu-id="7f146-103">CorElementType Enumeration</span></span>

<span data-ttu-id="7f146-104">Задает среду CLR <xref:System.Type> , модификатор типа или сведения о типе в сигнатуре типа метаданных.</span><span class="sxs-lookup"><span data-stu-id="7f146-104">Specifies a common language runtime <xref:System.Type>, a type modifier, or information about a type in a metadata type signature.</span></span>

## <a name="syntax"></a><span data-ttu-id="7f146-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="7f146-105">Syntax</span></span>

```cpp
typedef enum CorElementType {
    ELEMENT_TYPE_END            = 0x0,
    ELEMENT_TYPE_VOID           = 0x1,
    ELEMENT_TYPE_BOOLEAN        = 0x2,
    ELEMENT_TYPE_CHAR           = 0x3,
    ELEMENT_TYPE_I1             = 0x4,
    ELEMENT_TYPE_U1             = 0x5,
    ELEMENT_TYPE_I2             = 0x6,
    ELEMENT_TYPE_U2             = 0x7,
    ELEMENT_TYPE_I4             = 0x8,
    ELEMENT_TYPE_U4             = 0x9,
    ELEMENT_TYPE_I8             = 0xa,
    ELEMENT_TYPE_U8             = 0xb,
    ELEMENT_TYPE_R4             = 0xc,
    ELEMENT_TYPE_R8             = 0xd,
    ELEMENT_TYPE_STRING         = 0xe,

    ELEMENT_TYPE_PTR            = 0xf,
    ELEMENT_TYPE_BYREF          = 0x10,

    ELEMENT_TYPE_VALUETYPE      = 0x11,
    ELEMENT_TYPE_CLASS          = 0x12,
    ELEMENT_TYPE_VAR            = 0x13,
    ELEMENT_TYPE_ARRAY          = 0x14,
    ELEMENT_TYPE_GENERICINST    = 0x15,
    ELEMENT_TYPE_TYPEDBYREF     = 0x16,

    ELEMENT_TYPE_I              = 0x18,
    ELEMENT_TYPE_U              = 0x19,
    ELEMENT_TYPE_FNPTR          = 0x1B,
    ELEMENT_TYPE_OBJECT         = 0x1C,
    ELEMENT_TYPE_SZARRAY        = 0x1D,
    ELEMENT_TYPE_MVAR           = 0x1e,

    ELEMENT_TYPE_CMOD_REQD      = 0x1F,
    ELEMENT_TYPE_CMOD_OPT       = 0x20,

    ELEMENT_TYPE_INTERNAL       = 0x21,
    ELEMENT_TYPE_MAX            = 0x22,

    ELEMENT_TYPE_MODIFIER       = 0x40,
    ELEMENT_TYPE_SENTINEL       = 0x01 | ELEMENT_TYPE_MODIFIER,
    ELEMENT_TYPE_PINNED         = 0x05 | ELEMENT_TYPE_MODIFIER

} CorElementType;
```

## <a name="members"></a><span data-ttu-id="7f146-106">Члены</span><span class="sxs-lookup"><span data-stu-id="7f146-106">Members</span></span>

|<span data-ttu-id="7f146-107">Член</span><span class="sxs-lookup"><span data-stu-id="7f146-107">Member</span></span>|<span data-ttu-id="7f146-108">Описание</span><span class="sxs-lookup"><span data-stu-id="7f146-108">Description</span></span>|
|------------|-----------------|
|`ELEMENT_TYPE_END`|<span data-ttu-id="7f146-109">Для внутреннего использования.</span><span class="sxs-lookup"><span data-stu-id="7f146-109">Used internally.</span></span>|
|`ELEMENT_TYPE_VOID`|<span data-ttu-id="7f146-110">Тип void.</span><span class="sxs-lookup"><span data-stu-id="7f146-110">A void type.</span></span>|
|`ELEMENT_TYPE_BOOLEAN`|<span data-ttu-id="7f146-111">Логический тип</span><span class="sxs-lookup"><span data-stu-id="7f146-111">A Boolean type</span></span>|
|`ELEMENT_TYPE_CHAR`|<span data-ttu-id="7f146-112">Тип символа.</span><span class="sxs-lookup"><span data-stu-id="7f146-112">A character type.</span></span>|
|`ELEMENT_TYPE_I1`|<span data-ttu-id="7f146-113">1-байтовое целое число со знаком.</span><span class="sxs-lookup"><span data-stu-id="7f146-113">A signed 1-byte integer.</span></span>|
|`ELEMENT_TYPE_U1`|<span data-ttu-id="7f146-114">1-байтовое целое число без знака.</span><span class="sxs-lookup"><span data-stu-id="7f146-114">An unsigned 1-byte integer.</span></span>|
|`ELEMENT_TYPE_I2`|<span data-ttu-id="7f146-115">2-байтовое целое число со знаком.</span><span class="sxs-lookup"><span data-stu-id="7f146-115">A signed 2-byte integer.</span></span>|
|`ELEMENT_TYPE_U2`|<span data-ttu-id="7f146-116">2-байтовое целое число без знака.</span><span class="sxs-lookup"><span data-stu-id="7f146-116">An unsigned 2-byte integer.</span></span>|
|`ELEMENT_TYPE_I4`|<span data-ttu-id="7f146-117">4-байтовое целое число со знаком.</span><span class="sxs-lookup"><span data-stu-id="7f146-117">A signed 4-byte integer.</span></span>|
|`ELEMENT_TYPE_U4`|<span data-ttu-id="7f146-118">4-байтовое целое число без знака.</span><span class="sxs-lookup"><span data-stu-id="7f146-118">An unsigned 4-byte integer.</span></span>|
|`ELEMENT_TYPE_I8`|<span data-ttu-id="7f146-119">8-байтовое целое число со знаком.</span><span class="sxs-lookup"><span data-stu-id="7f146-119">A signed 8-byte integer.</span></span>|
|`ELEMENT_TYPE_U8`|<span data-ttu-id="7f146-120">8-байтовое целое число без знака.</span><span class="sxs-lookup"><span data-stu-id="7f146-120">An unsigned 8-byte integer.</span></span>|
|`ELEMENT_TYPE_R4`|<span data-ttu-id="7f146-121">4-байтовое число с плавающей запятой.</span><span class="sxs-lookup"><span data-stu-id="7f146-121">A 4-byte floating point.</span></span>|
|`ELEMENT_TYPE_R8`|<span data-ttu-id="7f146-122">8-байтная плавающая точка.</span><span class="sxs-lookup"><span data-stu-id="7f146-122">An 8-byte floating point.</span></span>|
|`ELEMENT_TYPE_STRING`|<span data-ttu-id="7f146-123">Тип System. String.</span><span class="sxs-lookup"><span data-stu-id="7f146-123">A System.String type.</span></span>|
|`ELEMENT_TYPE_PTR`|<span data-ttu-id="7f146-124">Модификатор типа указателя.</span><span class="sxs-lookup"><span data-stu-id="7f146-124">A pointer type modifier.</span></span>|
|`ELEMENT_TYPE_BYREF`|<span data-ttu-id="7f146-125">Модификатор ссылочного типа.</span><span class="sxs-lookup"><span data-stu-id="7f146-125">A reference type modifier.</span></span>|
|`ELEMENT_TYPE_VALUETYPE`|<span data-ttu-id="7f146-126">Модификатор типа значения.</span><span class="sxs-lookup"><span data-stu-id="7f146-126">A value type modifier.</span></span>|
|`ELEMENT_TYPE_CLASS`|<span data-ttu-id="7f146-127">Модификатор типа класса.</span><span class="sxs-lookup"><span data-stu-id="7f146-127">A class type modifier.</span></span>|
|`ELEMENT_TYPE_VAR`|<span data-ttu-id="7f146-128">Модификатор типа переменной класса.</span><span class="sxs-lookup"><span data-stu-id="7f146-128">A class variable type modifier.</span></span>|
|`ELEMENT_TYPE_ARRAY`|<span data-ttu-id="7f146-129">Модификатор многомерного типа массива.</span><span class="sxs-lookup"><span data-stu-id="7f146-129">A multi-dimensional array type modifier.</span></span>|
|`ELEMENT_TYPE_GENERICINST`|<span data-ttu-id="7f146-130">Модификатор типа для универсальных типов.</span><span class="sxs-lookup"><span data-stu-id="7f146-130">A type modifier for generic types.</span></span>|
|`ELEMENT_TYPE_TYPEDBYREF`|<span data-ttu-id="7f146-131">Типизированная ссылка.</span><span class="sxs-lookup"><span data-stu-id="7f146-131">A typed reference.</span></span>|
|`ELEMENT_TYPE_I`|<span data-ttu-id="7f146-132">Размер собственного целого числа.</span><span class="sxs-lookup"><span data-stu-id="7f146-132">Size of a native integer.</span></span>|
|`ELEMENT_TYPE_U`|<span data-ttu-id="7f146-133">Размер целого числа без знака в машинном кодах.</span><span class="sxs-lookup"><span data-stu-id="7f146-133">Size of an unsigned native integer.</span></span>|
|`ELEMENT_TYPE_FNPTR`|<span data-ttu-id="7f146-134">Указатель на функцию.</span><span class="sxs-lookup"><span data-stu-id="7f146-134">A pointer to a function.</span></span>|
|`ELEMENT_TYPE_OBJECT`|<span data-ttu-id="7f146-135">Тип System. Object.</span><span class="sxs-lookup"><span data-stu-id="7f146-135">A System.Object type.</span></span>|
|`ELEMENT_TYPE_SZARRAY`|<span data-ttu-id="7f146-136">Модификатор одномерного типа массива с нулевой нижней границей.</span><span class="sxs-lookup"><span data-stu-id="7f146-136">A single-dimensional, zero lower-bound array type modifier.</span></span>|
|`ELEMENT_TYPE_MVAR`|<span data-ttu-id="7f146-137">Модификатор типа переменной метода.</span><span class="sxs-lookup"><span data-stu-id="7f146-137">A method variable type modifier.</span></span>|
|`ELEMENT_TYPE_CMOD_REQD`|<span data-ttu-id="7f146-138">Обязательный модификатор языка C.</span><span class="sxs-lookup"><span data-stu-id="7f146-138">A C language required modifier.</span></span>|
|`ELEMENT_TYPE_CMOD_OPT`|<span data-ttu-id="7f146-139">Необязательный модификатор языка C.</span><span class="sxs-lookup"><span data-stu-id="7f146-139">A C language optional modifier.</span></span>|
|`ELEMENT_TYPE_INTERNAL`|<span data-ttu-id="7f146-140">Для внутреннего использования.</span><span class="sxs-lookup"><span data-stu-id="7f146-140">Used internally.</span></span>|
|`ELEMENT_TYPE_MAX`|<span data-ttu-id="7f146-141">Недопустимый тип.</span><span class="sxs-lookup"><span data-stu-id="7f146-141">An invalid type.</span></span>|
|`ELEMENT_TYPE_MODIFIER`|<span data-ttu-id="7f146-142">Для внутреннего использования.</span><span class="sxs-lookup"><span data-stu-id="7f146-142">Used internally.</span></span>|
|`ELEMENT_TYPE_SENTINEL`|<span data-ttu-id="7f146-143">Модификатор типа, который является Sentinel для списка переменного числа параметров.</span><span class="sxs-lookup"><span data-stu-id="7f146-143">A type modifier that is a sentinel for a list of a variable number of parameters.</span></span>|
|`ELEMENT_TYPE_PINNED`|<span data-ttu-id="7f146-144">Для внутреннего использования.</span><span class="sxs-lookup"><span data-stu-id="7f146-144">Used internally.</span></span>|

## <a name="remarks"></a><span data-ttu-id="7f146-145">Remarks</span><span class="sxs-lookup"><span data-stu-id="7f146-145">Remarks</span></span>

<span data-ttu-id="7f146-146">Модификаторы типа формируют базу для представления более сложных типов.</span><span class="sxs-lookup"><span data-stu-id="7f146-146">The type modifiers form the basis for representing more complex types.</span></span> <span data-ttu-id="7f146-147">`CorElementType`Значение модификатора типа применяется к значению, которое непосредственно следует за ним в сигнатуре типа.</span><span class="sxs-lookup"><span data-stu-id="7f146-147">A `CorElementType` type modifier value is applied to the value that immediately follows it in the type signature.</span></span> <span data-ttu-id="7f146-148">Значение, следующее за `CorElementType` значением модификатора типа, может быть `CorElementType` простым значением типа, маркером метаданных или другим значением, как указано в следующей таблице.</span><span class="sxs-lookup"><span data-stu-id="7f146-148">The value that follows the `CorElementType` type modifier value can be a `CorElementType` simple type value, a metadata token, or other value, as specified in the following table.</span></span>

> [!NOTE]
> <span data-ttu-id="7f146-149">Все числа (*число*, число *аргументов*, *маркер метаданных*, *ранг*, *количество* и *граница*) хранятся в виде сжатых целых чисел.</span><span class="sxs-lookup"><span data-stu-id="7f146-149">All numbers (*number*, *argument Count*, *metadata token*, *rank*, *count*, and *bound*) are stored as compressed integers.</span></span> <span data-ttu-id="7f146-150">Дополнительные сведения см. в статье [стандартный ECMA-335-Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm) на веб-сайте ECMA.</span><span class="sxs-lookup"><span data-stu-id="7f146-150">See [Standard ECMA-335 - Common Language Infrastructure (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm) on the ECMA Web site for details.</span></span>

|<span data-ttu-id="7f146-151">Модификатор типа</span><span class="sxs-lookup"><span data-stu-id="7f146-151">Type modifier</span></span>|<span data-ttu-id="7f146-152">Формат</span><span class="sxs-lookup"><span data-stu-id="7f146-152">Format</span></span>|
|-------------------|------------|
|`ELEMENT_TYPE_PTR`|<span data-ttu-id="7f146-153">ELEMENT_TYPE_PTR \<a `CorElementType` value></span><span class="sxs-lookup"><span data-stu-id="7f146-153">ELEMENT_TYPE_PTR \<a `CorElementType` value></span></span>|
|`ELEMENT_TYPE_BYREF`|<span data-ttu-id="7f146-154">ELEMENT_TYPE_BYREF \<a `CorElementType` value></span><span class="sxs-lookup"><span data-stu-id="7f146-154">ELEMENT_TYPE_BYREF \<a `CorElementType` value></span></span>|
|`ELEMENT_TYPE_VALUETYPE`|<span data-ttu-id="7f146-155">ELEMENT_TYPE_VALUETYPE \<an `mdTypeDef` metadata token></span><span class="sxs-lookup"><span data-stu-id="7f146-155">ELEMENT_TYPE_VALUETYPE \<an `mdTypeDef` metadata token></span></span>|
|`ELEMENT_TYPE_CLASS`|<span data-ttu-id="7f146-156">ELEMENT_TYPE_CLASS \<an `mdTypeDef` metadata token></span><span class="sxs-lookup"><span data-stu-id="7f146-156">ELEMENT_TYPE_CLASS \<an `mdTypeDef` metadata token></span></span>|
|`ELEMENT_TYPE_VAR`|<span data-ttu-id="7f146-157">ELEMENT_TYPE_VAR \<number></span><span class="sxs-lookup"><span data-stu-id="7f146-157">ELEMENT_TYPE_VAR \<number></span></span>|
|`ELEMENT_TYPE_ARRAY`|<span data-ttu-id="7f146-158">ELEMENT_TYPE_ARRAY \<a `CorElementType` value> \<rank> \<count1> \<bound1> ... \<countN>\<boundN></span><span class="sxs-lookup"><span data-stu-id="7f146-158">ELEMENT_TYPE_ARRAY \<a `CorElementType` value> \<rank> \<count1> \<bound1> ... \<countN> \<boundN></span></span>|
|`ELEMENT_TYPE_GENERICINST`|<span data-ttu-id="7f146-159">ELEMENT_TYPE_GENERICINST \<an `mdTypeDef` metadata token> \<argument Count> \<arg1> ... \<argN></span><span class="sxs-lookup"><span data-stu-id="7f146-159">ELEMENT_TYPE_GENERICINST \<an `mdTypeDef` metadata token> \<argument Count> \<arg1> ... \<argN></span></span>|
|`ELEMENT_TYPE_FNPTR`|<span data-ttu-id="7f146-160">ELEMENT_TYPE_FNPTR \<complete signature for the function, including calling convention></span><span class="sxs-lookup"><span data-stu-id="7f146-160">ELEMENT_TYPE_FNPTR \<complete signature for the function, including calling convention></span></span>|
|`ELEMENT_TYPE_SZARRAY`|<span data-ttu-id="7f146-161">ELEMENT_TYPE_SZARRAY \<a `CorElementType` value></span><span class="sxs-lookup"><span data-stu-id="7f146-161">ELEMENT_TYPE_SZARRAY \<a `CorElementType` value></span></span>|
|`ELEMENT_TYPE_MVAR`|<span data-ttu-id="7f146-162">ELEMENT_TYPE_MVAR \<number></span><span class="sxs-lookup"><span data-stu-id="7f146-162">ELEMENT_TYPE_MVAR \<number></span></span>|
|`ELEMENT_TYPE_CMOD_REQD`|<span data-ttu-id="7f146-163">ELEMENT_TYPE_\<a `mdTypeRef` or `mdTypeDef` metadata token></span><span class="sxs-lookup"><span data-stu-id="7f146-163">ELEMENT_TYPE_\<a `mdTypeRef` or `mdTypeDef` metadata token></span></span>|
|`ELEMENT_TYPE_CMOD_OPT`|<span data-ttu-id="7f146-164">E_T_CMOD_OPT \<a `mdTypeRef` or `mdTypeDef` metadata token></span><span class="sxs-lookup"><span data-stu-id="7f146-164">E_T_CMOD_OPT \<a `mdTypeRef` or `mdTypeDef` metadata token></span></span>|

## <a name="requirements"></a><span data-ttu-id="7f146-165">Требования</span><span class="sxs-lookup"><span data-stu-id="7f146-165">Requirements</span></span>

<span data-ttu-id="7f146-166">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7f146-166">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="7f146-167">**Заголовок:** Корхдр. h</span><span class="sxs-lookup"><span data-stu-id="7f146-167">**Header:** CorHdr.h</span></span>

<span data-ttu-id="7f146-168">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f146-168">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="7f146-169">См. также</span><span class="sxs-lookup"><span data-stu-id="7f146-169">See also</span></span>

- [<span data-ttu-id="7f146-170">Перечисления метаданных</span><span class="sxs-lookup"><span data-stu-id="7f146-170">Metadata Enumerations</span></span>](metadata-enumerations.md)
