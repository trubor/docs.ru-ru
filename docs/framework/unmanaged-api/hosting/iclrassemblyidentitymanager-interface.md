---
description: 'Дополнительные сведения о: интерфейс ICLRAssemblyIdentityManager'
title: Интерфейс ICLRAssemblyIdentityManager
ms.date: 03/30/2017
api_name:
- ICLRAssemblyIdentityManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRAssemblyIdentityManager
helpviewer_keywords:
- ICLRAssemblyIdentityManager interface [.NET Framework hosting]
ms.assetid: 6a81c6fe-cc22-4062-ae27-d6eeee03a7b9
topic_type:
- apiref
ms.openlocfilehash: d6238ec51a8cc1bb61eaa96e5297656c447df785
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790062"
---
# <a name="iclrassemblyidentitymanager-interface"></a><span data-ttu-id="573f2-103">Интерфейс ICLRAssemblyIdentityManager</span><span class="sxs-lookup"><span data-stu-id="573f2-103">ICLRAssemblyIdentityManager Interface</span></span>

<span data-ttu-id="573f2-104">Предоставляет методы, поддерживающие взаимодействие между узлом и общеязыковой средой выполнения (CLR) о сборках.</span><span class="sxs-lookup"><span data-stu-id="573f2-104">Provides methods that support communication between the host and the common language runtime (CLR) about assemblies.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="573f2-105">Методы</span><span class="sxs-lookup"><span data-stu-id="573f2-105">Methods</span></span>  
  
