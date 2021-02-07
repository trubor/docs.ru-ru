---
description: 'Дополнительные сведения о методе: Икордебугкомобжектвалуе:: Жеткачединтерфацепоинтерс'
title: Метод ICorDebugComObjectValue::GetCachedInterfacePointers
ms.date: 03/30/2017
api_name:
- ICorDebugComObjectValue::GetCachedInterfacePointers
api_location:
- mscordbi.dll
f1_keywords:
- ICorDebugComObjectValue::GetCachedInterfacePointers
helpviewer_keywords:
- ICorDebugComObjectValue::GetCachedInterfacePointers method [.NET Framework debugging]
- GetCachedInterfacePointers method, ICorDebugComObjectValue interface [.NET Framework debugging]
ms.assetid: 08dbd558-bd39-4263-94c2-71e70687aaf0
topic_type:
- apiref
ms.openlocfilehash: 737d71f6aa903a3dfa97f583b47a322ec074147f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710859"
---
# <a name="icordebugcomobjectvaluegetcachedinterfacepointers-method"></a><span data-ttu-id="5f0f7-103">Метод ICorDebugComObjectValue::GetCachedInterfacePointers</span><span class="sxs-lookup"><span data-stu-id="5f0f7-103">ICorDebugComObjectValue::GetCachedInterfacePointers Method</span></span>

<span data-ttu-id="5f0f7-104">Возвращает необработанные указатели интерфейса, кэшированные в текущей вызываемой оболочке времени выполнения (RCW).</span><span class="sxs-lookup"><span data-stu-id="5f0f7-104">Gets the raw interface pointers cached on the current runtime callable wrapper (RCW).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5f0f7-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="5f0f7-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCachedInterfacePointers(  
    [in] BOOL bIInspectableOnly,  
    [in] ULONG32 celt,  
    [out] ULONG32 *pceltFetched,  
    [out, size_is(celt), length_is(*pceltFetched) CORDB_ADDRESS *ptrs);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5f0f7-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="5f0f7-106">Parameters</span></span>  

 `bIInspectableOnly`  
 <span data-ttu-id="5f0f7-107">окне Значение, указывающее, будет ли метод возвращать только среда выполнения Windows интерфейсы ( `IInspectable` интерфейсы) или все COM-интерфейсы, которые кэшируются вызываемой оболочкой времени выполнения (RCW).</span><span class="sxs-lookup"><span data-stu-id="5f0f7-107">[in] A value that indicates whether the method will return only Windows Runtime interfaces (`IInspectable` interfaces) or all COM interfaces that are cached by the runtime callable wrapper (RCW).</span></span>  
  
 `celt`  
 <span data-ttu-id="5f0f7-108">окне Число объектов, адреса которых необходимо получить.</span><span class="sxs-lookup"><span data-stu-id="5f0f7-108">[in] The number of objects whose addresses are to be retrieved.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="5f0f7-109">заполняет Указатель на число `CORDB_ADDRESS` значений, фактически возвращаемых в `ptrs` .</span><span class="sxs-lookup"><span data-stu-id="5f0f7-109">[out] A pointer to the number of `CORDB_ADDRESS` values actually returned in `ptrs`.</span></span>  
  
 `ptrs`  
 <span data-ttu-id="5f0f7-110">Указатель на начальный адрес массива `CORDB_ADDRESS` значений, содержащих адреса кэшированных объектов интерфейса.</span><span class="sxs-lookup"><span data-stu-id="5f0f7-110">A pointer to the starting address of an array of `CORDB_ADDRESS` values that contain the addresses of cached interface objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5f0f7-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="5f0f7-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5f0f7-112">Требования</span><span class="sxs-lookup"><span data-stu-id="5f0f7-112">Requirements</span></span>  

 <span data-ttu-id="5f0f7-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5f0f7-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5f0f7-114">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5f0f7-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5f0f7-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5f0f7-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5f0f7-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5f0f7-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f0f7-117">См. также</span><span class="sxs-lookup"><span data-stu-id="5f0f7-117">See also</span></span>

- [<span data-ttu-id="5f0f7-118">Интерфейс ICorDebugComObjectValue Interface</span><span class="sxs-lookup"><span data-stu-id="5f0f7-118">ICorDebugComObjectValue Interface</span></span>](icordebugcomobjectvalue-interface.md)
- [<span data-ttu-id="5f0f7-119">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="5f0f7-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
