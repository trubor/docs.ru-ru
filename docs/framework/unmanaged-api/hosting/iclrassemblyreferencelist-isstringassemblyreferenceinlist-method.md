---
description: 'Дополнительные сведения о методе: ICLRAssemblyReferenceList:: IsStringAssemblyReferenceInList'
title: Метод ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList
ms.date: 03/30/2017
api_name:
- ICLRAssemblyReferenceList.IsStringAssemblyReferenceInList
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList
helpviewer_keywords:
- ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList method [.NET Framework hosting]
- IsStringAssemblyReferenceInList method [.NET Framework hosting]
ms.assetid: e6121cc3-2f11-42c7-bdae-47808581ff71
topic_type:
- apiref
ms.openlocfilehash: 667764337fbda22a526e51575faf049efc4b86ca
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790039"
---
# <a name="iclrassemblyreferencelistisstringassemblyreferenceinlist-method"></a><span data-ttu-id="902fd-103">Метод ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList</span><span class="sxs-lookup"><span data-stu-id="902fd-103">ICLRAssemblyReferenceList::IsStringAssemblyReferenceInList Method</span></span>

<span data-ttu-id="902fd-104">Возвращает значение, указывающее, совпадает ли заданное имя с именем сборки в списке.</span><span class="sxs-lookup"><span data-stu-id="902fd-104">Gets a value that indicates whether the supplied name matches the name of an assembly in the list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="902fd-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="902fd-105">Syntax</span></span>  
  
```cpp  
HRESULT IsStringAssemblyReferenceInList (  
    [in] LPCWSTR pwzAssemblyName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="902fd-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="902fd-106">Parameters</span></span>  

 `pwzAssemblyName`  
 <span data-ttu-id="902fd-107">окне Имя сборки, для которой необходимо выполнить поиск.</span><span class="sxs-lookup"><span data-stu-id="902fd-107">[in] The name of the assembly for which to search.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="902fd-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="902fd-108">Return Value</span></span>  
  
|<span data-ttu-id="902fd-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="902fd-109">HRESULT</span></span>|<span data-ttu-id="902fd-110">Описание:</span><span class="sxs-lookup"><span data-stu-id="902fd-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="902fd-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="902fd-111">S_OK</span></span>|<span data-ttu-id="902fd-112">Строка появится в списке.</span><span class="sxs-lookup"><span data-stu-id="902fd-112">The string appears in the list.</span></span>|  
|<span data-ttu-id="902fd-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="902fd-113">S_FALSE</span></span>|<span data-ttu-id="902fd-114">Строка не отображается в списке.</span><span class="sxs-lookup"><span data-stu-id="902fd-114">The string does not appear in the list.</span></span>|  
|<span data-ttu-id="902fd-115">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="902fd-115">E_FAIL</span></span>|<span data-ttu-id="902fd-116">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="902fd-116">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="902fd-117">После того как метод возвращает E_FAIL, среда CLR больше не будет использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="902fd-117">After a method returns E_FAIL, the common language runtime is no longer usable within the process.</span></span> <span data-ttu-id="902fd-118">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="902fd-118">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="902fd-119">Требования</span><span class="sxs-lookup"><span data-stu-id="902fd-119">Requirements</span></span>  

 <span data-ttu-id="902fd-120">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="902fd-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="902fd-121">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="902fd-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="902fd-122">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="902fd-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="902fd-123">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="902fd-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="902fd-124">См. также</span><span class="sxs-lookup"><span data-stu-id="902fd-124">See also</span></span>

- [<span data-ttu-id="902fd-125">Интерфейс ICLRAssemblyIdentityManager</span><span class="sxs-lookup"><span data-stu-id="902fd-125">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="902fd-126">Интерфейс ICLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="902fd-126">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="902fd-127">Интерфейс IHostAssemblyManager</span><span class="sxs-lookup"><span data-stu-id="902fd-127">IHostAssemblyManager Interface</span></span>](ihostassemblymanager-interface.md)
- [<span data-ttu-id="902fd-128">Интерфейс IHostAssemblyStore</span><span class="sxs-lookup"><span data-stu-id="902fd-128">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)
