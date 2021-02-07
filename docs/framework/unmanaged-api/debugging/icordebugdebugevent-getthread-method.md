---
description: 'Дополнительные сведения о методе: ICorDebugDebugEvent:: Thread'
title: ICorDebugDebugEvent::Метод GetThread
ms.date: 03/30/2017
ms.assetid: 4f2e9a2c-8369-4a07-a881-ad5422626353
ms.openlocfilehash: 1d476603572f31882f481d414e483c6712f1b5fc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710417"
---
# <a name="icordebugdebugeventgetthread-method"></a><span data-ttu-id="33f6b-103">ICorDebugDebugEvent::Метод GetThread</span><span class="sxs-lookup"><span data-stu-id="33f6b-103">ICorDebugDebugEvent::GetThread Method</span></span>

<span data-ttu-id="33f6b-104">Получает поток, в котором произошло событие.</span><span class="sxs-lookup"><span data-stu-id="33f6b-104">Gets the thread on which the event occurred.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33f6b-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="33f6b-105">Syntax</span></span>  
  
```cpp  
HRESULT GetThread(  
        [out]ICorDebugThread **ppThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="33f6b-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="33f6b-106">Parameters</span></span>  

 <span data-ttu-id="33f6b-107">ppThread</span><span class="sxs-lookup"><span data-stu-id="33f6b-107">ppThread</span></span>  
 <span data-ttu-id="33f6b-108">[выходной] Указатель на адрес объекта ICorDebugThread, представляющего поток, в котором произошло событие.</span><span class="sxs-lookup"><span data-stu-id="33f6b-108">[out] A pointer to the address of an ICorDebugThread object that represents the thread on which the event occurred.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="33f6b-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="33f6b-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="33f6b-110">Этот метод доступен только в машинном коде .NET.</span><span class="sxs-lookup"><span data-stu-id="33f6b-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33f6b-111">Требования</span><span class="sxs-lookup"><span data-stu-id="33f6b-111">Requirements</span></span>  

 <span data-ttu-id="33f6b-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="33f6b-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33f6b-113">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="33f6b-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="33f6b-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="33f6b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="33f6b-115">**Платформа .NET Framework версии:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="33f6b-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33f6b-116">См. также</span><span class="sxs-lookup"><span data-stu-id="33f6b-116">See also</span></span>

- [<span data-ttu-id="33f6b-117">Интерфейс ICorDebugDebugEvent</span><span class="sxs-lookup"><span data-stu-id="33f6b-117">ICorDebugDebugEvent Interface</span></span>](icordebugdebugevent-interface.md)
- [<span data-ttu-id="33f6b-118">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="33f6b-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
