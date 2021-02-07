---
description: 'Дополнительные сведения о методе: IHostSecurityManager:: Getsecuritycontext-'
title: Метод IHostSecurityManager::GetSecurityContext
ms.date: 03/30/2017
api_name:
- IHostSecurityManager.GetSecurityContext
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager::GetSecurityContext
helpviewer_keywords:
- GetSecurityContext method [.NET Framework hosting]
- IHostSecurityManager::GetSecurityContext method [.NET Framework hosting]
ms.assetid: 958970d6-f6a2-4b84-b32a-f555cbaf8f61
topic_type:
- apiref
ms.openlocfilehash: 0dc9e0380d2fb218b68f6beb85fa1ccba8826d85
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99671569"
---
# <a name="ihostsecuritymanagergetsecuritycontext-method"></a><span data-ttu-id="6944d-103">Метод IHostSecurityManager::GetSecurityContext</span><span class="sxs-lookup"><span data-stu-id="6944d-103">IHostSecurityManager::GetSecurityContext Method</span></span>

<span data-ttu-id="6944d-104">Возвращает запрошенный [IHostSecurityContext](ihostsecuritycontext-interface.md) из узла.</span><span class="sxs-lookup"><span data-stu-id="6944d-104">Gets the requested [IHostSecurityContext](ihostsecuritycontext-interface.md) from the host.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6944d-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="6944d-105">Syntax</span></span>  
  
```cpp
HRESULT GetSecurityContext (  
    [in]  EContextType eContextType,
    [out] IHostSecurityContext** ppSecurityContext  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6944d-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="6944d-106">Parameters</span></span>  

 `eContextType`  
 <span data-ttu-id="6944d-107">окне Одно из значений [еконтексттипе](econtexttype-enumeration.md) , указывающее тип возвращаемого контекста безопасности.</span><span class="sxs-lookup"><span data-stu-id="6944d-107">[in] One of the [EContextType](econtexttype-enumeration.md) values, indicating what type of security context to return.</span></span>  
  
 `ppSecurityContext`  
 <span data-ttu-id="6944d-108">заполняет Адрес указателя интерфейса на `IHostSecurityContext` `eContextType` .</span><span class="sxs-lookup"><span data-stu-id="6944d-108">[out] The address of an interface pointer to the `IHostSecurityContext` of `eContextType`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6944d-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="6944d-109">Return Value</span></span>  
  
|<span data-ttu-id="6944d-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="6944d-110">HRESULT</span></span>|<span data-ttu-id="6944d-111">Описание:</span><span class="sxs-lookup"><span data-stu-id="6944d-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="6944d-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="6944d-112">S_OK</span></span>|<span data-ttu-id="6944d-113">`GetSecurityContext` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="6944d-113">`GetSecurityContext` returned successfully.</span></span>|  
|<span data-ttu-id="6944d-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="6944d-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="6944d-115">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="6944d-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="6944d-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="6944d-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="6944d-117">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="6944d-117">The call timed out.</span></span>|  
|<span data-ttu-id="6944d-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="6944d-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="6944d-119">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="6944d-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="6944d-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="6944d-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="6944d-121">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="6944d-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="6944d-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="6944d-122">E_FAIL</span></span>|<span data-ttu-id="6944d-123">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="6944d-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="6944d-124">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="6944d-124">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="6944d-125">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="6944d-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6944d-126">Remarks</span><span class="sxs-lookup"><span data-stu-id="6944d-126">Remarks</span></span>  

 <span data-ttu-id="6944d-127">Узел может управлять доступом кода к маркерам потоков как средой CLR, так и кодом пользователя.</span><span class="sxs-lookup"><span data-stu-id="6944d-127">A host can control all code access to thread tokens by both the CLR and user code.</span></span> <span data-ttu-id="6944d-128">Он также может гарантировать, что полные сведения о контексте безопасности передаются по асинхронным операциям или кодовым точкам с ограниченным доступом к коду.</span><span class="sxs-lookup"><span data-stu-id="6944d-128">It can also ensure that complete security context information is passed across asynchronous operations or code points with restricted code access.</span></span> <span data-ttu-id="6944d-129">`IHostSecurityContext` инкапсулирует эти сведения о контексте безопасности, которые непрозрачны для среды CLR.</span><span class="sxs-lookup"><span data-stu-id="6944d-129">`IHostSecurityContext` encapsulates this security context information, which is opaque to the CLR.</span></span> <span data-ttu-id="6944d-130">Среда CLR захватывает эти сведения и перемещает их между отправкой рабочего элемента пула потоков, выполнением метода завершения, а также созданием модулей и классов.</span><span class="sxs-lookup"><span data-stu-id="6944d-130">The CLR captures this information and moves it across thread pool worker item dispatch, finalizer execution, and module and class construction.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6944d-131">Требования</span><span class="sxs-lookup"><span data-stu-id="6944d-131">Requirements</span></span>  

 <span data-ttu-id="6944d-132">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6944d-132">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6944d-133">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="6944d-133">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6944d-134">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6944d-134">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6944d-135">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6944d-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6944d-136">См. также</span><span class="sxs-lookup"><span data-stu-id="6944d-136">See also</span></span>

- [<span data-ttu-id="6944d-137">Перечисление EContextType</span><span class="sxs-lookup"><span data-stu-id="6944d-137">EContextType Enumeration</span></span>](econtexttype-enumeration.md)
- [<span data-ttu-id="6944d-138">Интерфейс IHostSecurityContext</span><span class="sxs-lookup"><span data-stu-id="6944d-138">IHostSecurityContext Interface</span></span>](ihostsecuritycontext-interface.md)
- [<span data-ttu-id="6944d-139">Интерфейс IHostSecurityManager</span><span class="sxs-lookup"><span data-stu-id="6944d-139">IHostSecurityManager Interface</span></span>](ihostsecuritymanager-interface.md)
