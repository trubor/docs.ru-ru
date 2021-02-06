---
description: 'Дополнительные сведения о методе ICorDebugThread:: Жетдебугстате'
title: Метод ICorDebugThread::GetDebugState
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetDebugState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetDebugState
helpviewer_keywords:
- GetDebugState method [.NET Framework debugging]
- ICorDebugThread::GetDebugState method [.NET Framework debugging]
ms.assetid: 9be27b0c-1d99-4722-b0d4-40cf6753ce5c
topic_type:
- apiref
ms.openlocfilehash: 86534dded9b8e931fe2a7e44f1c95dc2ec7b6f0d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99659157"
---
# <a name="icordebugthreadgetdebugstate-method"></a><span data-ttu-id="ccdcd-103">Метод ICorDebugThread::GetDebugState</span><span class="sxs-lookup"><span data-stu-id="ccdcd-103">ICorDebugThread::GetDebugState Method</span></span>

<span data-ttu-id="ccdcd-104">Возвращает текущее состояние отладки этого объекта ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="ccdcd-104">Gets the current debug state of this ICorDebugThread object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ccdcd-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ccdcd-105">Syntax</span></span>  
  
```cpp  
HRESULT GetDebugState (  
    [out] CorDebugThreadState   *pState  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ccdcd-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="ccdcd-106">Parameters</span></span>  

 `pState`  
 <span data-ttu-id="ccdcd-107">заполняет Указатель на побитовую комбинацию значений перечисления Кордебугсреадстате, описывающих текущее состояние отладки этого потока.</span><span class="sxs-lookup"><span data-stu-id="ccdcd-107">[out] A pointer to a bitwise combination of CorDebugThreadState enumeration values that describes the current debug state of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ccdcd-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="ccdcd-108">Remarks</span></span>  

 <span data-ttu-id="ccdcd-109">Если процесс в данный момент остановлен, `pState` представляет состояние отладки, которое существовало для этого потока, если процесс был продолжен, а не фактическое текущее состояние этого потока.</span><span class="sxs-lookup"><span data-stu-id="ccdcd-109">If the process is currently stopped, `pState` represents the debug state that would exist for this thread if the process were to be continued, not the actual current state of this thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ccdcd-110">Требования</span><span class="sxs-lookup"><span data-stu-id="ccdcd-110">Requirements</span></span>  

 <span data-ttu-id="ccdcd-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ccdcd-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ccdcd-112">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ccdcd-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ccdcd-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ccdcd-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ccdcd-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ccdcd-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
