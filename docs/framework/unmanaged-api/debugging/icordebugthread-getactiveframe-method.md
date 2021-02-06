---
description: 'Дополнительные сведения о методе ICorDebugThread:: Жетактивефраме'
title: Метод ICorDebugThread::GetActiveFrame
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetActiveFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetActiveFrame
helpviewer_keywords:
- ICorDebugThread::GetActiveFrame method [.NET Framework debugging]
- GetActiveFrame method, ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 8d6d3a1a-fef6-4f2f-a22c-3bdd30d70e07
topic_type:
- apiref
ms.openlocfilehash: 3b15aad39503dfec9ac8f98f839ee1a6b16b3f90
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99659264"
---
# <a name="icordebugthreadgetactiveframe-method"></a><span data-ttu-id="92eda-103">Метод ICorDebugThread::GetActiveFrame</span><span class="sxs-lookup"><span data-stu-id="92eda-103">ICorDebugThread::GetActiveFrame Method</span></span>

<span data-ttu-id="92eda-104">Возвращает указатель интерфейса на активный (самый последний) кадр для этого объекта ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="92eda-104">Gets an interface pointer to the active (most recent) frame on this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92eda-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="92eda-105">Syntax</span></span>  
  
```cpp  
HRESULT GetActiveFrame (  
    [out] ICorDebugFrame   **ppFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="92eda-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="92eda-106">Parameters</span></span>  

 `ppFrame`  
 <span data-ttu-id="92eda-107">заполняет Указатель на адрес объекта интерфейса ICorDebugFrame, который представляет кадр.</span><span class="sxs-lookup"><span data-stu-id="92eda-107">[out] A pointer to the address of an ICorDebugFrame interface object that represents a frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="92eda-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="92eda-108">Remarks</span></span>  

 <span data-ttu-id="92eda-109">`ppFrame`Если в настоящий момент нет активного кадра, параметр имеет значение null.</span><span class="sxs-lookup"><span data-stu-id="92eda-109">The `ppFrame` parameter is null if no frame is currently active.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92eda-110">Требования</span><span class="sxs-lookup"><span data-stu-id="92eda-110">Requirements</span></span>  

 <span data-ttu-id="92eda-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92eda-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92eda-112">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="92eda-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="92eda-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="92eda-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="92eda-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92eda-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
