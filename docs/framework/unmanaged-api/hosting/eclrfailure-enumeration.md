---
description: Дополнительные сведения о перечислении Еклрфаилуре
title: Перечисление EClrFailure
ms.date: 03/30/2017
api_name:
- EClrFailure
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EClrFailure
helpviewer_keywords:
- EClrFailure enumeration [.NET Framework hosting]
ms.assetid: 37b95cce-9bfb-4ecf-a00b-33dcba782c67
topic_type:
- apiref
ms.openlocfilehash: 9f3a2270651e5b05d2d31ed90511b8eb05dd4d44
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785592"
---
# <a name="eclrfailure-enumeration"></a><span data-ttu-id="ff7fd-103">Перечисление EClrFailure</span><span class="sxs-lookup"><span data-stu-id="ff7fd-103">EClrFailure Enumeration</span></span>

<span data-ttu-id="ff7fd-104">Описывает набор сбоев, для которых узел может задавать действия политики.</span><span class="sxs-lookup"><span data-stu-id="ff7fd-104">Describes the set of failures for which a host can set policy actions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff7fd-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ff7fd-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    FAIL_NonCriticalResource,  
    FAIL_CriticalResource,  
    FAIL_FatalRuntime,  
    FAIL_OrphanedLock  
    FAIL_StackOverflow  
    FAIL_AccessViolation  
    FAIL_CodeContract  
} EClrFailure;  
```  
  
## <a name="members"></a><span data-ttu-id="ff7fd-106">Члены</span><span class="sxs-lookup"><span data-stu-id="ff7fd-106">Members</span></span>  
  
|<span data-ttu-id="ff7fd-107">Член</span><span class="sxs-lookup"><span data-stu-id="ff7fd-107">Member</span></span>|<span data-ttu-id="ff7fd-108">Описание</span><span class="sxs-lookup"><span data-stu-id="ff7fd-108">Description</span></span>|  
|------------|-----------------|  
|`FAIL_NonCriticalResource`|<span data-ttu-id="ff7fd-109">Произошла ошибка при попытке выделения ресурса (например, потока, блока памяти или блокировки) в некритической области кода.</span><span class="sxs-lookup"><span data-stu-id="ff7fd-109">A failure occurred during an attempt to allocate a resource (such as a thread, a block of memory, or a lock) in a non-critical region of code.</span></span>|  
|`FAIL_CriticalResource`|<span data-ttu-id="ff7fd-110">Произошла ошибка при попытке выделения ресурса (например, потока, блока памяти или блокировки) в критической области кода.</span><span class="sxs-lookup"><span data-stu-id="ff7fd-110">A failure occurred during an attempt to allocate a resource (such as a thread, a block of memory, or a lock) in a critical region of code.</span></span>|  
|`FAIL_FatalRuntime`|<span data-ttu-id="ff7fd-111">Общеязыковая среда выполнения (CLR) больше не может выполнять управляемый код в процессе.</span><span class="sxs-lookup"><span data-stu-id="ff7fd-111">The common language runtime (CLR) is no longer able to run managed code in the process.</span></span> <span data-ttu-id="ff7fd-112">Исходя этого, вызовы любых функций размещения возвращают значение HRESULT, равное HOST_E_CLRNOTAVAILABLE.</span><span class="sxs-lookup"><span data-stu-id="ff7fd-112">Henceforth, calls to any hosting functions return an HRESULT value of HOST_E_CLRNOTAVAILABLE.</span></span>|  
|`FAIL_OrphanedLock`|<span data-ttu-id="ff7fd-113">Потоку не удалось снять блокировку после возврата из <xref:System.AppDomain> объекта.</span><span class="sxs-lookup"><span data-stu-id="ff7fd-113">A thread has failed to release a lock upon returning from an <xref:System.AppDomain> object.</span></span> <span data-ttu-id="ff7fd-114">Узлу не удается установить этот сбой, чтобы привести к прерыванию потока.</span><span class="sxs-lookup"><span data-stu-id="ff7fd-114">The host cannot set this failure to cause a thread to abort.</span></span>|  
|`FAIL_StackOverflow`|<span data-ttu-id="ff7fd-115">Произошло переполнение стека.</span><span class="sxs-lookup"><span data-stu-id="ff7fd-115">A stack overflow has occurred.</span></span>|  
|`FAIL_AccessViolation`|<span data-ttu-id="ff7fd-116">Предпринята попытка чтения или записи в защищенную память.</span><span class="sxs-lookup"><span data-stu-id="ff7fd-116">An attempt was made to read or write protected memory.</span></span> <span data-ttu-id="ff7fd-117">Не поддерживается в платформа .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="ff7fd-117">Not supported in the .NET Framework 4.</span></span>|  
|`FAIL_CodeContract`|<span data-ttu-id="ff7fd-118">Ошибка контракта кода.</span><span class="sxs-lookup"><span data-stu-id="ff7fd-118">A code contract failure occurred.</span></span> <span data-ttu-id="ff7fd-119">См. раздел [контракты кода](../../debug-trace-profile/code-contracts.md).</span><span class="sxs-lookup"><span data-stu-id="ff7fd-119">See [Code Contracts](../../debug-trace-profile/code-contracts.md).</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ff7fd-120">Remarks</span><span class="sxs-lookup"><span data-stu-id="ff7fd-120">Remarks</span></span>  

 <span data-ttu-id="ff7fd-121">Список значений [еполициактион](epolicyaction-enumeration.md) , которые узел может использовать для указания действий политики для условий сбоя, см. в описании метода [ICLRPolicyManager:: сетактиононфаилуре](iclrpolicymanager-setactiononfailure-method.md) .</span><span class="sxs-lookup"><span data-stu-id="ff7fd-121">See the [ICLRPolicyManager::SetActionOnFailure](iclrpolicymanager-setactiononfailure-method.md) method for a list of [EPolicyAction](epolicyaction-enumeration.md) values the host can use to specify the policy actions for failure conditions.</span></span> <span data-ttu-id="ff7fd-122">Дополнительные сведения о критических и некритических областях кода см. в разделе [еклроператион](eclroperation-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="ff7fd-122">For more information about critical and non-critical regions of code, see [EClrOperation](eclroperation-enumeration.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff7fd-123">Требования</span><span class="sxs-lookup"><span data-stu-id="ff7fd-123">Requirements</span></span>  

 <span data-ttu-id="ff7fd-124">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ff7fd-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff7fd-125">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ff7fd-125">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ff7fd-126">**Библиотека:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ff7fd-126">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ff7fd-127">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff7fd-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff7fd-128">См. также</span><span class="sxs-lookup"><span data-stu-id="ff7fd-128">See also</span></span>

- [<span data-ttu-id="ff7fd-129">Интерфейс ICLRPolicyManager</span><span class="sxs-lookup"><span data-stu-id="ff7fd-129">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="ff7fd-130">Метод SetActionOnFailure</span><span class="sxs-lookup"><span data-stu-id="ff7fd-130">SetActionOnFailure Method</span></span>](iclrpolicymanager-setactiononfailure-method.md)
- [<span data-ttu-id="ff7fd-131">Интерфейс IHostPolicyManager</span><span class="sxs-lookup"><span data-stu-id="ff7fd-131">IHostPolicyManager Interface</span></span>](ihostpolicymanager-interface.md)
- [<span data-ttu-id="ff7fd-132">Размещение перечислений</span><span class="sxs-lookup"><span data-stu-id="ff7fd-132">Hosting Enumerations</span></span>](hosting-enumerations.md)
