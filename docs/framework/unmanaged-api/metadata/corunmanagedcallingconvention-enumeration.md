---
description: Дополнительные сведения о перечислении Корунманажедкаллингконвентион
title: Перечисление CorUnmanagedCallingConvention
ms.date: 03/30/2017
api_name:
- CorUnmanagedCallingConvention
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorUnmanagedCallingConvention
helpviewer_keywords:
- CorUnmanagedCallingConvention enumeration [.NET Framework metadata]
ms.assetid: 83058790-160b-4703-a5eb-74b66acbdfa9
topic_type:
- apiref
ms.openlocfilehash: a4b5c70b7dcb4750d641540662941ed3cc08c94b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99707297"
---
# <a name="corunmanagedcallingconvention-enumeration"></a><span data-ttu-id="ca8c8-103">Перечисление CorUnmanagedCallingConvention</span><span class="sxs-lookup"><span data-stu-id="ca8c8-103">CorUnmanagedCallingConvention Enumeration</span></span>

<span data-ttu-id="ca8c8-104">Указывает соглашения о вызовах для неуправляемого кода.</span><span class="sxs-lookup"><span data-stu-id="ca8c8-104">Specifies the calling conventions for unmanaged code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ca8c8-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ca8c8-105">Syntax</span></span>  
  
```cpp  
typedef enum CorUnmanagedCallingConvention {  
  
    IMAGE_CEE_UNMANAGED_CALLCONV_C         = 0x1,  
    IMAGE_CEE_UNMANAGED_CALLCONV_STDCALL   = 0x2,  
    IMAGE_CEE_UNMANAGED_CALLCONV_THISCALL  = 0x3,  
    IMAGE_CEE_UNMANAGED_CALLCONV_FASTCALL  = 0x4,  
  
    IMAGE_CEE_CS_CALLCONV_C                = 0x1,  
    IMAGE_CEE_CS_CALLCONV_STDCALL          = 0x2,  
    IMAGE_CEE_CS_CALLCONV_THISCALL         = 0x3,  
    IMAGE_CEE_CS_CALLCONV_FASTCALL         = 0x4  
  
} CorUnmanagedCallingConvention;  
```  
  
## <a name="members"></a><span data-ttu-id="ca8c8-106">Члены</span><span class="sxs-lookup"><span data-stu-id="ca8c8-106">Members</span></span>  
  
|<span data-ttu-id="ca8c8-107">Член</span><span class="sxs-lookup"><span data-stu-id="ca8c8-107">Member</span></span>|<span data-ttu-id="ca8c8-108">Описание</span><span class="sxs-lookup"><span data-stu-id="ca8c8-108">Description</span></span>|  
|------------|-----------------|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_C`|<span data-ttu-id="ca8c8-109">Соглашение о вызовах языка C.</span><span class="sxs-lookup"><span data-stu-id="ca8c8-109">The C language calling convention.</span></span>|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_STDCALL`|<span data-ttu-id="ca8c8-110">Стандартное соглашение о вызовах.</span><span class="sxs-lookup"><span data-stu-id="ca8c8-110">The standard calling convention.</span></span>|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_THISCALL`|<span data-ttu-id="ca8c8-111">Соглашение о вызовах "this".</span><span class="sxs-lookup"><span data-stu-id="ca8c8-111">The "this" calling convention.</span></span>|  
|`IMAGE_CEE_UNMANAGED_CALLCONV_FASTCALL`|<span data-ttu-id="ca8c8-112">Соглашение о вызовах "Fast".</span><span class="sxs-lookup"><span data-stu-id="ca8c8-112">The "fast" calling convention.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_C`|<span data-ttu-id="ca8c8-113">Не используется.</span><span class="sxs-lookup"><span data-stu-id="ca8c8-113">Not used.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_STDCALL`|<span data-ttu-id="ca8c8-114">Не используется.</span><span class="sxs-lookup"><span data-stu-id="ca8c8-114">Not used.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_THISCALL`|<span data-ttu-id="ca8c8-115">Не используется.</span><span class="sxs-lookup"><span data-stu-id="ca8c8-115">Not used.</span></span>|  
|`IMAGE_CEE_CS_CALLCONV_FASTCALL`|<span data-ttu-id="ca8c8-116">Не используется.</span><span class="sxs-lookup"><span data-stu-id="ca8c8-116">Not used.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ca8c8-117">Remarks</span><span class="sxs-lookup"><span data-stu-id="ca8c8-117">Remarks</span></span>  

 <span data-ttu-id="ca8c8-118">Среда CLR не поддерживает "быстрое" соглашение о вызовах в платформа .NET Framework версии 1,0.</span><span class="sxs-lookup"><span data-stu-id="ca8c8-118">The CLR does not support the "fast" calling convention in the .NET Framework version 1.0.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ca8c8-119">Требования</span><span class="sxs-lookup"><span data-stu-id="ca8c8-119">Requirements</span></span>  

 <span data-ttu-id="ca8c8-120">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ca8c8-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ca8c8-121">**Заголовок:** Корхдр. h</span><span class="sxs-lookup"><span data-stu-id="ca8c8-121">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="ca8c8-122">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ca8c8-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ca8c8-123">См. также</span><span class="sxs-lookup"><span data-stu-id="ca8c8-123">See also</span></span>

- [<span data-ttu-id="ca8c8-124">Перечисления метаданных</span><span class="sxs-lookup"><span data-stu-id="ca8c8-124">Metadata Enumerations</span></span>](metadata-enumerations.md)
