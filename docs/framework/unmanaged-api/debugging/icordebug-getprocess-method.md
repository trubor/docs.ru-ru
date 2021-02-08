---
description: 'Дополнительные сведения: метод ICorDebug:: WebMethod'
title: Метод ICorDebug::GetProcess
ms.date: 03/30/2017
api_name:
- ICorDebug.GetProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::GetProcess
helpviewer_keywords:
- GetProcess method, ICorDebug interface [.NET Framework debugging]
- ICorDebug::GetProcess method [.NET Framework debugging]
ms.assetid: 10a40ba0-1b65-4721-bd11-cf12d57b280d
topic_type:
- apiref
ms.openlocfilehash: a24bb0ec645a337b1202b954c165a76bcf8fad9d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801310"
---
# <a name="icordebuggetprocess-method"></a><span data-ttu-id="35ac0-103">Метод ICorDebug::GetProcess</span><span class="sxs-lookup"><span data-stu-id="35ac0-103">ICorDebug::GetProcess Method</span></span>

<span data-ttu-id="35ac0-104">Возвращает указатель на экземпляр "ICorDebugProcess" для указанного процесса.</span><span class="sxs-lookup"><span data-stu-id="35ac0-104">Gets a pointer to the "ICorDebugProcess" instance for the specified process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35ac0-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="35ac0-105">Syntax</span></span>  
  
```cpp  
HRESULT GetProcess (  
    [in] DWORD               dwProcessId,  
    [out] ICorDebugProcess   **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="35ac0-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="35ac0-106">Parameters</span></span>  

 `dwProcessId`  
 <span data-ttu-id="35ac0-107">окне Идентификатор процесса.</span><span class="sxs-lookup"><span data-stu-id="35ac0-107">[in] The ID of the process.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="35ac0-108">заполняет Указатель на адрес `ICorDebugProcess` экземпляра для указанного процесса.</span><span class="sxs-lookup"><span data-stu-id="35ac0-108">[out] A pointer to the address of a `ICorDebugProcess` instance for the specified process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="35ac0-109">Требования</span><span class="sxs-lookup"><span data-stu-id="35ac0-109">Requirements</span></span>  

 <span data-ttu-id="35ac0-110">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="35ac0-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="35ac0-111">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="35ac0-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="35ac0-112">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="35ac0-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="35ac0-113">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="35ac0-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35ac0-114">См. также</span><span class="sxs-lookup"><span data-stu-id="35ac0-114">See also</span></span>

- [<span data-ttu-id="35ac0-115">Интерфейс ICorDebug</span><span class="sxs-lookup"><span data-stu-id="35ac0-115">ICorDebug Interface</span></span>](icordebug-interface.md)
