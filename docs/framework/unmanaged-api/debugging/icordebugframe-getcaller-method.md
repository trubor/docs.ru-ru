---
description: 'Дополнительные сведения о методе ICorDebugFrame:: вызывали'
title: Метод ICorDebugFrame::GetCaller
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetCaller
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetCaller
helpviewer_keywords:
- GetCaller method, ICorDebugFrame interface [.NET Framework debugging]
- ICorDebugFrame::GetCaller method [.NET Framework debugging]
ms.assetid: bfdc946b-8238-4eb9-8a85-884049fb0fd4
topic_type:
- apiref
ms.openlocfilehash: a042341f6edfa0e8f6ca00f758107852f9e381cb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693048"
---
# <a name="icordebugframegetcaller-method"></a><span data-ttu-id="aa9a2-103">Метод ICorDebugFrame::GetCaller</span><span class="sxs-lookup"><span data-stu-id="aa9a2-103">ICorDebugFrame::GetCaller Method</span></span>

<span data-ttu-id="aa9a2-104">Возвращает указатель на объект ICorDebugFrame в текущей цепочке, вызвавшей этот кадр.</span><span class="sxs-lookup"><span data-stu-id="aa9a2-104">Gets a pointer to the ICorDebugFrame object in the current chain that called this frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aa9a2-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="aa9a2-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCaller (  
    [out] ICorDebugFrame     **ppFrame  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aa9a2-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="aa9a2-106">Parameters</span></span>  

 `ppFrame`  
 <span data-ttu-id="aa9a2-107">заполняет Указатель на адрес `ICorDebugFrame` объекта, представляющий вызывающий кадр.</span><span class="sxs-lookup"><span data-stu-id="aa9a2-107">[out] A pointer to the address of an `ICorDebugFrame` object that represents the calling frame.</span></span> <span data-ttu-id="aa9a2-108">Это значение равно null, если вызываемый кадр является самым внешним кадром в текущей цепочке.</span><span class="sxs-lookup"><span data-stu-id="aa9a2-108">This value is null if the called frame is the outermost frame in the current chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aa9a2-109">Требования</span><span class="sxs-lookup"><span data-stu-id="aa9a2-109">Requirements</span></span>  

 <span data-ttu-id="aa9a2-110">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="aa9a2-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="aa9a2-111">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="aa9a2-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="aa9a2-112">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="aa9a2-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="aa9a2-113">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="aa9a2-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
