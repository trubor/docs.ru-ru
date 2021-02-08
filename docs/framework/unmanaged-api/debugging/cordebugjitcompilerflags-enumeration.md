---
description: Дополнительные сведения о перечислении CorDebugJITCompilerFlags
title: Перечисление CorDebugJITCompilerFlags
ms.date: 03/30/2017
api_name:
- CorDebugJITCompilerFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugJITCompilerFlags
helpviewer_keywords:
- CorDebugJITCompilerFlags enumeration [.NET Framework debugging]
ms.assetid: c0774f70-5bed-45e8-9922-fdad778c4c33
topic_type:
- apiref
ms.openlocfilehash: 7e5337293aa4fe446deb12653acd22864eb7679a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801609"
---
# <a name="cordebugjitcompilerflags-enumeration"></a><span data-ttu-id="1f459-103">Перечисление CorDebugJITCompilerFlags</span><span class="sxs-lookup"><span data-stu-id="1f459-103">CorDebugJITCompilerFlags Enumeration</span></span>

<span data-ttu-id="1f459-104">Содержит значения, которые влияют на поведение управляемого JIT-компилятора.</span><span class="sxs-lookup"><span data-stu-id="1f459-104">Contains values that influence the behavior of the managed just-in-time (JIT) compiler.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f459-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="1f459-105">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugJITCompilerFlags {  
  
    CORDEBUG_JIT_DEFAULT = 0x1,  
    CORDEBUG_JIT_DISABLE_OPTIMIZATION = 0x3,  
    CORDEBUG_JIT_ENABLE_ENC = 0x7  
  
} CorDebugJITCompilerFlags;  
```  
  
## <a name="members"></a><span data-ttu-id="1f459-106">Члены</span><span class="sxs-lookup"><span data-stu-id="1f459-106">Members</span></span>  
  
|<span data-ttu-id="1f459-107">Член</span><span class="sxs-lookup"><span data-stu-id="1f459-107">Member</span></span>|<span data-ttu-id="1f459-108">Описание</span><span class="sxs-lookup"><span data-stu-id="1f459-108">Description</span></span>|  
|------------|-----------------|  
|`CORDEBUG_JIT_DEFAULT`|<span data-ttu-id="1f459-109">Указывает, что компилятор должен отслеживанить данные компиляции и допускает оптимизацию.</span><span class="sxs-lookup"><span data-stu-id="1f459-109">Specifies that the compiler should track compilation data, and allows optimizations.</span></span>|  
|`CORDEBUG_JIT_DISABLE_OPTIMIZATION`|<span data-ttu-id="1f459-110">Указывает, что компилятор должен отслеживаниь данных компиляции, но отключает оптимизацию.</span><span class="sxs-lookup"><span data-stu-id="1f459-110">Specifies that the compiler should track compilation data, but disables optimizations.</span></span>|  
|`CORDEBUG_JIT_ENABLE_ENC`|<span data-ttu-id="1f459-111">Указывает, что компилятор должен выполнять трассировку данных компиляции, отключать оптимизации и включать технологии "изменить и продолжить".</span><span class="sxs-lookup"><span data-stu-id="1f459-111">Specifies that the compiler should track compilation data, disables optimizations, and enables Edit and Continue technologies.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="1f459-112">Требования</span><span class="sxs-lookup"><span data-stu-id="1f459-112">Requirements</span></span>  

 <span data-ttu-id="1f459-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1f459-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f459-114">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1f459-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1f459-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1f459-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1f459-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f459-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f459-117">См. также</span><span class="sxs-lookup"><span data-stu-id="1f459-117">See also</span></span>

- [<span data-ttu-id="1f459-118">Перечисления отладки</span><span class="sxs-lookup"><span data-stu-id="1f459-118">Debugging Enumerations</span></span>](debugging-enumerations.md)
