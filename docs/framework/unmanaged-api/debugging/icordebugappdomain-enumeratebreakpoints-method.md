---
description: 'Дополнительные сведения о методе: ICorDebugAppDomain:: EnumerateBreakpoints'
title: Метод ICorDebugAppDomain::EnumerateBreakpoints
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.EnumerateBreakpoints
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::EnumerateBreakpoints
helpviewer_keywords:
- ICorDebugAppDomain::EnumerateBreakpoints method [.NET Framework debugging]
- EnumerateBreakpoints method [.NET Framework debugging]
ms.assetid: 206069c5-25cb-4794-9d69-67c5aa7ed0af
topic_type:
- apiref
ms.openlocfilehash: 4bd9857b9c662bc76c7c9481f306b20e823e446f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772485"
---
# <a name="icordebugappdomainenumeratebreakpoints-method"></a><span data-ttu-id="1504e-103">Метод ICorDebugAppDomain::EnumerateBreakpoints</span><span class="sxs-lookup"><span data-stu-id="1504e-103">ICorDebugAppDomain::EnumerateBreakpoints Method</span></span>

<span data-ttu-id="1504e-104">Возвращает перечислитель для всех активных точек останова в домене приложения.</span><span class="sxs-lookup"><span data-stu-id="1504e-104">Gets an enumerator for all active breakpoints in the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1504e-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="1504e-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateBreakpoints (  
    [out] ICorDebugBreakpointEnum   **ppBreakpoints  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1504e-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="1504e-106">Parameters</span></span>  

 `ppBreakpoints`  
 <span data-ttu-id="1504e-107">заполняет Указатель на адрес объекта ICorDebugBreakpointEnum, который является перечислителем для всех активных точек останова в домене приложения.</span><span class="sxs-lookup"><span data-stu-id="1504e-107">[out] A pointer to the address of an ICorDebugBreakpointEnum object that is the enumerator for all active breakpoints in the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1504e-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="1504e-108">Remarks</span></span>  

 <span data-ttu-id="1504e-109">Перечислитель включает все типы точек останова, включая точки останова функции и точки останова в данных.</span><span class="sxs-lookup"><span data-stu-id="1504e-109">The enumerator includes all types of breakpoints, including function breakpoints and data breakpoints.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1504e-110">Требования</span><span class="sxs-lookup"><span data-stu-id="1504e-110">Requirements</span></span>  

 <span data-ttu-id="1504e-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1504e-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1504e-112">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1504e-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1504e-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1504e-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1504e-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1504e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
