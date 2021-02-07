---
description: 'Дополнительные сведения о методе: ICLRRuntimeHost:: GetCLRControl'
title: Метод ICLRRuntimeHost::GetCLRControl
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.GetCLRControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::GetCLRControl
helpviewer_keywords:
- ICLRRuntimeHost::GetCLRControl method [.NET Framework hosting]
- GetCLRControl method [.NET Framework hosting]
ms.assetid: e47e3655-efd5-4572-a1dc-50c69bf2a468
topic_type:
- apiref
ms.openlocfilehash: 832ae03c0126f0c08afa9b5c0312a636ec1de294
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753943"
---
# <a name="iclrruntimehostgetclrcontrol-method"></a><span data-ttu-id="70437-103">Метод ICLRRuntimeHost::GetCLRControl</span><span class="sxs-lookup"><span data-stu-id="70437-103">ICLRRuntimeHost::GetCLRControl Method</span></span>

<span data-ttu-id="70437-104">Возвращает указатель интерфейса типа [ICLRControl Interface](iclrcontrol-interface.md) , который может использоваться узлами для настройки аспектов среды CLR.</span><span class="sxs-lookup"><span data-stu-id="70437-104">Gets an interface pointer of type [ICLRControl Interface](iclrcontrol-interface.md) that hosts can use to customize aspects of the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="70437-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="70437-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCLRControl(  
    [out] ICLRControl** pCLRControl  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="70437-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="70437-106">Parameters</span></span>  

 `pCLRControl`  
 <span data-ttu-id="70437-107">заполняет Указатель интерфейса типа [ICLRControl Interface](iclrcontrol-interface.md) , который позволяет узлам настраивать дополнительные аспекты среды CLR.</span><span class="sxs-lookup"><span data-stu-id="70437-107">[out] An interface pointer of type [ICLRControl Interface](iclrcontrol-interface.md) that enables hosts to configure additional aspects of the CLR.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="70437-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="70437-108">Return Value</span></span>  
  
|<span data-ttu-id="70437-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="70437-109">HRESULT</span></span>|<span data-ttu-id="70437-110">Описание:</span><span class="sxs-lookup"><span data-stu-id="70437-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="70437-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="70437-111">S_OK</span></span>|<span data-ttu-id="70437-112">`GetCLRControl` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="70437-112">`GetCLRControl` returned successfully.</span></span>|  
|<span data-ttu-id="70437-113">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="70437-113">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="70437-114">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="70437-114">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="70437-115">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="70437-115">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="70437-116">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="70437-116">The call timed out.</span></span>|  
|<span data-ttu-id="70437-117">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="70437-117">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="70437-118">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="70437-118">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="70437-119">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="70437-119">HOST_E_ABANDONED</span></span>|<span data-ttu-id="70437-120">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="70437-120">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="70437-121">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="70437-121">E_FAIL</span></span>|<span data-ttu-id="70437-122">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="70437-122">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="70437-123">Если метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="70437-123">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="70437-124">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="70437-124">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="70437-125">HOST_E_INVALIDOPERATION</span><span class="sxs-lookup"><span data-stu-id="70437-125">HOST_E_INVALIDOPERATION</span></span>|<span data-ttu-id="70437-126">Среда CLR уже запущена.</span><span class="sxs-lookup"><span data-stu-id="70437-126">The CLR has already started.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="70437-127">Remarks</span><span class="sxs-lookup"><span data-stu-id="70437-127">Remarks</span></span>  

 <span data-ttu-id="70437-128">`ICLRControl` предоставляет метод [метода GetCLRManager](iclrcontrol-getclrmanager-method.md) , который позволяет узлу получить указатель интерфейса на один из типов диспетчера.</span><span class="sxs-lookup"><span data-stu-id="70437-128">`ICLRControl` provides the [GetCLRManager Method](iclrcontrol-getclrmanager-method.md) method, which enables the host to get an interface pointer to one of the manager types.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="70437-129">Требования</span><span class="sxs-lookup"><span data-stu-id="70437-129">Requirements</span></span>  

 <span data-ttu-id="70437-130">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="70437-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="70437-131">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="70437-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="70437-132">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="70437-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="70437-133">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="70437-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70437-134">См. также</span><span class="sxs-lookup"><span data-stu-id="70437-134">See also</span></span>

- [<span data-ttu-id="70437-135">Интерфейс ICLRControl</span><span class="sxs-lookup"><span data-stu-id="70437-135">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="70437-136">Интерфейс ICLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="70437-136">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)
