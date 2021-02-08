---
description: 'Дополнительные сведения о методе: Иклрхостпротектионманажер:: Сетеажерсериализегрантсетс'
title: Метод ICLRHostProtectionManager::SetEagerSerializeGrantSets
ms.date: 03/30/2017
api_name:
- ICLRHostProtectionManager.SetEagerSerializeGrantSets
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRHostProtectionManager::SetEagerSerializeGrantSets
helpviewer_keywords:
- SetEagerSerializeGrantSets method [.NET Framework hosting]
- ICLRHostProtectionManager::SetEagerSerializeGrantSets method [.NET Framework hosting]
ms.assetid: d6158360-22b1-4ace-ad85-d830b9964783
topic_type:
- apiref
ms.openlocfilehash: 04eb00b1422523e8057c3a0fc27dfe7e49f98f08
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789920"
---
# <a name="iclrhostprotectionmanagerseteagerserializegrantsets-method"></a><span data-ttu-id="2f5f7-103">Метод ICLRHostProtectionManager::SetEagerSerializeGrantSets</span><span class="sxs-lookup"><span data-stu-id="2f5f7-103">ICLRHostProtectionManager::SetEagerSerializeGrantSets Method</span></span>

<span data-ttu-id="2f5f7-104">Этот метод поддерживает инфраструктуру .NET Framework и не предназначен для использования непосредственно из программного кода.</span><span class="sxs-lookup"><span data-stu-id="2f5f7-104">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f5f7-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="2f5f7-105">Syntax</span></span>  
  
```cpp  
HRESULT SetEagerSerializeGrantSets ();  
```  
  
## <a name="return-value"></a><span data-ttu-id="2f5f7-106">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="2f5f7-106">Return Value</span></span>  
  
|<span data-ttu-id="2f5f7-107">HRESULT</span><span class="sxs-lookup"><span data-stu-id="2f5f7-107">HRESULT</span></span>|<span data-ttu-id="2f5f7-108">Описание:</span><span class="sxs-lookup"><span data-stu-id="2f5f7-108">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="2f5f7-109">S_OK</span><span class="sxs-lookup"><span data-stu-id="2f5f7-109">S_OK</span></span>|<span data-ttu-id="2f5f7-110">`SetEagerSerializeGrantSets` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="2f5f7-110">`SetEagerSerializeGrantSets` returned successfully.</span></span>|  
|<span data-ttu-id="2f5f7-111">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="2f5f7-111">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="2f5f7-112">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="2f5f7-112">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="2f5f7-113">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="2f5f7-113">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="2f5f7-114">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="2f5f7-114">The call timed out.</span></span>|  
|<span data-ttu-id="2f5f7-115">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="2f5f7-115">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="2f5f7-116">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="2f5f7-116">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="2f5f7-117">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="2f5f7-117">HOST_E_ABANDONED</span></span>|<span data-ttu-id="2f5f7-118">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="2f5f7-118">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="2f5f7-119">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="2f5f7-119">E_FAIL</span></span>|<span data-ttu-id="2f5f7-120">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="2f5f7-120">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="2f5f7-121">После того как метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="2f5f7-121">After a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="2f5f7-122">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="2f5f7-122">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2f5f7-123">Требования</span><span class="sxs-lookup"><span data-stu-id="2f5f7-123">Requirements</span></span>  

 <span data-ttu-id="2f5f7-124">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2f5f7-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f5f7-125">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="2f5f7-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2f5f7-126">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2f5f7-126">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2f5f7-127">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f5f7-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f5f7-128">См. также</span><span class="sxs-lookup"><span data-stu-id="2f5f7-128">See also</span></span>

- [<span data-ttu-id="2f5f7-129">Интерфейс ICLRControl</span><span class="sxs-lookup"><span data-stu-id="2f5f7-129">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
- [<span data-ttu-id="2f5f7-130">Интерфейс ICLRHostProtectionManager</span><span class="sxs-lookup"><span data-stu-id="2f5f7-130">ICLRHostProtectionManager Interface</span></span>](iclrhostprotectionmanager-interface.md)
