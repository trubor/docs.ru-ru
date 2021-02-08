---
description: Дополнительные сведения о перечислении Корнативетипе
title: Перечисление CorNativeType
ms.date: 03/30/2017
api_name:
- CorNativeType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorNativeType
helpviewer_keywords:
- CorNativeType enumeration [.NET Framework metadata]
ms.assetid: e47a72f1-9609-48ed-bb34-97170d7f6890
topic_type:
- apiref
ms.openlocfilehash: d2313eef124f3308c4792b47da8b7c8bba984597
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784331"
---
# <a name="cornativetype-enumeration"></a><span data-ttu-id="3f11c-103">Перечисление CorNativeType</span><span class="sxs-lookup"><span data-stu-id="3f11c-103">CorNativeType Enumeration</span></span>

<span data-ttu-id="3f11c-104">Содержит значения, описывающие собственные неуправляемые типы.</span><span class="sxs-lookup"><span data-stu-id="3f11c-104">Contains values that describe native unmanaged types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f11c-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="3f11c-105">Syntax</span></span>  
  
```cpp  
typedef enum CorNativeType {  
  
    NATIVE_TYPE_END                  = 0x0,  
    NATIVE_TYPE_VOID                 = 0x1,  
    NATIVE_TYPE_BOOLEAN              = 0x2,  
    NATIVE_TYPE_I1                   = 0x3,  
    NATIVE_TYPE_U1                   = 0x4,  
    NATIVE_TYPE_I2                   = 0x5,  
    NATIVE_TYPE_U2                   = 0x6,  
    NATIVE_TYPE_I4                   = 0x7,  
    NATIVE_TYPE_U4                   = 0x8,  
    NATIVE_TYPE_I8                   = 0x9,  
    NATIVE_TYPE_U8                   = 0xa,  
    NATIVE_TYPE_R4                   = 0xb,  
    NATIVE_TYPE_R8                   = 0xc,  
    NATIVE_TYPE_SYSCHAR              = 0xd,  
    NATIVE_TYPE_VARIANT              = 0xe,  
    NATIVE_TYPE_CURRENCY             = 0xf,  
    NATIVE_TYPE_PTR                  = 0x10,  
  
    NATIVE_TYPE_DECIMAL              = 0x11,  
    NATIVE_TYPE_DATE                 = 0x12,  
    NATIVE_TYPE_BSTR                 = 0x13,  
    NATIVE_TYPE_LPSTR                = 0x14,  
    NATIVE_TYPE_LPWSTR               = 0x15,  
    NATIVE_TYPE_LPTSTR               = 0x16,  
    NATIVE_TYPE_FIXEDSYSSTRING       = 0x17,  
    NATIVE_TYPE_OBJECTREF            = 0x18,  
    NATIVE_TYPE_IUNKNOWN             = 0x19,  
    NATIVE_TYPE_IDISPATCH            = 0x1a,  
    NATIVE_TYPE_STRUCT               = 0x1b,  
    NATIVE_TYPE_INTF                 = 0x1c,  
    NATIVE_TYPE_SAFEARRAY            = 0x1d,  
    NATIVE_TYPE_FIXEDARRAY           = 0x1e,  
    NATIVE_TYPE_INT                  = 0x1f,  
    NATIVE_TYPE_UINT                 = 0x20,  
  
    NATIVE_TYPE_NESTEDSTRUCT         = 0x21,  
    NATIVE_TYPE_BYVALSTR             = 0x22,  
    NATIVE_TYPE_ANSIBSTR             = 0x23,  
    NATIVE_TYPE_TBSTR                = 0x24,  
    NATIVE_TYPE_VARIANTBOOL          = 0x25,  
    NATIVE_TYPE_FUNC                 = 0x26,  
  
    NATIVE_TYPE_ASANY                = 0x28,  
    NATIVE_TYPE_ARRAY                = 0x2a,  
    NATIVE_TYPE_LPSTRUCT             = 0x2b,  
    NATIVE_TYPE_CUSTOMMARSHALER      = 0x2c,  
    NATIVE_TYPE_IINSPECTABLE         = 0x2e,  
    NATIVE_TYPE_HSTRING              = 0x2f,  
  
    NATIVE_TYPE_ERROR                = 0x2d,
  
    NATIVE_TYPE_MAX                  = 0x50  
  
} CorNativeType;  
```  
  
## <a name="members"></a><span data-ttu-id="3f11c-106">Члены</span><span class="sxs-lookup"><span data-stu-id="3f11c-106">Members</span></span>  
  
