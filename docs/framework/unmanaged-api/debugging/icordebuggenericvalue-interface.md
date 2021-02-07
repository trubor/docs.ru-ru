---
description: 'Дополнительные сведения о: Интерфейс ICorDebugGenericValue'
title: Интерфейс ICorDebugGenericValue
ms.date: 03/30/2017
api_name:
- ICorDebugGenericValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGenericValue
helpviewer_keywords:
- ICorDebugGenericValue interface [.NET Framework debugging]
ms.assetid: bc14f408-b359-4c8c-ade2-888ccdf7261b
topic_type:
- apiref
ms.openlocfilehash: 7c81855849d7b72bc509d20072b96bb64f5d395a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99692040"
---
# <a name="icordebuggenericvalue-interface"></a><span data-ttu-id="244d8-103">Интерфейс ICorDebugGenericValue</span><span class="sxs-lookup"><span data-stu-id="244d8-103">ICorDebugGenericValue Interface</span></span>

<span data-ttu-id="244d8-104">Подкласс "ICorDebugValue", который применяется ко всем значениям.</span><span class="sxs-lookup"><span data-stu-id="244d8-104">A subclass of "ICorDebugValue" that applies to all values.</span></span> <span data-ttu-id="244d8-105">Этот интерфейс предоставляет для значения методы Get и Set.</span><span class="sxs-lookup"><span data-stu-id="244d8-105">This interface provides Get and Set methods for the value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="244d8-106">Методы</span><span class="sxs-lookup"><span data-stu-id="244d8-106">Methods</span></span>  
  
|<span data-ttu-id="244d8-107">Метод</span><span class="sxs-lookup"><span data-stu-id="244d8-107">Method</span></span>|<span data-ttu-id="244d8-108">Описание</span><span class="sxs-lookup"><span data-stu-id="244d8-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="244d8-109">Метод GetValue</span><span class="sxs-lookup"><span data-stu-id="244d8-109">GetValue Method</span></span>](icordebuggenericvalue-getvalue-method.md)|<span data-ttu-id="244d8-110">Копирует значение в указанный буфер.</span><span class="sxs-lookup"><span data-stu-id="244d8-110">Copies the value into the specified buffer.</span></span>|  
|[<span data-ttu-id="244d8-111">Метод SetValue</span><span class="sxs-lookup"><span data-stu-id="244d8-111">SetValue Method</span></span>](icordebuggenericvalue-setvalue-method.md)|<span data-ttu-id="244d8-112">Копирует новое значение из указанного буфера.</span><span class="sxs-lookup"><span data-stu-id="244d8-112">Copies a new value from the specified buffer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="244d8-113">Remarks</span><span class="sxs-lookup"><span data-stu-id="244d8-113">Remarks</span></span>  

 <span data-ttu-id="244d8-114">`ICorDebugGenericValue` является подинтерфейсом, так как он не является удаленным.</span><span class="sxs-lookup"><span data-stu-id="244d8-114">`ICorDebugGenericValue` is a sub-interface because it is non-remotable.</span></span>  
  
 <span data-ttu-id="244d8-115">Для ссылочных типов значение является ссылкой, а не содержимым ссылки.</span><span class="sxs-lookup"><span data-stu-id="244d8-115">For reference types, the value is the reference rather than the contents of the reference.</span></span>  
  
 <span data-ttu-id="244d8-116">Этот интерфейс не поддерживает удаленные вызовы между компьютерами или между процессами.</span><span class="sxs-lookup"><span data-stu-id="244d8-116">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="244d8-117">Этот интерфейс не поддерживает удаленные вызовы между компьютерами или между процессами.</span><span class="sxs-lookup"><span data-stu-id="244d8-117">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="244d8-118">Требования</span><span class="sxs-lookup"><span data-stu-id="244d8-118">Requirements</span></span>  

 <span data-ttu-id="244d8-119">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="244d8-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="244d8-120">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="244d8-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="244d8-121">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="244d8-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="244d8-122">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="244d8-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="244d8-123">См. также</span><span class="sxs-lookup"><span data-stu-id="244d8-123">See also</span></span>

- [<span data-ttu-id="244d8-124">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="244d8-124">Debugging Interfaces</span></span>](debugging-interfaces.md)
