---
description: Дополнительные сведения о перечислении Еклрунхандледексцептион
title: Перечисление EClrUnhandledException
ms.date: 03/30/2017
api_name:
- EClrUnhandledException
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- EClrUnhandledException
helpviewer_keywords:
- EClrUnhandledException enumeration [.NET Framework hosting]
ms.assetid: d231044e-2b53-4836-93f9-8117ff0e5c3a
topic_type:
- apiref
ms.openlocfilehash: 088d448a92c4d9030208537b9c788477c85f9d37
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99785553"
---
# <a name="eclrunhandledexception-enumeration"></a><span data-ttu-id="30ca6-103">Перечисление EClrUnhandledException</span><span class="sxs-lookup"><span data-stu-id="30ca6-103">EClrUnhandledException Enumeration</span></span>

<span data-ttu-id="30ca6-104">Описывает доступные параметры для управления исключениями, которые не обрабатываются в пользовательском коде.</span><span class="sxs-lookup"><span data-stu-id="30ca6-104">Describes the available options for managing exceptions that are unhandled in user code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30ca6-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="30ca6-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    eRuntimeDeterminedPolicy,  
    eHostDeterminedPolicy  
} EClrUnhandledException;  
```  
  
## <a name="members"></a><span data-ttu-id="30ca6-106">Члены</span><span class="sxs-lookup"><span data-stu-id="30ca6-106">Members</span></span>  
  
|<span data-ttu-id="30ca6-107">Член</span><span class="sxs-lookup"><span data-stu-id="30ca6-107">Member</span></span>|<span data-ttu-id="30ca6-108">Описание</span><span class="sxs-lookup"><span data-stu-id="30ca6-108">Description</span></span>|  
|------------|-----------------|  
|`eRuntimeDeterminedPolicy`|<span data-ttu-id="30ca6-109">Указывает, что происходит поведение по умолчанию.</span><span class="sxs-lookup"><span data-stu-id="30ca6-109">Specifies that the default behavior occurs.</span></span> <span data-ttu-id="30ca6-110">Процесс разорван.</span><span class="sxs-lookup"><span data-stu-id="30ca6-110">The process is torn down.</span></span>|  
|`eHostDeterminedPolicy`|<span data-ttu-id="30ca6-111">Указывает, что среда CLR не обрабатывает необработанные исключения и позволяет узлу определить дальнейшие действия.</span><span class="sxs-lookup"><span data-stu-id="30ca6-111">Specifies that the common language runtime (CLR) ignores unhandled exceptions and lets the host determine any further action.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="30ca6-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="30ca6-112">Remarks</span></span>  

 <span data-ttu-id="30ca6-113">Чтобы указать, что среда CLR работает как более ранние версии, используйте `eHostDeterminedPolicy` член.</span><span class="sxs-lookup"><span data-stu-id="30ca6-113">To specify that the CLR behave like earlier versions, use the `eHostDeterminedPolicy` member.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30ca6-114">Требования</span><span class="sxs-lookup"><span data-stu-id="30ca6-114">Requirements</span></span>  

 <span data-ttu-id="30ca6-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="30ca6-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30ca6-116">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="30ca6-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="30ca6-117">**Библиотека:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="30ca6-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="30ca6-118">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30ca6-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30ca6-119">См. также</span><span class="sxs-lookup"><span data-stu-id="30ca6-119">See also</span></span>

- [<span data-ttu-id="30ca6-120">Перечисление EClrFailure</span><span class="sxs-lookup"><span data-stu-id="30ca6-120">EClrFailure Enumeration</span></span>](eclrfailure-enumeration.md)
- [<span data-ttu-id="30ca6-121">Перечисление EClrOperation</span><span class="sxs-lookup"><span data-stu-id="30ca6-121">EClrOperation Enumeration</span></span>](eclroperation-enumeration.md)
- [<span data-ttu-id="30ca6-122">Интерфейс ICLRPolicyManager</span><span class="sxs-lookup"><span data-stu-id="30ca6-122">ICLRPolicyManager Interface</span></span>](iclrpolicymanager-interface.md)
- [<span data-ttu-id="30ca6-123">Метод SetUnhandledExceptionPolicy</span><span class="sxs-lookup"><span data-stu-id="30ca6-123">SetUnhandledExceptionPolicy Method</span></span>](iclrpolicymanager-setunhandledexceptionpolicy-method.md)
- [<span data-ttu-id="30ca6-124">Интерфейс IHostPolicyManager</span><span class="sxs-lookup"><span data-stu-id="30ca6-124">IHostPolicyManager Interface</span></span>](ihostpolicymanager-interface.md)
- [<span data-ttu-id="30ca6-125">Размещение перечислений</span><span class="sxs-lookup"><span data-stu-id="30ca6-125">Hosting Enumerations</span></span>](hosting-enumerations.md)
