---
description: 'Дополнительные сведения о методе: IHostAssemblyStore::P Ровидемодуле'
title: Метод IHostAssemblyStore::ProvideModule
ms.date: 03/30/2017
api_name:
- IHostAssemblyStore.ProvideModule
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyStore::ProvideModule
helpviewer_keywords:
- IHostAssemblyStore::ProvideModule method [.NET Framework hosting]
- ProvideModule method [.NET Framework hosting]
ms.assetid: f42e3dd0-c88e-4748-b6c0-4c515a633180
topic_type:
- apiref
ms.openlocfilehash: 9e783b9f8db303d095995507689d7567225a51fd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99709031"
---
# <a name="ihostassemblystoreprovidemodule-method"></a><span data-ttu-id="1c9f7-103">Метод IHostAssemblyStore::ProvideModule</span><span class="sxs-lookup"><span data-stu-id="1c9f7-103">IHostAssemblyStore::ProvideModule Method</span></span>

<span data-ttu-id="1c9f7-104">Разрешает модуль в сборке или связанном (но не внедренном) файле ресурсов.</span><span class="sxs-lookup"><span data-stu-id="1c9f7-104">Resolves a module within an assembly or a linked (but not an embedded) resource file.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c9f7-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="1c9f7-105">Syntax</span></span>  
  
