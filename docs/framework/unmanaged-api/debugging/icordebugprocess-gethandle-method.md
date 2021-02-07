---
description: 'Дополнительные сведения о методе: ICorDebugProcess:: getHandler'
title: Метод ICorDebugProcess::GetHandle
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.GetHandle
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::GetHandle
helpviewer_keywords:
- GetHandle method, ICorDebugProcess interface [.NET Framework debugging]
- ICorDebugProcess::GetHandle method [.NET Framework debugging]
ms.assetid: e7d3ecf5-09d2-4d94-abb6-ff3483deebb6
topic_type:
- apiref
ms.openlocfilehash: fbc92be53b30d3c70f85fea36e05c6a5514b0f03
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99722130"
---
# <a name="icordebugprocessgethandle-method"></a><span data-ttu-id="91a91-103">Метод ICorDebugProcess::GetHandle</span><span class="sxs-lookup"><span data-stu-id="91a91-103">ICorDebugProcess::GetHandle Method</span></span>

<span data-ttu-id="91a91-104">Возвращает маркер процесса.</span><span class="sxs-lookup"><span data-stu-id="91a91-104">Gets a handle to the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91a91-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="91a91-105">Syntax</span></span>  
  
```cpp  
HRESULT GetHandle([out] HPROCESS *phProcessHandle);  
```  
  
## <a name="parameters"></a><span data-ttu-id="91a91-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="91a91-106">Parameters</span></span>  

 `phProcessHandle`  
 <span data-ttu-id="91a91-107">заполняет Указатель на `HPROCESS` , который является обработчиком для процесса.</span><span class="sxs-lookup"><span data-stu-id="91a91-107">[out] A pointer to an `HPROCESS` that is the handle to the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="91a91-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="91a91-108">Remarks</span></span>  

 <span data-ttu-id="91a91-109">Полученный обработчик принадлежит интерфейсу отладки.</span><span class="sxs-lookup"><span data-stu-id="91a91-109">The retrieved handle is owned by the debugging interface.</span></span> <span data-ttu-id="91a91-110">Отладчик должен дублировать этот обработчик перед его использованием.</span><span class="sxs-lookup"><span data-stu-id="91a91-110">The debugger should duplicate the handle before using it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91a91-111">Требования</span><span class="sxs-lookup"><span data-stu-id="91a91-111">Requirements</span></span>  

 <span data-ttu-id="91a91-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="91a91-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91a91-113">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="91a91-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="91a91-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="91a91-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="91a91-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91a91-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
