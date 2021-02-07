---
description: 'Дополнительные сведения о методе: метод ICorDebugProcess5:: Енумератехеап'
title: Метод ICorDebugProcess5::EnumerateHeap
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.EnumerateHeap
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnumerateHeap
helpviewer_keywords:
- EnumerateHeap method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateHeap method [.NET Framework debugging]
ms.assetid: b0192104-6073-4089-a4df-dc29ee033074
topic_type:
- apiref
ms.openlocfilehash: b43e7993b114ed64d009f91746ea987198edde74
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99722039"
---
# <a name="icordebugprocess5enumerateheap-method"></a><span data-ttu-id="287cd-103">Метод ICorDebugProcess5::EnumerateHeap</span><span class="sxs-lookup"><span data-stu-id="287cd-103">ICorDebugProcess5::EnumerateHeap Method</span></span>

<span data-ttu-id="287cd-104">Возвращает перечислитель для объектов в управляемой куче.</span><span class="sxs-lookup"><span data-stu-id="287cd-104">Gets an enumerator for the objects on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="287cd-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="287cd-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateHeap(  
    [out] ICorDebugHeapEnum **ppObjects  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="287cd-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="287cd-106">Parameters</span></span>  

 `ppObject`  
 <span data-ttu-id="287cd-107">заполняет Указатель на адрес объекта интерфейса [икордебугхеапенум](icordebugheapenum-interface.md) , который является перечислителем для объектов, находящихся в управляемой куче.</span><span class="sxs-lookup"><span data-stu-id="287cd-107">[out] A pointer to the address of an [ICorDebugHeapEnum](icordebugheapenum-interface.md) interface object that is an enumerator for the objects that reside on the managed heap.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="287cd-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="287cd-108">Remarks</span></span>  

 <span data-ttu-id="287cd-109">Перед вызовом `ICorDebugProcess5::EnumerateHeap` метода необходимо вызвать метод [метод ICorDebugProcess5:: GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md) и проверить значение `areGCStructuresValid` поля возвращенного [COR_HEAPINFO](cor-heapinfo-structure.md) объекта, чтобы гарантировать, что куча сборки мусора в ее текущем состоянии является перечислимым.</span><span class="sxs-lookup"><span data-stu-id="287cd-109">Before calling the `ICorDebugProcess5::EnumerateHeap` method, you should call the [ICorDebugProcess5::GetGCHeapInformation](icordebugprocess5-getgcheapinformation-method.md) method and examine the value of the `areGCStructuresValid` field of the returned [COR_HEAPINFO](cor-heapinfo-structure.md) object to ensure that the garbage collection heap in its current state is enumerable.</span></span> <span data-ttu-id="287cd-110">Кроме того, `ICorDebugProcess5::EnumerateHeap` возвращает, `E_FAIL` Если в течение времени существования процесса присоединяется слишком рано, до выделения памяти для управляемой кучи.</span><span class="sxs-lookup"><span data-stu-id="287cd-110">In addition, the `ICorDebugProcess5::EnumerateHeap` returns `E_FAIL` if you attach too early in the lifetime of the process, before memory for the managed heap is allocated.</span></span>  
  
 <span data-ttu-id="287cd-111">Объект интерфейса [икордебугхеапенум](icordebugheapenum-interface.md) является стандартным перечислителем, производным от интерфейса ICorDebugEnum, который позволяет перечислить [COR_HEAPOBJECTные](cor-heapobject-structure.md) объекты.</span><span class="sxs-lookup"><span data-stu-id="287cd-111">The [ICorDebugHeapEnum](icordebugheapenum-interface.md) interface object is a standard enumerator derived from the ICorDebugEnum interface that allows you to enumerate [COR_HEAPOBJECT](cor-heapobject-structure.md) objects.</span></span> <span data-ttu-id="287cd-112">Этот метод заполняет объект коллекции [икордебугхеапенум](icordebugheapenum-interface.md) экземплярами [COR_HEAPOBJECT](cor-heapobject-structure.md) , которые предоставляют сведения обо всех объектах.</span><span class="sxs-lookup"><span data-stu-id="287cd-112">This method populates the [ICorDebugHeapEnum](icordebugheapenum-interface.md) collection object with [COR_HEAPOBJECT](cor-heapobject-structure.md) instances that provide information about all objects.</span></span> <span data-ttu-id="287cd-113">Коллекция может также включать [COR_HEAPOBJECT](cor-heapobject-structure.md) экземпляры, предоставляющие сведения об объектах, которые не находятся в корне ни в одном объекте, но еще не были собраны сборщиком мусора.</span><span class="sxs-lookup"><span data-stu-id="287cd-113">The collection may also include [COR_HEAPOBJECT](cor-heapobject-structure.md) instances that provide information about objects that are not rooted by any object but have not yet been collected by the garbage collector.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="287cd-114">Требования</span><span class="sxs-lookup"><span data-stu-id="287cd-114">Requirements</span></span>  

 <span data-ttu-id="287cd-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="287cd-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="287cd-116">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="287cd-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="287cd-117">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="287cd-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="287cd-118">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="287cd-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="287cd-119">См. также</span><span class="sxs-lookup"><span data-stu-id="287cd-119">See also</span></span>

- [<span data-ttu-id="287cd-120">Интерфейс ICorDebugProcess5</span><span class="sxs-lookup"><span data-stu-id="287cd-120">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="287cd-121">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="287cd-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
