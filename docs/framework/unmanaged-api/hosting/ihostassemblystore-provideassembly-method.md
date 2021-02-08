---
description: 'Дополнительные сведения о методе: IHostAssemblyStore::P Ровидеассембли'
title: Метод IHostAssemblyStore::ProvideAssembly
ms.date: 03/30/2017
api_name:
- IHostAssemblyStore.ProvideAssembly
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyStore::ProvideAssembly
helpviewer_keywords:
- ProvideAssembly method [.NET Framework hosting]
- IHostAssemblyStore::ProvideAssembly method [.NET Framework hosting]
ms.assetid: 625c3dd5-a3f0-442c-adde-310dadbb5054
topic_type:
- apiref
ms.openlocfilehash: f8917cb28dd3898343a7b6ee08bd54096df8cfa7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99789506"
---
# <a name="ihostassemblystoreprovideassembly-method"></a><span data-ttu-id="4247f-103">Метод IHostAssemblyStore::ProvideAssembly</span><span class="sxs-lookup"><span data-stu-id="4247f-103">IHostAssemblyStore::ProvideAssembly Method</span></span>

<span data-ttu-id="4247f-104">Возвращает ссылку на сборку, на которую не ссылается [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) , возвращаемую из [IHostAssemblyManager:: GetNonHostStoreAssemblies](ihostassemblymanager-getnonhoststoreassemblies-method.md).</span><span class="sxs-lookup"><span data-stu-id="4247f-104">Gets a reference to an assembly that is not referenced by the [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) that is returned from [IHostAssemblyManager::GetNonHostStoreAssemblies](ihostassemblymanager-getnonhoststoreassemblies-method.md).</span></span> <span data-ttu-id="4247f-105">Среда CLR вызывает `ProvideAssembly` для каждой сборки, которая не отображается в списке.</span><span class="sxs-lookup"><span data-stu-id="4247f-105">The common language runtime (CLR) calls `ProvideAssembly` for each assembly that does not appear in the list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4247f-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="4247f-106">Syntax</span></span>  
  
