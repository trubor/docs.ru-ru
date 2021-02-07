---
description: 'Дополнительные сведения о методе: ICorDebugProcess:: EnumerateAppDomains'
title: Метод ICorDebugProcess::EnumerateAppDomains
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.EnumerateAppDomains
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::EnumerateAppDomains
helpviewer_keywords:
- ICorDebugProcess::EnumerateAppDomains method [.NET Framework debugging]
- EnumerateAppDomains method [.NET Framework debugging]
ms.assetid: d508981f-e2b2-445b-a649-69951c22702d
topic_type:
- apiref
ms.openlocfilehash: d212fafe7ae1355ba69e07b88c3b96119371fe43
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99691527"
---
# <a name="icordebugprocessenumerateappdomains-method"></a><span data-ttu-id="0b859-103">Метод ICorDebugProcess::EnumerateAppDomains</span><span class="sxs-lookup"><span data-stu-id="0b859-103">ICorDebugProcess::EnumerateAppDomains Method</span></span>

<span data-ttu-id="0b859-104">Перечисляет все домены приложений в этом процессе.</span><span class="sxs-lookup"><span data-stu-id="0b859-104">Enumerates all the application domains in this process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b859-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0b859-105">Syntax</span></span>  
  
``` cpp
HRESULT EnumerateAppDomains(  
    [out] ICorDebugAppDomainEnum **ppAppDomains);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0b859-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="0b859-106">Parameters</span></span>  

 `ppAppDomains`  
 <span data-ttu-id="0b859-107">заполняет Указатель на адрес [икордебугаппдомаиненум](icordebugappdomainenum-interface.md) , который является перечислителем для доменов приложений в этом процессе.</span><span class="sxs-lookup"><span data-stu-id="0b859-107">[out] A pointer to the address of an [ICorDebugAppDomainEnum](icordebugappdomainenum-interface.md) that is an enumerator for the application domains in this process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0b859-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="0b859-108">Remarks</span></span>  

 <span data-ttu-id="0b859-109">Этот метод можно использовать перед обратным вызовом [ICorDebugManagedCallback:: CreateProcess](icordebugmanagedcallback-createprocess-method.md) .</span><span class="sxs-lookup"><span data-stu-id="0b859-109">This method can be used before the [ICorDebugManagedCallback::CreateProcess](icordebugmanagedcallback-createprocess-method.md) callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b859-110">Требования</span><span class="sxs-lookup"><span data-stu-id="0b859-110">Requirements</span></span>  

 <span data-ttu-id="0b859-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b859-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b859-112">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0b859-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0b859-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0b859-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0b859-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b859-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
