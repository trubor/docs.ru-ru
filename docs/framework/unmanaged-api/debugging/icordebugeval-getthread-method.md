---
description: 'Дополнительные сведения о методе: ICorDebugEval:: Thread'
title: Метод ICorDebugEval::GetThread
ms.date: 03/30/2017
api_name:
- ICorDebugEval.GetThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::GetThread
helpviewer_keywords:
- GetThread method, ICorDebugEval interface [.NET Framework debugging]
- ICorDebugEval::GetThread method [.NET Framework debugging]
ms.assetid: 57163b0d-c8a7-44af-9078-e7a895d29f9a
topic_type:
- apiref
ms.openlocfilehash: 3e7120f618abce31b9940a886fd6b2b2f8639d2d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99694153"
---
# <a name="icordebugevalgetthread-method"></a><span data-ttu-id="c7f67-103">Метод ICorDebugEval::GetThread</span><span class="sxs-lookup"><span data-stu-id="c7f67-103">ICorDebugEval::GetThread Method</span></span>

<span data-ttu-id="c7f67-104">Возвращает поток, в котором выполняется эта оценка или она будет выполнена.</span><span class="sxs-lookup"><span data-stu-id="c7f67-104">Gets the thread in which this evaluation is executing or will execute.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7f67-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c7f67-105">Syntax</span></span>  
  
```cpp  
HRESULT GetThread (  
    [out] ICorDebugThread   **ppThread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c7f67-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="c7f67-106">Parameters</span></span>  

 `ppThread`  
 <span data-ttu-id="c7f67-107">заполняет Указатель на адрес объекта ICorDebugThread, представляющего поток.</span><span class="sxs-lookup"><span data-stu-id="c7f67-107">[out] A pointer to the address of an ICorDebugThread object that represents the thread.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c7f67-108">Требования</span><span class="sxs-lookup"><span data-stu-id="c7f67-108">Requirements</span></span>  

 <span data-ttu-id="c7f67-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c7f67-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c7f67-110">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c7f67-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c7f67-111">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c7f67-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c7f67-112">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c7f67-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
