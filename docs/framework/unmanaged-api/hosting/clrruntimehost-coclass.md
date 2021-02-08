---
description: 'Подробнее о: Клррунтимехост coclass'
title: Кокласс CLRRuntimeHost
ms.date: 03/30/2017
api_name:
- CLRRuntimeHost Coclass
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CLRRuntimeHost
helpviewer_keywords:
- CLRRuntimeHost coclass [.NET Framework hosting]
ms.assetid: 2ac9cbf5-8a2d-4e4f-8831-0dad8ef0a897
topic_type:
- apiref
ms.openlocfilehash: a371b9b7263f8bb58b5c513de6647320f000beed
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99799893"
---
# <a name="clrruntimehost-coclass"></a><span data-ttu-id="c0344-103">Кокласс CLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="c0344-103">CLRRuntimeHost Coclass</span></span>

<span data-ttu-id="c0344-104">Предоставляет интерфейсы для управления выполнением кода средой выполнения.</span><span class="sxs-lookup"><span data-stu-id="c0344-104">Provides interfaces for managing code execution by the runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0344-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c0344-105">Syntax</span></span>  
  
```cpp  
coclass CLRRuntimeHost {  
    [default] interface  ICLRRuntimeHost;  
    interface            ICLRValidator;  
};  
```  
  
## <a name="interfaces"></a><span data-ttu-id="c0344-106">Интерфейсы</span><span class="sxs-lookup"><span data-stu-id="c0344-106">Interfaces</span></span>  
  
|<span data-ttu-id="c0344-107">Интерфейс</span><span class="sxs-lookup"><span data-stu-id="c0344-107">Interface</span></span>|<span data-ttu-id="c0344-108">Описание</span><span class="sxs-lookup"><span data-stu-id="c0344-108">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="c0344-109">Интерфейс ICLRRuntimeHost</span><span class="sxs-lookup"><span data-stu-id="c0344-109">ICLRRuntimeHost Interface</span></span>](iclrruntimehost-interface.md)|<span data-ttu-id="c0344-110">Предоставляет методы для управления выполнением приложений средой выполнения.</span><span class="sxs-lookup"><span data-stu-id="c0344-110">Provides methods for controlling the execution of applications by the runtime.</span></span>|  
|[<span data-ttu-id="c0344-111">Интерфейс ICLRValidator</span><span class="sxs-lookup"><span data-stu-id="c0344-111">ICLRValidator Interface</span></span>](iclrvalidator-interface.md)|<span data-ttu-id="c0344-112">Предоставляет методы для проверки переносимых исполняемых образов и для подробных отчетов об ошибках проверки.</span><span class="sxs-lookup"><span data-stu-id="c0344-112">Provides methods for validation of portable executable images and for detailed reporting of validation errors.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="c0344-113">Требования</span><span class="sxs-lookup"><span data-stu-id="c0344-113">Requirements</span></span>  

 <span data-ttu-id="c0344-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c0344-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0344-115">**Заголовок:** MSCorEE. idl</span><span class="sxs-lookup"><span data-stu-id="c0344-115">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="c0344-116">**Библиотека:** Включается в качестве ресурса в MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="c0344-116">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="c0344-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c0344-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0344-118">См. также</span><span class="sxs-lookup"><span data-stu-id="c0344-118">See also</span></span>

- [<span data-ttu-id="c0344-119">Размещение коклассов</span><span class="sxs-lookup"><span data-stu-id="c0344-119">Hosting Coclasses</span></span>](hosting-coclasses.md)
