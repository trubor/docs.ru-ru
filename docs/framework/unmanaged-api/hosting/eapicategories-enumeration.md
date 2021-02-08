---
description: Дополнительные сведения о перечислении Еапикатегориес
title: Перечисление EApiCategories
ms.date: 03/30/2017
api_name:
- EApiCategories
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EApiCategories
helpviewer_keywords:
- EApiCategories enumeration [.NET Framework hosting]
ms.assetid: 3c4a8a5a-8a46-4ac9-947f-4959bc9d6ac6
topic_type:
- apiref
ms.openlocfilehash: 58a7d4fa4d0c965bf9158ad6713185782d4ae94a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785631"
---
# <a name="eapicategories-enumeration"></a><span data-ttu-id="f4e35-103">Перечисление EApiCategories</span><span class="sxs-lookup"><span data-stu-id="f4e35-103">EApiCategories Enumeration</span></span>

<span data-ttu-id="f4e35-104">Описывает категории возможностей, которые узел может блокировать при выполнении в частично доверенном коде.</span><span class="sxs-lookup"><span data-stu-id="f4e35-104">Describes the categories of capabilities that the host can block from running in partially trusted code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f4e35-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f4e35-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eNoCategory               = 0,  
    eSynchronization          = 0x1,  
    eSharedState              = 0x2,  
    eExternalProcessMgmt      = 0x4,  
    eSelfAffectingProcessMgmt = 0x8,  
    eExternalThreading        = 0x10,  
    eSelfAffectingThreading   = 0x20,  
    eSecurityInfrastructure   = 0x40,  
    eUI                       = 0x80,  
    eMayLeakOnAbort           = 0x100,  
    eAll                      = 0x1ff  
} EHostProtectionCategories;  
```  
  
## <a name="members"></a><span data-ttu-id="f4e35-106">Члены</span><span class="sxs-lookup"><span data-stu-id="f4e35-106">Members</span></span>  
  
|<span data-ttu-id="f4e35-107">Член</span><span class="sxs-lookup"><span data-stu-id="f4e35-107">Member</span></span>|<span data-ttu-id="f4e35-108">Описание</span><span class="sxs-lookup"><span data-stu-id="f4e35-108">Description</span></span>|  
|------------|-----------------|  
|`eAll`|<span data-ttu-id="f4e35-109">Указывает, что все управляемые классы и члены, охваченные другими `EApiCategories` полями, будут заблокированы в частично доверенном коде.</span><span class="sxs-lookup"><span data-stu-id="f4e35-109">Specifies that all managed classes and members that are covered by other `EApiCategories` fields be blocked from running in partially trusted code.</span></span>|  
|`eExternalProcessMgmt`|<span data-ttu-id="f4e35-110">Указывает, что управляемые классы и члены, разрешающие создание, обработку и уничтожение внешних процессов, блокируются в частично доверенном коде.</span><span class="sxs-lookup"><span data-stu-id="f4e35-110">Specifies that managed classes and members that allow the creation, manipulation, and destruction of external processes be blocked from running in partially trusted code.</span></span>|  
|`eExternalThreading`|<span data-ttu-id="f4e35-111">Указывает, что управляемые классы и члены, которые позволяют блокировать создание, обработку и уничтожение внешних потоков, должны быть заблокированы в частично доверенном коде.</span><span class="sxs-lookup"><span data-stu-id="f4e35-111">Specifies that managed classes and members that allow the creation, manipulation, and destruction of external threads be blocked from running in partially trusted code.</span></span>|  
|`eMayLeakOnAbort`|<span data-ttu-id="f4e35-112">Указывает, что управляемые типы и члены, которые могут привести к утечке памяти при прерывании, блокируются в частично доверенном коде.</span><span class="sxs-lookup"><span data-stu-id="f4e35-112">Specifies that managed types and members that could potentially leak memory on abort be blocked from running in partially trusted code.</span></span>|  
|`eNoCategory`|<span data-ttu-id="f4e35-113">Указывает, что ни одна из категорий управляемого кода не будет заблокирована в частично доверенном коде.</span><span class="sxs-lookup"><span data-stu-id="f4e35-113">Specifies that no managed code categories be blocked from running in partially trusted code.</span></span>|  
|`eSecurityInfrastructure`|<span data-ttu-id="f4e35-114">Указывает, что инфраструктура безопасности среды CLR должна быть заблокирована для частично доверенного кода.</span><span class="sxs-lookup"><span data-stu-id="f4e35-114">Specifies that the common language runtime (CLR) security infrastructure be blocked from being used by partially trusted code.</span></span>|  
|`eSelfAffectingProcessMgmt`|<span data-ttu-id="f4e35-115">Указывает, что управляемые классы и члены, возможности которых могут повлиять на работу размещенного процесса, должны быть заблокированы в частично доверенном коде.</span><span class="sxs-lookup"><span data-stu-id="f4e35-115">Specifies that managed classes and members whose capabilities can affect the hosted process be blocked from running in partially trusted code.</span></span>|  
|`eSelfAffectingThreading`|<span data-ttu-id="f4e35-116">Указывает, что управляемые классы и члены, возможности которых могут влиять на потоки в размещенном процессе, блокируются в частично доверенном коде.</span><span class="sxs-lookup"><span data-stu-id="f4e35-116">Specifies that managed classes and members whose capabilities can affect threads in the hosted process be blocked from running in partially trusted code.</span></span>|  
|`eSharedState`|<span data-ttu-id="f4e35-117">Указывает, что управляемые классы и члены, которые предоставляют общее состояние, будут заблокированы для выполнения в частично доверенном коде.</span><span class="sxs-lookup"><span data-stu-id="f4e35-117">Specifies that managed classes and members that expose shared state be blocked from running in partially trusted code.</span></span>|  
|`eSynchronization`|<span data-ttu-id="f4e35-118">Указывает, что классы и члены среды CLR, которые позволяют коду пользователя удерживать блокировки, блокируются в частично доверенном коде.</span><span class="sxs-lookup"><span data-stu-id="f4e35-118">Specifies that common language runtime classes and members that allow user code to hold locks be blocked from running in partially trusted code.</span></span>|  
|`eUI`|<span data-ttu-id="f4e35-119">Указывает, что управляемые классы и члены, которые разрешают или запрашивать взаимодействие с пользователем, блокируются в частично доверенном коде.</span><span class="sxs-lookup"><span data-stu-id="f4e35-119">Specifies that managed classes and members that allow or require human interaction be blocked from running in partially trusted code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f4e35-120">Remarks</span><span class="sxs-lookup"><span data-stu-id="f4e35-120">Remarks</span></span>  

 <span data-ttu-id="f4e35-121">Метод [иклрхостпротектионманажер:: SetProtectedCategories](iclrhostprotectionmanager-setprotectedcategories-method.md) принимает параметр типа `EApiCategories` .</span><span class="sxs-lookup"><span data-stu-id="f4e35-121">The [ICLRHostProtectionManager::SetProtectedCategories](iclrhostprotectionmanager-setprotectedcategories-method.md) method takes a parameter of type `EApiCategories`.</span></span>  
  
 <span data-ttu-id="f4e35-122">`EApiCategories`Перечисление и `SetProtectedCategories` метод напрямую связаны с управляемым <xref:System.Security.Permissions.HostProtectionAttribute?displayProperty=nameWithType> классом.</span><span class="sxs-lookup"><span data-stu-id="f4e35-122">The `EApiCategories` enumeration and the `SetProtectedCategories` method are directly related to the managed <xref:System.Security.Permissions.HostProtectionAttribute?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="f4e35-123">Управляемый класс используется с <xref:System.Security.Permissions.HostProtectionResource?displayProperty=nameWithType> перечислением, значения которого непосредственно соответствуют `EApiCategories` значениям, чтобы пометить управляемые типы и члены, которые предоставляют возможности, соответствующие категориям, описанным в `EApiCategories` .</span><span class="sxs-lookup"><span data-stu-id="f4e35-123">The managed class is used with the <xref:System.Security.Permissions.HostProtectionResource?displayProperty=nameWithType> enumeration, whose values correspond directly to the `EApiCategories` values, to mark managed types and members that expose capabilities corresponding to the categories described by `EApiCategories`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f4e35-124">Требования</span><span class="sxs-lookup"><span data-stu-id="f4e35-124">Requirements</span></span>  

 <span data-ttu-id="f4e35-125">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f4e35-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f4e35-126">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f4e35-126">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f4e35-127">**Библиотека:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="f4e35-127">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f4e35-128">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f4e35-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f4e35-129">См. также</span><span class="sxs-lookup"><span data-stu-id="f4e35-129">See also</span></span>

- [<span data-ttu-id="f4e35-130">Интерфейс ICLRHostProtectionManager</span><span class="sxs-lookup"><span data-stu-id="f4e35-130">ICLRHostProtectionManager Interface</span></span>](iclrhostprotectionmanager-interface.md)
- [<span data-ttu-id="f4e35-131">Размещение перечислений</span><span class="sxs-lookup"><span data-stu-id="f4e35-131">Hosting Enumerations</span></span>](hosting-enumerations.md)
