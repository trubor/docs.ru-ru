---
description: 'Дополнительные сведения о методе ICorDebugFrame:: Зовите.'
title: Метод ICorDebugFrame::GetCallee
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetCallee
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetCallee
helpviewer_keywords:
- ICorDebugFrame::GetCallee method [.NET Framework debugging]
- GetCallee method, ICorDebugFrame interface [.NET Framework debugging]
ms.assetid: 92d8136d-0436-4c7e-a6b2-80765f892a0d
topic_type:
- apiref
ms.openlocfilehash: 85b64933cb2f180445b88f7b19f8b78f1788252e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693074"
---
# <a name="icordebugframegetcallee-method"></a><span data-ttu-id="570fc-103">Метод ICorDebugFrame::GetCallee</span><span class="sxs-lookup"><span data-stu-id="570fc-103">ICorDebugFrame::GetCallee Method</span></span>

<span data-ttu-id="570fc-104">Возвращает указатель на объект ICorDebugFrame в текущей цепочке, вызвавшей этот кадр.</span><span class="sxs-lookup"><span data-stu-id="570fc-104">Gets a pointer to the ICorDebugFrame object in the current chain that this frame called.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="570fc-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="570fc-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCallee (  
    [out] ICorDebugFrame     **ppFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="570fc-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="570fc-106">Parameters</span></span>  

 `ppFrame`  
 <span data-ttu-id="570fc-107">заполняет Указатель на адрес `ICorDebugFrame` объекта, представляющий вызываемый кадр.</span><span class="sxs-lookup"><span data-stu-id="570fc-107">[out] A pointer to the address of an `ICorDebugFrame` object that represents the called frame.</span></span> <span data-ttu-id="570fc-108">Это значение равно null, если вызывающий кадр является самым внутренним кадром в текущей цепочке.</span><span class="sxs-lookup"><span data-stu-id="570fc-108">This value is null if the calling frame is the innermost frame in the current chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="570fc-109">Требования</span><span class="sxs-lookup"><span data-stu-id="570fc-109">Requirements</span></span>  

 <span data-ttu-id="570fc-110">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="570fc-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="570fc-111">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="570fc-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="570fc-112">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="570fc-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="570fc-113">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="570fc-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
