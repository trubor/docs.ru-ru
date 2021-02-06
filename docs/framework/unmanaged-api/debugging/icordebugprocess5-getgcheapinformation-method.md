---
description: 'Дополнительные сведения о методе: метод ICorDebugProcess5:: GetGCHeapInformation'
title: Метод ICorDebugProcess5::GetGCHeapInformation
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetGCHeapInformation
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetGCHeapInformation
helpviewer_keywords:
- ICorDebugProcess5::GetGCHeapInformation method [.NET Framework debugging]
- GetGCHeapInformation method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: b9538ceb-230a-4079-9cb2-903dbf5c1848
topic_type:
- apiref
ms.openlocfilehash: e63f8871a2c18d6daf2dcf93b92e49123c56442f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99649811"
---
# <a name="icordebugprocess5getgcheapinformation-method"></a><span data-ttu-id="98fee-103">Метод ICorDebugProcess5::GetGCHeapInformation</span><span class="sxs-lookup"><span data-stu-id="98fee-103">ICorDebugProcess5::GetGCHeapInformation Method</span></span>

<span data-ttu-id="98fee-104">Содержит общие сведения о куче сборки мусора, включая возможность перечисления в данный момент.</span><span class="sxs-lookup"><span data-stu-id="98fee-104">Provides general information about the garbage collection heap, including whether it is currently enumerable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98fee-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="98fee-105">Syntax</span></span>  
  
```cpp  
HRESULT GetGCHeapInformation(  
    [out] COR_HEAPINFO *pHeapInfo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="98fee-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="98fee-106">Parameters</span></span>  

 `pHeapInfo`  
 <span data-ttu-id="98fee-107">заполняет Указатель на [COR_HEAPINFO](cor-heapinfo-structure.md) значение, предоставляющее общие сведения о куче сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="98fee-107">[out] A pointer to a [COR_HEAPINFO](cor-heapinfo-structure.md) value that provides general information about the garbage collection heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="98fee-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="98fee-108">Remarks</span></span>  

 <span data-ttu-id="98fee-109">`ICorDebugProcess5::GetGCHeapInformation`Перед перечислением областей кучи или отдельных куч необходимо вызвать метод, чтобы убедиться в том, что структуры сборки мусора в этом процессе являются допустимыми.</span><span class="sxs-lookup"><span data-stu-id="98fee-109">The `ICorDebugProcess5::GetGCHeapInformation` method must be called before enumerating the heap or individual heap regions to ensure that the garbage collection structures in the process are currently valid.</span></span> <span data-ttu-id="98fee-110">Невозможно выполнить обход кучи сборки мусора, пока выполняется сбор.</span><span class="sxs-lookup"><span data-stu-id="98fee-110">The garbage collection heap cannot be walked while a collection is in progress.</span></span> <span data-ttu-id="98fee-111">В противном случае перечисление может собирать недопустимые структуры сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="98fee-111">Otherwise, the enumeration may capture garbage collection structures that are invalid.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98fee-112">Требования</span><span class="sxs-lookup"><span data-stu-id="98fee-112">Requirements</span></span>  

 <span data-ttu-id="98fee-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="98fee-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98fee-114">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="98fee-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="98fee-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="98fee-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="98fee-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98fee-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98fee-117">См. также</span><span class="sxs-lookup"><span data-stu-id="98fee-117">See also</span></span>

- [<span data-ttu-id="98fee-118">Интерфейс ICorDebugProcess5</span><span class="sxs-lookup"><span data-stu-id="98fee-118">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="98fee-119">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="98fee-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
