---
description: 'Дополнительные сведения о методе: ICLRAssemblyIdentityManager:: Жетпробингассемблиесфромреференце'
title: Метод ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager.GetProbingAssembliesFromReference
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference
helpviewer_keywords:
- ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference method [.NET Framework hosting]
- GetProbingAssembliesFromReference method [.NET Framework hosting]
ms.assetid: aec05744-e8d4-44c6-b4a8-e583229ac34e
topic_type:
- apiref
ms.openlocfilehash: 38fcea460537ebed0e54103b460a48c2e58d8173
ms.sourcegitcommit: 10e719780594efc781b15295e499c66f316068b8
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/14/2021
ms.locfileid: "100431429"
---
# <a name="iclrassemblyidentitymanagergetprobingassembliesfromreference-method"></a><span data-ttu-id="0e756-103">Метод ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference</span><span class="sxs-lookup"><span data-stu-id="0e756-103">ICLRAssemblyIdentityManager::GetProbingAssembliesFromReference Method</span></span>

<span data-ttu-id="0e756-104">Возвращает перечислитель [ICLRProbingAssemblyEnum](iclrprobingassemblyenum-interface.md) для удостоверений сборок, на которые ссылается сборка с указанным типом удостоверения.</span><span class="sxs-lookup"><span data-stu-id="0e756-104">Gets an [ICLRProbingAssemblyEnum](iclrprobingassemblyenum-interface.md) enumerator for the assembly identities referenced by the assembly with the specified identity type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0e756-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0e756-105">Syntax</span></span>  
  
```cpp  
HRESULT GetProbingAssembliesFromReference (  
    [in] DWORD   dwMachineType,  
    [in] DWORD   dwFlags,  
    [in] LPCWSTR pwzReferenceIdentity,  
    [out] ICLRProbingAssemblyEnum **ppProbingAssemblyEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0e756-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="0e756-106">Parameters</span></span>  

 `dwMachineType`  
 <span data-ttu-id="0e756-107">окне Допустимое значение, указывающее архитектуру процессора, как определено в WinNT. h.</span><span class="sxs-lookup"><span data-stu-id="0e756-107">[in] A valid value that specifies the processor architecture, as defined in WinNT.h.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="0e756-108">окне Предоставляется для будущего расширения.</span><span class="sxs-lookup"><span data-stu-id="0e756-108">[in] Provided for future extensibility.</span></span> <span data-ttu-id="0e756-109">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT является единственным значением, которое поддерживает Текущая версия среды CLR.</span><span class="sxs-lookup"><span data-stu-id="0e756-109">CLR_ASSEMBLY_IDENTITY_FLAGS_DEFAULT is the only value that the current version of the common language runtime (CLR) supports.</span></span>  
  
 `pwzReferenceIdentity`  
 <span data-ttu-id="0e756-110">окне Идентификатор привязки непрозрачной сборки, обычно возвращаемый из вызова метода [ICLRAssemblyIdentityManager:: GetBindingIdentityFromFile](iclrassemblyidentitymanager-getbindingidentityfromfile-method.md) или [ICLRAssemblyIdentityManager:: жетбиндингидентитифромстреам](iclrassemblyidentitymanager-getbindingidentityfromstream-method.md) .</span><span class="sxs-lookup"><span data-stu-id="0e756-110">[in] An opaque assembly binding identity, typically returned from a call to the [ICLRAssemblyIdentityManager::GetBindingIdentityFromFile](iclrassemblyidentitymanager-getbindingidentityfromfile-method.md) or [ICLRAssemblyIdentityManager::GetBindingIdentityFromStream](iclrassemblyidentitymanager-getbindingidentityfromstream-method.md) method.</span></span>  
  
 `ppProbingAssemblyEnum`  
 <span data-ttu-id="0e756-111">заполняет Указатель интерфейса на `ICLRProbingAssemblyEnum` перечислитель, содержащий ссылки на сборки, на которые ссылается сборка, определенная параметром `pwzReferenceIdentity` .</span><span class="sxs-lookup"><span data-stu-id="0e756-111">[out] An interface pointer to an `ICLRProbingAssemblyEnum` enumerator that contains references to the assemblies referenced by the assembly identified by `pwzReferenceIdentity`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0e756-112">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="0e756-112">Return Value</span></span>  
  
|<span data-ttu-id="0e756-113">HRESULT</span><span class="sxs-lookup"><span data-stu-id="0e756-113">HRESULT</span></span>|<span data-ttu-id="0e756-114">Описание:</span><span class="sxs-lookup"><span data-stu-id="0e756-114">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="0e756-115">S_OK</span><span class="sxs-lookup"><span data-stu-id="0e756-115">S_OK</span></span>|<span data-ttu-id="0e756-116">Метод возвратился успешно.</span><span class="sxs-lookup"><span data-stu-id="0e756-116">The method returned successfully.</span></span>|  
|<span data-ttu-id="0e756-117">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="0e756-117">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="0e756-118">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="0e756-118">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="0e756-119">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="0e756-119">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="0e756-120">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="0e756-120">The call timed out.</span></span>|  
|<span data-ttu-id="0e756-121">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="0e756-121">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="0e756-122">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="0e756-122">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="0e756-123">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="0e756-123">HOST_E_ABANDONED</span></span>|<span data-ttu-id="0e756-124">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="0e756-124">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="0e756-125">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="0e756-125">E_FAIL</span></span>|<span data-ttu-id="0e756-126">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="0e756-126">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="0e756-127">Если метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="0e756-127">If a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="0e756-128">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="0e756-128">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0e756-129">Требования</span><span class="sxs-lookup"><span data-stu-id="0e756-129">Requirements</span></span>  

 <span data-ttu-id="0e756-130">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0e756-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0e756-131">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0e756-131">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0e756-132">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0e756-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0e756-133">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e756-133">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0e756-134">См. также раздел</span><span class="sxs-lookup"><span data-stu-id="0e756-134">See also</span></span>

- [<span data-ttu-id="0e756-135">Интерфейс ICLRAssemblyIdentityManager</span><span class="sxs-lookup"><span data-stu-id="0e756-135">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="0e756-136">Интерфейс ICLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="0e756-136">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="0e756-137">Интерфейс ICLRProbingAssemblyEnum</span><span class="sxs-lookup"><span data-stu-id="0e756-137">ICLRProbingAssemblyEnum Interface</span></span>](iclrprobingassemblyenum-interface.md)
