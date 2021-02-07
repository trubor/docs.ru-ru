---
description: 'Дополнительные сведения о методе: Iclrerrorreportingmanagergetbucketparametersforcurrentexception:: BeginCustomDump'
title: Метод ICLRErrorReportingManager::BeginCustomDump
ms.date: 03/30/2017
api_name:
- ICLRErrorReportingManager.BeginCustomDump
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRErrorReportingManager::BeginCustomDump
helpviewer_keywords:
- ICLRErrorReportingManager::BeginCustomDump method [.NET Framework hosting]
- BeginCustomDump method
ms.assetid: 93424a87-ba13-4fa1-b4dc-69d44437b7ae
topic_type:
- apiref
ms.openlocfilehash: 3f8498068d50ffc6ea00cf4f08f969c92f010d6c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99689486"
---
# <a name="iclrerrorreportingmanagerbegincustomdump-method"></a><span data-ttu-id="0d779-103">Метод ICLRErrorReportingManager::BeginCustomDump</span><span class="sxs-lookup"><span data-stu-id="0d779-103">ICLRErrorReportingManager::BeginCustomDump Method</span></span>

<span data-ttu-id="0d779-104">Задает конфигурацию дампов пользовательской кучи для отчетов об ошибках.</span><span class="sxs-lookup"><span data-stu-id="0d779-104">Specifies the configuration of custom heap dumps for error reporting.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d779-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0d779-105">Syntax</span></span>  
  
```cpp  
HRESULT BeginCustomDump (  
    [in] ECustomDumpFlavor dwFlavor,  
    [in] DWORD dwNumItems,  
    [in, size_is(dwNumItems), length_is(dwNumItems)] CustomDumpItem items[],  
    DWORD dwReserved  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0d779-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="0d779-106">Parameters</span></span>  

 `dwFlavor`  
 <span data-ttu-id="0d779-107">окне Значение [екустомдумпфлавор](ecustomdumpflavor-enumeration.md) , указывающее тип дампа кучи, на основе которого создается дамп пользовательской кучи.</span><span class="sxs-lookup"><span data-stu-id="0d779-107">[in] A [ECustomDumpFlavor](ecustomdumpflavor-enumeration.md) value that indicates the kind of heap dump upon which to build the custom heap dump.</span></span>  
  
 `dwNumItems`  
 <span data-ttu-id="0d779-108">окне Длина `items` массива.</span><span class="sxs-lookup"><span data-stu-id="0d779-108">[in] The length of the `items` array.</span></span> <span data-ttu-id="0d779-109">Если `dwFlavor` значение не DUMP_FLAVOR_Mini, `dwNumItems` должно быть равно нулю.</span><span class="sxs-lookup"><span data-stu-id="0d779-109">If `dwFlavor` is not DUMP_FLAVOR_Mini, `dwNumItems` should be zero.</span></span>  
  
 `items`  
 <span data-ttu-id="0d779-110">окне Массив экземпляров [кустомдумпитем](customdumpitem-structure.md) , указывающий элементы для добавления в мини-дамп.</span><span class="sxs-lookup"><span data-stu-id="0d779-110">[in] An array of [CustomDumpItem](customdumpitem-structure.md) instances, specifying the items to add to the mini-dump.</span></span> <span data-ttu-id="0d779-111">Если `dwFlavor` значение не DUMP_FLAVOR_Mini, `items` должно быть равно null.</span><span class="sxs-lookup"><span data-stu-id="0d779-111">If `dwFlavor` is not DUMP_FLAVOR_Mini, `items` should be null.</span></span>  
  
 `dwReserved`  
 <span data-ttu-id="0d779-112">[in] Зарезервирован для будущего использования.</span><span class="sxs-lookup"><span data-stu-id="0d779-112">[in] Reserved for future use.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0d779-113">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="0d779-113">Return Value</span></span>  
  
|<span data-ttu-id="0d779-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0d779-114">HRESULT</span></span>|<span data-ttu-id="0d779-115">Описание:</span><span class="sxs-lookup"><span data-stu-id="0d779-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0d779-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="0d779-116">S_OK</span></span>|<span data-ttu-id="0d779-117">Метод возвратился успешно.</span><span class="sxs-lookup"><span data-stu-id="0d779-117">The method returned successfully.</span></span>|  
|<span data-ttu-id="0d779-118">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0d779-118">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0d779-119">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="0d779-119">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0d779-120">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0d779-120">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0d779-121">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="0d779-121">The call timed out.</span></span>|  
|<span data-ttu-id="0d779-122">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0d779-122">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0d779-123">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="0d779-123">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0d779-124">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0d779-124">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0d779-125">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="0d779-125">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0d779-126">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0d779-126">E_FAIL</span></span>|<span data-ttu-id="0d779-127">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="0d779-127">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0d779-128">После того как метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="0d779-128">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0d779-129">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="0d779-129">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0d779-130">Remarks</span><span class="sxs-lookup"><span data-stu-id="0d779-130">Remarks</span></span>  

 <span data-ttu-id="0d779-131">`BeginCustomDump`Метод задает конфигурацию дампа пользовательской кучи.</span><span class="sxs-lookup"><span data-stu-id="0d779-131">The `BeginCustomDump` method sets custom heap dump configuration.</span></span> <span data-ttu-id="0d779-132">Метод [ендкустомдумп](iclrerrorreportingmanager-endcustomdump-method.md) очищает конфигурацию дампа пользовательской кучи и освобождает любое связанное состояние.</span><span class="sxs-lookup"><span data-stu-id="0d779-132">The [EndCustomDump](iclrerrorreportingmanager-endcustomdump-method.md) method clears the custom heap dump configuration and frees any associated state.</span></span> <span data-ttu-id="0d779-133">Он должен вызываться после завершения создания дампа пользовательской кучи.</span><span class="sxs-lookup"><span data-stu-id="0d779-133">It should be called after the custom heap dump is complete.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="0d779-134">Сбой вызова `EndCustomDump` приводит к утечке памяти.</span><span class="sxs-lookup"><span data-stu-id="0d779-134">Failure to call `EndCustomDump` causes memory to leak.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0d779-135">Требования</span><span class="sxs-lookup"><span data-stu-id="0d779-135">Requirements</span></span>  

 <span data-ttu-id="0d779-136">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0d779-136">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d779-137">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0d779-137">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0d779-138">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0d779-138">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0d779-139">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d779-139">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d779-140">См. также</span><span class="sxs-lookup"><span data-stu-id="0d779-140">See also</span></span>

- [<span data-ttu-id="0d779-141">Структура CustomDumpItem</span><span class="sxs-lookup"><span data-stu-id="0d779-141">CustomDumpItem Structure</span></span>](customdumpitem-structure.md)
- [<span data-ttu-id="0d779-142">Перечисление ECustomDumpFlavor</span><span class="sxs-lookup"><span data-stu-id="0d779-142">ECustomDumpFlavor Enumeration</span></span>](ecustomdumpflavor-enumeration.md)
- [<span data-ttu-id="0d779-143">Интерфейс ICLRErrorReportingManager</span><span class="sxs-lookup"><span data-stu-id="0d779-143">ICLRErrorReportingManager Interface</span></span>](iclrerrorreportingmanager-interface.md)
