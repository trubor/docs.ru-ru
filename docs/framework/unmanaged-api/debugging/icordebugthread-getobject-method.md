---
description: 'Дополнительные сведения о методе ICorDebugThread:: GetObject'
title: Метод ICorDebugThread::GetObject
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetObject
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetObject
helpviewer_keywords:
- GetObject method, ICorDebugThread interface [.NET Framework debugging]
- ICorDebugThread::GetObject method [.NET Framework debugging]
ms.assetid: 1590febe-96c2-4046-97db-d81d81d67e01
topic_type:
- apiref
ms.openlocfilehash: db5760be0ef4230b2dccec9d1836ea0eee56f231
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99658962"
---
# <a name="icordebugthreadgetobject-method"></a><span data-ttu-id="cc18e-103">Метод ICorDebugThread::GetObject</span><span class="sxs-lookup"><span data-stu-id="cc18e-103">ICorDebugThread::GetObject Method</span></span>

<span data-ttu-id="cc18e-104">Возвращает указатель интерфейса на поток среды CLR.</span><span class="sxs-lookup"><span data-stu-id="cc18e-104">Gets an interface pointer to the common language runtime (CLR) thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc18e-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="cc18e-105">Syntax</span></span>  
  
```cpp  
HRESULT GetObject (  
    [out] ICorDebugValue   **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cc18e-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="cc18e-106">Parameters</span></span>  

 `ppObject`  
 <span data-ttu-id="cc18e-107">заполняет Указатель на адрес объекта интерфейса ICorDebugValue, который представляет поток среды CLR.</span><span class="sxs-lookup"><span data-stu-id="cc18e-107">[out] A pointer to the address of an ICorDebugValue interface object that represents the CLR thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc18e-108">Требования</span><span class="sxs-lookup"><span data-stu-id="cc18e-108">Requirements</span></span>  

 <span data-ttu-id="cc18e-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cc18e-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc18e-110">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cc18e-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cc18e-111">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cc18e-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cc18e-112">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc18e-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc18e-113">См. также</span><span class="sxs-lookup"><span data-stu-id="cc18e-113">See also</span></span>

- <xref:System.Threading.Thread>
