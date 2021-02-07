---
description: Дополнительные сведения о перечислении Кордебугжиткомпилерфлагсдепрекатед
title: Перечисление CorDebugJITCompilerFlagsDeprecated
ms.date: 03/30/2017
api_name:
- CorDebugJITCompilerFlagsDeprecated
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugJITCompilerFlagsDeprecated
helpviewer_keywords:
- CorDebugJITCompilerFlagsDeprecated enumeration [.NET Framework debugging]
ms.assetid: af15e2ca-6be1-472b-bd36-03644a1e3ddd
topic_type:
- apiref
ms.openlocfilehash: ac607766c484a63a757d726826c81d16edd48aae
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99661913"
---
# <a name="cordebugjitcompilerflagsdeprecated-enumeration"></a><span data-ttu-id="ec551-103">Перечисление CorDebugJITCompilerFlagsDeprecated</span><span class="sxs-lookup"><span data-stu-id="ec551-103">CorDebugJITCompilerFlagsDeprecated Enumeration</span></span>

<span data-ttu-id="ec551-104">Это перечисление устарело.</span><span class="sxs-lookup"><span data-stu-id="ec551-104">This enumeration is obsolete.</span></span> <span data-ttu-id="ec551-105">`CORDEBUG_JIT_DEFAULT`Вместо этого используйте член перечисления [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="ec551-105">Use the `CORDEBUG_JIT_DEFAULT` member of the [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) enumeration instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec551-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ec551-106">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugJITCompilerFlagsDeprecated {  
    CORDEBUG_JIT_TRACK_DEBUG_INFO  = 0x1  
} CorDebugJITCompilerFlagsDeprecated;  
```  
  
## <a name="members"></a><span data-ttu-id="ec551-107">Члены</span><span class="sxs-lookup"><span data-stu-id="ec551-107">Members</span></span>  
  
|<span data-ttu-id="ec551-108">Член</span><span class="sxs-lookup"><span data-stu-id="ec551-108">Member</span></span>|<span data-ttu-id="ec551-109">Описание</span><span class="sxs-lookup"><span data-stu-id="ec551-109">Description</span></span>|  
|------------|-----------------|  
|`CORDEBUG_JIT_TRACK_DEBUG_INFO`|<span data-ttu-id="ec551-110">Взамен рекомендуется использовать `CORDEBUG_JIT_DEFAULT`.</span><span class="sxs-lookup"><span data-stu-id="ec551-110">Use `CORDEBUG_JIT_DEFAULT` instead.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ec551-111">Требования</span><span class="sxs-lookup"><span data-stu-id="ec551-111">Requirements</span></span>  

 <span data-ttu-id="ec551-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ec551-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec551-113">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ec551-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ec551-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ec551-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ec551-115">**Платформа .NET Framework версии:** 1,0, 1,1</span><span class="sxs-lookup"><span data-stu-id="ec551-115">**.NET Framework Versions:** 1.0, 1.1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec551-116">См. также</span><span class="sxs-lookup"><span data-stu-id="ec551-116">See also</span></span>

- [<span data-ttu-id="ec551-117">Перечисления отладки</span><span class="sxs-lookup"><span data-stu-id="ec551-117">Debugging Enumerations</span></span>](debugging-enumerations.md)
