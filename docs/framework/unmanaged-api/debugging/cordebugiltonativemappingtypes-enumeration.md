---
description: Дополнительные сведения о перечислении Кордебугилтонативемаппингтипес
title: Перечисление CorDebugIlToNativeMappingTypes
ms.date: 03/30/2017
api_name:
- CorDebugIlToNativeMappingTypes
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugIlToNativeMappingTypes
helpviewer_keywords:
- CorDebugIIToNativeMappingTypes enumeration [.NET Framework debugging]
ms.assetid: c35e2919-42c3-4ba0-ae28-443c35f66f93
topic_type:
- apiref
ms.openlocfilehash: bcca11bf3c7574fe76684f6786d7408c80acfa43
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801638"
---
# <a name="cordebugiltonativemappingtypes-enumeration"></a><span data-ttu-id="310a9-103">Перечисление CorDebugIlToNativeMappingTypes</span><span class="sxs-lookup"><span data-stu-id="310a9-103">CorDebugIlToNativeMappingTypes Enumeration</span></span>

<span data-ttu-id="310a9-104">Указывает, соответствует ли определенный диапазон машинных инструкций, представленный экземпляром структуры COR_DEBUG_IL_TO_NATIVE_MAP, Специальному региону кода.</span><span class="sxs-lookup"><span data-stu-id="310a9-104">Indicates whether a particular range of native instructions, represented by an instance of the COR_DEBUG_IL_TO_NATIVE_MAP structure, corresponds to a special code region.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="310a9-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="310a9-105">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugIlToNativeMappingTypes {  
    NO_MAPPING = -1,  
    PROLOG     = -2,  
    EPILOG     = -3  
} CorDebugIlToNativeMappingTypes;  
```  
  
## <a name="members"></a><span data-ttu-id="310a9-106">Члены</span><span class="sxs-lookup"><span data-stu-id="310a9-106">Members</span></span>  
  
|<span data-ttu-id="310a9-107">Член</span><span class="sxs-lookup"><span data-stu-id="310a9-107">Member</span></span>|<span data-ttu-id="310a9-108">Описание</span><span class="sxs-lookup"><span data-stu-id="310a9-108">Description</span></span>|  
|------------|-----------------|  
|`NO_MAPPING`|<span data-ttu-id="310a9-109">Диапазон машинных инструкций не соответствует ни одной специальной области кода.</span><span class="sxs-lookup"><span data-stu-id="310a9-109">The range of native instructions does not correspond to any special code region.</span></span>|  
|`PROLOG`|<span data-ttu-id="310a9-110">Диапазон машинных инструкций соответствует прологу.</span><span class="sxs-lookup"><span data-stu-id="310a9-110">The range of native instructions corresponds to the prolog.</span></span>|  
|`EPILOG`|<span data-ttu-id="310a9-111">Диапазон машинных инструкций соответствует заключительному фрагменту.</span><span class="sxs-lookup"><span data-stu-id="310a9-111">The range of native instructions corresponds to the epilog.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="310a9-112">Требования</span><span class="sxs-lookup"><span data-stu-id="310a9-112">Requirements</span></span>  

 <span data-ttu-id="310a9-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="310a9-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="310a9-114">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="310a9-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="310a9-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="310a9-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="310a9-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="310a9-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="310a9-117">См. также</span><span class="sxs-lookup"><span data-stu-id="310a9-117">See also</span></span>

- [<span data-ttu-id="310a9-118">Метод GetILToNativeMapping</span><span class="sxs-lookup"><span data-stu-id="310a9-118">GetILToNativeMapping Method</span></span>](icordebugcode-getiltonativemapping-method.md)
- [<span data-ttu-id="310a9-119">Перечисления отладки</span><span class="sxs-lookup"><span data-stu-id="310a9-119">Debugging Enumerations</span></span>](debugging-enumerations.md)
