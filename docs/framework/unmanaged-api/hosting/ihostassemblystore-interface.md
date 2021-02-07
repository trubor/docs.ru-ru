---
description: 'Дополнительные сведения о: Интерфейс IHostAssemblyStore'
title: Интерфейс IHostAssemblyStore
ms.date: 03/30/2017
api_name:
- IHostAssemblyStore
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyStore
helpviewer_keywords:
- IHostAssemblyStore interface [.NET Framework hosting]
ms.assetid: cccb650f-abe0-41e2-9fd1-b383788eb1f6
topic_type:
- apiref
ms.openlocfilehash: a05fee7916911687143d5953e26187162a2fa544
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99709039"
---
# <a name="ihostassemblystore-interface"></a><span data-ttu-id="f6ba9-103">Интерфейс IHostAssemblyStore</span><span class="sxs-lookup"><span data-stu-id="f6ba9-103">IHostAssemblyStore Interface</span></span>

<span data-ttu-id="f6ba9-104">Предоставляет методы, позволяющие узлу загружать сборки и модули независимо от общеязыковой среды выполнения (CLR).</span><span class="sxs-lookup"><span data-stu-id="f6ba9-104">Provides methods that allow a host to load assemblies and modules independently of the common language runtime (CLR).</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f6ba9-105">Методы</span><span class="sxs-lookup"><span data-stu-id="f6ba9-105">Methods</span></span>  
  
|<span data-ttu-id="f6ba9-106">Метод</span><span class="sxs-lookup"><span data-stu-id="f6ba9-106">Method</span></span>|<span data-ttu-id="f6ba9-107">Описание</span><span class="sxs-lookup"><span data-stu-id="f6ba9-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f6ba9-108">Метод ProvideAssembly</span><span class="sxs-lookup"><span data-stu-id="f6ba9-108">ProvideAssembly Method</span></span>](ihostassemblystore-provideassembly-method.md)|<span data-ttu-id="f6ba9-109">Возвращает ссылку на сборку, на которую не ссылается [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) , возвращенную из вызова [IHostAssemblyManager:: GetNonHostStoreAssemblies](ihostassemblymanager-getnonhoststoreassemblies-method.md).</span><span class="sxs-lookup"><span data-stu-id="f6ba9-109">Gets a reference to an assembly that is not referenced by the [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) returned from a call to [IHostAssemblyManager::GetNonHostStoreAssemblies](ihostassemblymanager-getnonhoststoreassemblies-method.md).</span></span>|  
|[<span data-ttu-id="f6ba9-110">Метод ProvideModule</span><span class="sxs-lookup"><span data-stu-id="f6ba9-110">ProvideModule Method</span></span>](ihostassemblystore-providemodule-method.md)|<span data-ttu-id="f6ba9-111">Разрешает модуль в сборке или в связанном (не внедренном) файле ресурсов.</span><span class="sxs-lookup"><span data-stu-id="f6ba9-111">Resolves a module within an assembly or a linked (not embedded) resource file.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f6ba9-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="f6ba9-112">Remarks</span></span>  

 <span data-ttu-id="f6ba9-113">`IHostAssemblyStore` Предоставляет узлу способ эффективного загрузки сборок на основе удостоверения сборки.</span><span class="sxs-lookup"><span data-stu-id="f6ba9-113">`IHostAssemblyStore` provides a way for a host to load assemblies efficiently based on assembly identity.</span></span> <span data-ttu-id="f6ba9-114">Узел загружает сборки, возвращая `IStream` экземпляры, которые указывают непосредственно в байтах.</span><span class="sxs-lookup"><span data-stu-id="f6ba9-114">The host loads assemblies by returning `IStream` instances that point directly at the bytes.</span></span>  
  
 <span data-ttu-id="f6ba9-115">Среда CLR определяет, реализован ли узел `IHostAssemblyStore` путем вызова `IHostAssemblyManager::GetNonHostAssemblyStores` после инициализации.</span><span class="sxs-lookup"><span data-stu-id="f6ba9-115">The CLR determines whether a host has implemented `IHostAssemblyStore` by calling `IHostAssemblyManager::GetNonHostAssemblyStores` upon initialization.</span></span> <span data-ttu-id="f6ba9-116">Это позволяет узлу, например, управлять привязкой к пользовательским сборкам, а также использовать среду выполнения для привязки к платформа .NET Framework сборкам.</span><span class="sxs-lookup"><span data-stu-id="f6ba9-116">This allows the host, for example, to control binding to user assemblies, but to rely on the runtime to bind to .NET Framework assemblies.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f6ba9-117">При предоставлении реализации `IHostAssemblyStore` узел определяет его цель для разрешения всех сборок, на которые не ссылается объект, `ICLRAssemblyReferenceList` возвращенный из `IHostAssemblyManager::GetNonHostStoreAssemblies` .</span><span class="sxs-lookup"><span data-stu-id="f6ba9-117">In providing an implementation of `IHostAssemblyStore`, the host specifies its intent to resolve all assemblies that are not referenced by the `ICLRAssemblyReferenceList` returned from `IHostAssemblyManager::GetNonHostStoreAssemblies`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f6ba9-118">Платформа .NET Framework версии 2,0 не позволяет узлу загружать машинный образ сборки, как это предоставляется программой [генератора образов в машинном код (Ngen.exe)](../../tools/ngen-exe-native-image-generator.md) .</span><span class="sxs-lookup"><span data-stu-id="f6ba9-118">The .NET Framework version 2.0 does not provide a way for the host to load the native image of an assembly, as provided by the [Native Image Generator (Ngen.exe)](../../tools/ngen-exe-native-image-generator.md) utility.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6ba9-119">Требования</span><span class="sxs-lookup"><span data-stu-id="f6ba9-119">Requirements</span></span>  

 <span data-ttu-id="f6ba9-120">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f6ba9-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6ba9-121">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f6ba9-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f6ba9-122">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f6ba9-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f6ba9-123">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f6ba9-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6ba9-124">См. также</span><span class="sxs-lookup"><span data-stu-id="f6ba9-124">See also</span></span>

- [<span data-ttu-id="f6ba9-125">Интерфейс ICLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="f6ba9-125">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="f6ba9-126">Интерфейс IHostAssemblyManager</span><span class="sxs-lookup"><span data-stu-id="f6ba9-126">IHostAssemblyManager Interface</span></span>](ihostassemblymanager-interface.md)
- [<span data-ttu-id="f6ba9-127">Интерфейсы размещения</span><span class="sxs-lookup"><span data-stu-id="f6ba9-127">Hosting Interfaces</span></span>](hosting-interfaces.md)
