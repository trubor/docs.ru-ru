---
description: 'Дополнительные сведения о: структура Ассемблибиндинфо'
title: Структура AssemblyBindInfo
ms.date: 03/30/2017
api_name:
- AssemblyBindInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- AssemblyBindInfo
helpviewer_keywords:
- AssemblyBindInfo structure [.NET Framework hosting]
ms.assetid: 6fc01e98-c2e7-49de-ab9f-95937cc89017
topic_type:
- apiref
ms.openlocfilehash: 3e11e05924ee6818737f84d9ca92394ee5313292
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799984"
---
# <a name="assemblybindinfo-structure"></a><span data-ttu-id="26f81-103">Структура AssemblyBindInfo</span><span class="sxs-lookup"><span data-stu-id="26f81-103">AssemblyBindInfo Structure</span></span>

<span data-ttu-id="26f81-104">Предоставляет подробные сведения о сборке, на которую указывает ссылка.</span><span class="sxs-lookup"><span data-stu-id="26f81-104">Provides detailed information about the referenced assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26f81-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="26f81-105">Syntax</span></span>  
  
```cpp  
typedef struct _AssemblyBindInfo {  
    DWORD       dwAppDomainId;  
    LPCWSTR     lpReferencedIdentity;  
    LPCWSTR     lpPostPolicyIdentity;  
    DWORD       ePolicyLevel;  
} AssemblyBindInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="26f81-106">Члены</span><span class="sxs-lookup"><span data-stu-id="26f81-106">Members</span></span>  
  
|<span data-ttu-id="26f81-107">Член</span><span class="sxs-lookup"><span data-stu-id="26f81-107">Member</span></span>|<span data-ttu-id="26f81-108">Описание</span><span class="sxs-lookup"><span data-stu-id="26f81-108">Description</span></span>|  
|------------|-----------------|  
|`dwAppDomainId`|<span data-ttu-id="26f81-109">Уникальный идентификатор для, `IStream` возвращаемого вызовом метода [IHostAssemblyStore::P ровидеассембли](ihostassemblystore-provideassembly-method.md), из которого загружается сборка, на которую указывает ссылка.</span><span class="sxs-lookup"><span data-stu-id="26f81-109">A unique identifier for the `IStream` returned by a call to [IHostAssemblyStore::ProvideAssembly](ihostassemblystore-provideassembly-method.md), from which the referenced assembly is to be loaded.</span></span>|  
|`lpReferencedIdentity`|<span data-ttu-id="26f81-110">Уникальный идентификатор сборки, на которую указывает ссылка.</span><span class="sxs-lookup"><span data-stu-id="26f81-110">A unique identifier for the referenced assembly.</span></span>|  
|`lpPostPolicyIdentity`|<span data-ttu-id="26f81-111">Идентификатор сборки, на которую указывает ссылка, после применения любых значений политики привязки.</span><span class="sxs-lookup"><span data-stu-id="26f81-111">The identifier for the referenced assembly after the application of any binding policy values.</span></span>|  
|`ePolicyLevel`|<span data-ttu-id="26f81-112">Одно из значений [еполициактион](epolicyaction-enumeration.md) , указывающее, какие политики управления версиями должны применяться к сборке, на которую указывает ссылка.</span><span class="sxs-lookup"><span data-stu-id="26f81-112">One of the [EPolicyAction](epolicyaction-enumeration.md) values that indicate which versioning policies, if any, should be applied to the referenced assembly.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="26f81-113">Remarks</span><span class="sxs-lookup"><span data-stu-id="26f81-113">Remarks</span></span>  

 <span data-ttu-id="26f81-114">Узел предоставляет уникальный идентификатор среде CLR `dwAppDomainId` .</span><span class="sxs-lookup"><span data-stu-id="26f81-114">The host supplies the unique identifier `dwAppDomainId` to the common language runtime (CLR).</span></span> <span data-ttu-id="26f81-115">После `IHostAssemblyStore::ProvideAssembly` возврата вызова среда выполнения использует идентификатор, чтобы определить, `IStream` сопоставлено ли содержимое объекта.</span><span class="sxs-lookup"><span data-stu-id="26f81-115">After a call to `IHostAssemblyStore::ProvideAssembly` returns, the runtime uses the identifier to determine whether the contents of the `IStream` have been mapped.</span></span> <span data-ttu-id="26f81-116">Если это так, среда выполнения загружает существующую копию вместо повторного сопоставления потока.</span><span class="sxs-lookup"><span data-stu-id="26f81-116">If so, the runtime loads the existing copy rather than remapping the stream.</span></span> <span data-ttu-id="26f81-117">Среда выполнения также использует этот идентификатор в качестве ключа поиска для потоков, возвращаемых из вызовов [IHostAssemblyStore::P ровидемодуле](ihostassemblystore-providemodule-method.md).</span><span class="sxs-lookup"><span data-stu-id="26f81-117">The runtime also uses this identifier as a lookup key for streams returned from calls to [IHostAssemblyStore::ProvideModule](ihostassemblystore-providemodule-method.md).</span></span> <span data-ttu-id="26f81-118">Таким образом, идентификатор должен быть уникальным для запросов модуля и для запросов сборки.</span><span class="sxs-lookup"><span data-stu-id="26f81-118">Therefore, the identifier must be unique for module requests and for assembly requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26f81-119">Требования</span><span class="sxs-lookup"><span data-stu-id="26f81-119">Requirements</span></span>  

 <span data-ttu-id="26f81-120">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="26f81-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26f81-121">**Заголовок:** MSCorEE. idl</span><span class="sxs-lookup"><span data-stu-id="26f81-121">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="26f81-122">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="26f81-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="26f81-123">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26f81-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26f81-124">См. также</span><span class="sxs-lookup"><span data-stu-id="26f81-124">See also</span></span>

- [<span data-ttu-id="26f81-125">Структуры размещения</span><span class="sxs-lookup"><span data-stu-id="26f81-125">Hosting Structures</span></span>](hosting-structures.md)
- [<span data-ttu-id="26f81-126">Интерфейс ICLRAssemblyIdentityManager</span><span class="sxs-lookup"><span data-stu-id="26f81-126">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="26f81-127">Интерфейс ICLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="26f81-127">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="26f81-128">Интерфейс IHostAssemblyManager</span><span class="sxs-lookup"><span data-stu-id="26f81-128">IHostAssemblyManager Interface</span></span>](ihostassemblymanager-interface.md)
- [<span data-ttu-id="26f81-129">Интерфейс IHostAssemblyStore</span><span class="sxs-lookup"><span data-stu-id="26f81-129">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)
- [<span data-ttu-id="26f81-130">Структура ModuleBindInfo</span><span class="sxs-lookup"><span data-stu-id="26f81-130">ModuleBindInfo Structure</span></span>](modulebindinfo-structure.md)
