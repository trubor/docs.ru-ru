---
description: Дополнительные сведения о перечислении Кордеклсекурити
title: Перечисление CorDeclSecurity
ms.date: 03/30/2017
api_name:
- CorDeclSecurity
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorDeclSecurity
helpviewer_keywords:
- CorDeclSecurity enumeration [.NET Framework metadata]
ms.assetid: 864f1267-d267-4696-8df7-1f83f8444d6f
topic_type:
- apiref
ms.openlocfilehash: 4c4b57c09ea8b3ec1b98ff120d72a5920dc5aa4a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99784552"
---
# <a name="cordeclsecurity-enumeration"></a><span data-ttu-id="18784-103">Перечисление CorDeclSecurity</span><span class="sxs-lookup"><span data-stu-id="18784-103">CorDeclSecurity Enumeration</span></span>

<span data-ttu-id="18784-104">Указывает действия безопасности, которые можно выполнить с помощью декларативной безопасности.</span><span class="sxs-lookup"><span data-stu-id="18784-104">Specifies the security actions that can be performed using declarative security.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18784-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="18784-105">Syntax</span></span>  
  
```cpp  
typedef enum CorDeclSecurity {  
  
    dclActionMask               =   0x001f,  
    dclActionNil                =   0x0000,  
    dclRequest                  =   0x0001,  
    dclDemand                   =   0x0002,  
    dclAssert                   =   0x0003,  
    dclDeny                     =   0x0004,  
    dclPermitOnly               =   0x0005,  
    dclLinktimeCheck            =   0x0006,  
    dclInheritanceCheck         =   0x0007,  
    dclRequestMinimum           =   0x0008,  
    dclRequestOptional          =   0x0009,  
    dclRequestRefuse            =   0x000a,  
    dclPrejitGrant              =   0x000b,  
    dclPrejitDenied             =   0x000c,  
    dclNonCasDemand             =   0x000d,  
    dclNonCasLinkDemand         =   0x000e,  
    dclNonCasInheritance        =   0x000f,  
    dclLinkDemandChoice         =   0x0010,  
    dclInheritanceDemandChoice  =   0x0011,  
    dclDemandChoice             =   0x0012,  
    dclMaximumValue             =   0x0012  
  
} CorDeclSecurity;  
```  
  
## <a name="members"></a><span data-ttu-id="18784-106">Члены</span><span class="sxs-lookup"><span data-stu-id="18784-106">Members</span></span>  
  
