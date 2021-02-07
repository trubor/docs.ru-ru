---
description: 'Дополнительные сведения о: интерфейс ICLRAssemblyReferenceList'
title: Интерфейс ICLRAssemblyReferenceList
ms.date: 03/30/2017
api_name:
- ICLRAssemblyReferenceList
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyReferenceList
helpviewer_keywords:
- ICLRAssemblyReferenceList interface [.NET Framework hosting]
ms.assetid: 5f890fdf-d22a-429e-a35f-135273d1a636
topic_type:
- apiref
ms.openlocfilehash: f5ef4efd343ebc18c443482f4697a3d299c5aac1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99716827"
---
# <a name="iclrassemblyreferencelist-interface"></a><span data-ttu-id="0c106-103">Интерфейс ICLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="0c106-103">ICLRAssemblyReferenceList Interface</span></span>

<span data-ttu-id="0c106-104">Управляет списком сборок, загружаемых средой CLR, а не узлом.</span><span class="sxs-lookup"><span data-stu-id="0c106-104">Manages a list of assemblies that are loaded by the common language runtime (CLR) and not by the host.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0c106-105">Методы</span><span class="sxs-lookup"><span data-stu-id="0c106-105">Methods</span></span>  
  
|<span data-ttu-id="0c106-106">Метод</span><span class="sxs-lookup"><span data-stu-id="0c106-106">Method</span></span>|<span data-ttu-id="0c106-107">Описание</span><span class="sxs-lookup"><span data-stu-id="0c106-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0c106-108">Метод IsAssemblyReferenceInList</span><span class="sxs-lookup"><span data-stu-id="0c106-108">IsAssemblyReferenceInList Method</span></span>](iclrassemblyreferencelist-isassemblyreferenceinlist-method.md)|<span data-ttu-id="0c106-109">Возвращает значение, указывающее, ссылается ли указанный указатель на сборку в списке.</span><span class="sxs-lookup"><span data-stu-id="0c106-109">Gets a value that indicates whether the supplied pointer references an assembly in the list.</span></span>|  
|[<span data-ttu-id="0c106-110">Метод IsStringAssemblyReferenceInList</span><span class="sxs-lookup"><span data-stu-id="0c106-110">IsStringAssemblyReferenceInList Method</span></span>](iclrassemblyreferencelist-isstringassemblyreferenceinlist-method.md)|<span data-ttu-id="0c106-111">Возвращает значение, указывающее, совпадает ли заданное имя с именем сборки в списке.</span><span class="sxs-lookup"><span data-stu-id="0c106-111">Gets a value that indicates whether the supplied name matches the name of an assembly in the list.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0c106-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="0c106-112">Remarks</span></span>  

 <span data-ttu-id="0c106-113">Вызовите метод [ICLRAssemblyIdentityManager:: getclrassemblyreferencelist-](iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md) , чтобы получить указатель на экземпляр `ICLRAssemblyReferenceList` .</span><span class="sxs-lookup"><span data-stu-id="0c106-113">Call the [ICLRAssemblyIdentityManager::GetCLRAssemblyReferenceList](iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md) method to get a pointer to an instance of `ICLRAssemblyReferenceList`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c106-114">Требования</span><span class="sxs-lookup"><span data-stu-id="0c106-114">Requirements</span></span>  

 <span data-ttu-id="0c106-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0c106-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c106-116">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="0c106-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="0c106-117">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="0c106-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="0c106-118">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c106-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c106-119">См. также</span><span class="sxs-lookup"><span data-stu-id="0c106-119">See also</span></span>

- [<span data-ttu-id="0c106-120">Интерфейс ICLRAssemblyIdentityManager</span><span class="sxs-lookup"><span data-stu-id="0c106-120">ICLRAssemblyIdentityManager Interface</span></span>](iclrassemblyidentitymanager-interface.md)
- [<span data-ttu-id="0c106-121">Интерфейс IHostAssemblyStore</span><span class="sxs-lookup"><span data-stu-id="0c106-121">IHostAssemblyStore Interface</span></span>](ihostassemblystore-interface.md)
- [<span data-ttu-id="0c106-122">Интерфейсы размещения</span><span class="sxs-lookup"><span data-stu-id="0c106-122">Hosting Interfaces</span></span>](hosting-interfaces.md)
