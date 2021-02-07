---
description: 'Дополнительные сведения о методе: ICorDebugProcess:: EnableLogMessages'
title: Метод ICorDebugProcess::EnableLogMessages
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.EnableLogMessages
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::EnableLogMessages
helpviewer_keywords:
- ICorDebugProcess::EnableLogMessages method [.NET Framework debugging]
- EnableLogMessages method [.NET Framework debugging]
ms.assetid: 14a4e5a3-3eaf-4f53-9dd1-762726963a23
topic_type:
- apiref
ms.openlocfilehash: d44f1a14611493372c7321feaa14329d5d77b01b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753995"
---
# <a name="icordebugprocessenablelogmessages-method"></a><span data-ttu-id="68d85-103">Метод ICorDebugProcess::EnableLogMessages</span><span class="sxs-lookup"><span data-stu-id="68d85-103">ICorDebugProcess::EnableLogMessages Method</span></span>

<span data-ttu-id="68d85-104">Включает и отключает передачу сообщений журнала отладчику.</span><span class="sxs-lookup"><span data-stu-id="68d85-104">Enables and disables the transmission of log messages to the debugger.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68d85-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="68d85-105">Syntax</span></span>  
  
```cpp  
HRESULT EnableLogMessages([in]BOOL fOnOff);  
```  
  
## <a name="parameters"></a><span data-ttu-id="68d85-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="68d85-106">Parameters</span></span>  

 `fOnOff`  
 <span data-ttu-id="68d85-107">[входные] `true` включает передачу сообщений журнала; `false` отключает передачу.</span><span class="sxs-lookup"><span data-stu-id="68d85-107">[in] `true` enables the transmission of log messages; `false` disables the transmission.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="68d85-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="68d85-108">Remarks</span></span>  

 <span data-ttu-id="68d85-109">Этот метод допустим только после возникновения обратного вызова [ICorDebugManagedCallback:: CreateProcess](icordebugmanagedcallback-createprocess-method.md) .</span><span class="sxs-lookup"><span data-stu-id="68d85-109">This method is valid only after the [ICorDebugManagedCallback::CreateProcess](icordebugmanagedcallback-createprocess-method.md) callback occurs.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68d85-110">Требования</span><span class="sxs-lookup"><span data-stu-id="68d85-110">Requirements</span></span>  

 <span data-ttu-id="68d85-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="68d85-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68d85-112">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="68d85-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="68d85-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="68d85-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="68d85-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68d85-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
