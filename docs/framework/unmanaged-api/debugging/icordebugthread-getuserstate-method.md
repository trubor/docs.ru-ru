---
description: 'Дополнительные сведения о методе ICorDebugThread:: Жетусерстате'
title: Метод ICorDebugThread::GetUserState
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetUserState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetUserState
helpviewer_keywords:
- GetUserState method, ICorDebugThread interface [.NET Framework debugging]
- ICorDebugThread::GetUserState method [.NET Framework debugging]
ms.assetid: ae0cfd73-8ead-4d36-9310-dccaac9db0bd
topic_type:
- apiref
ms.openlocfilehash: b63b474525534f9e934954ebe660691db90b8b67
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99658871"
---
# <a name="icordebugthreadgetuserstate-method"></a><span data-ttu-id="bf02f-103">Метод ICorDebugThread::GetUserState</span><span class="sxs-lookup"><span data-stu-id="bf02f-103">ICorDebugThread::GetUserState Method</span></span>

<span data-ttu-id="bf02f-104">Возвращает текущее пользовательское состояние этого ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="bf02f-104">Gets the current user state of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bf02f-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="bf02f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetUserState (  
    [out] CorDebugUserState   *pState  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bf02f-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="bf02f-106">Parameters</span></span>  

 `pState`  
 <span data-ttu-id="bf02f-107">заполняет Указатель на побитовую комбинацию значений перечисления Кордебугусерстате, описывающих текущее пользовательское состояние этого потока.</span><span class="sxs-lookup"><span data-stu-id="bf02f-107">[out] A pointer to a bitwise combination of CorDebugUserState enumeration values that describe the current user state of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bf02f-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="bf02f-108">Remarks</span></span>  

 <span data-ttu-id="bf02f-109">Пользовательское состояние потока — это состояние потока, которое проверяется отлаживаемой программой.</span><span class="sxs-lookup"><span data-stu-id="bf02f-109">The user state of the thread is the state of the thread when it is examined by the program that is being debugged.</span></span> <span data-ttu-id="bf02f-110">Для потока может быть задано несколько битов состояния.</span><span class="sxs-lookup"><span data-stu-id="bf02f-110">A thread may have multiple state bits set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf02f-111">Требования</span><span class="sxs-lookup"><span data-stu-id="bf02f-111">Requirements</span></span>  

 <span data-ttu-id="bf02f-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bf02f-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf02f-113">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bf02f-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bf02f-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bf02f-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bf02f-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf02f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
