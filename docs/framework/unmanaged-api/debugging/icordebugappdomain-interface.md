---
description: 'Дополнительные сведения о: интерфейс ICorDebugAppDomain'
title: Интерфейс ICorDebugAppDomain
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain
api_location:
- corguids.lib
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain
helpviewer_keywords:
- ICorDebugAppDomain interface [.NET Framework debugging]
ms.assetid: be7ae711-1217-4a44-be40-166e29641b77
topic_type:
- apiref
ms.openlocfilehash: 5f1ac20a7376a741da2e34de74c810c0f45e8293
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754203"
---
# <a name="icordebugappdomain-interface"></a><span data-ttu-id="9fcb7-103">Интерфейс ICorDebugAppDomain</span><span class="sxs-lookup"><span data-stu-id="9fcb7-103">ICorDebugAppDomain Interface</span></span>

<span data-ttu-id="9fcb7-104">Предоставляет методы для отладки доменов приложения.</span><span class="sxs-lookup"><span data-stu-id="9fcb7-104">Provides methods for debugging application domains.</span></span> <span data-ttu-id="9fcb7-105">Этот интерфейс является подклассом ICorDebugController.</span><span class="sxs-lookup"><span data-stu-id="9fcb7-105">This interface is a subclass of ICorDebugController.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9fcb7-106">Методы</span><span class="sxs-lookup"><span data-stu-id="9fcb7-106">Methods</span></span>  
  
|<span data-ttu-id="9fcb7-107">Метод</span><span class="sxs-lookup"><span data-stu-id="9fcb7-107">Method</span></span>|<span data-ttu-id="9fcb7-108">Описание</span><span class="sxs-lookup"><span data-stu-id="9fcb7-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9fcb7-109">Метод Attach</span><span class="sxs-lookup"><span data-stu-id="9fcb7-109">Attach Method</span></span>](icordebugappdomain-attach-method.md)|<span data-ttu-id="9fcb7-110">Присоединяет отладчик к домену приложения.</span><span class="sxs-lookup"><span data-stu-id="9fcb7-110">Attaches the debugger to the application domain.</span></span>|  
|[<span data-ttu-id="9fcb7-111">Метод EnumerateAssemblies</span><span class="sxs-lookup"><span data-stu-id="9fcb7-111">EnumerateAssemblies Method</span></span>](icordebugappdomain-enumerateassemblies-method.md)|<span data-ttu-id="9fcb7-112">Возвращает перечислитель для сборок в домене приложения.</span><span class="sxs-lookup"><span data-stu-id="9fcb7-112">Gets an enumerator for the assemblies in the application domain.</span></span>|  
|[<span data-ttu-id="9fcb7-113">Метод EnumerateBreakpoints</span><span class="sxs-lookup"><span data-stu-id="9fcb7-113">EnumerateBreakpoints Method</span></span>](icordebugappdomain-enumeratebreakpoints-method.md)|<span data-ttu-id="9fcb7-114">Возвращает перечислитель для всех активных точек останова в домене приложения.</span><span class="sxs-lookup"><span data-stu-id="9fcb7-114">Gets an enumerator for all active breakpoints in the application domain.</span></span>|  
|[<span data-ttu-id="9fcb7-115">Метод EnumerateSteppers</span><span class="sxs-lookup"><span data-stu-id="9fcb7-115">EnumerateSteppers Method</span></span>](icordebugappdomain-enumeratesteppers-method.md)|<span data-ttu-id="9fcb7-116">Возвращает перечислитель для всех активных шагов в домене приложения.</span><span class="sxs-lookup"><span data-stu-id="9fcb7-116">Gets an enumerator for all active steppers in the application domain.</span></span>|  
|[<span data-ttu-id="9fcb7-117">Метод GetId</span><span class="sxs-lookup"><span data-stu-id="9fcb7-117">GetId Method</span></span>](icordebugappdomain-getid-method.md)|<span data-ttu-id="9fcb7-118">Возвращает уникальный идентификатор домена приложения.</span><span class="sxs-lookup"><span data-stu-id="9fcb7-118">Gets the unique ID of the application domain.</span></span>|  
|[<span data-ttu-id="9fcb7-119">Метод GetModuleFromMetaDataInterface</span><span class="sxs-lookup"><span data-stu-id="9fcb7-119">GetModuleFromMetaDataInterface Method</span></span>](icordebugappdomain-getmodulefrommetadatainterface-method.md)|<span data-ttu-id="9fcb7-120">Возвращает объект ICorDebugModule с заданным интерфейсом метаданных.</span><span class="sxs-lookup"><span data-stu-id="9fcb7-120">Gets the ICorDebugModule object with the given metadata interface.</span></span>|  
|[<span data-ttu-id="9fcb7-121">Метод GetName</span><span class="sxs-lookup"><span data-stu-id="9fcb7-121">GetName Method</span></span>](icordebugappdomain-getname-method.md)|<span data-ttu-id="9fcb7-122">Возвращает имя домена приложения.</span><span class="sxs-lookup"><span data-stu-id="9fcb7-122">Gets the name of the application domain.</span></span>|  
|[<span data-ttu-id="9fcb7-123">Метод GetObject</span><span class="sxs-lookup"><span data-stu-id="9fcb7-123">GetObject Method</span></span>](icordebugappdomain-getobject-method.md)|<span data-ttu-id="9fcb7-124">Возвращает указатель интерфейса на домен приложения среды CLR.</span><span class="sxs-lookup"><span data-stu-id="9fcb7-124">Gets an interface pointer to the common language runtime (CLR) application domain.</span></span>|  
|[<span data-ttu-id="9fcb7-125">Метод GetProcess</span><span class="sxs-lookup"><span data-stu-id="9fcb7-125">GetProcess Method</span></span>](icordebugappdomain-getprocess-method.md)|<span data-ttu-id="9fcb7-126">Возвращает процесс, содержащий домен приложения.</span><span class="sxs-lookup"><span data-stu-id="9fcb7-126">Gets the process containing the application domain.</span></span>|  
|[<span data-ttu-id="9fcb7-127">Метод IsAttached</span><span class="sxs-lookup"><span data-stu-id="9fcb7-127">IsAttached Method</span></span>](icordebugappdomain-isattached-method.md)|<span data-ttu-id="9fcb7-128">Определяет, присоединен ли отладчик к домену приложения.</span><span class="sxs-lookup"><span data-stu-id="9fcb7-128">Determines whether the debugger is attached to the application domain.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9fcb7-129">Remarks</span><span class="sxs-lookup"><span data-stu-id="9fcb7-129">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9fcb7-130">Этот интерфейс не поддерживает удаленные вызовы между компьютерами или между процессами.</span><span class="sxs-lookup"><span data-stu-id="9fcb7-130">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9fcb7-131">Требования</span><span class="sxs-lookup"><span data-stu-id="9fcb7-131">Requirements</span></span>  

 <span data-ttu-id="9fcb7-132">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9fcb7-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9fcb7-133">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9fcb7-133">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9fcb7-134">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9fcb7-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9fcb7-135">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9fcb7-135">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fcb7-136">См. также</span><span class="sxs-lookup"><span data-stu-id="9fcb7-136">See also</span></span>

- [<span data-ttu-id="9fcb7-137">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="9fcb7-137">Debugging Interfaces</span></span>](debugging-interfaces.md)
