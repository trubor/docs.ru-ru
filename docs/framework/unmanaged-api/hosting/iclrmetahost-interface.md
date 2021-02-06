---
description: 'Дополнительные сведения о: интерфейс ICLRMetaHost'
title: Интерфейс ICLRMetaHost
ms.date: 03/30/2017
api_name:
- ICLRMetaHost
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMetaHost
helpviewer_keywords:
- ICLRMetaHost interface [.NET Framework hosting]
ms.assetid: c627fcdd-fc4f-4b1c-8e91-df8536f627d8
topic_type:
- apiref
ms.openlocfilehash: 5dc50af85c067bcb525414e47cddd34070b83a27
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637512"
---
# <a name="iclrmetahost-interface"></a><span data-ttu-id="ceee4-103">Интерфейс ICLRMetaHost</span><span class="sxs-lookup"><span data-stu-id="ceee4-103">ICLRMetaHost Interface</span></span>

<span data-ttu-id="ceee4-104">Предоставляет методы, возвращающие определенную версию среды CLR на основе ее номера версии, список всех установленных CLR, список всех сред выполнения, загруженных в указанный процесс, обнаружение версии среды CLR, используемой для компиляции сборки, выхода из процесса с чистым завершением работы среды выполнения и запроса привязки API прежних версий.</span><span class="sxs-lookup"><span data-stu-id="ceee4-104">Provides methods that return a specific version of the common language runtime (CLR) based on its version number, list all installed CLRs, list all runtimes that are loaded in a specified process, discover the CLR version used to compile an assembly, exit a process with a clean runtime shutdown, and query legacy API binding.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ceee4-105">Методы</span><span class="sxs-lookup"><span data-stu-id="ceee4-105">Methods</span></span>  
  
