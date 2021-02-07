---
description: 'Дополнительные сведения о методе: ICLRAssemblyReferenceList:: IsAssemblyReferenceInList'
title: Метод ICLRAssemblyReferenceList::IsAssemblyReferenceInList
ms.date: 03/30/2017
api_name:
- ICLRAssemblyReferenceList.IsAssemblyReferenceInList
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyReferenceList::IsAssemblyReferenceInList
helpviewer_keywords:
- ICLRAssemblyReferenceList::IsAssemblyReferenceInList method [.NET Framework hosting]
- IsAssemblyReferenceInList method [.NET Framework hosting]
ms.assetid: 8a570813-21be-407e-92a6-7ae8de3bc728
topic_type:
- apiref
ms.openlocfilehash: ce90423715d6cbe07c1112cb2136c11fd58c982a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99716774"
---
# <a name="iclrassemblyreferencelistisassemblyreferenceinlist-method"></a><span data-ttu-id="15c90-103">Метод ICLRAssemblyReferenceList::IsAssemblyReferenceInList</span><span class="sxs-lookup"><span data-stu-id="15c90-103">ICLRAssemblyReferenceList::IsAssemblyReferenceInList Method</span></span>

<span data-ttu-id="15c90-104">Возвращает значение, указывающее, ссылается ли заданный указатель на сборку в списке.</span><span class="sxs-lookup"><span data-stu-id="15c90-104">Gets a value that indicates whether the supplied pointer refers to an assembly in the list.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15c90-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="15c90-105">Syntax</span></span>  
  
```cpp  
HRESULT IsAssemblyReferenceInList (  
    [in] IUnknown *pName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="15c90-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="15c90-106">Parameters</span></span>  

 `pName`  
 <span data-ttu-id="15c90-107">окне Указатель интерфейса на сборку, для которой необходимо выполнить поиск.</span><span class="sxs-lookup"><span data-stu-id="15c90-107">[in] An interface pointer to the assembly for which to search.</span></span> <span data-ttu-id="15c90-108">Допустимые значения имеют тип `IAssemblyName` или `IReferenceIdentity` .</span><span class="sxs-lookup"><span data-stu-id="15c90-108">Valid values are of type `IAssemblyName` or `IReferenceIdentity`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="15c90-109">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="15c90-109">Return Value</span></span>  
  
|<span data-ttu-id="15c90-110">HRESULT</span><span class="sxs-lookup"><span data-stu-id="15c90-110">HRESULT</span></span>|<span data-ttu-id="15c90-111">Описание:</span><span class="sxs-lookup"><span data-stu-id="15c90-111">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="15c90-112">S_OK</span><span class="sxs-lookup"><span data-stu-id="15c90-112">S_OK</span></span>|<span data-ttu-id="15c90-113">Строка появится в списке.</span><span class="sxs-lookup"><span data-stu-id="15c90-113">The string appears in the list.</span></span>|  
|<span data-ttu-id="15c90-114">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="15c90-114">S_FALSE</span></span>|<span data-ttu-id="15c90-115">Строка не отображается в списке.</span><span class="sxs-lookup"><span data-stu-id="15c90-115">The string does not appear in the list.</span></span>|  
|<span data-ttu-id="15c90-116">E_FAIL</span><span class="sxs-lookup"><span data-stu-id="15c90-116">E_FAIL</span></span>|<span data-ttu-id="15c90-117">Произошла неизвестная фатальная ошибка.</span><span class="sxs-lookup"><span data-stu-id="15c90-117">An unknown catastrophic failure occurred.</span></span> <span data-ttu-id="15c90-118">После того как метод возвращает E_FAIL, среда CLR больше не будет использоваться в процессе.</span><span class="sxs-lookup"><span data-stu-id="15c90-118">After a method returns E_FAIL, the common language runtime is no longer usable within the process.</span></span> <span data-ttu-id="15c90-119">Последующие вызовы методов размещения возвращают HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="15c90-119">Subsequent calls to hosting methods return HOST_E_CLRNOTAVAILABLE.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="15c90-120">Требования</span><span class="sxs-lookup"><span data-stu-id="15c90-120">Requirements</span></span>  

 <span data-ttu-id="15c90-121">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="15c90-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15c90-122">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="15c90-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="15c90-123">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="15c90-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="15c90-124">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15c90-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15c90-125">См. также</span><span class="sxs-lookup"><span data-stu-id="15c90-125">See also</span></span>

- [<span data-ttu-id="15c90-126">Интерфейс ICLRAssemblyIdentityManager</span><span class="sxs-lookup"><span data-stu-id="15c90-126">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="15c90-127">Интерфейс ICLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="15c90-127">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="15c90-128">Интерфейс IHostAssemblyManager</span><span class="sxs-lookup"><span data-stu-id="15c90-128">IHostAssemblyManager Interface</span></span>](ihostassemblymanager-interface.md)
- [<span data-ttu-id="15c90-129">Интерфейс IHostAssemblyStore</span><span class="sxs-lookup"><span data-stu-id="15c90-129">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)