|<span data-ttu-id="18784-107">Член</span><span class="sxs-lookup"><span data-stu-id="18784-107">Member</span></span>|<span data-ttu-id="18784-108">Описание</span><span class="sxs-lookup"><span data-stu-id="18784-108">Description</span></span>|  
|------------|-----------------|  
|`dclActionMask`|<span data-ttu-id="18784-109">Зарезервировано.</span><span class="sxs-lookup"><span data-stu-id="18784-109">Reserved.</span></span>|  
|`dclActionNil`|<span data-ttu-id="18784-110">Зарезервировано.</span><span class="sxs-lookup"><span data-stu-id="18784-110">Reserved.</span></span>|  
|`dclRequest`|<span data-ttu-id="18784-111">Зарезервировано.</span><span class="sxs-lookup"><span data-stu-id="18784-111">Reserved.</span></span>|  
|`dclDemand`|<span data-ttu-id="18784-112">Всем вызывающим объектам выше в стеке вызовов должно быть предоставлено разрешение, заданное текущим объектом разрешений.</span><span class="sxs-lookup"><span data-stu-id="18784-112">All callers higher in the call stack are required to have been granted the permission specified by the current permission object.</span></span>|  
|`dclAssert`|<span data-ttu-id="18784-113">Вызывающий код может получить доступ к ресурсу, определяемому текущим объектом разрешения, даже если вызывающим объектам выше в стеке не предоставлено разрешение на доступ к ресурсу.</span><span class="sxs-lookup"><span data-stu-id="18784-113">The calling code can access the resource identified by the current permission object, even if callers higher in the stack have not been granted permission to access the resource</span></span>|  
|`dclDeny`|<span data-ttu-id="18784-114">Доступ к ресурсу, указанному текущим объектом разрешения, запрещен для вызывающих объектов, даже если им предоставлено разрешение на доступ к нему.</span><span class="sxs-lookup"><span data-stu-id="18784-114">The ability to access the resource specified by the current permission object is denied to callers, even if they have been granted permission to access it.</span></span>|  
|`dclPermitOnly`|<span data-ttu-id="18784-115">Доступ можно получить только к ресурсам, указанным данным объектом разрешения, даже если коду предоставлено разрешение на доступ к другим ресурсам.</span><span class="sxs-lookup"><span data-stu-id="18784-115">Only the resources specified by this permission object can be accessed, even if the code has been granted permission to access other resources.</span></span>|  
|`dclLinktimeCheck`|<span data-ttu-id="18784-116">Непосредственный вызывающий объект должен предоставить указанное разрешение в течение заданного периода времени.</span><span class="sxs-lookup"><span data-stu-id="18784-116">The immediate caller is required to have been granted the specified permission for a given period of time.</span></span>|  
|`dclInheritanceCheck`|<span data-ttu-id="18784-117">Производный класс, наследующий от другого класса или переопределяющий метод, должен предоставить указанное разрешение.</span><span class="sxs-lookup"><span data-stu-id="18784-117">The derived class inheriting another class or overriding a method is required to have been granted the specified permission.</span></span>|  
|`dclRequestMinimum`|<span data-ttu-id="18784-118">Вызывающий объект может запросить минимальные разрешения, необходимые для выполнения кода.</span><span class="sxs-lookup"><span data-stu-id="18784-118">The caller can request for the minimum permissions required for code to run.</span></span> <span data-ttu-id="18784-119">Это действие может использоваться только в пределах сборки.</span><span class="sxs-lookup"><span data-stu-id="18784-119">This action can only be used within the scope of the assembly.</span></span>|  
|`dclRequestOptional`|<span data-ttu-id="18784-120">Вызывающий объект может запросить дополнительные разрешения, которые являются необязательными (не требуются для запуска).</span><span class="sxs-lookup"><span data-stu-id="18784-120">The caller can request for additional permissions that are optional (not required to run).</span></span> <span data-ttu-id="18784-121">Этот запрос неявно отклоняет все прочие разрешения, не запрошенные специально.</span><span class="sxs-lookup"><span data-stu-id="18784-121">This request implicitly refuses all other permissions not specifically requested.</span></span> <span data-ttu-id="18784-122">Это действие может использоваться только в пределах сборки.</span><span class="sxs-lookup"><span data-stu-id="18784-122">This action can only be used within the scope of the assembly.</span></span>|  
|`dclRequestRefuse`|<span data-ttu-id="18784-123">Запрос вызывающего объекта для разрешений, которые могут быть неправильно использованы, не будет предоставлен.</span><span class="sxs-lookup"><span data-stu-id="18784-123">The caller's request for permissions that might be misused will not be granted.</span></span> <span data-ttu-id="18784-124">Это действие может использоваться только в пределах сборки.</span><span class="sxs-lookup"><span data-stu-id="18784-124">This action can only be used within the scope of the assembly.</span></span>|  
|`dclPrejitGrant`|<span data-ttu-id="18784-125">Зарезервировано.</span><span class="sxs-lookup"><span data-stu-id="18784-125">Reserved.</span></span>|  
|`dclPrejitDenied`|<span data-ttu-id="18784-126">Зарезервировано.</span><span class="sxs-lookup"><span data-stu-id="18784-126">Reserved.</span></span>|  
|`dclNonCasDemand`|<span data-ttu-id="18784-127">Зарезервировано.</span><span class="sxs-lookup"><span data-stu-id="18784-127">Reserved.</span></span>|  
|`dclNonCasLinkDemand`|<span data-ttu-id="18784-128">Указанное разрешение необходимо предоставить непосредственно вызывающему объекту.</span><span class="sxs-lookup"><span data-stu-id="18784-128">The immediate caller is required to have been granted the specified permission.</span></span>|  
|`dclNonCasInheritance`|<span data-ttu-id="18784-129">Зарезервировано.</span><span class="sxs-lookup"><span data-stu-id="18784-129">Reserved.</span></span>|  
|`dclLinkDemandChoice`|<span data-ttu-id="18784-130">Зарезервировано.</span><span class="sxs-lookup"><span data-stu-id="18784-130">Reserved.</span></span>|  
|`dclInheritanceDemandChoice`|<span data-ttu-id="18784-131">Зарезервировано.</span><span class="sxs-lookup"><span data-stu-id="18784-131">Reserved.</span></span>|  
|`dclDemandChoice`|<span data-ttu-id="18784-132">Зарезервировано.</span><span class="sxs-lookup"><span data-stu-id="18784-132">Reserved.</span></span>|  
|`dclMaximumValue`|<span data-ttu-id="18784-133">Зарезервировано.</span><span class="sxs-lookup"><span data-stu-id="18784-133">Reserved.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="18784-134">Требования</span><span class="sxs-lookup"><span data-stu-id="18784-134">Requirements</span></span>  

 <span data-ttu-id="18784-135">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="18784-135">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="18784-136">**Заголовок:** Корхдр. h</span><span class="sxs-lookup"><span data-stu-id="18784-136">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="18784-137">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="18784-137">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18784-138">См. также</span><span class="sxs-lookup"><span data-stu-id="18784-138">See also</span></span>

- [<span data-ttu-id="18784-139">Перечисления метаданных</span><span class="sxs-lookup"><span data-stu-id="18784-139">Metadata Enumerations</span></span>](metadata-enumerations.md)