|<span data-ttu-id="ceee4-106">Метод</span><span class="sxs-lookup"><span data-stu-id="ceee4-106">Method</span></span>|<span data-ttu-id="ceee4-107">Описание</span><span class="sxs-lookup"><span data-stu-id="ceee4-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ceee4-108">Метод EnumerateInstalledRuntimes</span><span class="sxs-lookup"><span data-stu-id="ceee4-108">EnumerateInstalledRuntimes Method</span></span>](iclrmetahost-enumerateinstalledruntimes-method.md)|<span data-ttu-id="ceee4-109">Возвращает перечисление, содержащее допустимый указатель интерфейса [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) для каждой версии среды CLR, установленной на компьютере.</span><span class="sxs-lookup"><span data-stu-id="ceee4-109">Returns an enumeration that contains a valid [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface pointer for each CLR version that is installed on a computer.</span></span>|  
|[<span data-ttu-id="ceee4-110">Метод EnumerateLoadedRuntimes</span><span class="sxs-lookup"><span data-stu-id="ceee4-110">EnumerateLoadedRuntimes Method</span></span>](iclrmetahost-enumerateloadedruntimes-method.md)|<span data-ttu-id="ceee4-111">Возвращает перечисление, содержащее допустимый указатель интерфейса [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) для каждой среды CLR, загруженной в заданный процесс.</span><span class="sxs-lookup"><span data-stu-id="ceee4-111">Returns an enumeration that contains a valid [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface pointer for each CLR that is loaded in a given process.</span></span> <span data-ttu-id="ceee4-112">Этот метод заменяет [GetVersionFromProcess](getversionfromprocess-function.md).</span><span class="sxs-lookup"><span data-stu-id="ceee4-112">This method supersedes [GetVersionFromProcess](getversionfromprocess-function.md).</span></span>|  
|[<span data-ttu-id="ceee4-113">Метод ExitProcess</span><span class="sxs-lookup"><span data-stu-id="ceee4-113">ExitProcess Method</span></span>](iclrmetahost-exitprocess-method.md)|<span data-ttu-id="ceee4-114">Пытается корректно завершить работу всех загруженных сред выполнения, а затем завершить процесс.</span><span class="sxs-lookup"><span data-stu-id="ceee4-114">Attempts to shut down all loaded runtimes gracefully and then terminates the process.</span></span> <span data-ttu-id="ceee4-115">Заменяет функцию [корекситпроцесс](corexitprocess-function.md) .</span><span class="sxs-lookup"><span data-stu-id="ceee4-115">Supersedes the [CorExitProcess](corexitprocess-function.md) function.</span></span>|  
|[<span data-ttu-id="ceee4-116">Метод GetRuntime</span><span class="sxs-lookup"><span data-stu-id="ceee4-116">GetRuntime Method</span></span>](iclrmetahost-getruntime-method.md)|<span data-ttu-id="ceee4-117">Возвращает интерфейс [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) , соответствующий определенной версии среды CLR.</span><span class="sxs-lookup"><span data-stu-id="ceee4-117">Gets the [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) interface that corresponds to a particular CLR version.</span></span> <span data-ttu-id="ceee4-118">Этот метод заменяет функцию [CorBindToRuntimeEx](corbindtoruntimeex-function.md) , используемую с флагом [STARTUP_LOADER_SAFEMODE](startup-flags-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="ceee4-118">This method supersedes the [CorBindToRuntimeEx](corbindtoruntimeex-function.md) function used with the [STARTUP_LOADER_SAFEMODE](startup-flags-enumeration.md) flag.</span></span>|  
|[<span data-ttu-id="ceee4-119">Метод GetVersionFromFile</span><span class="sxs-lookup"><span data-stu-id="ceee4-119">GetVersionFromFile Method</span></span>](iclrmetahost-getversionfromfile-method.md)|<span data-ttu-id="ceee4-120">Возвращает исходную версию компиляции платформа .NET Framework сборки (хранится в метаданных) по указанному пути к файлу.</span><span class="sxs-lookup"><span data-stu-id="ceee4-120">Gets the assembly's original .NET Framework compilation version (stored in the metadata), given its file path.</span></span> <span data-ttu-id="ceee4-121">Этот метод заменяет [жетфилеверсион](getfileversion-function.md).</span><span class="sxs-lookup"><span data-stu-id="ceee4-121">This method supersedes [GetFileVersion](getfileversion-function.md).</span></span>|  
|[<span data-ttu-id="ceee4-122">Метод QueryLegacyV2RuntimeBinding</span><span class="sxs-lookup"><span data-stu-id="ceee4-122">QueryLegacyV2RuntimeBinding Method</span></span>](iclrmetahost-querylegacyv2runtimebinding-method.md)|<span data-ttu-id="ceee4-123">Возвращает интерфейс, представляющий среду выполнения, к которой привязана политика устаревшей активации, например, с помощью `useLegacyV2RuntimeActivationPolicy` атрибута в записи файла конфигурации [ \<startup> элемента](../../configure-apps/file-schema/startup/startup-element.md) , путем непосредственного использования устаревших API-интерфейсов активации или путем вызова метода [ICLRRuntimeInfo:: BindAsLegacyV2Runtime](iclrruntimeinfo-bindaslegacyv2runtime-method.md) .</span><span class="sxs-lookup"><span data-stu-id="ceee4-123">Returns an interface that represents a runtime to which legacy activation policy has been bound, for example by using the `useLegacyV2RuntimeActivationPolicy` attribute on the [\<startup> Element](../../configure-apps/file-schema/startup/startup-element.md) configuration file entry, by direct use of the legacy activation APIs, or by calling the [ICLRRuntimeInfo::BindAsLegacyV2Runtime](iclrruntimeinfo-bindaslegacyv2runtime-method.md) method.</span></span>|  
|[<span data-ttu-id="ceee4-124">Метод RequestRuntimeLoadedNotification</span><span class="sxs-lookup"><span data-stu-id="ceee4-124">RequestRuntimeLoadedNotification Method</span></span>](iclrmetahost-requestruntimeloadednotification-method.md)|<span data-ttu-id="ceee4-125">Гарантирует обратный вызов к указанному указателю функции при первой загрузке версии среды CLR, но еще не запущенной.</span><span class="sxs-lookup"><span data-stu-id="ceee4-125">Guarantees a callback to the specified function pointer when a CLR version is first loaded, but not yet started.</span></span> <span data-ttu-id="ceee4-126">Этот метод заменяет [локкклрверсион](lockclrversion-function.md)</span><span class="sxs-lookup"><span data-stu-id="ceee4-126">This method supersedes [LockClrVersion](lockclrversion-function.md)</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ceee4-127">Remarks</span><span class="sxs-lookup"><span data-stu-id="ceee4-127">Remarks</span></span>  

 <span data-ttu-id="ceee4-128">Единственный способ получить экземпляр этого интерфейса — вызвать функцию [клркреатеинстанце](clrcreateinstance-function.md) следующим образом:</span><span class="sxs-lookup"><span data-stu-id="ceee4-128">The only way to get an instance of this interface is by calling the [CLRCreateInstance](clrcreateinstance-function.md) function as follows:</span></span>  
  
```cpp  
ICLRMetaHost *pMetaHost = NULL;  
HRESULT hr = CLRCreateInstance(CLSID_CLRMetaHost,  
                   IID_ICLRMetaHost, (LPVOID*)&pMetaHost);  
```  
  
## <a name="requirements"></a><span data-ttu-id="ceee4-129">Требования</span><span class="sxs-lookup"><span data-stu-id="ceee4-129">Requirements</span></span>  

 <span data-ttu-id="ceee4-130">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ceee4-130">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ceee4-131">**Заголовок:** Метахост. h</span><span class="sxs-lookup"><span data-stu-id="ceee4-131">**Header:** MetaHost.h</span></span>  
  
 <span data-ttu-id="ceee4-132">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ceee4-132">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ceee4-133">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ceee4-133">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ceee4-134">См. также</span><span class="sxs-lookup"><span data-stu-id="ceee4-134">See also</span></span>

- [<span data-ttu-id="ceee4-135">Интерфейсы размещения</span><span class="sxs-lookup"><span data-stu-id="ceee4-135">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="ceee4-136">Размещение</span><span class="sxs-lookup"><span data-stu-id="ceee4-136">Hosting</span></span>](index.md)
