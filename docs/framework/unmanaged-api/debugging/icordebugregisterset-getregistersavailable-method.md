---
description: 'Дополнительные сведения о методе: ICorDebugRegisterSet:: Жетрегистерсаваилабле'
title: Метод ICorDebugRegisterSet::GetRegistersAvailable
ms.date: 03/30/2017
api_name:
- ICorDebugRegisterSet.GetRegistersAvailable
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugRegisterSet::GetRegistersAvailable
helpviewer_keywords:
- ICorDebugRegisterSet::GetRegistersAvailable method [.NET Framework debugging]
- GetRegistersAvailable method, ICorDebugRegisterSet interface [.NET Framework debugging]
ms.assetid: 4ba08ffa-55a2-4662-9d6d-4738f1db60c9
topic_type:
- apiref
ms.openlocfilehash: a1727c594733fe6529fe1e78f341723623b68be2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99690825"
---
# <a name="icordebugregistersetgetregistersavailable-method"></a><span data-ttu-id="82da9-103">Метод ICorDebugRegisterSet::GetRegistersAvailable</span><span class="sxs-lookup"><span data-stu-id="82da9-103">ICorDebugRegisterSet::GetRegistersAvailable Method</span></span>

<span data-ttu-id="82da9-104">Возвращает битовую маску, указывающую, какие регистры в этом [ICorDebugRegisterSet](icordebugregisterset-interface.md) в настоящее время доступны.</span><span class="sxs-lookup"><span data-stu-id="82da9-104">Gets a bit mask indicating which registers in this [ICorDebugRegisterSet](icordebugregisterset-interface.md) are currently available.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82da9-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="82da9-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRegistersAvailable (  
    [out] ULONG64   *pAvailable  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="82da9-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="82da9-106">Parameters</span></span>  

 `pAvailable`  
 <span data-ttu-id="82da9-107">заполняет Битовая маска, указывающая, какие регистры доступны в настоящее время.</span><span class="sxs-lookup"><span data-stu-id="82da9-107">[out] A bit mask that indicates which registers are currently available.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="82da9-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="82da9-108">Remarks</span></span>  

 <span data-ttu-id="82da9-109">Регистр может быть недоступен, если его значение не может быть определено для данной ситуации.</span><span class="sxs-lookup"><span data-stu-id="82da9-109">A register may be unavailable if its value cannot be determined for the given situation.</span></span>  
  
 <span data-ttu-id="82da9-110">Возвращаемая маска содержит бит для каждого регистра (1 << индекс регистра).</span><span class="sxs-lookup"><span data-stu-id="82da9-110">The returned mask contains a bit for each register (1 << the register index).</span></span> <span data-ttu-id="82da9-111">Значение бита равно 1, если регистр доступен, или 0, если он недоступен.</span><span class="sxs-lookup"><span data-stu-id="82da9-111">The bit value is 1 if the register is available, or 0 if it is not available.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="82da9-112">Требования</span><span class="sxs-lookup"><span data-stu-id="82da9-112">Requirements</span></span>  

 <span data-ttu-id="82da9-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="82da9-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="82da9-114">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="82da9-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="82da9-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="82da9-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="82da9-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="82da9-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82da9-117">См. также</span><span class="sxs-lookup"><span data-stu-id="82da9-117">See also</span></span>

- [<span data-ttu-id="82da9-118">Интерфейс ICorDebugRegisterSet</span><span class="sxs-lookup"><span data-stu-id="82da9-118">ICorDebugRegisterSet Interface</span></span>](icordebugregisterset-interface.md)
- [<span data-ttu-id="82da9-119">Интерфейс ICorDebugRegisterSet2</span><span class="sxs-lookup"><span data-stu-id="82da9-119">ICorDebugRegisterSet2 Interface</span></span>](icordebugregisterset2-interface.md)
