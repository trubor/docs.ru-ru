---
description: Дополнительные сведения о перечислении ILCodeKind
title: Перечисление ILCodeKind
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ILCodeKind
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: b91765e4-82db-46f9-a6dc-6b80610276af
topic_type:
- apiref
ms.openlocfilehash: 2d3163b2c601c6f53d9a532fa877c014a67b3e18
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790468"
---
# <a name="ilcodekind-enumeration"></a><span data-ttu-id="48418-103">Перечисление ILCodeKind</span><span class="sxs-lookup"><span data-stu-id="48418-103">ILCodeKind Enumeration</span></span>

<span data-ttu-id="48418-104">[Поддерживается в .NET Framework 4.5.2 и более поздних версиях.]</span><span class="sxs-lookup"><span data-stu-id="48418-104">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="48418-105">Предоставляет значения, которые указывают, может ли отладчик получить доступ к локальным переменным или коду, добавленным в инструментарий ReJIT профилировщика.</span><span class="sxs-lookup"><span data-stu-id="48418-105">Provides values that specify whether the debugger is able to access local variables or code added in profiler ReJIT instrumentation.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48418-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="48418-106">Syntax</span></span>  
  
```cpp
typedef enum ILCodeKind {  
   ILCODE_ORIGINAL_IL = 0x1,  
   ILCODE_REJIT_IL = 0x2,  
} ILCodeKind;  
```  
  
## <a name="members"></a><span data-ttu-id="48418-107">Члены</span><span class="sxs-lookup"><span data-stu-id="48418-107">Members</span></span>  
  
|<span data-ttu-id="48418-108">Имя участника</span><span class="sxs-lookup"><span data-stu-id="48418-108">Member name</span></span>|<span data-ttu-id="48418-109">Описание</span><span class="sxs-lookup"><span data-stu-id="48418-109">Description</span></span>|  
|-----------------|-----------------|  
|`ILCODE_ORIGINAL_IL`|<span data-ttu-id="48418-110">Отладчик не имеет доступа к информации из инструментария ReJIT.</span><span class="sxs-lookup"><span data-stu-id="48418-110">The debugger does not have access to information from ReJIT instrumentation.</span></span>|  
|`ILCODE_REJIT_IL`|<span data-ttu-id="48418-111">Отладчик имеет доступ к информации из инструментария ReJIT.</span><span class="sxs-lookup"><span data-stu-id="48418-111">The debugger has access to information from ReJIT instrumentation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="48418-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="48418-112">Remarks</span></span>  

 <span data-ttu-id="48418-113">Член `ILCodeKind` перечисления может быть передан методам [EnumerateLocalVariablesEx](icordebugilframe4-enumeratelocalvariablesex-method.md) и [GetLocalVariableEx](icordebugilframe4-getlocalvariableex-method.md) , чтобы определить, может ли отладчик получить доступ к переменным, добавленным в инструментарий профилировщика ReJIT, а также к методу [GetCodeEx](icordebugilframe4-getcodeex-method.md) , чтобы определить, может ли отладчик получить доступ к инструментированному IL.</span><span class="sxs-lookup"><span data-stu-id="48418-113">A member of the `ILCodeKind` enumeration can be passed to the [EnumerateLocalVariablesEx](icordebugilframe4-enumeratelocalvariablesex-method.md) and [GetLocalVariableEx](icordebugilframe4-getlocalvariableex-method.md) methods to determine whether the debugger can access variables added in profiler ReJIT instrumentation, and to the [GetCodeEx](icordebugilframe4-getcodeex-method.md) method to determine whether the debugger can access instrumented IL.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48418-114">Требования</span><span class="sxs-lookup"><span data-stu-id="48418-114">Requirements</span></span>  

 <span data-ttu-id="48418-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="48418-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48418-116">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="48418-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="48418-117">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="48418-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="48418-118">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48418-118">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48418-119">См. также</span><span class="sxs-lookup"><span data-stu-id="48418-119">See also</span></span>

- [<span data-ttu-id="48418-120">Перечисления отладки</span><span class="sxs-lookup"><span data-stu-id="48418-120">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="48418-121">Интерфейс ICorDebugILFrame4</span><span class="sxs-lookup"><span data-stu-id="48418-121">ICorDebugILFrame4 Interface</span></span>](icordebugilframe4-interface.md)
- [<span data-ttu-id="48418-122">ReJIT: руководство по How-To</span><span class="sxs-lookup"><span data-stu-id="48418-122">ReJIT: A How-To Guide</span></span>](/archive/blogs/davbr/rejit-a-how-to-guide)
