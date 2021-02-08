---
description: 'Дополнительные сведения о методе: ICorDebugAppDomain:: onprocess'
title: Метод ICorDebugAppDomain::GetProcess
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.GetProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::GetProcess
helpviewer_keywords:
- GetProcess method, ICorDebugAppDomain interface [.NET Framework debugging]
- ICorDebugAppDomain::GetProcess method [.NET Framework debugging]
ms.assetid: 9d0b9628-a91c-40d0-b9bc-00b34a396b8f
topic_type:
- apiref
ms.openlocfilehash: a681e58334df5dd7373e49b70c096fa1ff10773f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772410"
---
# <a name="icordebugappdomaingetprocess-method"></a><span data-ttu-id="7403b-103">Метод ICorDebugAppDomain::GetProcess</span><span class="sxs-lookup"><span data-stu-id="7403b-103">ICorDebugAppDomain::GetProcess Method</span></span>

<span data-ttu-id="7403b-104">Возвращает процесс, содержащий домен приложения.</span><span class="sxs-lookup"><span data-stu-id="7403b-104">Gets the process containing the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7403b-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="7403b-105">Syntax</span></span>  
  
```cpp  
HRESULT GetProcess (  
    [out] ICorDebugProcess   **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7403b-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="7403b-106">Parameters</span></span>  

 `ppProcess`  
 <span data-ttu-id="7403b-107">заполняет Указатель на адрес объекта ICorDebugProcess, который представляет процесс.</span><span class="sxs-lookup"><span data-stu-id="7403b-107">[out] A pointer to the address of an ICorDebugProcess object that represents the process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7403b-108">Требования</span><span class="sxs-lookup"><span data-stu-id="7403b-108">Requirements</span></span>  

 <span data-ttu-id="7403b-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7403b-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7403b-110">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7403b-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7403b-111">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7403b-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7403b-112">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7403b-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
