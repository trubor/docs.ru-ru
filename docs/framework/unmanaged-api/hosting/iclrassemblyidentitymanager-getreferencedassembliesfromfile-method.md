---
description: 'Дополнительные сведения о методе: ICLRAssemblyIdentityManager:: Жетреференцедассемблиесфромфиле'
title: Метод ICLRAssemblyIdentityManager::GetReferencedAssembliesFromFile
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager.GetReferencedAssembliesFromFile
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager::GetReferencedAssembliesFromFile
helpviewer_keywords:
- ICLRAssemblyIdentityManager::GetReferenceAssembliesFromFile method [.NET Framework hosting]
- GetReferenceAssembliesFromFile method [.NET Framework hosting]
ms.assetid: eed63d31-d977-4c7d-9443-f9d37a2a7d81
topic_type:
- apiref
ms.openlocfilehash: 46b2f392746c6e23e2a8a11aded5eacd8f5a597b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790063"
---
# <a name="iclrassemblyidentitymanagergetreferencedassembliesfromfile-method"></a><span data-ttu-id="933ae-103">Метод ICLRAssemblyIdentityManager::GetReferencedAssembliesFromFile</span><span class="sxs-lookup"><span data-stu-id="933ae-103">ICLRAssemblyIdentityManager::GetReferencedAssembliesFromFile Method</span></span>

<span data-ttu-id="933ae-104">Возвращает экземпляр [ICLRReferenceAssemblyEnum](iclrreferenceassemblyenum-interface.md) , содержащий список сборок, на которые ссылается сборка по указанному пути к файлу.</span><span class="sxs-lookup"><span data-stu-id="933ae-104">Gets an [ICLRReferenceAssemblyEnum](iclrreferenceassemblyenum-interface.md) instance that contains a list of assemblies referenced by the assembly at the specified file path.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="933ae-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="933ae-105">Syntax</span></span>  
  
```cpp  
HRESULT GetReferencedAssembliesFromFile (  
    [in]  LPCWSTR pwzFilePath,  
    [in]  DWORD   dwFlags,  
    [in]  ICLRAssemblyReferenceList   *pExcludeAssembliesList,  
    [out] ICLRReferenceAssemblyEnum  **ppReferenceEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="933ae-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="933ae-106">Parameters</span></span>  

 `pwzFilePath`  
 <span data-ttu-id="933ae-107">окне Путь к сборке, которую необходимо вычислить.</span><span class="sxs-lookup"><span data-stu-id="933ae-107">[in] The path to the assembly to be evaluated.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="933ae-108">окне Предоставляется для будущего расширения.</span><span class="sxs-lookup"><span data-stu-id="933ae-108">[in] Provided for future extensibility.</span></span> <span data-ttu-id="933ae-109">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT является единственным значением, которое поддерживает Текущая версия среды CLR.</span><span class="sxs-lookup"><span data-stu-id="933ae-109">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pExcludeAssembliesList`  
 <span data-ttu-id="933ae-110">окне Указатель на объект [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) , представляющий сборки, которые должны быть исключены из `ppReferenceEnum` .</span><span class="sxs-lookup"><span data-stu-id="933ae-110">[in] A pointer to an [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) object that represents assemblies that should be excluded from `ppReferenceEnum`.</span></span>  
  
 `ppReferenceEnum`  
 <span data-ttu-id="933ae-111">заполняет Указатель на адрес `ICLRReferenceAssemblyEnum` объекта, который содержит данные идентификации сборки для сборок, на которые ссылается сборка `pwzFilePath` , за исключением сборок, представленных в `pExcludeAssembliesList` .</span><span class="sxs-lookup"><span data-stu-id="933ae-111">[out] A pointer to the address of an `ICLRReferenceAssemblyEnum` object that contains assembly identity data for the assemblies referenced by the assembly at `pwzFilePath`, excluding the assemblies represented by `pExcludeAssembliesList`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="933ae-112">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="933ae-112">Return Value</span></span>  
  
|<span data-ttu-id="933ae-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="933ae-113">HRESULT</span></span>|<span data-ttu-id="933ae-114">Описание:</span><span class="sxs-lookup"><span data-stu-id="933ae-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="933ae-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="933ae-115">S_OK</span></span>|<span data-ttu-id="933ae-116">Метод возвратился успешно.</span><span class="sxs-lookup"><span data-stu-id="933ae-116">The method returned successfully.</span></span>|  
|<span data-ttu-id="933ae-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="933ae-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="933ae-118">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="933ae-118">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="933ae-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="933ae-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="933ae-120">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="933ae-120">The call timed out.</span></span>|  
|<span data-ttu-id="933ae-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="933ae-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="933ae-122">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="933ae-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="933ae-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="933ae-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="933ae-124">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="933ae-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="933ae-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="933ae-125">E_FAIL</span></span>|<span data-ttu-id="933ae-126">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="933ae-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="933ae-127">Если метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="933ae-127">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="933ae-128">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="933ae-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="933ae-129">Remarks</span><span class="sxs-lookup"><span data-stu-id="933ae-129">Remarks</span></span>  

 <span data-ttu-id="933ae-130">Вызывающий объект может исключить набор известных ссылок на сборки из возвращенного списка.</span><span class="sxs-lookup"><span data-stu-id="933ae-130">The caller can choose to exclude a set of known assembly references from the returned list.</span></span> <span data-ttu-id="933ae-131">Этот набор определяется `pExcludeAssembliesList` параметром.</span><span class="sxs-lookup"><span data-stu-id="933ae-131">This set is defined by the `pExcludeAssembliesList` parameter.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="933ae-132">Требования</span><span class="sxs-lookup"><span data-stu-id="933ae-132">Requirements</span></span>  

 <span data-ttu-id="933ae-133">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="933ae-133">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="933ae-134">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="933ae-134">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="933ae-135">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="933ae-135">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="933ae-136">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="933ae-136">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="933ae-137">См. также</span><span class="sxs-lookup"><span data-stu-id="933ae-137">See also</span></span>

- [<span data-ttu-id="933ae-138">Интерфейс ICLRAssemblyIdentityManager</span><span class="sxs-lookup"><span data-stu-id="933ae-138">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="933ae-139">Интерфейс ICLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="933ae-139">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="933ae-140">Интерфейс ICLRReferenceAssemblyEnum</span><span class="sxs-lookup"><span data-stu-id="933ae-140">ICLRReferenceAssemblyEnum Interface</span></span>](iclrreferenceassemblyenum-interface.md)
