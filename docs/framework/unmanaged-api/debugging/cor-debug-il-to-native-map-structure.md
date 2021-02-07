---
description: 'Дополнительные сведения: структура COR_DEBUG_IL_TO_NATIVE_MAP'
title: Структура COR_DEBUG_IL_TO_NATIVE_MAP
ms.date: 03/30/2017
api_name:
- COR_DEBUG_IL_TO_NATIVE_MAP
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_DEBUG_IL_TO_NATIVE_MAP
helpviewer_keywords:
- COR_DEBUG_IL_TO_NATIVE_MAP structure [.NET Framework debugging]
ms.assetid: 06f3b504-085f-4142-934a-25381fe23d4c
topic_type:
- apiref
ms.openlocfilehash: ec722b86f95e75d4ac00e04e8a602c6b6da64de5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99747196"
---
# <a name="cor_debug_il_to_native_map-structure"></a><span data-ttu-id="fc2e4-103">Структура COR_DEBUG_IL_TO_NATIVE_MAP</span><span class="sxs-lookup"><span data-stu-id="fc2e4-103">COR_DEBUG_IL_TO_NATIVE_MAP Structure</span></span>

<span data-ttu-id="fc2e4-104">Содержит смещения, которые используются для сопоставления кода MSIL с машинным кодом.</span><span class="sxs-lookup"><span data-stu-id="fc2e4-104">Contains the offsets that are used to map Microsoft intermediate language (MSIL) code to native code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc2e4-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="fc2e4-105">Syntax</span></span>  
  
```cpp  
typedef struct COR_DEBUG_IL_TO_NATIVE_MAP {  
    ULONG32  ilOffset;  
    ULONG32  nativeStartOffset;  
    ULONG32  nativeEndOffset;  
} COR_DEBUG_IL_TO_NATIVE_MAP;  
```  
  
## <a name="members"></a><span data-ttu-id="fc2e4-106">Члены</span><span class="sxs-lookup"><span data-stu-id="fc2e4-106">Members</span></span>  
  
|<span data-ttu-id="fc2e4-107">Член</span><span class="sxs-lookup"><span data-stu-id="fc2e4-107">Member</span></span>|<span data-ttu-id="fc2e4-108">Описание</span><span class="sxs-lookup"><span data-stu-id="fc2e4-108">Description</span></span>|  
|------------|-----------------|  
|`ilOffset`|<span data-ttu-id="fc2e4-109">Смещение кода MSIL.</span><span class="sxs-lookup"><span data-stu-id="fc2e4-109">The offset of the MSIL code.</span></span>|  
|`nativeStartOffset`|<span data-ttu-id="fc2e4-110">Смещение начала машинного кода.</span><span class="sxs-lookup"><span data-stu-id="fc2e4-110">The offset of the start of the native code.</span></span>|  
|`nativeEndOffset`|<span data-ttu-id="fc2e4-111">Смещение конца машинного кода.</span><span class="sxs-lookup"><span data-stu-id="fc2e4-111">The offset of the end of the native code.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fc2e4-112">Требования</span><span class="sxs-lookup"><span data-stu-id="fc2e4-112">Requirements</span></span>  

 <span data-ttu-id="fc2e4-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc2e4-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc2e4-114">**Заголовок:** CorProf. idl, CorDebug. idl</span><span class="sxs-lookup"><span data-stu-id="fc2e4-114">**Header:** CorProf.idl, CorDebug.idl</span></span>  
  
 <span data-ttu-id="fc2e4-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fc2e4-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fc2e4-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc2e4-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc2e4-117">См. также</span><span class="sxs-lookup"><span data-stu-id="fc2e4-117">See also</span></span>

- [<span data-ttu-id="fc2e4-118">Метод GetILToNativeMapping</span><span class="sxs-lookup"><span data-stu-id="fc2e4-118">GetILToNativeMapping Method</span></span>](../profiling/icorprofilerinfo-getiltonativemapping-method.md)
- [<span data-ttu-id="fc2e4-119">Метод GetILToNativeMapping</span><span class="sxs-lookup"><span data-stu-id="fc2e4-119">GetILToNativeMapping Method</span></span>](icordebugcode-getiltonativemapping-method.md)
- [<span data-ttu-id="fc2e4-120">Структуры отладки</span><span class="sxs-lookup"><span data-stu-id="fc2e4-120">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="fc2e4-121">Отладка</span><span class="sxs-lookup"><span data-stu-id="fc2e4-121">Debugging</span></span>](index.md)
