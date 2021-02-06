---
description: 'Дополнительные сведения о: интерфейс метод ICorDebugProcess5'
title: Интерфейс ICorDebugProcess5
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5
helpviewer_keywords:
- ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: 30a39d79-1f10-4328-9c5d-094ed824e2ba
topic_type:
- apiref
ms.openlocfilehash: 880c305c1d9786f87d9727836a973696aa686ecf
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99649771"
---
# <a name="icordebugprocess5-interface"></a><span data-ttu-id="068e9-103">Интерфейс ICorDebugProcess5</span><span class="sxs-lookup"><span data-stu-id="068e9-103">ICorDebugProcess5 Interface</span></span>

<span data-ttu-id="068e9-104">Расширяет интерфейс ICorDebugProcess для поддержки доступа к управляемой куче, предоставляет сведения о сборке мусора управляемых объектов и определяет, загружает ли отладчик изображения из локального кэша образов в машинном код.</span><span class="sxs-lookup"><span data-stu-id="068e9-104">Extends the ICorDebugProcess interface to support access to the managed heap, to provide information about garbage collection of managed objects, and to determine whether a debugger loads images from the application local native image cache.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="068e9-105">Методы</span><span class="sxs-lookup"><span data-stu-id="068e9-105">Methods</span></span>  
  
