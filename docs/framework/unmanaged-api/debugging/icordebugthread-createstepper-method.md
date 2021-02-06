---
description: 'Дополнительные сведения о методе ICorDebugThread:: Креатестеппер'
title: Метод ICorDebugThread::CreateStepper
ms.date: 03/30/2017
api_name:
- ICorDebugThread.CreateStepper
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::CreateStepper
helpviewer_keywords:
- ICorDebugThread::CreateStepper method [.NET Framework debugging]
- CreateStepper method, ICorDebugThread interface [.NET Framework debugging]
ms.assetid: 4657443f-dd12-431b-a648-175c23f13c83
topic_type:
- apiref
ms.openlocfilehash: 378ce28281f4f284c36194f993a53598a9de3854
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99659365"
---
# <a name="icordebugthreadcreatestepper-method"></a><span data-ttu-id="b0692-103">Метод ICorDebugThread::CreateStepper</span><span class="sxs-lookup"><span data-stu-id="b0692-103">ICorDebugThread::CreateStepper Method</span></span>

<span data-ttu-id="b0692-104">Создает объект ICorDebugStepper, позволяющий выполнять пошаговую отладку активной рамки этого ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="b0692-104">Creates an ICorDebugStepper object that allows stepping through the active frame of this ICorDebugThread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b0692-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b0692-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateStepper (  
    [out] ICorDebugStepper **ppStepper  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b0692-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="b0692-106">Parameters</span></span>  

 `ppStepper`  
 <span data-ttu-id="b0692-107">заполняет Указатель на адрес `ICorDebugStepper` объекта, который допускает пошаговое выполнение активного кадра этого потока.</span><span class="sxs-lookup"><span data-stu-id="b0692-107">[out] A pointer to the address of an `ICorDebugStepper` object that allows stepping through the active frame of this thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b0692-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="b0692-108">Remarks</span></span>  

 <span data-ttu-id="b0692-109">Активным кадром может быть неуправляемый код.</span><span class="sxs-lookup"><span data-stu-id="b0692-109">The active frame may be unmanaged code.</span></span>  
  
 <span data-ttu-id="b0692-110">`ICorDebugStepper`Для выполнения фактического пошагового шага необходимо использовать интерфейс.</span><span class="sxs-lookup"><span data-stu-id="b0692-110">The `ICorDebugStepper` interface must be used to perform the actual stepping.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0692-111">Требования</span><span class="sxs-lookup"><span data-stu-id="b0692-111">Requirements</span></span>  

 <span data-ttu-id="b0692-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b0692-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0692-113">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b0692-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b0692-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b0692-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b0692-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0692-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