|<span data-ttu-id="3f11c-107">Член</span><span class="sxs-lookup"><span data-stu-id="3f11c-107">Member</span></span>|<span data-ttu-id="3f11c-108">Описание</span><span class="sxs-lookup"><span data-stu-id="3f11c-108">Description</span></span>|  
|------------|-----------------|  
|`NATIVE_TYPE_END`|<span data-ttu-id="3f11c-109">Является устаревшей.</span><span class="sxs-lookup"><span data-stu-id="3f11c-109">Obsolete.</span></span>|  
|`NATIVE_TYPE_VOID`|<span data-ttu-id="3f11c-110">Является устаревшей.</span><span class="sxs-lookup"><span data-stu-id="3f11c-110">Obsolete.</span></span>|  
|`NATIVE_TYPE_BOOLEAN`|<span data-ttu-id="3f11c-111">4-байтовое логическое значение, где TRUE — ненулевое, а FALSE — ноль.</span><span class="sxs-lookup"><span data-stu-id="3f11c-111">A 4-byte Boolean value, where TRUE is non-zero and FALSE is zero.</span></span>|  
|`NATIVE_TYPE_I1`|<span data-ttu-id="3f11c-112">8-разрядное целое значение со знаком.</span><span class="sxs-lookup"><span data-stu-id="3f11c-112">A signed 8-bit integer value.</span></span>|  
|`NATIVE_TYPE_U1`|<span data-ttu-id="3f11c-113">8-разрядное целочисленное значение без знака.</span><span class="sxs-lookup"><span data-stu-id="3f11c-113">An unsigned 8-bit integer value.</span></span>|  
|`NATIVE_TYPE_I2`|<span data-ttu-id="3f11c-114">16-разрядное целое значение со знаком.</span><span class="sxs-lookup"><span data-stu-id="3f11c-114">A signed 16-bit integer value.</span></span>|  
|`NATIVE_TYPE_U2`|<span data-ttu-id="3f11c-115">16-разрядное целочисленное значение без знака.</span><span class="sxs-lookup"><span data-stu-id="3f11c-115">An unsigned 16-bit integer value.</span></span>|  
|`NATIVE_TYPE_I4`|<span data-ttu-id="3f11c-116">32-разрядное целое значение со знаком.</span><span class="sxs-lookup"><span data-stu-id="3f11c-116">A signed 32-bit integer value.</span></span>|  
|`NATIVE_TYPE_U4`|<span data-ttu-id="3f11c-117">32-разрядное целое значение без знака.</span><span class="sxs-lookup"><span data-stu-id="3f11c-117">An unsigned 32-bit integer value.</span></span>|  
|`NATIVE_TYPE_I8`|<span data-ttu-id="3f11c-118">64-разрядное целочисленное значение со знаком.</span><span class="sxs-lookup"><span data-stu-id="3f11c-118">A signed 64-bit integer value.</span></span>|  
|`NATIVE_TYPE_U8`|<span data-ttu-id="3f11c-119">64-разрядное целочисленное значение без знака.</span><span class="sxs-lookup"><span data-stu-id="3f11c-119">An unsigned 64-bit integer value.</span></span>|  
|`NATIVE_TYPE_R4`|<span data-ttu-id="3f11c-120">4-байтовое числовое значение с плавающей запятой.</span><span class="sxs-lookup"><span data-stu-id="3f11c-120">A 4-byte floating-point numeric value.</span></span>|  
|`NATIVE_TYPE_R8`|<span data-ttu-id="3f11c-121">8-байтовое числовое значение с плавающей запятой.</span><span class="sxs-lookup"><span data-stu-id="3f11c-121">An 8-byte floating-point numeric value.</span></span>|  
|`NATIVE_TYPE_SYSCHAR`|<span data-ttu-id="3f11c-122">Является устаревшей.</span><span class="sxs-lookup"><span data-stu-id="3f11c-122">Obsolete.</span></span>|  
|`NATIVE_TYPE_VARIANT`|<span data-ttu-id="3f11c-123">Является устаревшей.</span><span class="sxs-lookup"><span data-stu-id="3f11c-123">Obsolete.</span></span>|  
|`NATIVE_TYPE_CURRENCY`|<span data-ttu-id="3f11c-124">Числовой COM-тип, соответствующий управляемому <xref:System.Decimal> типу.</span><span class="sxs-lookup"><span data-stu-id="3f11c-124">A numeric COM type that corresponds to the managed <xref:System.Decimal> type.</span></span>|  
|`NATIVE_TYPE_PTR`|<span data-ttu-id="3f11c-125">Является устаревшей.</span><span class="sxs-lookup"><span data-stu-id="3f11c-125">Obsolete.</span></span>|  
|`NATIVE_TYPE_DECIMAL`|<span data-ttu-id="3f11c-126">Является устаревшей.</span><span class="sxs-lookup"><span data-stu-id="3f11c-126">Obsolete.</span></span>|  
|`NATIVE_TYPE_DATE`|<span data-ttu-id="3f11c-127">Является устаревшей.</span><span class="sxs-lookup"><span data-stu-id="3f11c-127">Obsolete.</span></span>|  
|`NATIVE_TYPE_BSTR`|<span data-ttu-id="3f11c-128">COM-взаимодействие.</span><span class="sxs-lookup"><span data-stu-id="3f11c-128">COM Interop.</span></span>|  
|`NATIVE_TYPE_LPSTR`|<span data-ttu-id="3f11c-129">Строковое значение LPSTR.</span><span class="sxs-lookup"><span data-stu-id="3f11c-129">An LPSTR string value.</span></span>|  
|`NATIVE_TYPE_LPWSTR`|<span data-ttu-id="3f11c-130">Строковое значение LPWSTR.</span><span class="sxs-lookup"><span data-stu-id="3f11c-130">An LPWSTR string value.</span></span>|  
|`NATIVE_TYPE_LPTSTR`|<span data-ttu-id="3f11c-131">Строковое значение LPTSTR.</span><span class="sxs-lookup"><span data-stu-id="3f11c-131">An LPTSTR string value.</span></span>|  
|`NATIVE_TYPE_FIXEDSYSSTRING`|<span data-ttu-id="3f11c-132">Фиксированное, определяемое системой строковое значение.</span><span class="sxs-lookup"><span data-stu-id="3f11c-132">A fixed, system-defined string value.</span></span>|  
|`NATIVE_TYPE_OBJECTREF`|<span data-ttu-id="3f11c-133">Является устаревшей.</span><span class="sxs-lookup"><span data-stu-id="3f11c-133">Obsolete.</span></span>|  
|`NATIVE_TYPE_IUNKNOWN`|<span data-ttu-id="3f11c-134">COM-взаимодействие.</span><span class="sxs-lookup"><span data-stu-id="3f11c-134">COM Interop.</span></span>|  
|`NATIVE_TYPE_IDISPATCH`|<span data-ttu-id="3f11c-135">COM-взаимодействие.</span><span class="sxs-lookup"><span data-stu-id="3f11c-135">COM Interop.</span></span>|  
|`NATIVE_TYPE_STRUCT`|<span data-ttu-id="3f11c-136">Значение собственной структуры.</span><span class="sxs-lookup"><span data-stu-id="3f11c-136">A native structure value.</span></span>|  
|`NATIVE_TYPE_INTF`|<span data-ttu-id="3f11c-137">COM-взаимодействие.</span><span class="sxs-lookup"><span data-stu-id="3f11c-137">COM Interop.</span></span>|  
|`NATIVE_TYPE_SAFEARRAY`|<span data-ttu-id="3f11c-138">COM-взаимодействие.</span><span class="sxs-lookup"><span data-stu-id="3f11c-138">COM Interop.</span></span>|  
|`NATIVE_TYPE_FIXEDARRAY`|<span data-ttu-id="3f11c-139">Значение массива фиксированной длины.</span><span class="sxs-lookup"><span data-stu-id="3f11c-139">A fixed-length array value.</span></span>|  
|`NATIVE_TYPE_INT`|<span data-ttu-id="3f11c-140">Собственное 16-разрядное целое число со знаком.</span><span class="sxs-lookup"><span data-stu-id="3f11c-140">A native 16-bit signed integer value.</span></span>|  
|`NATIVE_TYPE_UINT`|<span data-ttu-id="3f11c-141">Собственное 16-битовое целочисленное значение без знака.</span><span class="sxs-lookup"><span data-stu-id="3f11c-141">A native 16-bit unsigned integer value.</span></span>|  
|`NATIVE_TYPE_NESTEDSTRUCT`|<span data-ttu-id="3f11c-142">Является устаревшей.</span><span class="sxs-lookup"><span data-stu-id="3f11c-142">Obsolete.</span></span><br /><br /> <span data-ttu-id="3f11c-143">Используйте NATIVE_TYPE_STRUCT.</span><span class="sxs-lookup"><span data-stu-id="3f11c-143">Use NATIVE_TYPE_STRUCT.</span></span>|  
|`NATIVE_TYPE_BYVALSTR`|<span data-ttu-id="3f11c-144">COM-взаимодействие.</span><span class="sxs-lookup"><span data-stu-id="3f11c-144">COM Interop.</span></span>|  
|`NATIVE_TYPE_ANSIBSTR`|<span data-ttu-id="3f11c-145">COM-взаимодействие.</span><span class="sxs-lookup"><span data-stu-id="3f11c-145">COM Interop.</span></span>|  
|`NATIVE_TYPE_TBSTR`|<span data-ttu-id="3f11c-146">COM-взаимодействие.</span><span class="sxs-lookup"><span data-stu-id="3f11c-146">COM Interop.</span></span><br /><br /> <span data-ttu-id="3f11c-147">Выберите BSTR или АНСИБСТР в зависимости от платформы.</span><span class="sxs-lookup"><span data-stu-id="3f11c-147">Select BSTR or ANSIBSTR depending on the platform.</span></span>|  
|`NATIVE_TYPE_VARIANTBOOL`|<span data-ttu-id="3f11c-148">2-байтовое логическое значение, где TRUE равно-1, а FALSE — нуль.</span><span class="sxs-lookup"><span data-stu-id="3f11c-148">A 2-byte Boolean value, where TRUE is -1 and FALSE is zero.</span></span>|  
|`NATIVE_TYPE_FUNC`|<span data-ttu-id="3f11c-149">Указатель функции.</span><span class="sxs-lookup"><span data-stu-id="3f11c-149">A function pointer.</span></span>|  
|`NATIVE_TYPE_ASANY`|<span data-ttu-id="3f11c-150">Ссылка на любой собственный тип.</span><span class="sxs-lookup"><span data-stu-id="3f11c-150">A reference to any native type.</span></span>|  
|`NATIVE_TYPE_ARRAY`|<span data-ttu-id="3f11c-151">Ссылка на массив с элементами незаданного типа.</span><span class="sxs-lookup"><span data-stu-id="3f11c-151">A reference to an array with members of an unspecified type.</span></span>|  
|`NATIVE_TYPE_LPSTRUCT`|<span data-ttu-id="3f11c-152">32-разрядный целочисленный указатель на структуру.</span><span class="sxs-lookup"><span data-stu-id="3f11c-152">A 32-bit integer pointer to a structure.</span></span>|  
|`NATIVE_TYPE_CUSTOMMARSHALER`|<span data-ttu-id="3f11c-153">Собственный тип пользовательского модуля упаковки.</span><span class="sxs-lookup"><span data-stu-id="3f11c-153">A custom marshaler native type.</span></span><br /><br /> <span data-ttu-id="3f11c-154">После этого должен быть указан строковый формат: "имя собственного типа/имя типа модуля маршалирования/0Optional cookie/0" или "{native Type GUID}/0Custom имя типа-маршалером/0Optional файл cookie/0"</span><span class="sxs-lookup"><span data-stu-id="3f11c-154">This must be followed by a string of the following format: "Native type name/0Custom marshaler type name/0Optional cookie/0" or "{Native type GUID}/0Custom marshaler type name/0Optional cookie/0"</span></span>|  
|`NATIVE_TYPE_ERROR`|<span data-ttu-id="3f11c-155">COM-взаимодействие.</span><span class="sxs-lookup"><span data-stu-id="3f11c-155">COM Interop.</span></span><br /><br /> <span data-ttu-id="3f11c-156">С ELEMENT_TYPE_I4 этот тип сопоставляется с VT_HRESULT.</span><span class="sxs-lookup"><span data-stu-id="3f11c-156">With ELEMENT_TYPE_I4 this type maps to VT_HRESULT.</span></span>|  
|`NATIVE_TYPE_IINSPECTABLE`|<span data-ttu-id="3f11c-157">Собственный `IInspectable` тип.</span><span class="sxs-lookup"><span data-stu-id="3f11c-157">A native `IInspectable` type.</span></span>|  
|`NATIVE_TYPE_HSTRING`|<span data-ttu-id="3f11c-158">Собственный `HString` .</span><span class="sxs-lookup"><span data-stu-id="3f11c-158">A native `HString`.</span></span>|  
|`NATIVE_TYPE_MAX`|<span data-ttu-id="3f11c-159">Недопустимое значение.</span><span class="sxs-lookup"><span data-stu-id="3f11c-159">An invalid value.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3f11c-160">Требования</span><span class="sxs-lookup"><span data-stu-id="3f11c-160">Requirements</span></span>  

 <span data-ttu-id="3f11c-161">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3f11c-161">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f11c-162">**Заголовок:** Корхдр. h</span><span class="sxs-lookup"><span data-stu-id="3f11c-162">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="3f11c-163">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f11c-163">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f11c-164">См. также</span><span class="sxs-lookup"><span data-stu-id="3f11c-164">See also</span></span>

- <xref:System.Runtime.InteropServices.UnmanagedType>
- [<span data-ttu-id="3f11c-165">Перечисления метаданных</span><span class="sxs-lookup"><span data-stu-id="3f11c-165">Metadata Enumerations</span></span>](metadata-enumerations.md)
