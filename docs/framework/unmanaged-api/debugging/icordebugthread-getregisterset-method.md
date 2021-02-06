---
description: 'Дополнительные сведения о методе ICorDebugThread:: with Register'
title: Метод ICorDebugThread::GetRegisterSet
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetRegisterSet
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetRegisterSet
helpviewer_keywords:
- ICorDebugThread::GetRegisterSet method [.NET Framework debugging]
- GetRegisterSet method, ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 3b9b6260-98ac-4cfd-88e5-5d7614f94a0c
topic_type:
- apiref
ms.openlocfilehash: f61ccb34eabc1f4d8b8db8a0b78e3ddde9aa136d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99658901"
---
# <a name="icordebugthreadgetregisterset-method"></a><span data-ttu-id="d2fbf-103">Метод ICorDebugThread::GetRegisterSet</span><span class="sxs-lookup"><span data-stu-id="d2fbf-103">ICorDebugThread::GetRegisterSet Method</span></span>

<span data-ttu-id="d2fbf-104">Возвращает указатель интерфейса на набор регистров, связанный с активной частью этого объекта ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="d2fbf-104">Gets an interface pointer to the register set that is associated with the active part of this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d2fbf-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d2fbf-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRegisterSet (  
    [out] ICorDebugRegisterSet **ppRegisters  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d2fbf-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="d2fbf-106">Parameters</span></span>  

 `ppRegisters`  
 <span data-ttu-id="d2fbf-107">заполняет Указатель на адрес объекта интерфейса [ICorDebugRegisterSet](icordebugregisterset-interface.md) , представляющий набор регистров для активной части этого потока.</span><span class="sxs-lookup"><span data-stu-id="d2fbf-107">[out] A pointer to the address of an [ICorDebugRegisterSet](icordebugregisterset-interface.md) interface object that represents the register set for the active part of this thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d2fbf-108">Требования</span><span class="sxs-lookup"><span data-stu-id="d2fbf-108">Requirements</span></span>  

 <span data-ttu-id="d2fbf-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d2fbf-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d2fbf-110">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d2fbf-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d2fbf-111">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d2fbf-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d2fbf-112">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d2fbf-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
