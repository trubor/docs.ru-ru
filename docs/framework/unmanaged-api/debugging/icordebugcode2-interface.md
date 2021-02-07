---
description: 'Дополнительные сведения о: интерфейс ICorDebugCode2'
title: Интерфейс ICorDebugCode2
ms.date: 03/30/2017
api_name:
- ICorDebugCode2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode2
helpviewer_keywords:
- ICorDebugCode2 interface [.NET Framework debugging]
ms.assetid: 9321903b-7dea-40d8-ba32-99016c00cc46
topic_type:
- apiref
ms.openlocfilehash: 29fd657ec56993d47ee57aa41c81b45e75352697
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99765052"
---
# <a name="icordebugcode2-interface"></a><span data-ttu-id="181fc-103">Интерфейс ICorDebugCode2</span><span class="sxs-lookup"><span data-stu-id="181fc-103">ICorDebugCode2 Interface</span></span>

<span data-ttu-id="181fc-104">Предоставляет методы, расширяющие возможности "ICorDebugCode".</span><span class="sxs-lookup"><span data-stu-id="181fc-104">Provides methods that extend the capabilities of "ICorDebugCode".</span></span>  
  
## <a name="methods"></a><span data-ttu-id="181fc-105">Методы</span><span class="sxs-lookup"><span data-stu-id="181fc-105">Methods</span></span>  
  
|<span data-ttu-id="181fc-106">Метод</span><span class="sxs-lookup"><span data-stu-id="181fc-106">Method</span></span>|<span data-ttu-id="181fc-107">Описание</span><span class="sxs-lookup"><span data-stu-id="181fc-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="181fc-108">Метод GetCodeChunks</span><span class="sxs-lookup"><span data-stu-id="181fc-108">GetCodeChunks Method</span></span>](icordebugcode2-getcodechunks-method.md)|<span data-ttu-id="181fc-109">Возвращает фрагменты кода, из которого состоит этот объект кода.</span><span class="sxs-lookup"><span data-stu-id="181fc-109">Gets the chunks of code that this code object is composed of.</span></span>|  
|[<span data-ttu-id="181fc-110">Метод GetCompilerFlags</span><span class="sxs-lookup"><span data-stu-id="181fc-110">GetCompilerFlags Method</span></span>](icordebugcode2-getcompilerflags-method.md)|<span data-ttu-id="181fc-111">Возвращает флаги, указывающие условия, при которых этот объект кода был либо JIT-скомпилирован, либо создан с помощью генератора образов в машинном коде (Ngen.exe).</span><span class="sxs-lookup"><span data-stu-id="181fc-111">Gets the flags that specify the conditions under which this code object was either just-in-time (JIT) compiled or generated using the native image generator (Ngen.exe).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="181fc-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="181fc-112">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="181fc-113">Этот интерфейс не поддерживает удаленные вызовы между компьютерами или между процессами.</span><span class="sxs-lookup"><span data-stu-id="181fc-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="181fc-114">Требования</span><span class="sxs-lookup"><span data-stu-id="181fc-114">Requirements</span></span>  

 <span data-ttu-id="181fc-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="181fc-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="181fc-116">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="181fc-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="181fc-117">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="181fc-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="181fc-118">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="181fc-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="181fc-119">См. также</span><span class="sxs-lookup"><span data-stu-id="181fc-119">See also</span></span>

- [<span data-ttu-id="181fc-120">Интерфейс ICorDebugCode3</span><span class="sxs-lookup"><span data-stu-id="181fc-120">ICorDebugCode3 Interface</span></span>](icordebugcode3-interface.md)
- [<span data-ttu-id="181fc-121">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="181fc-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
