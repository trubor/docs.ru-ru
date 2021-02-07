---
description: 'Дополнительные сведения о методе: ICorDebugProcess:: Модифилогсвитч'
title: Метод ICorDebugProcess::ModifyLogSwitch
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.ModifyLogSwitch
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::ModifyLogSwitch
helpviewer_keywords:
- ICorDebugProcess::ModifyLogSwitch method [.NET Framework debugging]
- ModifyLogSwitch method [.NET Framework debugging]
ms.assetid: 5fd30875-555e-4e96-877b-5dd266cde7c4
topic_type:
- apiref
ms.openlocfilehash: 3c825d6c6b075139793b54526dca696c8fba35a4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99746780"
---
# <a name="icordebugprocessmodifylogswitch-method"></a><span data-ttu-id="d1278-103">Метод ICorDebugProcess::ModifyLogSwitch</span><span class="sxs-lookup"><span data-stu-id="d1278-103">ICorDebugProcess::ModifyLogSwitch Method</span></span>

<span data-ttu-id="d1278-104">Задает уровень серьезности указанного переключателя журнала.</span><span class="sxs-lookup"><span data-stu-id="d1278-104">Sets the severity level of the specified log switch.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1278-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d1278-105">Syntax</span></span>  
  
```cpp  
HRESULT ModifyLogSwitch(  
    [in] WCHAR *pLogSwitchName,  
    [in] LONG  lLevel);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d1278-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="d1278-106">Parameters</span></span>  

 `pLogSwitchName`  
 <span data-ttu-id="d1278-107">окне Указатель на строку, указывающую имя переключателя журнала.</span><span class="sxs-lookup"><span data-stu-id="d1278-107">[in] A pointer to a string that specifies the name of the log switch.</span></span>  
  
 `lLevel`  
 <span data-ttu-id="d1278-108">окне Уровень серьезности, заданный для указанного переключателя журнала.</span><span class="sxs-lookup"><span data-stu-id="d1278-108">[in] The severity level to be set for the specified log switch.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d1278-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="d1278-109">Remarks</span></span>  

 <span data-ttu-id="d1278-110">Этот метод допустим только после выполнения обратного вызова [ICorDebugManagedCallback:: CreateProcess](icordebugmanagedcallback-createprocess-method.md) .</span><span class="sxs-lookup"><span data-stu-id="d1278-110">This method is valid only after the [ICorDebugManagedCallback::CreateProcess](icordebugmanagedcallback-createprocess-method.md) callback has occurred.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1278-111">Требования</span><span class="sxs-lookup"><span data-stu-id="d1278-111">Requirements</span></span>  

 <span data-ttu-id="d1278-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d1278-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1278-113">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d1278-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d1278-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d1278-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d1278-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1278-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