```cpp  
HRESULT ProvideModule (  
    [in]  ModuleBindInfo *pBindInfo,  
    [out] DWORD          *pdwModuleId,  
    [out] IStream        **ppStmModuleImage,  
    [out] IStream        **ppStmPDB  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1c9f7-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="1c9f7-106">Parameters</span></span>  

 `pBindInfo`  
 <span data-ttu-id="1c9f7-107">окне Указатель на экземпляр [модулебиндинфо](modulebindinfo-structure.md) , который описывает имя запрашиваемого модуля <xref:System.AppDomain> , сборки и имени модуля.</span><span class="sxs-lookup"><span data-stu-id="1c9f7-107">[in] A pointer to a [ModuleBindInfo](modulebindinfo-structure.md) instance that describes the requested module's <xref:System.AppDomain>, assembly, and module name.</span></span>  
  
 `pdwModuleId`  
 <span data-ttu-id="1c9f7-108">заполняет Указатель на уникальный идентификатор для `IStream` содержащего загруженного модуля.</span><span class="sxs-lookup"><span data-stu-id="1c9f7-108">[out] A pointer to a unique identifier for the `IStream` containing the loaded module.</span></span>  
  
 `ppStmModuleImage`  
 <span data-ttu-id="1c9f7-109">заполняет Указатель на адрес `IStream` объекта, который содержит загружаемый переносимый исполняемый файл (PE), или значение null, если не удалось найти модуль.</span><span class="sxs-lookup"><span data-stu-id="1c9f7-109">[out] A pointer to the address of an `IStream` object, which contains the portable executable (PE) image to be loaded, or null if the module could not be found.</span></span>  
  
 `ppStmPDB`  
 <span data-ttu-id="1c9f7-110">заполняет Указатель на адрес `IStream` объекта, который содержит сведения об отладке программы (PDB) для запрошенного модуля, или значение null, если PDB-файл найти не удалось.</span><span class="sxs-lookup"><span data-stu-id="1c9f7-110">[out] A pointer to the address of an `IStream` object, which contains the program debug (PDB) information for the requested module, or null if the .pdb file could not be found.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1c9f7-111">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="1c9f7-111">Return Value</span></span>  
  
|<span data-ttu-id="1c9f7-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="1c9f7-112">HRESULT</span></span>|<span data-ttu-id="1c9f7-113">Описание:</span><span class="sxs-lookup"><span data-stu-id="1c9f7-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="1c9f7-114">S_OK</span><span class="sxs-lookup"><span data-stu-id="1c9f7-114">S_OK</span></span>|<span data-ttu-id="1c9f7-115">`ProvideModule` успешно возвращено.</span><span class="sxs-lookup"><span data-stu-id="1c9f7-115">`ProvideModule` returned successfully.</span></span>|  
|<span data-ttu-id="1c9f7-116">HOST_E_CLRNOTAVAILABLE</span><span class="sxs-lookup"><span data-stu-id="1c9f7-116">HOST_E_CLRNOTAVAILABLE</span></span>|<span data-ttu-id="1c9f7-117">Среда CLR не была загружена в процесс, или среда CLR находится в состоянии, в котором она не может выполнить управляемый код или успешно обработать вызов.</span><span class="sxs-lookup"><span data-stu-id="1c9f7-117">The common language runtime (CLR) has not been loaded into a process, or the CLR is in a state in which it cannot run managed code or process the call successfully.</span></span>|  
|<span data-ttu-id="1c9f7-118">HOST_E_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="1c9f7-118">HOST_E_TIMEOUT</span></span>|<span data-ttu-id="1c9f7-119">Время ожидания вызова истекло.</span><span class="sxs-lookup"><span data-stu-id="1c9f7-119">The call timed out.</span></span>|  
|<span data-ttu-id="1c9f7-120">HOST_E_NOT_OWNER</span><span class="sxs-lookup"><span data-stu-id="1c9f7-120">HOST_E_NOT_OWNER</span></span>|<span data-ttu-id="1c9f7-121">Вызывающий объект не владеет блокировкой.</span><span class="sxs-lookup"><span data-stu-id="1c9f7-121">The caller does not own the lock.</span></span>|  
|<span data-ttu-id="1c9f7-122">HOST_E_ABANDONED</span><span class="sxs-lookup"><span data-stu-id="1c9f7-122">HOST_E_ABANDONED</span></span>|<span data-ttu-id="1c9f7-123">Событие было отменено, пока заблокированный поток или волокно ожидают его.</span><span class="sxs-lookup"><span data-stu-id="1c9f7-123">An event was canceled while a blocked thread or fiber was waiting on it.</span></span>|  
|<span data-ttu-id="1c9f7-124">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="1c9f7-124">E_FAIL</span></span>|<span data-ttu-id="1c9f7-125">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="1c9f7-125">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="1c9f7-126">Когда метод возвращает E_FAIL, среда CLR больше не может использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="1c9f7-126">When a method returns E_FAIL, the CLR is no longer usable within the process.</span></span> <span data-ttu-id="1c9f7-127">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="1c9f7-127">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
|<span data-ttu-id="1c9f7-128">COR_E_FILENOTFOUND (0x80070002)</span><span class="sxs-lookup"><span data-stu-id="1c9f7-128">COR_E_FILENOTFOUND (0x80070002)</span></span>|<span data-ttu-id="1c9f7-129">Не удалось найти запрошенную сборку или связанный ресурс.</span><span class="sxs-lookup"><span data-stu-id="1c9f7-129">The requested assembly or linked resource could not be located.</span></span>|  
|<span data-ttu-id="1c9f7-130">E_NOT_SUFFICIENT_BUFFER</span><span class="sxs-lookup"><span data-stu-id="1c9f7-130">E_NOT_SUFFICIENT_BUFFER</span></span>|<span data-ttu-id="1c9f7-131">`pdwModuleId` недостаточно велик, чтобы вместить идентификатор, который требуется вернуть узлу.</span><span class="sxs-lookup"><span data-stu-id="1c9f7-131">`pdwModuleId` is not large enough to contain the identifier that the host wants to return.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1c9f7-132">Remarks</span><span class="sxs-lookup"><span data-stu-id="1c9f7-132">Remarks</span></span>  

 <span data-ttu-id="1c9f7-133">Значение идентификатора, возвращенное для `pdwModuleId` , задается узлом.</span><span class="sxs-lookup"><span data-stu-id="1c9f7-133">The identity value returned for `pdwModuleId` is specified by the host.</span></span> <span data-ttu-id="1c9f7-134">Идентификаторы должны быть уникальными в течение всего времени существования процесса.</span><span class="sxs-lookup"><span data-stu-id="1c9f7-134">Identifiers must be unique within the lifetime of a process.</span></span> <span data-ttu-id="1c9f7-135">Среда CLR использует это значение в качестве уникального идентификатора для связанного потока.</span><span class="sxs-lookup"><span data-stu-id="1c9f7-135">The CLR uses this value as the unique identifier for the associated stream.</span></span> <span data-ttu-id="1c9f7-136">Он проверяет каждое значение по значениям `pAssemblyId` , возвращаемым вызовами [провидеассембли](ihostassemblystore-provideassembly-method.md) , и значениями, `pdwModuleId` возвращаемыми другими вызовами метода `ProvideModule` .</span><span class="sxs-lookup"><span data-stu-id="1c9f7-136">It checks each value against the values for `pAssemblyId` returned by calls to [ProvideAssembly](ihostassemblystore-provideassembly-method.md) and against the values for `pdwModuleId` returned by other calls to `ProvideModule`.</span></span> <span data-ttu-id="1c9f7-137">Если узел возвращает одно и то же значение идентификатора для другого `IStream` , среда CLR проверяет, было ли уже сопоставлено содержимое этого потока.</span><span class="sxs-lookup"><span data-stu-id="1c9f7-137">If the host returns the same identifier value for another `IStream`, the CLR checks whether the contents of that stream have already been mapped.</span></span> <span data-ttu-id="1c9f7-138">Если это так, среда CLR загружает существующую копию изображения вместо сопоставления нового.</span><span class="sxs-lookup"><span data-stu-id="1c9f7-138">If so, the CLR loads the existing copy of the image instead of mapping a new one.</span></span> <span data-ttu-id="1c9f7-139">Таким образом, идентификатор также не должен перекрываться с идентификаторами сборок, возвращенными из `ProvideAssembly` .</span><span class="sxs-lookup"><span data-stu-id="1c9f7-139">Therefore, the identifier must also not overlap with the assembly identifiers returned from `ProvideAssembly`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c9f7-140">Требования</span><span class="sxs-lookup"><span data-stu-id="1c9f7-140">Requirements</span></span>  

 <span data-ttu-id="1c9f7-141">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1c9f7-141">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c9f7-142">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="1c9f7-142">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1c9f7-143">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="1c9f7-143">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1c9f7-144">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c9f7-144">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c9f7-145">См. также</span><span class="sxs-lookup"><span data-stu-id="1c9f7-145">See also</span></span>

- [<span data-ttu-id="1c9f7-146">Интерфейс ICLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="1c9f7-146">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="1c9f7-147">Интерфейс IHostAssemblyManager</span><span class="sxs-lookup"><span data-stu-id="1c9f7-147">IHostAssemblyManager Interface</span></span>](ihostassemblymanager-interface.md)
- [<span data-ttu-id="1c9f7-148">Интерфейс IHostAssemblyStore</span><span class="sxs-lookup"><span data-stu-id="1c9f7-148">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)
