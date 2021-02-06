---
description: 'Дополнительные сведения о методе: метод ICorDebugProcess5:: Енумератехеапрегионс'
title: Метод ICorDebugProcess5::EnumerateHeapRegions
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.EnumerateHeapRegions
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnumerateHeapRegions
helpviewer_keywords:
- EnumerateHeapRegions method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateHeapRegions method [.NET Framework debugging]
ms.assetid: b1edba68-9c36-4f69-be9f-678ce0b33480
topic_type:
- apiref
ms.openlocfilehash: 034b1ebcd003e6854fa4f308b0464aac0a8c4839
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99649849"
---
# <a name="icordebugprocess5enumerateheapregions-method"></a><span data-ttu-id="1e2ce-103">Метод ICorDebugProcess5::EnumerateHeapRegions</span><span class="sxs-lookup"><span data-stu-id="1e2ce-103">ICorDebugProcess5::EnumerateHeapRegions Method</span></span>

<span data-ttu-id="1e2ce-104">Возвращает перечислитель для диапазонов памяти управляемой кучи.</span><span class="sxs-lookup"><span data-stu-id="1e2ce-104">Gets an enumerator for the memory ranges of the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e2ce-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="1e2ce-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateHeapRegions(  
   [out] ICorDebugHeapSegmentEnum **ppRegions  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1e2ce-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="1e2ce-106">Parameters</span></span>  

 `ppRegions`  
 <span data-ttu-id="1e2ce-107">заполняет Указатель на адрес объекта интерфейса [икордебугхеапсегментенум](icordebugheapsegmentenum-interface.md) , который является перечислителем для диапазонов памяти, в которых объекты находятся в управляемой куче.</span><span class="sxs-lookup"><span data-stu-id="1e2ce-107">[out] A pointer to the address of an [ICorDebugHeapSegmentEnum](icordebugheapsegmentenum-interface.md) interface object that is an enumerator for the ranges of memory in which objects reside in the managed heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1e2ce-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="1e2ce-108">Remarks</span></span>  

 <span data-ttu-id="1e2ce-109">Перед вызовом `ICorDebugProcess5::EnumerateHeapRegions` метода необходимо вызвать метод [метод ICorDebugProcess5:: GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md) и проверить значение `areGCStructuresValid` поля возвращенного [COR_HEAPINFO](cor-heapinfo-structure.md) объекта, чтобы гарантировать, что куча сборки мусора в ее текущем состоянии является перечислимым.</span><span class="sxs-lookup"><span data-stu-id="1e2ce-109">Before calling the `ICorDebugProcess5::EnumerateHeapRegions` method, you should call the [ICorDebugProcess5::GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md) method and examine the value of the `areGCStructuresValid` field of the returned [COR_HEAPINFO](cor-heapinfo-structure.md) object to ensure that the garbage collection heap in its current state is enumerable.</span></span> <span data-ttu-id="1e2ce-110">Кроме `ICorDebugProcess5::EnumerateHeapRegions` того, метод возвращает, `E_FAIL` Если вы присоединяетесь слишком рано в течение времени существования процесса до создания областей памяти.</span><span class="sxs-lookup"><span data-stu-id="1e2ce-110">In addition, the `ICorDebugProcess5::EnumerateHeapRegions` method returns `E_FAIL` if you attach too early in the lifetime of the process, before memory regions are created.</span></span>  
  
 <span data-ttu-id="1e2ce-111">Этот метод гарантирует перечисление всех областей памяти, которые могут содержать управляемые объекты, но не гарантирует, что управляемые объекты фактически находятся в этих регионах.</span><span class="sxs-lookup"><span data-stu-id="1e2ce-111">This method is guaranteed to enumerate all memory regions that may contain managed objects, but it does not guarantee that managed objects actually reside in those regions.</span></span> <span data-ttu-id="1e2ce-112">Объект коллекции [икордебугхеапсегментенум](icordebugheapsegmentenum-interface.md) может включать в себя пустые или зарезервированные регионы памяти.</span><span class="sxs-lookup"><span data-stu-id="1e2ce-112">The [ICorDebugHeapSegmentEnum](icordebugheapsegmentenum-interface.md) collection object may include empty or reserved memory regions.</span></span>  
  
 <span data-ttu-id="1e2ce-113">Объект интерфейса [икордебугхеапсегментенум](icordebugheapsegmentenum-interface.md) является стандартным перечислителем, производным от интерфейса ICorDebugEnum, который позволяет перечислить [COR_SEGMENTные](cor-segment-structure.md) объекты.</span><span class="sxs-lookup"><span data-stu-id="1e2ce-113">The [ICorDebugHeapSegmentEnum](icordebugheapsegmentenum-interface.md) interface object is a standard enumerator derived from the ICorDebugEnum interface that allows you to enumerate [COR_SEGMENT](cor-segment-structure.md) objects.</span></span> <span data-ttu-id="1e2ce-114">Каждый объект [COR_SEGMENT](cor-segment-structure.md) предоставляет сведения о диапазоне памяти определенного сегмента вместе с поколением объектов в этом сегменте.</span><span class="sxs-lookup"><span data-stu-id="1e2ce-114">Each [COR_SEGMENT](cor-segment-structure.md) object provides information about the memory range of a particular segment, along with the generation of the objects in that segment.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1e2ce-115">Требования</span><span class="sxs-lookup"><span data-stu-id="1e2ce-115">Requirements</span></span>  

 <span data-ttu-id="1e2ce-116">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1e2ce-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1e2ce-117">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1e2ce-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1e2ce-118">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1e2ce-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1e2ce-119">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1e2ce-119">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e2ce-120">См. также</span><span class="sxs-lookup"><span data-stu-id="1e2ce-120">See also</span></span>

- [<span data-ttu-id="1e2ce-121">Интерфейс ICorDebugProcess5</span><span class="sxs-lookup"><span data-stu-id="1e2ce-121">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="1e2ce-122">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="1e2ce-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
