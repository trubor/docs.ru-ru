---
description: 'Дополнительные сведения о методе ICorDebugThread:: "AppDomain"'
title: Метод ICorDebugThread::GetAppDomain
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetAppDomain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetAppDomain
helpviewer_keywords:
- GetAppDomain method, ICorDebugThread interface [.NET Framework debugging]
- ICorDebugThread::GetAppDomain method [.NET Framework debugging]
ms.assetid: 415b3d34-8b35-4b60-a318-140646cc83f8
topic_type:
- apiref
ms.openlocfilehash: 416ab80fa08786fb5e95776b164723317fa59ca6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99659209"
---
# <a name="icordebugthreadgetappdomain-method"></a><span data-ttu-id="15d10-103">Метод ICorDebugThread::GetAppDomain</span><span class="sxs-lookup"><span data-stu-id="15d10-103">ICorDebugThread::GetAppDomain Method</span></span>

<span data-ttu-id="15d10-104">Возвращает указатель интерфейса на домен приложения, в котором выполняется данный интерфейс ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="15d10-104">Gets an interface pointer to the application domain in which this ICorDebugThread is currently executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15d10-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="15d10-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAppDomain (  
    [out] ICorDebugAppDomain  **ppAppDomain  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="15d10-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="15d10-106">Parameters</span></span>  

 `ppAppDomain`  
 <span data-ttu-id="15d10-107">заполняет Указатель на объект ICorDebugAppDomain, представляющий домен приложения, в котором выполняется данный поток в данный момент.</span><span class="sxs-lookup"><span data-stu-id="15d10-107">[out] A pointer to an ICorDebugAppDomain object that represents the application domain in which this thread is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15d10-108">Требования</span><span class="sxs-lookup"><span data-stu-id="15d10-108">Requirements</span></span>  

 <span data-ttu-id="15d10-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="15d10-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15d10-110">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="15d10-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="15d10-111">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="15d10-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="15d10-112">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15d10-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