```cpp  
HRESULT ProvideAssembly (  
    [in]  AssemblyBindInfo *pBindInfo,  
    [out] UINT64           *pAssemblyId,  
    [out] UINT64           *pHostContext,  
    [out] IStream          **ppStmAssemblyImage,  
    [out] IStream          **ppStmPDB  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4247f-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="4247f-107">Parameters</span></span>  

 `pBindInfo`  
 <span data-ttu-id="4247f-108">окне Указатель на экземпляр [ассемблибиндинфо](assemblybindinfo-structure.md) , используемый узлом для определения определенных характеристик привязки, включая присутствие или отсутствие политики управления версиями, а также сборку, к которой необходимо выполнить привязку.</span><span class="sxs-lookup"><span data-stu-id="4247f-108">[in] A pointer to an [AssemblyBindInfo](assemblybindinfo-structure.md) instance that the host uses to determine certain bind characteristics, including the presence or absence of any versioning policy, and which assembly to bind to.</span></span>  
  
 `pAssemblyId`  
 <span data-ttu-id="4247f-109">заполняет Указатель на уникальный идентификатор для запрошенной сборки для этого `IStream` .</span><span class="sxs-lookup"><span data-stu-id="4247f-109">[out] A pointer to a unique identifier for the requested assembly for this `IStream`.</span></span>  
  
 `pHostContext`  
 <span data-ttu-id="4247f-110">заполняет Указатель на данные конкретного узла, который используется для определения свидетельства запрошенной сборки без вызова неуправляемого кода.</span><span class="sxs-lookup"><span data-stu-id="4247f-110">[out] A pointer to host-specific data that is used to determine the evidence of the requested assembly without the need of a platform invoke call.</span></span> <span data-ttu-id="4247f-111">`pHostContext` соответствует <xref:System.Reflection.Assembly.HostContext%2A> свойству управляемого <xref:System.Reflection.Assembly> класса.</span><span class="sxs-lookup"><span data-stu-id="4247f-111">`pHostContext` corresponds to the <xref:System.Reflection.Assembly.HostContext%2A> property of the managed <xref:System.Reflection.Assembly> class.</span></span>  
  
 `ppStmAssemblyImage`  
 <span data-ttu-id="4247f-112">заполняет Указатель на адрес объекта `IStream` , который содержит загружаемый переносимый исполняемый файл (PE), или значение null, если сборку найти не удалось.</span><span class="sxs-lookup"><span data-stu-id="4247f-112">[out] A pointer to the address of an `IStream` that contains the portable executable (PE) image to be loaded, or null if the assembly could not be found.</span></span>  
  
 `ppStmPDB`  
 <span data-ttu-id="4247f-113">заполняет Указатель на адрес `IStream` , содержащий сведения об отладке программы (PDB), или значение null, если PDB-файл не найден.</span><span class="sxs-lookup"><span data-stu-id="4247f-113">[out] A pointer to the address of an `IStream` that contains the program debug (PDB) information, or null if the .pdb file could not be found.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4247f-114">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="4247f-114">Return Value</span></span>  
  
|<span data-ttu-id="4247f-115">HRESULT</span><span class="sxs-lookup"><span data-stu-id="4247f-115">HRESULT</span></span>|<span data-ttu-id="4247f-116">Описание:</span><span class="sxs-lookup"><span data-stu-id="4247f-116">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="4247f-117">S_OK</span><span class="sxs-lookup"><span data-stu-id="4247f-117">S_OK</span></span>|<span data-ttu-id="4247f-118">`ProvideAssembly` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="4247f-118">`ProvideAssembly` returned successfully.</span></span>|  
|<span data-ttu-id="4247f-119">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="4247f-119">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="4247f-120">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="4247f-120">The CLR has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="4247f-121">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="4247f-121">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="4247f-122">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="4247f-122">The call timed out.</span></span>|  
|<span data-ttu-id="4247f-123">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="4247f-123">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="4247f-124">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="4247f-124">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="4247f-125">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="4247f-125">HOST_E_ABANDONED</span></span>|<span data-ttu-id="4247f-126">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="4247f-126">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="4247f-127">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="4247f-127">E_FAIL</span></span>|<span data-ttu-id="4247f-128">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="4247f-128">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="4247f-129">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="4247f-129">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="4247f-130">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="4247f-130">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="4247f-131">COR_E_FILENOTFOUND (0x80070002)</span><span class="sxs-lookup"><span data-stu-id="4247f-131">COR_E_FILENOTFOUND (0x80070002)</span></span>|<span data-ttu-id="4247f-132">Не удалось найти запрошенную сборку.</span><span class="sxs-lookup"><span data-stu-id="4247f-132">The requested assembly could not be located.</span></span>|  
|<span data-ttu-id="4247f-133">E_NOT_SUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="4247f-133">E_NOT_SUFFICIENT_BUFFER</span></span>|<span data-ttu-id="4247f-134">Размер буфера, указанный в, `pAssemblyId` недостаточно велик для хранения идентификатора, который требуется вернуть узлу.</span><span class="sxs-lookup"><span data-stu-id="4247f-134">The buffer size specified by `pAssemblyId` is not large enough to hold the identifier that the host wants to return.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4247f-135">Remarks</span><span class="sxs-lookup"><span data-stu-id="4247f-135">Remarks</span></span>  

 <span data-ttu-id="4247f-136">Значение идентификатора, возвращенное для `pAssemblyId` , задается узлом.</span><span class="sxs-lookup"><span data-stu-id="4247f-136">The identity value returned for `pAssemblyId` is specified by the host.</span></span> <span data-ttu-id="4247f-137">Идентификаторы должны быть уникальными в течение всего времени существования процесса.</span><span class="sxs-lookup"><span data-stu-id="4247f-137">Identifiers must be unique within the lifetime of a process.</span></span> <span data-ttu-id="4247f-138">Среда CLR использует это значение в качестве уникального идентификатора потока.</span><span class="sxs-lookup"><span data-stu-id="4247f-138">The CLR uses this value as a unique identifier for the stream.</span></span> <span data-ttu-id="4247f-139">Он проверяет каждое значение по значениям `pAssemblyId` , возвращаемым другими вызовами метода `ProvideAssembly` .</span><span class="sxs-lookup"><span data-stu-id="4247f-139">It checks each value against the values for `pAssemblyId` returned by other calls to `ProvideAssembly`.</span></span> <span data-ttu-id="4247f-140">Если узел возвращает одно и то же `pAssemblyId` значение для другого `IStream` , среда CLR проверяет, было ли уже сопоставлено содержимое этого потока.</span><span class="sxs-lookup"><span data-stu-id="4247f-140">If the host returns the same `pAssemblyId` value for another `IStream`, the CLR checks whether the contents of that stream have already been mapped.</span></span> <span data-ttu-id="4247f-141">Если это так, среда выполнения загружает существующую копию изображения вместо сопоставления нового.</span><span class="sxs-lookup"><span data-stu-id="4247f-141">If so, the runtime loads the existing copy of the image instead of mapping a new one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4247f-142">Требования</span><span class="sxs-lookup"><span data-stu-id="4247f-142">Requirements</span></span>  

 <span data-ttu-id="4247f-143">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4247f-143">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4247f-144">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="4247f-144">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4247f-145">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="4247f-145">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4247f-146">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4247f-146">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4247f-147">См. также</span><span class="sxs-lookup"><span data-stu-id="4247f-147">See also</span></span>

- [<span data-ttu-id="4247f-148">Интерфейс ICLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="4247f-148">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="4247f-149">Интерфейс IHostAssemblyManager</span><span class="sxs-lookup"><span data-stu-id="4247f-149">IHostAssemblyManager Interface</span></span>](ihostassemblymanager-interface.md)
- [<span data-ttu-id="4247f-150">Интерфейс IHostAssemblyStore</span><span class="sxs-lookup"><span data-stu-id="4247f-150">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)