|<span data-ttu-id="068e9-106">Метод</span><span class="sxs-lookup"><span data-stu-id="068e9-106">Method</span></span>|<span data-ttu-id="068e9-107">Описание</span><span class="sxs-lookup"><span data-stu-id="068e9-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="068e9-108">Метод EnableNGenPolicy</span><span class="sxs-lookup"><span data-stu-id="068e9-108">EnableNGenPolicy Method</span></span>](icordebugprocess5-enablengenpolicy-method.md)|<span data-ttu-id="068e9-109">Задает значение, определяющее, как приложение загружает образы в машинном кодах при выполнении в управляемом отладчике.</span><span class="sxs-lookup"><span data-stu-id="068e9-109">Sets a value that determines how an application loads native images while running under a managed debugger.</span></span>|  
|[<span data-ttu-id="068e9-110">Метод EnumerateGCReferences</span><span class="sxs-lookup"><span data-stu-id="068e9-110">EnumerateGCReferences Method</span></span>](icordebugprocess5-enumerategcreferences-method.md)|<span data-ttu-id="068e9-111">Возвращает перечислитель для всех объектов, которые должны быть собраны в процессе сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="068e9-111">Gets an enumerator for all objects that are to be garbage-collected in a process.</span></span>|  
|[<span data-ttu-id="068e9-112">Метод EnumerateHandles</span><span class="sxs-lookup"><span data-stu-id="068e9-112">EnumerateHandles Method</span></span>](icordebugprocess5-enumeratehandles-method.md)|<span data-ttu-id="068e9-113">Возвращает перечислитель для дескрипторов объектов в процессе.</span><span class="sxs-lookup"><span data-stu-id="068e9-113">Gets an enumerator for object handles in a process.</span></span>|  
|[<span data-ttu-id="068e9-114">Метод EnumerateHeap</span><span class="sxs-lookup"><span data-stu-id="068e9-114">EnumerateHeap Method</span></span>](icordebugprocess5-enumerateheap-method.md)|<span data-ttu-id="068e9-115">Возвращает перечислитель для объектов в управляемой куче.</span><span class="sxs-lookup"><span data-stu-id="068e9-115">Gets an enumerator for objects on the managed heap.</span></span>|  
|[<span data-ttu-id="068e9-116">Метод EnumerateHeapRegions</span><span class="sxs-lookup"><span data-stu-id="068e9-116">EnumerateHeapRegions Method</span></span>](icordebugprocess5-enumerateheapregions-method.md)|<span data-ttu-id="068e9-117">Возвращает перечислитель для регионов управляемой кучи.</span><span class="sxs-lookup"><span data-stu-id="068e9-117">Gets an enumerator for regions of the managed heap.</span></span>|  
|[<span data-ttu-id="068e9-118">Метод GetArrayLayout</span><span class="sxs-lookup"><span data-stu-id="068e9-118">GetArrayLayout Method</span></span>](icordebugprocess5-getarraylayout-method.md)|<span data-ttu-id="068e9-119">Возвращает сведения о макете массива в памяти.</span><span class="sxs-lookup"><span data-stu-id="068e9-119">Gets information about the layout of an array in memory.</span></span>|  
|[<span data-ttu-id="068e9-120">Метод GetGCHeapInformation</span><span class="sxs-lookup"><span data-stu-id="068e9-120">GetGCHeapInformation Method</span></span>](icordebugprocess5-getgcheapinformation-method.md)|<span data-ttu-id="068e9-121">Возвращает указатель на структуру [COR_HEAPINFO](cor-heapinfo-structure.md) , содержащую сведения об объектах, которые должны быть собраны сборщиком мусора в управляемой куче.</span><span class="sxs-lookup"><span data-stu-id="068e9-121">Gets a pointer to a [COR_HEAPINFO](cor-heapinfo-structure.md) structure that contains information about objects that are to be garbage-collected on the managed heap.</span></span>|  
|[<span data-ttu-id="068e9-122">Метод GetObject</span><span class="sxs-lookup"><span data-stu-id="068e9-122">GetObject Method</span></span>](icordebugprocess5-getobject-method.md)|<span data-ttu-id="068e9-123">Возвращает указатель на объект в управляемой куче.</span><span class="sxs-lookup"><span data-stu-id="068e9-123">Gets a pointer to an object on the managed heap.</span></span>|  
|[<span data-ttu-id="068e9-124">Метод GetTypeFields</span><span class="sxs-lookup"><span data-stu-id="068e9-124">GetTypeFields Method</span></span>](icordebugprocess5-gettypefields-method.md)|<span data-ttu-id="068e9-125">Возвращает указатель на массив, содержащий сведения о поле для типа на основе его идентификатора типа.</span><span class="sxs-lookup"><span data-stu-id="068e9-125">Gets a pointer to an array that contains field information for a type based on its type identifier.</span></span>|  
|[<span data-ttu-id="068e9-126">Метод GetTypeForTypeID</span><span class="sxs-lookup"><span data-stu-id="068e9-126">GetTypeForTypeID Method</span></span>](icordebugprocess5-gettypefortypeid-method.md)|<span data-ttu-id="068e9-127">Возвращает объект типа, предоставляющий сведения об объекте на основе его идентификаторов типов.</span><span class="sxs-lookup"><span data-stu-id="068e9-127">Gets a type object that provides information about an object based on its type identifiers.</span></span>|  
|[<span data-ttu-id="068e9-128">Метод GetTypeID</span><span class="sxs-lookup"><span data-stu-id="068e9-128">GetTypeID Method</span></span>](icordebugprocess5-gettypeid-method.md)|<span data-ttu-id="068e9-129">Возвращает идентификатор типа для объекта по указанному адресу.</span><span class="sxs-lookup"><span data-stu-id="068e9-129">Gets the type identifier for the object at a specified address.</span></span>|  
|[<span data-ttu-id="068e9-130">Метод GetTypeLayout</span><span class="sxs-lookup"><span data-stu-id="068e9-130">GetTypeLayout Method</span></span>](icordebugprocess5-gettypelayout-method.md)|<span data-ttu-id="068e9-131">Возвращает сведения о макете объекта в памяти на основе его идентификатора типа.</span><span class="sxs-lookup"><span data-stu-id="068e9-131">Gets information about the layout of an object in memory based on its type identifier.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="068e9-132">Remarks</span><span class="sxs-lookup"><span data-stu-id="068e9-132">Remarks</span></span>  

 <span data-ttu-id="068e9-133">Этот интерфейс логически расширяет интерфейсы ICorDebugProcess, ICorDebugProcess2 и [ICorDebugProcess3](icordebugprocess3-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="068e9-133">This interface logically extends the ICorDebugProcess, ICorDebugProcess2, and [ICorDebugProcess3](icordebugprocess3-interface.md) interfaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="068e9-134">Этот интерфейс не поддерживает удаленный вызов на другом компьютере или другом процессе.</span><span class="sxs-lookup"><span data-stu-id="068e9-134">This interface does not support being called remotely, either from another machine or from another process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="068e9-135">Требования</span><span class="sxs-lookup"><span data-stu-id="068e9-135">Requirements</span></span>  

 <span data-ttu-id="068e9-136">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="068e9-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="068e9-137">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="068e9-137">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="068e9-138">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="068e9-138">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="068e9-139">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="068e9-139">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="068e9-140">См. также</span><span class="sxs-lookup"><span data-stu-id="068e9-140">See also</span></span>

- [<span data-ttu-id="068e9-141">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="068e9-141">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="068e9-142">Отладка</span><span class="sxs-lookup"><span data-stu-id="068e9-142">Debugging</span></span>](index.md)
