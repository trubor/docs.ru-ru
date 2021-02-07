---
description: 'Дополнительные сведения о: интерфейс Iclrerrorreportingmanagergetbucketparametersforcurrentexception'
title: Интерфейс ICLRErrorReportingManager
ms.date: 03/30/2017
api_name:
- ICLRErrorReportingManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRErrorReportingManager
helpviewer_keywords:
- ICLRErrorReportingManager interface [.NET Framework hosting]
ms.assetid: ea8af0d5-4133-4472-8a1f-50570d7e85fa
topic_type:
- apiref
ms.openlocfilehash: 094fe52858983fd0e1e5826e823932cb150b6087
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99689278"
---
# <a name="iclrerrorreportingmanager-interface"></a><span data-ttu-id="6917a-103">Интерфейс ICLRErrorReportingManager</span><span class="sxs-lookup"><span data-stu-id="6917a-103">ICLRErrorReportingManager Interface</span></span>

<span data-ttu-id="6917a-104">Предоставляет методы, позволяющие основному приложению настраивать пользовательские дампы стека для отчетов об ошибках.</span><span class="sxs-lookup"><span data-stu-id="6917a-104">Provides methods that allow the host to configure custom stack dumps for error reporting.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6917a-105">Методы</span><span class="sxs-lookup"><span data-stu-id="6917a-105">Methods</span></span>  
  
|<span data-ttu-id="6917a-106">Метод</span><span class="sxs-lookup"><span data-stu-id="6917a-106">Method</span></span>|<span data-ttu-id="6917a-107">Описание</span><span class="sxs-lookup"><span data-stu-id="6917a-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6917a-108">Метод BeginCustomDump</span><span class="sxs-lookup"><span data-stu-id="6917a-108">BeginCustomDump Method</span></span>](iclrerrorreportingmanager-begincustomdump-method.md)|<span data-ttu-id="6917a-109">Задает конфигурацию пользовательских дампов стека для отчетов об ошибках.</span><span class="sxs-lookup"><span data-stu-id="6917a-109">Specifies the configuration of custom stack dumps for error reporting.</span></span>|  
|[<span data-ttu-id="6917a-110">Метод EndCustomDump</span><span class="sxs-lookup"><span data-stu-id="6917a-110">EndCustomDump Method</span></span>](iclrerrorreportingmanager-endcustomdump-method.md)|<span data-ttu-id="6917a-111">Очищает конфигурацию пользовательского дампа стека, которая была задана предыдущим вызовом метода `BeginCustomDump` .</span><span class="sxs-lookup"><span data-stu-id="6917a-111">Clears the custom stack dump configuration that was set by an earlier call to `BeginCustomDump`.</span></span>|  
|[<span data-ttu-id="6917a-112">Метод GetBucketParametersForCurrentException</span><span class="sxs-lookup"><span data-stu-id="6917a-112">GetBucketParametersForCurrentException Method</span></span>](iclrerrorreportingmanager-getbucketparametersforcurrentexception-method.md)|<span data-ttu-id="6917a-113">Возвращает контейнер Watson для текущего исключения в вызывающем потоке.</span><span class="sxs-lookup"><span data-stu-id="6917a-113">Gets the Watson bucket for the current exception on the calling thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6917a-114">Remarks</span><span class="sxs-lookup"><span data-stu-id="6917a-114">Remarks</span></span>  

 <span data-ttu-id="6917a-115">`BeginCustomDump`Метод задает конфигурацию пользовательского дампа стека.</span><span class="sxs-lookup"><span data-stu-id="6917a-115">The `BeginCustomDump` method sets custom stack dump configuration.</span></span> <span data-ttu-id="6917a-116">`EndCustomDump`Метод очищает конфигурацию дампа пользовательского стека и освобождает любое связанное состояние.</span><span class="sxs-lookup"><span data-stu-id="6917a-116">The `EndCustomDump` method clears the custom stack dump configuration and frees any associated state.</span></span> <span data-ttu-id="6917a-117">Он должен вызываться после завершения пользовательского дампа.</span><span class="sxs-lookup"><span data-stu-id="6917a-117">It should be called after the custom dump is complete.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="6917a-118">Сбой вызова `EndCustomDump` приводит к утечке памяти.</span><span class="sxs-lookup"><span data-stu-id="6917a-118">Failure to call `EndCustomDump` causes memory to leak.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6917a-119">Требования</span><span class="sxs-lookup"><span data-stu-id="6917a-119">Requirements</span></span>  

 <span data-ttu-id="6917a-120">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6917a-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6917a-121">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="6917a-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6917a-122">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6917a-122">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="6917a-123">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6917a-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6917a-124">См. также</span><span class="sxs-lookup"><span data-stu-id="6917a-124">See also</span></span>

- [<span data-ttu-id="6917a-125">Перечисление ECustomDumpItemKind</span><span class="sxs-lookup"><span data-stu-id="6917a-125">ECustomDumpItemKind Enumeration</span></span>](ecustomdumpitemkind-enumeration.md)
- [<span data-ttu-id="6917a-126">Интерфейсы размещения</span><span class="sxs-lookup"><span data-stu-id="6917a-126">Hosting Interfaces</span></span>](hosting-interfaces.md)
