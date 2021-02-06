---
description: 'Дополнительные сведения о методе ICorDebugThread:: GetID'
title: Метод ICorDebugThread::GetID
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetID
helpviewer_keywords:
- ICorDebugThread::GetID method [.NET Framework debugging]
- GetID method, ICorDebugThread interface [.NET Framework debugging]
ms.assetid: f1de4584-92df-42f3-9da4-fca03a1c6821
topic_type:
- apiref
ms.openlocfilehash: d089201527da67299b64cdf074bdd331f22375a1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99659092"
---
# <a name="icordebugthreadgetid-method"></a><span data-ttu-id="0fb86-103">Метод ICorDebugThread::GetID</span><span class="sxs-lookup"><span data-stu-id="0fb86-103">ICorDebugThread::GetID Method</span></span>

<span data-ttu-id="0fb86-104">Возвращает идентификатор текущей операционной системы активной части этого ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="0fb86-104">Gets the current operating system identifier of the active part of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0fb86-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0fb86-105">Syntax</span></span>  
  
```cpp  
HRESULT GetID (  
    [out] DWORD *pdwThreadId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0fb86-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="0fb86-106">Parameters</span></span>  

 `pdwThreadId`  
 <span data-ttu-id="0fb86-107">заполняет Идентификатор потока.</span><span class="sxs-lookup"><span data-stu-id="0fb86-107">[out] The identifier of the thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0fb86-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="0fb86-108">Remarks</span></span>  

 <span data-ttu-id="0fb86-109">Идентификатор операционной системы потенциально может изменяться во время выполнения процесса и может быть другим значением для разных частей потока.</span><span class="sxs-lookup"><span data-stu-id="0fb86-109">The operating system identifier can potentially change during execution of a process, and can be a different value for different parts of the thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0fb86-110">Требования</span><span class="sxs-lookup"><span data-stu-id="0fb86-110">Requirements</span></span>  

 <span data-ttu-id="0fb86-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0fb86-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0fb86-112">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0fb86-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0fb86-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0fb86-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0fb86-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0fb86-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
