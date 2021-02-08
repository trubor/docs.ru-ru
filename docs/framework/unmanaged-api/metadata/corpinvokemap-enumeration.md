---
description: Дополнительные сведения о перечислении CorPinvokeMap
title: Перечисление CorPinvokeMap
ms.date: 03/30/2017
api_name:
- CorPinvokeMap
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorPinvokeMap
helpviewer_keywords:
- CorPinvokeMap enumeration [.NET Framework metadata]
ms.assetid: f14f986e-f6ce-42bc-aa23-18150c46d28c
topic_type:
- apiref
ms.openlocfilehash: 8285632725096b4e6afc85fe54a89f12fc899dd1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784266"
---
# <a name="corpinvokemap-enumeration"></a><span data-ttu-id="13c62-103">Перечисление CorPinvokeMap</span><span class="sxs-lookup"><span data-stu-id="13c62-103">CorPinvokeMap Enumeration</span></span>

<span data-ttu-id="13c62-104">Задает параметры для вызова PInvoke.</span><span class="sxs-lookup"><span data-stu-id="13c62-104">Specifies options for a PInvoke call.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13c62-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="13c62-105">Syntax</span></span>  
  
```cpp  
typedef enum  CorPinvokeMap {  
  
    pmNoMangle          = 0x0001,  
  
    pmCharSetMask       = 0x0006,  
    pmCharSetNotSpec    = 0x0000,  
    pmCharSetAnsi       = 0x0002,  
    pmCharSetUnicode    = 0x0004,  
    pmCharSetAuto       = 0x0006,  
  
    pmBestFitUseAssem   = 0x0000,  
    pmBestFitEnabled    = 0x0010,  
    pmBestFitDisabled   = 0x0020,  
    pmBestFitMask       = 0x0030,  
  
    pmThrowOnUnmappableCharUseAssem   = 0x0000,  
    pmThrowOnUnmappableCharEnabled    = 0x1000,  
    pmThrowOnUnmappableCharDisabled   = 0x2000,  
    pmThrowOnUnmappableCharMask       = 0x3000,  
  
    pmSupportsLastError = 0x0040,
  
    pmCallConvMask      = 0x0700,  
    pmCallConvWinapi    = 0x0100,  
    pmCallConvCdecl     = 0x0200,  
    pmCallConvStdcall   = 0x0300,  
    pmCallConvThiscall  = 0x0400,  
    pmCallConvFastcall  = 0x0500,  
  
    pmMaxValue          = 0xFFFF  
  
} CorPinvokeMap;  
```  
  
## <a name="members"></a><span data-ttu-id="13c62-106">Члены</span><span class="sxs-lookup"><span data-stu-id="13c62-106">Members</span></span>  
  
