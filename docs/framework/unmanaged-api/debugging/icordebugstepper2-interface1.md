---
description: 'Дополнительные сведения о: интерфейс ICorDebugStepper2'
title: Интерфейс ICorDebugStepper2
ms.date: 03/30/2017
api_name:
- ICorDebugStepper2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStepper2
helpviewer_keywords:
- ICorDebugStepper2 interface [.NET Framework debugging]
ms.assetid: 7a191c2a-95ea-4d47-83b0-44de2b632d63
topic_type:
- apiref
ms.openlocfilehash: 31e9216535da239573a7a4ecde8cb2e670ad5418
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99717554"
---
# <a name="icordebugstepper2-interface"></a><span data-ttu-id="bef8e-103">Интерфейс ICorDebugStepper2</span><span class="sxs-lookup"><span data-stu-id="bef8e-103">ICorDebugStepper2 Interface</span></span>

<span data-ttu-id="bef8e-104">Обеспечивает поддержку отладки "только мой код" (JMC).</span><span class="sxs-lookup"><span data-stu-id="bef8e-104">Provides support for just my code (JMC) debugging.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bef8e-105">Методы</span><span class="sxs-lookup"><span data-stu-id="bef8e-105">Methods</span></span>  
  
|<span data-ttu-id="bef8e-106">Метод</span><span class="sxs-lookup"><span data-stu-id="bef8e-106">Method</span></span>|<span data-ttu-id="bef8e-107">Описание</span><span class="sxs-lookup"><span data-stu-id="bef8e-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bef8e-108">Метод SetJMC</span><span class="sxs-lookup"><span data-stu-id="bef8e-108">SetJMC Method</span></span>](icordebugstepper2-setjmc-method.md)|<span data-ttu-id="bef8e-109">Задает значение, указывающее, следует ли выполнить шаги для этого параметра ICorDebugStepper только с помощью кода, созданного разработчиком приложения.</span><span class="sxs-lookup"><span data-stu-id="bef8e-109">Sets a value that specifies whether this ICorDebugStepper steps only through code that is authored by an application's developer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bef8e-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="bef8e-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="bef8e-111">Этот интерфейс не поддерживает удаленные вызовы между компьютерами или между процессами.</span><span class="sxs-lookup"><span data-stu-id="bef8e-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bef8e-112">Требования</span><span class="sxs-lookup"><span data-stu-id="bef8e-112">Requirements</span></span>  

 <span data-ttu-id="bef8e-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bef8e-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bef8e-114">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bef8e-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bef8e-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bef8e-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bef8e-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bef8e-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bef8e-117">См. также</span><span class="sxs-lookup"><span data-stu-id="bef8e-117">See also</span></span>

- [<span data-ttu-id="bef8e-118">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="bef8e-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