|<span data-ttu-id="573f2-106">Метод</span><span class="sxs-lookup"><span data-stu-id="573f2-106">Method</span></span>|<span data-ttu-id="573f2-107">Описание</span><span class="sxs-lookup"><span data-stu-id="573f2-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="573f2-108">Метод GetBindingIdentityFromFile</span><span class="sxs-lookup"><span data-stu-id="573f2-108">GetBindingIdentityFromFile Method</span></span>](iclrassemblyidentitymanager-getbindingidentityfromfile-method.md)|<span data-ttu-id="573f2-109">Возвращает данные привязки удостоверения сборки для сборки по указанному пути к файлу.</span><span class="sxs-lookup"><span data-stu-id="573f2-109">Gets the assembly identity binding data for the assembly at the specified file path.</span></span>|  
|[<span data-ttu-id="573f2-110">Метод GetBindingIdentityFromStream</span><span class="sxs-lookup"><span data-stu-id="573f2-110">GetBindingIdentityFromStream Method</span></span>](iclrassemblyidentitymanager-getbindingidentityfromstream-method.md)|<span data-ttu-id="573f2-111">Возвращает канонические данные удостоверений сборки для сборки в указанном потоке.</span><span class="sxs-lookup"><span data-stu-id="573f2-111">Gets the canonical assembly identity data for the assembly in the specified stream.</span></span>|  
|[<span data-ttu-id="573f2-112">Метод GetCLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="573f2-112">GetCLRAssemblyReferenceList Method</span></span>](iclrassemblyidentitymanager-getclrassemblyreferencelist-method.md)|<span data-ttu-id="573f2-113">Возвращает экземпляр [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) из заданного списка частичных идентификаторов сборки.</span><span class="sxs-lookup"><span data-stu-id="573f2-113">Gets an [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) instance from the supplied list of partial assembly identities.</span></span>|  
|[<span data-ttu-id="573f2-114">Метод GetProbingAssembliesFromReference</span><span class="sxs-lookup"><span data-stu-id="573f2-114">GetProbingAssembliesFromReference Method</span></span>](iclrassemblyidentitymanager-getprobingassembliesfromreference-method.md)|<span data-ttu-id="573f2-115">Возвращает перечислитель [ICLRProbingAssemblyEnum](iclrprobingassemblyenum-interface.md) для удостоверений сборок, на которые ссылается сборка с указанным удостоверением.</span><span class="sxs-lookup"><span data-stu-id="573f2-115">Gets an [ICLRProbingAssemblyEnum](iclrprobingassemblyenum-interface.md) enumerator for the assembly identities referenced by the assembly with the specified identity.</span></span>|  
|[<span data-ttu-id="573f2-116">Метод GetReferencedAssembliesFromFile</span><span class="sxs-lookup"><span data-stu-id="573f2-116">GetReferencedAssembliesFromFile Method</span></span>](iclrassemblyidentitymanager-getreferencedassembliesfromfile-method.md)|<span data-ttu-id="573f2-117">Возвращает экземпляр [ICLRReferenceAssemblyEnum](iclrreferenceassemblyenum-interface.md) , содержащий список сборок, на которые ссылается сборка по указанному пути к файлу.</span><span class="sxs-lookup"><span data-stu-id="573f2-117">Gets an [ICLRReferenceAssemblyEnum](iclrreferenceassemblyenum-interface.md) instance that contains a list of assemblies referenced by the assembly at the specified file path.</span></span>|  
|[<span data-ttu-id="573f2-118">Метод GetReferencedAssembliesFromStream</span><span class="sxs-lookup"><span data-stu-id="573f2-118">GetReferencedAssembliesFromStream Method</span></span>](iclrassemblyidentitymanager-getreferencedassembliesfromstream-method.md)|<span data-ttu-id="573f2-119">Возвращает указатель на `ICLRReferenceAssemblyEnum` объект, содержащий данные идентификации сборки для сборок, на которые ссылается сборка в указанном потоке.</span><span class="sxs-lookup"><span data-stu-id="573f2-119">Gets a pointer to an `ICLRReferenceAssemblyEnum` object that contains assembly identity data for the assemblies referenced by the assembly in the specified stream.</span></span>|  
|[<span data-ttu-id="573f2-120">Метод IsStronglyNamed</span><span class="sxs-lookup"><span data-stu-id="573f2-120">IsStronglyNamed Method</span></span>](iclrassemblyidentitymanager-isstronglynamed-method.md)|<span data-ttu-id="573f2-121">Возвращает значение, указывающее, является ли указанная сборка строго именованной.</span><span class="sxs-lookup"><span data-stu-id="573f2-121">Gets a value that indicates whether the specified assembly is strongly named.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="573f2-122">Remarks</span><span class="sxs-lookup"><span data-stu-id="573f2-122">Remarks</span></span>  

 <span data-ttu-id="573f2-123">Используйте `ICLRAssemblyIdentityManager` для получения экземпляров `ICLRAssemblyReferenceList` и для перечисления идентификаторов сборок.</span><span class="sxs-lookup"><span data-stu-id="573f2-123">Use `ICLRAssemblyIdentityManager` to get instances of `ICLRAssemblyReferenceList` and to enumerate assembly identities.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="573f2-124">Требования</span><span class="sxs-lookup"><span data-stu-id="573f2-124">Requirements</span></span>  

 <span data-ttu-id="573f2-125">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="573f2-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="573f2-126">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="573f2-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="573f2-127">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="573f2-127">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="573f2-128">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="573f2-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="573f2-129">См. также</span><span class="sxs-lookup"><span data-stu-id="573f2-129">See also</span></span>

- [<span data-ttu-id="573f2-130">Интерфейс ICLRAssemblyReferenceList</span><span class="sxs-lookup"><span data-stu-id="573f2-130">ICLRAssemblyReferenceList Interface</span></span>](iclrassemblyreferencelist-interface.md)
- [<span data-ttu-id="573f2-131">Интерфейс ICLRProbingAssemblyEnum</span><span class="sxs-lookup"><span data-stu-id="573f2-131">ICLRProbingAssemblyEnum Interface</span></span>](iclrprobingassemblyenum-interface.md)
- [<span data-ttu-id="573f2-132">Интерфейсы размещения</span><span class="sxs-lookup"><span data-stu-id="573f2-132">Hosting Interfaces</span></span>](hosting-interfaces.md)
