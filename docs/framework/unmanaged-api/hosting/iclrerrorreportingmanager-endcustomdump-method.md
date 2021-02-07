---
description: 'Дополнительные сведения о методе: Iclrerrorreportingmanagergetbucketparametersforcurrentexception:: Ендкустомдумп'
title: Метод ICLRErrorReportingManager::EndCustomDump
ms.date: 03/30/2017
api_name:
- ICLRErrorReportingManager.EndCustomDump
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRErrorReportingManager::EndCustomDump
helpviewer_keywords:
- ICLRErrorReportingManager::EndCustomDump method [.NET Framework hosting]
- EndCustomDump method [.NET Framework hosting]
ms.assetid: 88a5da04-8729-4108-82c4-af206a7d483e
topic_type:
- apiref
ms.openlocfilehash: 406d7d77f4cd63c69fec56acb0819d56c6271630
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99689473"
---
# <a name="iclrerrorreportingmanagerendcustomdump-method"></a><span data-ttu-id="dfb9e-103">Метод ICLRErrorReportingManager::EndCustomDump</span><span class="sxs-lookup"><span data-stu-id="dfb9e-103">ICLRErrorReportingManager::EndCustomDump Method</span></span>

<span data-ttu-id="dfb9e-104">Удаляет конфигурацию пользовательского дампа стека, которая была указана в предыдущем вызове метода [iclrerrorreportingmanagergetbucketparametersforcurrentexception:: BeginCustomDump](iclrerrorreportingmanager-begincustomdump-method.md) .</span><span class="sxs-lookup"><span data-stu-id="dfb9e-104">Removes the custom stack dump configuration that was specified in an earlier call to the [ICLRErrorReportingManager::BeginCustomDump](iclrerrorreportingmanager-begincustomdump-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dfb9e-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="dfb9e-105">Syntax</span></span>  
  
```cpp  
HRESULT EndCustomDump ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="dfb9e-106">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="dfb9e-106">Return Value</span></span>  
  
|<span data-ttu-id="dfb9e-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="dfb9e-107">HRESULT</span></span>|<span data-ttu-id="dfb9e-108">Описание:</span><span class="sxs-lookup"><span data-stu-id="dfb9e-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="dfb9e-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="dfb9e-109">S_OK</span></span>|<span data-ttu-id="dfb9e-110">`EndCustomDump` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="dfb9e-110">`EndCustomDump` returned successfully.</span></span>|  
|<span data-ttu-id="dfb9e-111">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="dfb9e-111">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="dfb9e-112">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="dfb9e-112">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="dfb9e-113">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="dfb9e-113">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="dfb9e-114">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="dfb9e-114">The call timed out.</span></span>|  
|<span data-ttu-id="dfb9e-115">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="dfb9e-115">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="dfb9e-116">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="dfb9e-116">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="dfb9e-117">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="dfb9e-117">HOST_E_ABANDONED</span></span>|<span data-ttu-id="dfb9e-118">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="dfb9e-118">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="dfb9e-119">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="dfb9e-119">E_FAIL</span></span>|<span data-ttu-id="dfb9e-120">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="dfb9e-120">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="dfb9e-121">После того как метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="dfb9e-121">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="dfb9e-122">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="dfb9e-122">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dfb9e-123">Remarks</span><span class="sxs-lookup"><span data-stu-id="dfb9e-123">Remarks</span></span>  

 <span data-ttu-id="dfb9e-124">`EndCustomDump`Метод очищает конфигурацию пользовательского дампа стека, заданную предыдущим вызовом `BeginCustomDump` метода, и освобождает любое связанное состояние.</span><span class="sxs-lookup"><span data-stu-id="dfb9e-124">The `EndCustomDump` method clears the custom stack dump configuration set by an earlier call to the `BeginCustomDump` method and frees any associated state.</span></span> <span data-ttu-id="dfb9e-125">Он должен вызываться после завершения создания пользовательского дампа стека.</span><span class="sxs-lookup"><span data-stu-id="dfb9e-125">It should be called after the custom stack dump is complete.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="dfb9e-126">Сбой вызова `EndCustomDump` приводит к утечке памяти.</span><span class="sxs-lookup"><span data-stu-id="dfb9e-126">Failure to call `EndCustomDump` causes memory to leak.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dfb9e-127">Требования</span><span class="sxs-lookup"><span data-stu-id="dfb9e-127">Requirements</span></span>  

 <span data-ttu-id="dfb9e-128">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dfb9e-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dfb9e-129">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="dfb9e-129">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dfb9e-130">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="dfb9e-130">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dfb9e-131">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dfb9e-131">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dfb9e-132">См. также</span><span class="sxs-lookup"><span data-stu-id="dfb9e-132">See also</span></span>

- [<span data-ttu-id="dfb9e-133">Структура CustomDumpItem</span><span class="sxs-lookup"><span data-stu-id="dfb9e-133">CustomDumpItem Structure</span></span>](customdumpitem-structure.md)
- [<span data-ttu-id="dfb9e-134">Перечисление ECustomDumpFlavor</span><span class="sxs-lookup"><span data-stu-id="dfb9e-134">ECustomDumpFlavor Enumeration</span></span>](ecustomdumpflavor-enumeration.md)
- [<span data-ttu-id="dfb9e-135">Интерфейс ICLRErrorReportingManager</span><span class="sxs-lookup"><span data-stu-id="dfb9e-135">ICLRErrorReportingManager Interface</span></span>](iclrerrorreportingmanager-interface.md)
