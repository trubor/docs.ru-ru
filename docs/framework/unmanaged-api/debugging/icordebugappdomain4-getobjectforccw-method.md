---
description: 'Дополнительные сведения о методе: ICorDebugAppDomain4:: GetObjectForCCW'
title: Метод ICorDebugAppDomain4::GetObjectForCCW
ms.date: 03/30/2017
ms.assetid: 2cacdb85-e7b8-42e7-b310-c3e8c22e5d33
ms.openlocfilehash: 5ba4923c933d02f5d6ad5c1fd8c4d0e2ddb410d3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754138"
---
# <a name="icordebugappdomain4getobjectforccw-method"></a><span data-ttu-id="6742d-103">Метод ICorDebugAppDomain4::GetObjectForCCW</span><span class="sxs-lookup"><span data-stu-id="6742d-103">ICorDebugAppDomain4::GetObjectForCCW Method</span></span>

<span data-ttu-id="6742d-104">Возвращает управляемый объект из вызываемой оболочки COMr (CCW).</span><span class="sxs-lookup"><span data-stu-id="6742d-104">Gets a managed object from a COM callable wrapper (CCW) pointer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6742d-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="6742d-105">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectForCCW(  
   [in]CORDB_ADDRESS ccwPointer,
   [out]ICorDebugValue **ppManagedObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6742d-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="6742d-106">Parameters</span></span>  

 `ccwPointer`  
 <span data-ttu-id="6742d-107">[in] Указатель вызываемой оболочки COM (CCW).</span><span class="sxs-lookup"><span data-stu-id="6742d-107">[in] A COM callable wrapper (CCW) pointer.</span></span>  
  
 `ppManagedObject`  
 <span data-ttu-id="6742d-108">заполняет Указатель на адрес объекта ICorDebugValue, который представляет управляемый объект, соответствующий заданному указателю CCW.</span><span class="sxs-lookup"><span data-stu-id="6742d-108">[out] A pointer to the address of an "ICorDebugValue" object that represents the managed object that corresponds to the given CCW pointer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6742d-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="6742d-109">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6742d-110">Требования</span><span class="sxs-lookup"><span data-stu-id="6742d-110">Requirements</span></span>  

 <span data-ttu-id="6742d-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6742d-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6742d-112">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6742d-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6742d-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6742d-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6742d-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6742d-114">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6742d-115">См. также</span><span class="sxs-lookup"><span data-stu-id="6742d-115">See also</span></span>

- [<span data-ttu-id="6742d-116">Интерфейс ICorDebugAppDomain4</span><span class="sxs-lookup"><span data-stu-id="6742d-116">ICorDebugAppDomain4 Interface</span></span>](icordebugappdomain4-interface.md)
- [<span data-ttu-id="6742d-117">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="6742d-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
