---
description: 'Дополнительные сведения о методе: ICorDebugProcess:: GetID'
title: Метод ICorDebugProcess::GetID
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.GetID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::GetID
helpviewer_keywords:
- GetID method, ICorDebugProcess interface [.NET Framework debugging]
- ICorDebugProcess::GetID method [.NET Framework debugging]
ms.assetid: b0ba8453-fa7e-4c14-93e5-335409cd4a47
topic_type:
- apiref
ms.openlocfilehash: 806e73724a88d08235f4a3e751f771abace1ad56
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99746988"
---
# <a name="icordebugprocessgetid-method"></a><span data-ttu-id="b15c7-103">Метод ICorDebugProcess::GetID</span><span class="sxs-lookup"><span data-stu-id="b15c7-103">ICorDebugProcess::GetID Method</span></span>

<span data-ttu-id="b15c7-104">Возвращает идентификатор операционной системы (ОС) процесса.</span><span class="sxs-lookup"><span data-stu-id="b15c7-104">Gets the operating system (OS) ID of the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b15c7-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b15c7-105">Syntax</span></span>  
  
```cpp  
HRESULT GetID([out] DWORD *pdwProcessId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b15c7-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="b15c7-106">Parameters</span></span>  

 `pdwProcessId`  
 <span data-ttu-id="b15c7-107">заполняет Уникальный идентификатор процесса.</span><span class="sxs-lookup"><span data-stu-id="b15c7-107">[out] The unique ID of the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b15c7-108">Требования</span><span class="sxs-lookup"><span data-stu-id="b15c7-108">Requirements</span></span>  

 <span data-ttu-id="b15c7-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b15c7-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b15c7-110">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b15c7-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b15c7-111">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b15c7-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b15c7-112">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b15c7-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
