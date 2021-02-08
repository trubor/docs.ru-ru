---
description: Дополнительные сведения о перечислении Кордебугунмаппедстоп
title: Перечисление CorDebugUnmappedStop
ms.date: 03/30/2017
api_name:
- CorDebugUnmappedStop
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugUnmappedStop
helpviewer_keywords:
- CorDebugUnmappedStop enumeration [.NET Framework debugging]
ms.assetid: a684f7d7-d0c2-4690-b721-639e613f11f8
topic_type:
- apiref
ms.openlocfilehash: 9c4f70c5de451689f98a1c08627fd6df5128fdbd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801531"
---
# <a name="cordebugunmappedstop-enumeration"></a><span data-ttu-id="b8b91-103">Перечисление CorDebugUnmappedStop</span><span class="sxs-lookup"><span data-stu-id="b8b91-103">CorDebugUnmappedStop Enumeration</span></span>

<span data-ttu-id="b8b91-104">Указывает тип несопоставимого кода, который может привести к прерыванию выполнения кода пошаговым средством.</span><span class="sxs-lookup"><span data-stu-id="b8b91-104">Specifies the type of unmapped code that can trigger a halt in code execution by the stepper.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8b91-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b8b91-105">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugUnmappedStop {  
    STOP_NONE               = 0x0,  
    STOP_PROLOG             = 0x01,  
    STOP_EPILOG             = 0x02,  
    STOP_NO_MAPPING_INFO    = 0x04,  
    STOP_OTHER_UNMAPPED     = 0x08,  
    STOP_UNMANAGED          = 0x10,  
    STOP_ALL                = 0xffff,  
} CorDebugUnmappedStop;  
```  
  
## <a name="members"></a><span data-ttu-id="b8b91-106">Члены</span><span class="sxs-lookup"><span data-stu-id="b8b91-106">Members</span></span>  
  
|<span data-ttu-id="b8b91-107">Член</span><span class="sxs-lookup"><span data-stu-id="b8b91-107">Member</span></span>|<span data-ttu-id="b8b91-108">Описание</span><span class="sxs-lookup"><span data-stu-id="b8b91-108">Description</span></span>|  
|------------|-----------------|  
|`STOP_NONE`|<span data-ttu-id="b8b91-109">Не останавливайте в любом типе несопоставленного кода.</span><span class="sxs-lookup"><span data-stu-id="b8b91-109">Do not stop in any type of unmapped code.</span></span>|  
|`STOP_PROLOG`|<span data-ttu-id="b8b91-110">Останавливает в коде пролога.</span><span class="sxs-lookup"><span data-stu-id="b8b91-110">Stop in prolog code.</span></span>|  
|`STOP_EPILOG`|<span data-ttu-id="b8b91-111">Прерывать в коде эпилога.</span><span class="sxs-lookup"><span data-stu-id="b8b91-111">Stop in epilog code.</span></span>|  
|`STOP_NO_MAPPING_INFO`|<span data-ttu-id="b8b91-112">Прерывать в коде, не имеющем сведений о сопоставлении.</span><span class="sxs-lookup"><span data-stu-id="b8b91-112">Stop in code that has no mapping information.</span></span>|  
|`STOP_OTHER_UNMAPPED`|<span data-ttu-id="b8b91-113">Прерывать в несопоставленном коде, который не помещается ни в прологе, ни в том, ни в какую информацию, ни в неуправляемой категории.</span><span class="sxs-lookup"><span data-stu-id="b8b91-113">Stop in unmapped code that does not fit into the prolog, epilog, no-mapping-information, or unmanaged category.</span></span>|  
|`STOP_UNMANAGED`|<span data-ttu-id="b8b91-114">Останавливает в неуправляемом коде.</span><span class="sxs-lookup"><span data-stu-id="b8b91-114">Stop in unmanaged code.</span></span> <span data-ttu-id="b8b91-115">Это значение допустимо только при отладке взаимодействия.</span><span class="sxs-lookup"><span data-stu-id="b8b91-115">This value is valid only with interop debugging.</span></span>|  
|`STOP_ALL`|<span data-ttu-id="b8b91-116">Останавливаются во всех типах несопоставленного кода.</span><span class="sxs-lookup"><span data-stu-id="b8b91-116">Stop in all types of unmapped code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b8b91-117">Remarks</span><span class="sxs-lookup"><span data-stu-id="b8b91-117">Remarks</span></span>  

 <span data-ttu-id="b8b91-118">Используйте метод [ICorDebugStepper:: сетунмаппедстопмаск](icordebugstepper-setunmappedstopmask-method.md) , чтобы задать флаги, указывающие Несопоставленный код, в котором будет останавливаться средство Организации.</span><span class="sxs-lookup"><span data-stu-id="b8b91-118">Use the [ICorDebugStepper::SetUnmappedStopMask](icordebugstepper-setunmappedstopmask-method.md) method to set the flags that specify the unmapped code in which the stepper will stop.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8b91-119">Требования</span><span class="sxs-lookup"><span data-stu-id="b8b91-119">Requirements</span></span>  

 <span data-ttu-id="b8b91-120">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b8b91-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8b91-121">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b8b91-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b8b91-122">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b8b91-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b8b91-123">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8b91-123">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8b91-124">См. также</span><span class="sxs-lookup"><span data-stu-id="b8b91-124">See also</span></span>

- [<span data-ttu-id="b8b91-125">Перечисления отладки</span><span class="sxs-lookup"><span data-stu-id="b8b91-125">Debugging Enumerations</span></span>](debugging-enumerations.md)
