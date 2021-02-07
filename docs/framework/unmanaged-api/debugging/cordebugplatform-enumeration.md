---
description: Дополнительные сведения о перечислении Кордебугплатформ
title: Перечисление CorDebugPlatform
ms.date: 03/30/2017
api_name:
- CorDebugPlatformEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugPlatformEnum
helpviewer_keywords:
- CorDebugPlatformEnum enumeration [.NET Framework debugging]
ms.assetid: c5444816-7378-4521-afd3-bf5e4b5303d5
topic_type:
- apiref
ms.openlocfilehash: d6a78ec00f99ff34158f784e039372c8937e6d16
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99661861"
---
# <a name="cordebugplatform-enumeration"></a><span data-ttu-id="f1bea-103">Перечисление CorDebugPlatform</span><span class="sxs-lookup"><span data-stu-id="f1bea-103">CorDebugPlatform Enumeration</span></span>

<span data-ttu-id="f1bea-104">Предоставляет значения целевой платформы, используемые методом [ICorDebugDataTarget::](icordebugdatatarget-getplatform-method.md) WebMethod.</span><span class="sxs-lookup"><span data-stu-id="f1bea-104">Provides target platform values that are used by the [ICorDebugDataTarget::GetPlatform](icordebugdatatarget-getplatform-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1bea-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f1bea-105">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugPlatform  
{  
    CORDB_PLATFORM_WINDOWS_X86,    // Windows on Intel x86  
    CORDB_PLATFORM_WINDOWS_AMD64,  // Windows x64 (AMD64, Intel EM64T)  
    CORDB_PLATFORM_WINDOWS_IA64,   // Windows on Intel IA-64  
    CORDB_PLATFORM_MAC_PPC,        // Macintosh OS on PowerPC  
    CORDB_PLATFORM_MAC_X86,        // Macintosh OS on Intel x86  
    CORDB_PLATFORM_WINDOWS_ARM,    // Windows on ARM  
    CORDB_PLATFORM_MAC_AMD64       // MacOS on Intel x64  
} CorDebugPlatform;  
```  
  
## <a name="members"></a><span data-ttu-id="f1bea-106">Члены</span><span class="sxs-lookup"><span data-stu-id="f1bea-106">Members</span></span>  
  
|<span data-ttu-id="f1bea-107">Член</span><span class="sxs-lookup"><span data-stu-id="f1bea-107">Member</span></span>|<span data-ttu-id="f1bea-108">Описание</span><span class="sxs-lookup"><span data-stu-id="f1bea-108">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="f1bea-109">CORDB_PLATFORM_WINDOWS_X86</span><span class="sxs-lookup"><span data-stu-id="f1bea-109">CORDB_PLATFORM_WINDOWS_X86</span></span>|<span data-ttu-id="f1bea-110">Целевая платформа — ОС Windows, работающая на процессоре Intel x86.</span><span class="sxs-lookup"><span data-stu-id="f1bea-110">The target platform is Windows running on Intel x86 hardware.</span></span>|  
|<span data-ttu-id="f1bea-111">CORDB_PLATFORM_WINDOWS_AMD64</span><span class="sxs-lookup"><span data-stu-id="f1bea-111">CORDB_PLATFORM_WINDOWS_AMD64</span></span>|<span data-ttu-id="f1bea-112">Целевая платформа — 64-разрядная версия ОС Windows, работающая на процессоре AMD64 или Intel EM64T.</span><span class="sxs-lookup"><span data-stu-id="f1bea-112">The target platform is 64 bit Windows running on AMD64 or Intel EM64T hardware.</span></span>|  
|<span data-ttu-id="f1bea-113">CORDB_PLATFORM_WINDOWS_IA64</span><span class="sxs-lookup"><span data-stu-id="f1bea-113">CORDB_PLATFORM_WINDOWS_IA64</span></span>|<span data-ttu-id="f1bea-114">Целевая платформа — 32-разрядная версия ОС Windows, работающая на процессоре IA-64.</span><span class="sxs-lookup"><span data-stu-id="f1bea-114">The target platform is 32 bit Windows running on Intel IA-64 hardware.</span></span>|  
|<span data-ttu-id="f1bea-115">CORDB_PLATFORM_MAC_PPC</span><span class="sxs-lookup"><span data-stu-id="f1bea-115">CORDB_PLATFORM_MAC_PPC</span></span>|<span data-ttu-id="f1bea-116">Целевая платформа — это операционная система Macintosh, которая работает на оборудовании PowerPC.</span><span class="sxs-lookup"><span data-stu-id="f1bea-116">The target platform is the Macintosh operating system running on PowerPC hardware.</span></span>|  
|<span data-ttu-id="f1bea-117">CORDB_PLATFORM_MAC_X86</span><span class="sxs-lookup"><span data-stu-id="f1bea-117">CORDB_PLATFORM_MAC_X86</span></span>|<span data-ttu-id="f1bea-118">Целевая платформа — это операционная система Macintosh, работающая на оборудовании Intel x86.</span><span class="sxs-lookup"><span data-stu-id="f1bea-118">The target platform is the Macintosh operating system running on Intel x86 hardware.</span></span>|  
|<span data-ttu-id="f1bea-119">CORDB_PLATFORM_WINDOWS_ARM</span><span class="sxs-lookup"><span data-stu-id="f1bea-119">CORDB_PLATFORM_WINDOWS_ARM</span></span>|<span data-ttu-id="f1bea-120">Целевая платформа — это операционная система Macintosh, которая работает на оборудовании Windows ARM.</span><span class="sxs-lookup"><span data-stu-id="f1bea-120">The target platform is the Macintosh operating system running on Windows ARM hardware.</span></span>|  
|<span data-ttu-id="f1bea-121">CORDB_PLATFORM_MAC_AMD64</span><span class="sxs-lookup"><span data-stu-id="f1bea-121">CORDB_PLATFORM_MAC_AMD64</span></span>|<span data-ttu-id="f1bea-122">Целевая платформа — это операционная система Macintosh, работающая на оборудовании AMD64.</span><span class="sxs-lookup"><span data-stu-id="f1bea-122">The target platform is the Macintosh operating system running on AMD64 hardware.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f1bea-123">Требования</span><span class="sxs-lookup"><span data-stu-id="f1bea-123">Requirements</span></span>  

 <span data-ttu-id="f1bea-124">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f1bea-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f1bea-125">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f1bea-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f1bea-126">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f1bea-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f1bea-127">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f1bea-127">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
 <span data-ttu-id="f1bea-128">Члены `CORDB_PLATFORM_WINDOWS_ARM` и `CORDB_PLATFORM_MAC_AMD64` доступны в платформе .NET Framework версии 4.5.2 и более поздних.</span><span class="sxs-lookup"><span data-stu-id="f1bea-128">The `CORDB_PLATFORM_WINDOWS_ARM` and `CORDB_PLATFORM_MAC_AMD64` members are available in the .NET Framework 4.5.2 and later versions.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1bea-129">См. также</span><span class="sxs-lookup"><span data-stu-id="f1bea-129">See also</span></span>

- [<span data-ttu-id="f1bea-130">Перечисления отладки</span><span class="sxs-lookup"><span data-stu-id="f1bea-130">Debugging Enumerations</span></span>](debugging-enumerations.md)
