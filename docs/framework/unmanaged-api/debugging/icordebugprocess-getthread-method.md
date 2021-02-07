---
description: 'Дополнительные сведения о методе: ICorDebugProcess:: Thread'
title: Метод ICorDebugProcess::GetThread
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.GetThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::GetThread
helpviewer_keywords:
- ICorDebugProcess::GetThread method [.NET Framework debugging]
- GetThread method, ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: a48261ed-700b-41c9-8cb4-18c526546603
topic_type:
- apiref
ms.openlocfilehash: bd636df50afd3f12901c1b48559c44ac6ad0cb81
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99746910"
---
# <a name="icordebugprocessgetthread-method"></a><span data-ttu-id="7e2a3-103">Метод ICorDebugProcess::GetThread</span><span class="sxs-lookup"><span data-stu-id="7e2a3-103">ICorDebugProcess::GetThread Method</span></span>

<span data-ttu-id="7e2a3-104">Возвращает поток этого процесса с указанным ИДЕНТИФИКАТОРом потока операционной системы (ОС).</span><span class="sxs-lookup"><span data-stu-id="7e2a3-104">Gets this process's thread that has the specified operating system (OS) thread ID.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e2a3-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="7e2a3-105">Syntax</span></span>  
  
```cpp  
HRESULT GetThread(  
    [in] DWORD dwThreadId,  
    [out] ICorDebugThread **ppThread);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7e2a3-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="7e2a3-106">Parameters</span></span>  

 `dwThreadId`  
 <span data-ttu-id="7e2a3-107">окне Идентификатор потока операционной системы для извлекаемого потока.</span><span class="sxs-lookup"><span data-stu-id="7e2a3-107">[in] The OS thread ID of the thread to be retrieved.</span></span>  
  
 `ppThread`  
 <span data-ttu-id="7e2a3-108">заполняет Указатель на адрес объекта ICorDebugThread, представляющего поток.</span><span class="sxs-lookup"><span data-stu-id="7e2a3-108">[out] A pointer to the address of an ICorDebugThread object that represents the thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e2a3-109">Требования</span><span class="sxs-lookup"><span data-stu-id="7e2a3-109">Requirements</span></span>  

 <span data-ttu-id="7e2a3-110">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e2a3-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e2a3-111">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7e2a3-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7e2a3-112">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7e2a3-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7e2a3-113">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e2a3-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
