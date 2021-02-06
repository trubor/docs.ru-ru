---
description: 'Дополнительные сведения о методе ICorDebugThread:: WebMethod'
title: Метод ICorDebugThread::GetProcess
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetProcess
helpviewer_keywords:
- ICorDebugThread::GetProcess method [.NET Framework debugging]
- GetProcess method, ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 163816e7-0739-4566-b3df-cd256be8b8a4
topic_type:
- apiref
ms.openlocfilehash: dac5da30b343ebd17c1b1ebdd6d4cfa38b78f0bd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99658957"
---
# <a name="icordebugthreadgetprocess-method"></a><span data-ttu-id="40944-103">Метод ICorDebugThread::GetProcess</span><span class="sxs-lookup"><span data-stu-id="40944-103">ICorDebugThread::GetProcess Method</span></span>

<span data-ttu-id="40944-104">Возвращает указатель интерфейса на процесс, в котором этот интерфейс формы является частью.</span><span class="sxs-lookup"><span data-stu-id="40944-104">Gets an interface pointer to the process of which this ICorDebugThread forms a part.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40944-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="40944-105">Syntax</span></span>  
  
```cpp  
HRESULT GetProcess (  
    [out] ICorDebugProcess   **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="40944-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="40944-106">Parameters</span></span>  

 `ppProcess`  
 <span data-ttu-id="40944-107">заполняет Указатель на адрес объекта интерфейса ICorDebugProcess, который представляет процесс.</span><span class="sxs-lookup"><span data-stu-id="40944-107">[out] A pointer to the address of an ICorDebugProcess interface object that represents the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40944-108">Требования</span><span class="sxs-lookup"><span data-stu-id="40944-108">Requirements</span></span>  

 <span data-ttu-id="40944-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="40944-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40944-110">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="40944-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="40944-111">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="40944-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="40944-112">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40944-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
