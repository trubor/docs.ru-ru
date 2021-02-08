---
description: Дополнительные сведения о функции GetStartupNotificationEvent
title: Функция GetStartupNotificationEvent
ms.date: 03/30/2017
api_name:
- GetStartupNotificationEvent
api_location:
- dbgshim.dll
api_type:
- COM
f1_keywords:
- GetStartupNotificationEvent
helpviewer_keywords:
- GetStartupNotificationEvent function
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: c94b1b61-045a-4695-bacd-0f18c5acc246
topic_type:
- apiref
ms.openlocfilehash: 49b0e3f9b2acec87e419bae03086a7e437f45f98
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801388"
---
# <a name="getstartupnotificationevent-function"></a><span data-ttu-id="7a29c-103">Функция GetStartupNotificationEvent</span><span class="sxs-lookup"><span data-stu-id="7a29c-103">GetStartupNotificationEvent Function</span></span>

<span data-ttu-id="7a29c-104">Создает или открывает обработчик событий, который будет информироваться любой средой CLR, загружаемой в указанный целевой процесс.</span><span class="sxs-lookup"><span data-stu-id="7a29c-104">Creates or opens an event handle that will be signaled upon by any common language runtime (CLR) that is loading in the specified target process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a29c-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="7a29c-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStartupNotificationEvent  
    (  
    [in]  DWORD     debuggeePID,  
    [out]  HANDLE*  phStartupEvent  
    );  
```  
  
## <a name="parameters"></a><span data-ttu-id="7a29c-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="7a29c-106">Parameters</span></span>  

 `debuggeePID`  
 <span data-ttu-id="7a29c-107">[in] Идентификатор целевого процесса, из которого следует получать уведомления при запуске среды CLR.</span><span class="sxs-lookup"><span data-stu-id="7a29c-107">[in] Process identifier of the target process from which to receive CLR startup notifications.</span></span>  
  
 `phStartupEvent`  
 <span data-ttu-id="7a29c-108">[out] Указатель на дескриптор, который будет оповещаться средой CLR при запуске.</span><span class="sxs-lookup"><span data-stu-id="7a29c-108">[out] A pointer to a handle that will be signaled by a CLR on startup.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7a29c-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="7a29c-109">Return Value</span></span>  

 <span data-ttu-id="7a29c-110">S_OK</span><span class="sxs-lookup"><span data-stu-id="7a29c-110">S_OK</span></span>  
 <span data-ttu-id="7a29c-111">Успешно получен дескриптор события уведомления при запуске.</span><span class="sxs-lookup"><span data-stu-id="7a29c-111">Successfully obtained the handle to the startup notification event.</span></span>  
  
 <span data-ttu-id="7a29c-112">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="7a29c-112">E_INVALIDARG</span></span>  
 <span data-ttu-id="7a29c-113">`phStartupEvent` имеет значение null, или `debuggeePID` не ссылается на процесс, выполняющийся в текущий момент.</span><span class="sxs-lookup"><span data-stu-id="7a29c-113">`phStartupEvent` is null or `debuggeePID` does not refer to a process that is currently running.</span></span>  
  
 <span data-ttu-id="7a29c-114">E_FAIL (или другие коды возврата E_)</span><span class="sxs-lookup"><span data-stu-id="7a29c-114">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="7a29c-115">Не удалось получить дескриптор события уведомления при запуске.</span><span class="sxs-lookup"><span data-stu-id="7a29c-115">Unable to obtain the handle to the startup notification event.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7a29c-116">Remarks</span><span class="sxs-lookup"><span data-stu-id="7a29c-116">Remarks</span></span>  

 <span data-ttu-id="7a29c-117">В операционной системе Windows `debuggeePID` сопоставляется с идентификатором процесса ОС.</span><span class="sxs-lookup"><span data-stu-id="7a29c-117">On the Windows operating system, `debuggeePID` maps to an OS process identifier.</span></span>  
  
 <span data-ttu-id="7a29c-118">Событие сигнализирует перед любым выполнением управляемого кода средой CLR, которая оповещает событие.</span><span class="sxs-lookup"><span data-stu-id="7a29c-118">The event is signaled before any managed code is executed by the CLR that signaled the event.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a29c-119">Требования</span><span class="sxs-lookup"><span data-stu-id="7a29c-119">Requirements</span></span>  

 <span data-ttu-id="7a29c-120">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7a29c-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a29c-121">**Заголовок:** dbgshim. h</span><span class="sxs-lookup"><span data-stu-id="7a29c-121">**Header:** dbgshim.h</span></span>  
  
 <span data-ttu-id="7a29c-122">**Библиотека:** dbgshim.dll</span><span class="sxs-lookup"><span data-stu-id="7a29c-122">**Library:** dbgshim.dll</span></span>  
  
 <span data-ttu-id="7a29c-123">**Платформа .NET Framework версии:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="7a29c-123">**.NET Framework Versions:** 3.5 SP1</span></span>
