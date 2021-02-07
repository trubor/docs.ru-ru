---
description: Дополнительные сведения о перечислении CorDebugGenerationTypes
title: Перечисление CorDebugGenerationTypes
ms.date: 03/30/2017
api_name:
- CorDebugGenerationTypes
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugGenerationTypes
helpviewer_keywords:
- CorDebugGenerationTypes enumeration [.NET Framework debugging]
ms.assetid: 9f25b64f-eedd-4ae5-8b0e-cfdfb9b6c5d8
topic_type:
- apiref
ms.openlocfilehash: f86b2bc9bf947c6b285c50678f46494005bb5537
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99662134"
---
# <a name="cordebuggenerationtypes-enumeration"></a><span data-ttu-id="fcfbf-103">Перечисление CorDebugGenerationTypes</span><span class="sxs-lookup"><span data-stu-id="fcfbf-103">CorDebugGenerationTypes Enumeration</span></span>

<span data-ttu-id="fcfbf-104">Указывает на создание области памяти в управляемой куче.</span><span class="sxs-lookup"><span data-stu-id="fcfbf-104">Specifies the generation of a region of memory on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fcfbf-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="fcfbf-105">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugGenerationTypes {  
    CorDebug_Gen0 = 0,  
    CorDebug_Gen1 = 1,  
    CorDebug_Gen2 = 2,  
    CorDebug_LOH  = 3,  
} CorDebugRegionTypes;  
```  
  
## <a name="members"></a><span data-ttu-id="fcfbf-106">Члены</span><span class="sxs-lookup"><span data-stu-id="fcfbf-106">Members</span></span>  
  
|<span data-ttu-id="fcfbf-107">Имя участника</span><span class="sxs-lookup"><span data-stu-id="fcfbf-107">Member name</span></span>|<span data-ttu-id="fcfbf-108">Описание</span><span class="sxs-lookup"><span data-stu-id="fcfbf-108">Description</span></span>|  
|-----------------|-----------------|  
|`CorDebug_Gen0`|<span data-ttu-id="fcfbf-109">Поколение 0.</span><span class="sxs-lookup"><span data-stu-id="fcfbf-109">Generation 0.</span></span>|  
|`CorDebug_Gen1`|<span data-ttu-id="fcfbf-110">Поколение 1.</span><span class="sxs-lookup"><span data-stu-id="fcfbf-110">Generation 1.</span></span>|  
|`CorDebug_Gen2`|<span data-ttu-id="fcfbf-111">Поколение 2.</span><span class="sxs-lookup"><span data-stu-id="fcfbf-111">Generation 2.</span></span>|  
|`CorDebug_LOH`|<span data-ttu-id="fcfbf-112">Куча больших объектов.</span><span class="sxs-lookup"><span data-stu-id="fcfbf-112">The large object heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fcfbf-113">Remarks</span><span class="sxs-lookup"><span data-stu-id="fcfbf-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fcfbf-114">Требования</span><span class="sxs-lookup"><span data-stu-id="fcfbf-114">Requirements</span></span>  

 <span data-ttu-id="fcfbf-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fcfbf-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fcfbf-116">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fcfbf-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fcfbf-117">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fcfbf-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fcfbf-118">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fcfbf-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcfbf-119">См. также</span><span class="sxs-lookup"><span data-stu-id="fcfbf-119">See also</span></span>

- [<span data-ttu-id="fcfbf-120">Перечисления отладки</span><span class="sxs-lookup"><span data-stu-id="fcfbf-120">Debugging Enumerations</span></span>](debugging-enumerations.md)