|<span data-ttu-id="13c62-107">Член</span><span class="sxs-lookup"><span data-stu-id="13c62-107">Member</span></span>|<span data-ttu-id="13c62-108">Описание</span><span class="sxs-lookup"><span data-stu-id="13c62-108">Description</span></span>|  
|------------|-----------------|  
|`pmNoMangle`|<span data-ttu-id="13c62-109">Используйте каждое имя элемента, как указано.</span><span class="sxs-lookup"><span data-stu-id="13c62-109">Use each member name as specified.</span></span>|  
|`pmCharSetMask`|<span data-ttu-id="13c62-110">Зарезервировано.</span><span class="sxs-lookup"><span data-stu-id="13c62-110">Reserved.</span></span>|  
|`pmCharSetNotSpec`|<span data-ttu-id="13c62-111">Зарезервировано.</span><span class="sxs-lookup"><span data-stu-id="13c62-111">Reserved.</span></span>|  
|`pmCharSetAnsi`|<span data-ttu-id="13c62-112">Маршалирует строки в виде строк многобайтовых символов.</span><span class="sxs-lookup"><span data-stu-id="13c62-112">Marshal strings as multiple-byte character strings.</span></span>|  
|`pmCharSetUnicode`|<span data-ttu-id="13c62-113">Маршалирует строки в виде 2-байтных символов Юникода.</span><span class="sxs-lookup"><span data-stu-id="13c62-113">Marshal strings as Unicode 2-byte characters.</span></span>|  
|`pmCharSetAuto`|<span data-ttu-id="13c62-114">Выполняет автоматический маршалинг строк способом, соответствующим целевой операционной системе.</span><span class="sxs-lookup"><span data-stu-id="13c62-114">Automatically marshal strings appropriately for the target operating system.</span></span> <span data-ttu-id="13c62-115">По умолчанию используется Юникод в Windows NT, Windows 2000, Windows XP и семействе Windows Server 2003. значение по умолчанию — ANSI в Windows 98 и Windows Me.</span><span class="sxs-lookup"><span data-stu-id="13c62-115">The default is Unicode on Windows NT, Windows 2000, Windows XP, and the Windows Server 2003 family; the default is ANSI on Windows 98 and Windows Me.</span></span>|  
|`pmBestFitUseAssem`|<span data-ttu-id="13c62-116">Зарезервировано.</span><span class="sxs-lookup"><span data-stu-id="13c62-116">Reserved.</span></span>|  
|`pmBestFitEnabled`|<span data-ttu-id="13c62-117">Выполните наилучшее сопоставление символов Юникода, не имея точного соответствия в кодировке ANSI.</span><span class="sxs-lookup"><span data-stu-id="13c62-117">Perform best-fit mapping of Unicode characters that lack an exact match in the ANSI character set.</span></span>|  
|`pmBestFitDisabled`|<span data-ttu-id="13c62-118">Не выполняйте наилучшее соответствие символов Юникода.</span><span class="sxs-lookup"><span data-stu-id="13c62-118">Do not perform best-fit mapping of Unicode characters.</span></span> <span data-ttu-id="13c62-119">В этом случае все несопоставимые символы будут заменены символом "?".</span><span class="sxs-lookup"><span data-stu-id="13c62-119">In this case, all unmappable characters will be replaced by a ‘?’.</span></span>|  
|`pmBestFitMask`|<span data-ttu-id="13c62-120">Зарезервировано.</span><span class="sxs-lookup"><span data-stu-id="13c62-120">Reserved.</span></span>|  
|`pmThrowOnUnmappableCharUseAssem`|<span data-ttu-id="13c62-121">Зарезервировано.</span><span class="sxs-lookup"><span data-stu-id="13c62-121">Reserved.</span></span>|  
|`pmThrowOnUnmappableCharEnabled`|<span data-ttu-id="13c62-122">Создавать исключение, когда модуль маршалинга взаимодействия встречает несопоставимый символ.</span><span class="sxs-lookup"><span data-stu-id="13c62-122">Throw an exception when the interop marshaler encounters an unmappable character.</span></span>|  
|`pmThrowOnUnmappableCharDisabled`|<span data-ttu-id="13c62-123">Не вызывайте исключение, если модуль маршалинга взаимодействия встречает несопоставимый символ.</span><span class="sxs-lookup"><span data-stu-id="13c62-123">Do not throw an exception when the interop marshaler encounters an unmappable character.</span></span>|  
|`pmThrowOnUnmappableCharMask`|<span data-ttu-id="13c62-124">Зарезервировано</span><span class="sxs-lookup"><span data-stu-id="13c62-124">Reserved</span></span>|  
|`pmSupportsLastError`|<span data-ttu-id="13c62-125">Разрешить вызываемому `SetLastError` методу вызывать функцию Win32 перед возвратом из метода с атрибутом.</span><span class="sxs-lookup"><span data-stu-id="13c62-125">Allow the callee to call the Win32 `SetLastError` function before returning from the attributed method.</span></span>|  
|`pmCallConvMask`|<span data-ttu-id="13c62-126">Зарезервировано</span><span class="sxs-lookup"><span data-stu-id="13c62-126">Reserved</span></span>|  
|`pmCallConvWinapi`|<span data-ttu-id="13c62-127">Используйте соглашение о вызовах платформы по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="13c62-127">Use the default platform calling convention.</span></span> <span data-ttu-id="13c62-128">Например, в Windows значение по умолчанию — `StdCall` и на Windows CE .NET — `Cdecl` .</span><span class="sxs-lookup"><span data-stu-id="13c62-128">For example, on Windows the default is `StdCall` and on Windows CE .NET it is `Cdecl`.</span></span>|  
|`pmCallConvCdecl`|<span data-ttu-id="13c62-129">Используйте `Cdecl` соглашение о вызовах.</span><span class="sxs-lookup"><span data-stu-id="13c62-129">Use the `Cdecl` calling convention.</span></span> <span data-ttu-id="13c62-130">В этом случае вызывающий объект очищает стек.</span><span class="sxs-lookup"><span data-stu-id="13c62-130">In this case, the caller cleans the stack.</span></span> <span data-ttu-id="13c62-131">Это позволяет вызывать функции с `varargs` (то есть функциями, принимающими переменное количество параметров).</span><span class="sxs-lookup"><span data-stu-id="13c62-131">This enables calling functions with `varargs` (that is, functions that accept a variable number of parameters).</span></span>|  
|`pmCallConvStdcall`|<span data-ttu-id="13c62-132">Используйте `StdCall` соглашение о вызовах.</span><span class="sxs-lookup"><span data-stu-id="13c62-132">Use the `StdCall` calling convention.</span></span> <span data-ttu-id="13c62-133">В этом случае вызываемый объект очищает стек.</span><span class="sxs-lookup"><span data-stu-id="13c62-133">In this case, the callee cleans the stack.</span></span> <span data-ttu-id="13c62-134">Это соглашение, используемое по умолчанию для вызова неуправляемых функций с вызовом неуправляемого кода.</span><span class="sxs-lookup"><span data-stu-id="13c62-134">This is the default convention for calling unmanaged functions with platform invoke.</span></span>|  
|`pmCallConvThiscall`|<span data-ttu-id="13c62-135">Используйте `ThisCall` соглашение о вызовах.</span><span class="sxs-lookup"><span data-stu-id="13c62-135">Use the `ThisCall` calling convention.</span></span> <span data-ttu-id="13c62-136">В этом случае первый параметр является `this` указателем и хранится в регистре ECX.</span><span class="sxs-lookup"><span data-stu-id="13c62-136">In this case, the first parameter is the `this` pointer and is stored in register ECX.</span></span> <span data-ttu-id="13c62-137">Другие параметры помещаются в стек.</span><span class="sxs-lookup"><span data-stu-id="13c62-137">Other parameters are pushed on the stack.</span></span> <span data-ttu-id="13c62-138">`ThisCall`Соглашение о вызовах используется для вызова методов для классов, экспортируемых из неуправляемой библиотеки DLL.</span><span class="sxs-lookup"><span data-stu-id="13c62-138">The `ThisCall` calling convention is used to call methods on classes exported from an unmanaged DLL.</span></span>|  
|`pmCallConvFastcall`|<span data-ttu-id="13c62-139">Зарезервировано.</span><span class="sxs-lookup"><span data-stu-id="13c62-139">Reserved.</span></span>|  
|`pmMaxValue`|<span data-ttu-id="13c62-140">Зарезервировано.</span><span class="sxs-lookup"><span data-stu-id="13c62-140">Reserved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="13c62-141">Требования</span><span class="sxs-lookup"><span data-stu-id="13c62-141">Requirements</span></span>  

 <span data-ttu-id="13c62-142">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="13c62-142">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13c62-143">**Заголовок:** Корхдр. h</span><span class="sxs-lookup"><span data-stu-id="13c62-143">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="13c62-144">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="13c62-144">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13c62-145">См. также</span><span class="sxs-lookup"><span data-stu-id="13c62-145">See also</span></span>

- [<span data-ttu-id="13c62-146">Перечисления метаданных</span><span class="sxs-lookup"><span data-stu-id="13c62-146">Metadata Enumerations</span></span>](metadata-enumerations.md)
