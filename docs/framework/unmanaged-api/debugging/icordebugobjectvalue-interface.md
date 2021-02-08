---
description: 'Дополнительные сведения о: интерфейс ICorDebugObjectValue'
title: Интерфейс ICorDebugObjectValue
ms.date: 03/30/2017
api_name:
- ICorDebugObjectValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectValue
helpviewer_keywords:
- ICorDebugObjectValue interface [.NET Framework debugging]
ms.assetid: 937de6a0-6fbf-4ddc-80ea-a6217b73e62b
topic_type:
- apiref
ms.openlocfilehash: a2af438bbb4c2f56eb1a72151e339b6b0a978eec
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794778"
---
# <a name="icordebugobjectvalue-interface"></a><span data-ttu-id="9189e-103">Интерфейс ICorDebugObjectValue</span><span class="sxs-lookup"><span data-stu-id="9189e-103">ICorDebugObjectValue Interface</span></span>

<span data-ttu-id="9189e-104">Подкласс "ICorDebugValue", представляющий значение, которое содержит объект.</span><span class="sxs-lookup"><span data-stu-id="9189e-104">A subclass of "ICorDebugValue" that represents a value that contains an object.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9189e-105">Методы</span><span class="sxs-lookup"><span data-stu-id="9189e-105">Methods</span></span>  
  
|<span data-ttu-id="9189e-106">Метод</span><span class="sxs-lookup"><span data-stu-id="9189e-106">Method</span></span>|<span data-ttu-id="9189e-107">Описание</span><span class="sxs-lookup"><span data-stu-id="9189e-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9189e-108">Метод GetClass</span><span class="sxs-lookup"><span data-stu-id="9189e-108">GetClass Method</span></span>](icordebugobjectvalue-getclass-method.md)|<span data-ttu-id="9189e-109">Возвращает указатель интерфейса на общеязыковую среду выполнения (CLR) <xref:System.Type> объекта, `ICorDebugObjectValue` на который ссылается эта ссылка.</span><span class="sxs-lookup"><span data-stu-id="9189e-109">Gets an interface pointer to the common language runtime (CLR) <xref:System.Type> of the object that this `ICorDebugObjectValue` references.</span></span>|  
|[<span data-ttu-id="9189e-110">Метод GetContext</span><span class="sxs-lookup"><span data-stu-id="9189e-110">GetContext Method</span></span>](icordebugobjectvalue-getcontext-method.md)|<span data-ttu-id="9189e-111">Не реализован.</span><span class="sxs-lookup"><span data-stu-id="9189e-111">Not implemented.</span></span>|  
|[<span data-ttu-id="9189e-112">Метод GetFieldValue</span><span class="sxs-lookup"><span data-stu-id="9189e-112">GetFieldValue Method</span></span>](icordebugobjectvalue-getfieldvalue-method.md)|<span data-ttu-id="9189e-113">Возвращает указатель интерфейса на объект [ICorDebugValue](icordebugvalue-interface.md) , представляющий значение указанного поля указанного класса.</span><span class="sxs-lookup"><span data-stu-id="9189e-113">Gets an interface pointer to an [ICorDebugValue](icordebugvalue-interface.md) that represents the value of the specified field of the specified class.</span></span>|  
|[<span data-ttu-id="9189e-114">Метод GetManagedCopy</span><span class="sxs-lookup"><span data-stu-id="9189e-114">GetManagedCopy Method</span></span>](icordebugobjectvalue-getmanagedcopy-method.md)|<span data-ttu-id="9189e-115">Является устаревшей.</span><span class="sxs-lookup"><span data-stu-id="9189e-115">Obsolete.</span></span> <span data-ttu-id="9189e-116">Этот метод не следует вызывать.</span><span class="sxs-lookup"><span data-stu-id="9189e-116">Do not call this method.</span></span>|  
|[<span data-ttu-id="9189e-117">Метод GetVirtualMethod</span><span class="sxs-lookup"><span data-stu-id="9189e-117">GetVirtualMethod Method</span></span>](icordebugobjectvalue-getvirtualmethod-method.md)|<span data-ttu-id="9189e-118">Не реализован.</span><span class="sxs-lookup"><span data-stu-id="9189e-118">Not implemented.</span></span>|  
|[<span data-ttu-id="9189e-119">Метод IsValueClass</span><span class="sxs-lookup"><span data-stu-id="9189e-119">IsValueClass Method</span></span>](icordebugobjectvalue-isvalueclass-method.md)|<span data-ttu-id="9189e-120">Возвращает значение, указывающее, является ли объект, на который ссылается это, `ICorDebugObjectValue` типом значения.</span><span class="sxs-lookup"><span data-stu-id="9189e-120">Gets a value that indicates whether the object referenced by this `ICorDebugObjectValue` is a value type.</span></span>|  
|[<span data-ttu-id="9189e-121">Метод SetFromManagedCopy</span><span class="sxs-lookup"><span data-stu-id="9189e-121">SetFromManagedCopy Method</span></span>](icordebugobjectvalue-setfrommanagedcopy-method.md)|<span data-ttu-id="9189e-122">Является устаревшей.</span><span class="sxs-lookup"><span data-stu-id="9189e-122">Obsolete.</span></span> <span data-ttu-id="9189e-123">Этот метод не следует вызывать.</span><span class="sxs-lookup"><span data-stu-id="9189e-123">Do not call this method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9189e-124">Remarks</span><span class="sxs-lookup"><span data-stu-id="9189e-124">Remarks</span></span>  

 <span data-ttu-id="9189e-125">`ICorDebugObjectValue`Остается действительным до тех пор, пока отлаживаемый процесс не будет продолжен.</span><span class="sxs-lookup"><span data-stu-id="9189e-125">An `ICorDebugObjectValue` remains valid until the process being debugged is continued.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9189e-126">Этот интерфейс не поддерживает удаленные вызовы между компьютерами или между процессами.</span><span class="sxs-lookup"><span data-stu-id="9189e-126">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9189e-127">Требования</span><span class="sxs-lookup"><span data-stu-id="9189e-127">Requirements</span></span>  

 <span data-ttu-id="9189e-128">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9189e-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9189e-129">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9189e-129">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9189e-130">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9189e-130">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9189e-131">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9189e-131">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9189e-132">См. также</span><span class="sxs-lookup"><span data-stu-id="9189e-132">See also</span></span>

- [<span data-ttu-id="9189e-133">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="9189e-133">Debugging Interfaces</span></span>](debugging-interfaces.md)
