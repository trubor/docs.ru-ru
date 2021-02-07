---
description: 'Дополнительные сведения о методе: ICLRAssemblyIdentityManager:: GetBindingIdentityFromFile'
title: Метод ICLRAssemblyIdentityManager::GetBindingIdentityFromFile
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager.GetBindingIdentityFromFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager::GetBindingIdentityFromFile
helpviewer_keywords:
- GetBindingIdentityFromFile method [.NET Framework hosting]
- ICLRAssemblyIdentityManager::GetBindingIdentifyFromFile method [.NET Framework hosting]
ms.assetid: 7797562d-7b4c-4bd9-8b93-f35e0e2869e4
topic_type:
- apiref
ms.openlocfilehash: 82e72155b38f71fe2c024994f07178638095be9a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99689553"
---
# <a name="iclrassemblyidentitymanagergetbindingidentityfromfile-method"></a><span data-ttu-id="a8f03-103">Метод ICLRAssemblyIdentityManager::GetBindingIdentityFromFile</span><span class="sxs-lookup"><span data-stu-id="a8f03-103">ICLRAssemblyIdentityManager::GetBindingIdentityFromFile Method</span></span>

<span data-ttu-id="a8f03-104">Возвращает данные привязки удостоверения сборки для сборки по указанному пути к файлу.</span><span class="sxs-lookup"><span data-stu-id="a8f03-104">Gets the assembly identity binding data for the assembly at the specified file path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8f03-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a8f03-105">Syntax</span></span>  
  
```cpp  
HRESULT GetBindingIdentityFromFile(  
    [in] LPCWSTR     pwzFilePath,  
    [in] DWORD       dwFlags,  
    [out, size_is(*pcchBufferSize)] LPWSTR pwzBuffer,  
    [in, out] DWORD *pcchBufferSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a8f03-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="a8f03-106">Parameters</span></span>  

 `pwzFilePath`  
 <span data-ttu-id="a8f03-107">окне Путь к файлу, который необходимо вычислить.</span><span class="sxs-lookup"><span data-stu-id="a8f03-107">[in] The path to the file to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="a8f03-108">окне Значение перечисления [ECLRAssemblyIdentityFlags](eclrassemblyidentityflags-enumeration.md) , указывающее тип удостоверения сборки.</span><span class="sxs-lookup"><span data-stu-id="a8f03-108">[in] A value of the [ECLRAssemblyIdentityFlags](eclrassemblyidentityflags-enumeration.md) enumeration that indicates an assembly's identity type.</span></span> <span data-ttu-id="a8f03-109">Предоставляется для будущего расширения.</span><span class="sxs-lookup"><span data-stu-id="a8f03-109">Provided for future extensibility.</span></span> <span data-ttu-id="a8f03-110">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT — единственное значение, поддерживаемое общеязыковой средой выполнения (CLR) версии 2,0.</span><span class="sxs-lookup"><span data-stu-id="a8f03-110">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the common language runtime (CLR) version 2.0 supports.</span></span>  
  
 `pwzBuffer`  
 <span data-ttu-id="a8f03-111">заполняет Буфер, содержащий непрозрачные данные идентификации сборки.</span><span class="sxs-lookup"><span data-stu-id="a8f03-111">[out] A buffer containing the opaque assembly identity data.</span></span>  
  
 `pcchBufferSize`  
 <span data-ttu-id="a8f03-112">[вход, выход] Указатель на размер `pwzBuffer` .</span><span class="sxs-lookup"><span data-stu-id="a8f03-112">[in, out] A pointer to the size of `pwzBuffer`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a8f03-113">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="a8f03-113">Return Value</span></span>  
  
|<span data-ttu-id="a8f03-114">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a8f03-114">HRESULT</span></span>|<span data-ttu-id="a8f03-115">Описание:</span><span class="sxs-lookup"><span data-stu-id="a8f03-115">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a8f03-116">S_OK</span><span class="sxs-lookup"><span data-stu-id="a8f03-116">S_OK</span></span>|<span data-ttu-id="a8f03-117">Метод возвратился успешно.</span><span class="sxs-lookup"><span data-stu-id="a8f03-117">The method returned successfully.</span></span>|  
|<span data-ttu-id="a8f03-118">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="a8f03-118">E_INVALIDARG</span></span>|<span data-ttu-id="a8f03-119">Переданный параметр `pwzFilePath` имеет значение null.</span><span class="sxs-lookup"><span data-stu-id="a8f03-119">The supplied `pwzFilePath` is null.</span></span>|  
|<span data-ttu-id="a8f03-120">ERROR_INSUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="a8f03-120">ERROR_INSUFFICIENT_BUFFER</span></span>|<span data-ttu-id="a8f03-121">Размер `pwzBuffer` слишком мал.</span><span class="sxs-lookup"><span data-stu-id="a8f03-121">The size of `pwzBuffer` is too small.</span></span>|  
|<span data-ttu-id="a8f03-122">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="a8f03-122">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="a8f03-123">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="a8f03-123">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="a8f03-124">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="a8f03-124">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="a8f03-125">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="a8f03-125">The call timed out.</span></span>|  
|<span data-ttu-id="a8f03-126">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="a8f03-126">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="a8f03-127">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="a8f03-127">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="a8f03-128">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="a8f03-128">HOST_E_ABANDONED</span></span>|<span data-ttu-id="a8f03-129">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="a8f03-129">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="a8f03-130">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="a8f03-130">E_FAIL</span></span>|<span data-ttu-id="a8f03-131">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="a8f03-131">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="a8f03-132">Если метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="a8f03-132">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="a8f03-133">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="a8f03-133">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a8f03-134">Remarks</span><span class="sxs-lookup"><span data-stu-id="a8f03-134">Remarks</span></span>  

 <span data-ttu-id="a8f03-135">`GetBindingIdentityFromFile` обычно вызывается дважды.</span><span class="sxs-lookup"><span data-stu-id="a8f03-135">`GetBindingIdentityFromFile` is typically called twice.</span></span> <span data-ttu-id="a8f03-136">Первый вызов предоставляет значение NULL для `pwzBuffer` , а метод возвращает соответствующий размер в `pcchBufferSize` .</span><span class="sxs-lookup"><span data-stu-id="a8f03-136">The first call supplies a null value for `pwzBuffer`, and the method returns the appropriate size in `pcchBufferSize`.</span></span> <span data-ttu-id="a8f03-137">Второй вызов предоставляет соответствующий буфер, а метод возвращает фактические данные буфера после завершения.</span><span class="sxs-lookup"><span data-stu-id="a8f03-137">The second call supplies an appropriately allocated buffer, and the method returns with the actual buffer data upon completion.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a8f03-138">Требования</span><span class="sxs-lookup"><span data-stu-id="a8f03-138">Requirements</span></span>  

 <span data-ttu-id="a8f03-139">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a8f03-139">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8f03-140">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a8f03-140">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a8f03-141">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a8f03-141">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a8f03-142">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8f03-142">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8f03-143">См. также</span><span class="sxs-lookup"><span data-stu-id="a8f03-143">See also</span></span>

- [<span data-ttu-id="a8f03-144">Интерфейс ICLRAssemblyIdentityManager</span><span class="sxs-lookup"><span data-stu-id="a8f03-144">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="a8f03-145">Интерфейс ICLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="a8f03-145">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="a8f03-146">Интерфейс ICLRHostBindingPolicyManager</span><span class="sxs-lookup"><span data-stu-id="a8f03-146">ICLRHostBindingPolicyManager Interface</span></span>](iclrhostbindingpolicymanager-interface.md)
