---
description: 'Дополнительные сведения о методе: ICLRRuntimeHost:: ExecuteInDefaultAppDomain'
title: Метод ICLRRuntimeHost::ExecuteInDefaultAppDomain
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.ExecuteInDefaultAppDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::ExecuteInDefaultAppDomain
helpviewer_keywords:
- ICLRRuntimeHost::ExecuteInDefaultAppDomain method [.NET Framework hosting]
- ExecuteInDefaultAppDomain method [.NET Framework hosting]
ms.assetid: 30b5cf9a-a762-4bd4-be12-d6c1442b78b1
topic_type:
- apiref
ms.openlocfilehash: 0fae9be69cf67da252dcdb423432ec922c0b00ac
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785139"
---
# <a name="iclrruntimehostexecuteindefaultappdomain-method"></a><span data-ttu-id="4049d-103">Метод ICLRRuntimeHost::ExecuteInDefaultAppDomain</span><span class="sxs-lookup"><span data-stu-id="4049d-103">ICLRRuntimeHost::ExecuteInDefaultAppDomain Method</span></span>

<span data-ttu-id="4049d-104">Вызывает указанный метод указанного типа в указанной управляемой сборке.</span><span class="sxs-lookup"><span data-stu-id="4049d-104">Calls the specified method of the specified type in the specified managed assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4049d-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="4049d-105">Syntax</span></span>  
  
```cpp  
HRESULT ExecuteInDefaultAppDomain (  
    [in] LPCWSTR pwzAssemblyPath,  
    [in] LPCWSTR pwzTypeName,
    [in] LPCWSTR pwzMethodName,  
    [in] LPCWSTR pwzArgument,  
    [out] DWORD *pReturnValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4049d-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="4049d-106">Parameters</span></span>  

 `pwzAssemblyPath`  
 <span data-ttu-id="4049d-107">окне Путь к элементу <xref:System.Reflection.Assembly> , который определяет <xref:System.Type> метод, для которого нужно вызвать.</span><span class="sxs-lookup"><span data-stu-id="4049d-107">[in] The path to the <xref:System.Reflection.Assembly> that defines the <xref:System.Type> whose method is to be invoked.</span></span>  
  
 `pwzTypeName`  
 <span data-ttu-id="4049d-108">окне Имя объекта <xref:System.Type> , определяющего вызываемый метод.</span><span class="sxs-lookup"><span data-stu-id="4049d-108">[in] The name of the <xref:System.Type> that defines the method to invoke.</span></span>  
  
 `pwzMethodName`  
 <span data-ttu-id="4049d-109">окне Имя вызываемого метода.</span><span class="sxs-lookup"><span data-stu-id="4049d-109">[in] The name of the method to invoke.</span></span>  
  
 `pwzArgument`  
 <span data-ttu-id="4049d-110">окне Строковый параметр для передачи в метод.</span><span class="sxs-lookup"><span data-stu-id="4049d-110">[in] The string parameter to pass to the method.</span></span>  
  
 `pReturnValue`  
 <span data-ttu-id="4049d-111">заполняет Целочисленное значение, возвращаемое вызванным методом.</span><span class="sxs-lookup"><span data-stu-id="4049d-111">[out] The integer value returned by the invoked method.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4049d-112">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="4049d-112">Return Value</span></span>  
  
|<span data-ttu-id="4049d-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4049d-113">HRESULT</span></span>|<span data-ttu-id="4049d-114">Описание:</span><span class="sxs-lookup"><span data-stu-id="4049d-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4049d-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="4049d-115">S_OK</span></span>|<span data-ttu-id="4049d-116">`ExecuteInDefaultAppDomain` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="4049d-116">`ExecuteInDefaultAppDomain` returned successfully.</span></span>|  
|<span data-ttu-id="4049d-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4049d-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4049d-118">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="4049d-118">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4049d-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4049d-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4049d-120">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="4049d-120">The call timed out.</span></span>|  
|<span data-ttu-id="4049d-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4049d-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4049d-122">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="4049d-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4049d-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4049d-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4049d-124">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="4049d-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4049d-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4049d-125">E_FAIL</span></span>|<span data-ttu-id="4049d-126">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="4049d-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4049d-127">Если метод возвращает E_FAIL, список отзыва сертификатов больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="4049d-127">If a method returns E_FAIL, the CRL is no longer usable within the process.</span></span> <span data-ttu-id="4049d-128">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="4049d-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4049d-129">Remarks</span><span class="sxs-lookup"><span data-stu-id="4049d-129">Remarks</span></span>  

 <span data-ttu-id="4049d-130">Вызванный метод должен иметь следующую сигнатуру:</span><span class="sxs-lookup"><span data-stu-id="4049d-130">The invoked method must have the following signature:</span></span>  
  
```cpp  
static int pwzMethodName (String pwzArgument)  
```  
  
 <span data-ttu-id="4049d-131">где `pwzMethodName` представляет имя вызванного метода и `pwzArgument` представляет строковое значение, передаваемое в качестве параметра этому методу.</span><span class="sxs-lookup"><span data-stu-id="4049d-131">where `pwzMethodName` represents the name of the invoked method, and `pwzArgument` represents the string value passed as a parameter to that method.</span></span> <span data-ttu-id="4049d-132">Если значение HRESULT установлено в S_OK, то для параметра задается `pReturnValue` целочисленное значение, возвращаемое вызванным методом.</span><span class="sxs-lookup"><span data-stu-id="4049d-132">If the HRESULT value is set to S_OK, `pReturnValue` is set to the integer value returned by the invoked method.</span></span> <span data-ttu-id="4049d-133">В противном случае `pReturnValue` значение не задано.</span><span class="sxs-lookup"><span data-stu-id="4049d-133">Otherwise, `pReturnValue` is not set.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4049d-134">Требования</span><span class="sxs-lookup"><span data-stu-id="4049d-134">Requirements</span></span>  

 <span data-ttu-id="4049d-135">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4049d-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4049d-136">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="4049d-136">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4049d-137">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4049d-137">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4049d-138">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4049d-138">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4049d-139">См. также</span><span class="sxs-lookup"><span data-stu-id="4049d-139">See also</span></span>

- [<span data-ttu-id="4049d-140">Интерфейс ICLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="4049d-140">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)
