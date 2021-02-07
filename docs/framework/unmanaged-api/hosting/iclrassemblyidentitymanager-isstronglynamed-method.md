---
description: 'Дополнительные сведения о методе: ICLRAssemblyIdentityManager:: IsStronglyNamed'
title: Метод ICLRAssemblyIdentityManager::IsStronglyNamed
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager.IsStronglyNamed
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager::IsStronglyNamed
helpviewer_keywords:
- IsStronglyNamed method [.NET Framework hosting]
- ICLRAssemblyIdentityManager::IsStronglyNamed method [.NET Framework hosting]
ms.assetid: 954bd386-2076-4d00-9d46-38c728aa9cab
topic_type:
- apiref
ms.openlocfilehash: f6f1715513fba56e10b10c14c298d3c553fd4652
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99716852"
---
# <a name="iclrassemblyidentitymanagerisstronglynamed-method"></a><span data-ttu-id="fc356-103">Метод ICLRAssemblyIdentityManager::IsStronglyNamed</span><span class="sxs-lookup"><span data-stu-id="fc356-103">ICLRAssemblyIdentityManager::IsStronglyNamed Method</span></span>

<span data-ttu-id="fc356-104">Возвращает значение, указывающее, является ли указанная сборка строго именованной.</span><span class="sxs-lookup"><span data-stu-id="fc356-104">Gets a value that indicates whether the specified assembly is strongly named.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc356-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="fc356-105">Syntax</span></span>  
  
```cpp  
RESULT IsStronglyNamed (  
    [in]  LPCWSTR  pwzAssemblyIdentity,  
    [out] BOOL    *pbIsStronglyNamed  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fc356-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="fc356-106">Parameters</span></span>  

 `pwzAssemblyIdentity`  
 <span data-ttu-id="fc356-107">окне Непрозрачные канонические данные идентификации сборки для оценки.</span><span class="sxs-lookup"><span data-stu-id="fc356-107">[in] The opaque canonical assembly identity data of the assembly to be evaluated.</span></span>  
  
 `pbIsStronglyNamed`  
 <span data-ttu-id="fc356-108">[out] `true` , если сборка, на которую ссылается `pwzAssemblyIdentity` параметр, имеет строгое имя; в противном случае — значение `false` .</span><span class="sxs-lookup"><span data-stu-id="fc356-108">[out] `true`, if the assembly referenced by the `pwzAssemblyIdentity` parameter is strongly named; otherwise, `false`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fc356-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="fc356-109">Return Value</span></span>  
  
|<span data-ttu-id="fc356-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="fc356-110">HRESULT</span></span>|<span data-ttu-id="fc356-111">Описание:</span><span class="sxs-lookup"><span data-stu-id="fc356-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="fc356-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="fc356-112">S_OK</span></span>|<span data-ttu-id="fc356-113">Метод возвратился успешно.</span><span class="sxs-lookup"><span data-stu-id="fc356-113">The method returned successfully.</span></span>|  
|<span data-ttu-id="fc356-114">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="fc356-114">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="fc356-115">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="fc356-115">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="fc356-116">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="fc356-116">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="fc356-117">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="fc356-117">The call timed out.</span></span>|  
|<span data-ttu-id="fc356-118">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="fc356-118">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="fc356-119">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="fc356-119">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="fc356-120">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="fc356-120">HOST_E_ABANDONED</span></span>|<span data-ttu-id="fc356-121">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="fc356-121">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="fc356-122">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="fc356-122">E_FAIL</span></span>|<span data-ttu-id="fc356-123">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="fc356-123">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="fc356-124">Если метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="fc356-124">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="fc356-125">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="fc356-125">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="fc356-126">Требования</span><span class="sxs-lookup"><span data-stu-id="fc356-126">Requirements</span></span>  

 <span data-ttu-id="fc356-127">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc356-127">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc356-128">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="fc356-128">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="fc356-129">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fc356-129">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fc356-130">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc356-130">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc356-131">См. также</span><span class="sxs-lookup"><span data-stu-id="fc356-131">See also</span></span>

- [<span data-ttu-id="fc356-132">Интерфейс ICLRAssemblyIdentityManager</span><span class="sxs-lookup"><span data-stu-id="fc356-132">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
