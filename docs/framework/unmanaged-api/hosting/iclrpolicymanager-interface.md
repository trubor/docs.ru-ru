---
description: 'Дополнительные сведения о: интерфейс ICLRPolicyManager'
title: Интерфейс ICLRPolicyManager
ms.date: 03/30/2017
api_name:
- ICLRPolicyManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRPolicyManager
helpviewer_keywords:
- ICLRPolicyManager interface [.NET Framework hosting]
ms.assetid: 5c834aa1-f2db-408a-b230-c7bec093d364
topic_type:
- apiref
ms.openlocfilehash: 8823f1db8b15b327306ff3c592b46c94537f4331
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99637382"
---
# <a name="iclrpolicymanager-interface"></a><span data-ttu-id="7fd73-103">Интерфейс ICLRPolicyManager</span><span class="sxs-lookup"><span data-stu-id="7fd73-103">ICLRPolicyManager Interface</span></span>

<span data-ttu-id="7fd73-104">Предоставляет методы, позволяющие основному приложению указывать действия политики, выполняемые в случае сбоев и истечения времени ожидания.</span><span class="sxs-lookup"><span data-stu-id="7fd73-104">Provides methods that allow the host to specify policy actions to be taken in the event of failures and timeouts.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7fd73-105">Методы</span><span class="sxs-lookup"><span data-stu-id="7fd73-105">Methods</span></span>  
  
|<span data-ttu-id="7fd73-106">Метод</span><span class="sxs-lookup"><span data-stu-id="7fd73-106">Method</span></span>|<span data-ttu-id="7fd73-107">Описание</span><span class="sxs-lookup"><span data-stu-id="7fd73-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7fd73-108">Метод SetActionOnFailure</span><span class="sxs-lookup"><span data-stu-id="7fd73-108">SetActionOnFailure Method</span></span>](iclrpolicymanager-setactiononfailure-method.md)|<span data-ttu-id="7fd73-109">Указывает действие политики, которое должна выполнять среда CLR при возникновении указанного сбоя.</span><span class="sxs-lookup"><span data-stu-id="7fd73-109">Specifies the policy action the common language runtime (CLR) should take when the specified failure occurs.</span></span>|  
|[<span data-ttu-id="7fd73-110">Метод SetActionOnTimeout</span><span class="sxs-lookup"><span data-stu-id="7fd73-110">SetActionOnTimeout Method</span></span>](iclrpolicymanager-setactionontimeout-method.md)|<span data-ttu-id="7fd73-111">Указывает действие политики, которое должна выполнять среда CLR при истечении времени ожидания указанной операции.</span><span class="sxs-lookup"><span data-stu-id="7fd73-111">Specifies the policy action the CLR should take when the specified operation times out.</span></span>|  
|[<span data-ttu-id="7fd73-112">Метод SetDefaultAction</span><span class="sxs-lookup"><span data-stu-id="7fd73-112">SetDefaultAction Method</span></span>](iclrpolicymanager-setdefaultaction-method.md)|<span data-ttu-id="7fd73-113">Указывает действие политики, которое должна выполнять среда CLR при выполнении указанной операции.</span><span class="sxs-lookup"><span data-stu-id="7fd73-113">Specifies the policy action the CLR should take when the specified operation occurs.</span></span>|  
|[<span data-ttu-id="7fd73-114">Метод SetTimeout</span><span class="sxs-lookup"><span data-stu-id="7fd73-114">SetTimeout Method</span></span>](iclrpolicymanager-settimeout-method.md)|<span data-ttu-id="7fd73-115">Задает значение времени ожидания для указанной операции.</span><span class="sxs-lookup"><span data-stu-id="7fd73-115">Sets a timeout value for the specified operation.</span></span>|  
|[<span data-ttu-id="7fd73-116">Метод SetTimeoutAndAction</span><span class="sxs-lookup"><span data-stu-id="7fd73-116">SetTimeoutAndAction Method</span></span>](iclrpolicymanager-settimeoutandaction-method.md)|<span data-ttu-id="7fd73-117">Задает значение времени ожидания для указанной операции и указывает действие политики, которое должна выполнять среда CLR при выполнении операции.</span><span class="sxs-lookup"><span data-stu-id="7fd73-117">Sets a timeout value for the specified operation, and specifies the policy action the CLR should take when the operation occurs.</span></span>|  
|[<span data-ttu-id="7fd73-118">Метод SetUnhandledExceptionPolicy</span><span class="sxs-lookup"><span data-stu-id="7fd73-118">SetUnhandledExceptionPolicy Method</span></span>](iclrpolicymanager-setunhandledexceptionpolicy-method.md)|<span data-ttu-id="7fd73-119">Задает поведение среды CLR при возникновении необработанного исключения.</span><span class="sxs-lookup"><span data-stu-id="7fd73-119">Specifies the behavior of the CLR when an unhandled exception occurs.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7fd73-120">Требования</span><span class="sxs-lookup"><span data-stu-id="7fd73-120">Requirements</span></span>  

 <span data-ttu-id="7fd73-121">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7fd73-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7fd73-122">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="7fd73-122">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7fd73-123">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7fd73-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7fd73-124">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7fd73-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fd73-125">См. также</span><span class="sxs-lookup"><span data-stu-id="7fd73-125">See also</span></span>

- [<span data-ttu-id="7fd73-126">Перечисление EClrFailure</span><span class="sxs-lookup"><span data-stu-id="7fd73-126">EClrFailure Enumeration</span></span>](eclrfailure-enumeration.md)
- [<span data-ttu-id="7fd73-127">Перечисление EClrOperation</span><span class="sxs-lookup"><span data-stu-id="7fd73-127">EClrOperation Enumeration</span></span>](eclroperation-enumeration.md)
- [<span data-ttu-id="7fd73-128">Перечисление EPolicyAction</span><span class="sxs-lookup"><span data-stu-id="7fd73-128">EPolicyAction Enumeration</span></span>](epolicyaction-enumeration.md)
- [<span data-ttu-id="7fd73-129">Интерфейс ICLRControl</span><span class="sxs-lookup"><span data-stu-id="7fd73-129">ICLRControl Interface</span></span>](iclrcontrol-interface.md)
