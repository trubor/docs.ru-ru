---
description: 'Дополнительные сведения о методе: Иклрвалидатор:: FormatEventInfo'
title: Метод ICLRValidator::FormatEventInfo
ms.date: 03/30/2017
api_name:
- ICLRValidator.FormatEventInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRValidator::FormatEventInfo
helpviewer_keywords:
- FormatEventInfo method, ICLRValidator interface [.NET Framework hosting]
- ICLRValidator::FormatEventInfo method [.NET Framework hosting]
ms.assetid: 808e1f1d-52f4-47c4-83cc-dcf47d075219
topic_type:
- apiref
ms.openlocfilehash: 3d8d1eff8c638517e201905d0313ee824490acf4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99636797"
---
# <a name="iclrvalidatorformateventinfo-method"></a><span data-ttu-id="30a06-103">Метод ICLRValidator::FormatEventInfo</span><span class="sxs-lookup"><span data-stu-id="30a06-103">ICLRValidator::FormatEventInfo Method</span></span>

<span data-ttu-id="30a06-104">Возвращает подробное сообщение об указанной ошибке проверки.</span><span class="sxs-lookup"><span data-stu-id="30a06-104">Gets a detailed message about the specified validation error.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30a06-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="30a06-105">Syntax</span></span>  
  
```cpp  
HRESULT FormatEventInfo (  
    [in] HRESULT            hVECode,  
    [in] VEContext          Context,  
    [in, out] LPWSTR        msg,  
    [in] unsigned long      ulMaxLength,  
    [in] SAFEARRAY(VARIANT) psa  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="30a06-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="30a06-106">Parameters</span></span>  

 `hVECode`  
 <span data-ttu-id="30a06-107">окне Значение HRESULT, которое было передано обработчику ошибок проверки.</span><span class="sxs-lookup"><span data-stu-id="30a06-107">[in] The HRESULT value that was passed to the validation error handler.</span></span>  
  
 `Context`  
 <span data-ttu-id="30a06-108">окне `VEContext` Экземпляр, содержащий контекстные сведения об ошибках проверки.</span><span class="sxs-lookup"><span data-stu-id="30a06-108">[in] A `VEContext` instance that contains context information about the validation errors.</span></span>  
  
 `msg`  
 <span data-ttu-id="30a06-109">[вход, выход] Понятное сообщение об ошибке.</span><span class="sxs-lookup"><span data-stu-id="30a06-109">[in, out] The friendly error message.</span></span>  
  
 `ulMaxLength`  
 <span data-ttu-id="30a06-110">окне Максимальная длина сообщения об ошибке.</span><span class="sxs-lookup"><span data-stu-id="30a06-110">[in] The maximum length of the error message.</span></span>  
  
 `psa`  
 <span data-ttu-id="30a06-111">окне Защищенный массив дополнительных параметров, которые будут использоваться в сообщении.</span><span class="sxs-lookup"><span data-stu-id="30a06-111">[in] A safe array of additional parameters to be used in the message.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="30a06-112">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="30a06-112">Return Value</span></span>  
  
|<span data-ttu-id="30a06-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="30a06-113">HRESULT</span></span>|<span data-ttu-id="30a06-114">Описание:</span><span class="sxs-lookup"><span data-stu-id="30a06-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="30a06-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="30a06-115">S_OK</span></span>|<span data-ttu-id="30a06-116">`FormatEventInfo` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="30a06-116">`FormatEventInfo` returned successfully.</span></span>|  
|<span data-ttu-id="30a06-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="30a06-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="30a06-118">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="30a06-118">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="30a06-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="30a06-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="30a06-120">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="30a06-120">The call timed out.</span></span>|  
|<span data-ttu-id="30a06-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="30a06-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="30a06-122">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="30a06-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="30a06-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="30a06-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="30a06-124">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="30a06-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="30a06-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="30a06-125">E_FAIL</span></span>|<span data-ttu-id="30a06-126">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="30a06-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="30a06-127">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="30a06-127">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="30a06-128">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="30a06-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="30a06-129">Требования</span><span class="sxs-lookup"><span data-stu-id="30a06-129">Requirements</span></span>  

 <span data-ttu-id="30a06-130">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="30a06-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30a06-131">**Заголовок:** IValidator. idl, IValidator. h</span><span class="sxs-lookup"><span data-stu-id="30a06-131">**Header:** IValidator.idl, IValidator.h</span></span>  
  
 <span data-ttu-id="30a06-132">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="30a06-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="30a06-133">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30a06-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30a06-134">См. также</span><span class="sxs-lookup"><span data-stu-id="30a06-134">See also</span></span>

- [<span data-ttu-id="30a06-135">Интерфейс ICLRErrorReportingManager</span><span class="sxs-lookup"><span data-stu-id="30a06-135">ICLRErrorReportingManager Interface</span></span>](iclrerrorreportingmanager-interface.md)
- [<span data-ttu-id="30a06-136">Интерфейс ICLRValidator</span><span class="sxs-lookup"><span data-stu-id="30a06-136">ICLRValidator Interface</span></span>](iclrvalidator-interface.md)
