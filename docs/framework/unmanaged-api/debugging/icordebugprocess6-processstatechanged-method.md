---
description: 'Дополнительные сведения о методе: ICorDebugProcess6::P Роцессстатечанжед'
title: Метод ICorDebugProcess6::ProcessStateChanged
ms.date: 03/30/2017
ms.assetid: fb6d30d9-54f3-462b-8ebf-ce0440791ad5
ms.openlocfilehash: 8060c29598adf5d4bbe7bffb4cd6611ee19a2669
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99691371"
---
# <a name="icordebugprocess6processstatechanged-method"></a><span data-ttu-id="b8fc3-103">Метод ICorDebugProcess6::ProcessStateChanged</span><span class="sxs-lookup"><span data-stu-id="b8fc3-103">ICorDebugProcess6::ProcessStateChanged Method</span></span>

<span data-ttu-id="b8fc3-104">Уведомляет [ICorDebug](icordebug-interface.md) о том, что процесс выполняется.</span><span class="sxs-lookup"><span data-stu-id="b8fc3-104">Notifies [ICorDebug](icordebug-interface.md) that the process is running.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8fc3-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b8fc3-105">Syntax</span></span>  
  
```cpp  
HRESULT ProcessStateChanged(   [in] CorDebugStateChange change);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b8fc3-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="b8fc3-106">Parameters</span></span>  

 `change`  
 <span data-ttu-id="b8fc3-107">окне Член перечисления [ProcessStateChanged](icordebugprocess6-processstatechanged-method.md)</span><span class="sxs-lookup"><span data-stu-id="b8fc3-107">[in] A member of the [ProcessStateChanged](icordebugprocess6-processstatechanged-method.md) enumeration</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b8fc3-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="b8fc3-108">Remarks</span></span>  

 <span data-ttu-id="b8fc3-109">Отладчик вызывает этот метод, чтобы уведомить [ICorDebug](icordebug-interface.md) о том, что процесс выполняется.</span><span class="sxs-lookup"><span data-stu-id="b8fc3-109">The debugger calls this method to notify [ICorDebug](icordebug-interface.md) that the process is running.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b8fc3-110">Этот метод доступен только в машинном коде .NET.</span><span class="sxs-lookup"><span data-stu-id="b8fc3-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8fc3-111">Требования</span><span class="sxs-lookup"><span data-stu-id="b8fc3-111">Requirements</span></span>  

 <span data-ttu-id="b8fc3-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b8fc3-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8fc3-113">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b8fc3-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b8fc3-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b8fc3-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b8fc3-115">**Платформа .NET Framework версии:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b8fc3-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8fc3-116">См. также</span><span class="sxs-lookup"><span data-stu-id="b8fc3-116">See also</span></span>

- [<span data-ttu-id="b8fc3-117">Интерфейс ICorDebugProcess6</span><span class="sxs-lookup"><span data-stu-id="b8fc3-117">ICorDebugProcess6 Interface</span></span>](icordebugprocess6-interface.md)
- [<span data-ttu-id="b8fc3-118">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="b8fc3-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
