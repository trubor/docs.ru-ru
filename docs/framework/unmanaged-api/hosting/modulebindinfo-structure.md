---
description: 'Дополнительные сведения о: структура Модулебиндинфо'
title: Структура ModuleBindInfo
ms.date: 03/30/2017
api_name:
- ModuleBindInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ModuleBindInfo
helpviewer_keywords:
- ModuleBindInfo structure [.NET Framework hosting]
ms.assetid: 632d4adc-dbc9-4ce8-9397-abc3285c1c69
topic_type:
- apiref
ms.openlocfilehash: 0969c0ecc459414336800e8e7da5817ac0c1a8ce
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99679632"
---
# <a name="modulebindinfo-structure"></a><span data-ttu-id="fc188-103">Структура ModuleBindInfo</span><span class="sxs-lookup"><span data-stu-id="fc188-103">ModuleBindInfo Structure</span></span>

<span data-ttu-id="fc188-104">Предоставляет подробные сведения о модуле, на который указывает ссылка, и содержащей его сборку.</span><span class="sxs-lookup"><span data-stu-id="fc188-104">Provides detailed information about the referenced module and the assembly that contains it.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc188-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="fc188-105">Syntax</span></span>  
  
```cpp  
typedef struct _ModuleBindInfo {  
    DWORD    dwAppDomainId;  
    LPCWSTR  lpAssemblyIdentity;  
    LPCWSTR  lpModuleName  
} ModuleBindInfo;  
```  
  
## <a name="members"></a><span data-ttu-id="fc188-106">Члены</span><span class="sxs-lookup"><span data-stu-id="fc188-106">Members</span></span>  
  
|<span data-ttu-id="fc188-107">Член</span><span class="sxs-lookup"><span data-stu-id="fc188-107">Member</span></span>|<span data-ttu-id="fc188-108">Описание</span><span class="sxs-lookup"><span data-stu-id="fc188-108">Description</span></span>|  
|------------|-----------------|  
|`dwAppDomainId`|<span data-ttu-id="fc188-109">Уникальный идентификатор для `IStream` , возвращаемый вызовом метода [IHostAssemblyStore::P ровидемодуле](ihostassemblystore-providemodule-method.md) , из которого загружается указанный модуль.</span><span class="sxs-lookup"><span data-stu-id="fc188-109">A unique identifier for the `IStream` that is returned by a call to the [IHostAssemblyStore::ProvideModule](ihostassemblystore-providemodule-method.md) method from which the referenced module is to be loaded.</span></span>|  
|`lpAssemblyIdentity`|<span data-ttu-id="fc188-110">Уникальный идентификатор сборки, содержащей упоминаемый модуль.</span><span class="sxs-lookup"><span data-stu-id="fc188-110">A unique identifier for the assembly that contains the referenced module.</span></span>|  
|`lpModuleName`|<span data-ttu-id="fc188-111">Имя модуля, на который указывает ссылка.</span><span class="sxs-lookup"><span data-stu-id="fc188-111">The name of the referenced module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fc188-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="fc188-112">Remarks</span></span>  

 <span data-ttu-id="fc188-113">`ModuleBindInfo` передается в качестве параметра в `IHostAssemblyStore::ProvideModule` .</span><span class="sxs-lookup"><span data-stu-id="fc188-113">`ModuleBindInfo` is passed as a parameter to `IHostAssemblyStore::ProvideModule`.</span></span> <span data-ttu-id="fc188-114">Узел предоставляет уникальный идентификатор среде CLR `dwAppDomainId` .</span><span class="sxs-lookup"><span data-stu-id="fc188-114">The host supplies the unique identifier `dwAppDomainId` to the common language runtime (CLR).</span></span> <span data-ttu-id="fc188-115">После вызова метода [IHostAssemblyStore::P ровидеассембли](ihostassemblystore-provideassembly-method.md) среда выполнения использует идентификатор, чтобы определить, `IStream` сопоставлено ли содержимое объекта.</span><span class="sxs-lookup"><span data-stu-id="fc188-115">After a call to the [IHostAssemblyStore::ProvideAssembly](ihostassemblystore-provideassembly-method.md) method returns, the runtime uses the identifier to determine whether the contents of the `IStream` have been mapped.</span></span> <span data-ttu-id="fc188-116">Если это так, среда выполнения загружает существующую копию вместо повторного сопоставления потока.</span><span class="sxs-lookup"><span data-stu-id="fc188-116">If so, the runtime loads the existing copy rather than remapping the stream.</span></span> <span data-ttu-id="fc188-117">Среда выполнения также использует этот идентификатор в качестве ключа поиска для потоков, возвращаемых из вызовов `IHostAssemblyStore::ProvideAssembly` метода.</span><span class="sxs-lookup"><span data-stu-id="fc188-117">The runtime also uses this identifier as a lookup key for streams that are returned from calls to the `IHostAssemblyStore::ProvideAssembly` method.</span></span> <span data-ttu-id="fc188-118">Таким образом, идентификатор должен быть уникальным для запросов модуля, а также для запросов сборки.</span><span class="sxs-lookup"><span data-stu-id="fc188-118">Therefore, the identifier must be unique for module requests as well as for assembly requests.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc188-119">Требования</span><span class="sxs-lookup"><span data-stu-id="fc188-119">Requirements</span></span>  

 <span data-ttu-id="fc188-120">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc188-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc188-121">**Заголовок:** MSCorEE. idl</span><span class="sxs-lookup"><span data-stu-id="fc188-121">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="fc188-122">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="fc188-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="fc188-123">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc188-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc188-124">См. также</span><span class="sxs-lookup"><span data-stu-id="fc188-124">See also</span></span>

- [<span data-ttu-id="fc188-125">Структуры размещения</span><span class="sxs-lookup"><span data-stu-id="fc188-125">Hosting Structures</span></span>](hosting-structures.md)
- [<span data-ttu-id="fc188-126">Структура AssemblyBindInfo</span><span class="sxs-lookup"><span data-stu-id="fc188-126">AssemblyBindInfo Structure</span></span>](assemblybindinfo-structure.md)
- [<span data-ttu-id="fc188-127">Интерфейс ICLRAssemblyIdentityManager</span><span class="sxs-lookup"><span data-stu-id="fc188-127">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="fc188-128">Интерфейс ICLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="fc188-128">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="fc188-129">Интерфейс IHostAssemblyManager</span><span class="sxs-lookup"><span data-stu-id="fc188-129">IHostAssemblyManager Interface</span></span>](ihostassemblymanager-interface.md)
