---
description: 'Дополнительные сведения о методе: IManagedObject:: Getobjectidentity-'
title: Метод IManagedObject::GetObjectIdentity
ms.date: 03/30/2017
api_name:
- IManagedObject.GetObjectIdentity
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetObjectIdentity
helpviewer_keywords:
- GetObjectIdentity method [.NET Framework hosting]
- IManagedObject::GetObjectIdentity method [.NET Framework hosting]
ms.assetid: b862ff3e-e480-4cdf-84e2-e1013334a467
topic_type:
- apiref
ms.openlocfilehash: 8929819bbf490680b5f3f1f47b9f3b8e830d57ba
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99671169"
---
# <a name="imanagedobjectgetobjectidentity-method"></a><span data-ttu-id="17299-103">Метод IManagedObject::GetObjectIdentity</span><span class="sxs-lookup"><span data-stu-id="17299-103">IManagedObject::GetObjectIdentity Method</span></span>

<span data-ttu-id="17299-104">Возвращает удостоверение этого управляемого объекта.</span><span class="sxs-lookup"><span data-stu-id="17299-104">Gets the identity of this managed object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17299-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="17299-105">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectIdentity (  
    [out] BSTR*   pBSTRGUID,  
    [out] int*    AppDomainID,  
    [out] CCW_PTR pCCW  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="17299-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="17299-106">Parameters</span></span>  

 `pBSTRGUID`  
 <span data-ttu-id="17299-107">заполняет Указатель на идентификатор GUID процесса, в котором находится объект.</span><span class="sxs-lookup"><span data-stu-id="17299-107">[out] A pointer to the GUID of the process in which the object resides.</span></span>  
  
 `AppDomainID`  
 <span data-ttu-id="17299-108">заполняет Указатель на идентификатор домена приложения объекта.</span><span class="sxs-lookup"><span data-stu-id="17299-108">[out] A pointer to the ID of the object's application domain.</span></span>  
  
 `pCCW`  
 <span data-ttu-id="17299-109">заполняет Указатель на индекс объекта в классической таблице v-таблицы COM.</span><span class="sxs-lookup"><span data-stu-id="17299-109">[out] A pointer to object's index in the COM classic v-table.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="17299-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="17299-110">Remarks</span></span>  

 <span data-ttu-id="17299-111">Удостоверение управляемого объекта включает идентификатор GUID процесса, идентификатор домена приложения и индекс объекта в классической таблице v-таблицы COM.</span><span class="sxs-lookup"><span data-stu-id="17299-111">The identity of a managed object includes process GUID, application domain ID, and the object's index in the COM classic v-table.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17299-112">Требования</span><span class="sxs-lookup"><span data-stu-id="17299-112">Requirements</span></span>  

 <span data-ttu-id="17299-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="17299-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17299-114">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="17299-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="17299-115">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="17299-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="17299-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17299-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17299-117">См. также</span><span class="sxs-lookup"><span data-stu-id="17299-117">See also</span></span>

- [<span data-ttu-id="17299-118">Интерфейс IManagedObject</span><span class="sxs-lookup"><span data-stu-id="17299-118">IManagedObject Interface</span></span>](imanagedobject-interface.md)
