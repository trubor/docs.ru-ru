---
description: 'Дополнительные сведения о методе: метод ICorDebugProcess5:: EnableNGENPolicy'
title: Метод ICorDebugProcess5::EnableNGENPolicy
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5::EnableNGenPolicy
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnableNGENPolicy
helpviewer_keywords:
- ICorDebugProcess5::EnableNGENPolicy method [.NET Framework debugging]
- EnableNGENPolicy method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: 3b8e15ca-3c72-4685-a937-da4c739cb9e9
topic_type:
- apiref
ms.openlocfilehash: 0f3194893665bfe9fff802a293aaafed8254f2e3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99649927"
---
# <a name="icordebugprocess5enablengenpolicy-method"></a><span data-ttu-id="7e088-103">Метод ICorDebugProcess5::EnableNGENPolicy</span><span class="sxs-lookup"><span data-stu-id="7e088-103">ICorDebugProcess5::EnableNGENPolicy Method</span></span>

<span data-ttu-id="7e088-104">Задает значение, определяющее, как приложение загружает образы в машинном кодах при выполнении в управляемом отладчике.</span><span class="sxs-lookup"><span data-stu-id="7e088-104">Sets a value that determines how an application loads native images while running under a managed debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e088-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="7e088-105">Syntax</span></span>  
  
```cpp  
HRESULT EnableNGENPolicy(  
    [in] CorDebugNGENPolicy ePolicy  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7e088-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="7e088-106">Parameters</span></span>  

 `ePolicy`  
 <span data-ttu-id="7e088-107">окне Константа [кордебугнженполици](cordebugngenpolicy-enumeration.md) , определяющая, как приложение загружает образы в машинном кодах при работе в управляемом отладчике.</span><span class="sxs-lookup"><span data-stu-id="7e088-107">[in] A [CorDebugNGenPolicy](cordebugngenpolicy-enumeration.md) constant that determines how an application loads native images while running under a managed debugger.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7e088-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="7e088-108">Remarks</span></span>  

 <span data-ttu-id="7e088-109">Если политика успешно установлена, метод возвращает значение `S_OK` .</span><span class="sxs-lookup"><span data-stu-id="7e088-109">If the policy is set successfully, the method returns `S_OK`.</span></span> <span data-ttu-id="7e088-110">Если `ePolicy` находится вне диапазона перечисляемых значений, определенных параметром [кордебугнженполици](cordebugngenpolicy-enumeration.md), метод возвращает значение, `E_INVALIDARG` и вызов метода не оказывает никакого влияния.</span><span class="sxs-lookup"><span data-stu-id="7e088-110">If `ePolicy` is outside the range of the enumerated values defined by [CorDebugNGenPolicy](cordebugngenpolicy-enumeration.md), the method returns `E_INVALIDARG` and the method call has no effect.</span></span> <span data-ttu-id="7e088-111">Если не удается обновить политику генератора образов в машинном кодах (Ngen.exe), метод возвращает `E_FAIL` .</span><span class="sxs-lookup"><span data-stu-id="7e088-111">If the policy of the Native Image Generator (Ngen.exe) cannot be updated, the method returns `E_FAIL`.</span></span>  
  
 <span data-ttu-id="7e088-112">`ICorDebugProcess5::EnableNGenPolicy`Метод может быть вызван в любой момент времени существования процесса.</span><span class="sxs-lookup"><span data-stu-id="7e088-112">The `ICorDebugProcess5::EnableNGenPolicy` method can be called at any time during the lifetime of the process.</span></span> <span data-ttu-id="7e088-113">Политика действует для всех модулей, загруженных после установки политики.</span><span class="sxs-lookup"><span data-stu-id="7e088-113">The policy is in effect for any modules that are loaded after the policy is set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e088-114">Требования</span><span class="sxs-lookup"><span data-stu-id="7e088-114">Requirements</span></span>  

 <span data-ttu-id="7e088-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e088-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e088-116">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7e088-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7e088-117">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7e088-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7e088-118">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e088-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e088-119">См. также</span><span class="sxs-lookup"><span data-stu-id="7e088-119">See also</span></span>

- [<span data-ttu-id="7e088-120">Интерфейс ICorDebugProcess5</span><span class="sxs-lookup"><span data-stu-id="7e088-120">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="7e088-121">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="7e088-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="7e088-122">Отладка</span><span class="sxs-lookup"><span data-stu-id="7e088-122">Debugging</span></span>](index.md)
