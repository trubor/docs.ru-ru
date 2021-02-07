---
description: Дополнительные сведения о перечислении StackOverflowType
title: Перечисление StackOverflowType
ms.date: 03/30/2017
api_name:
- StackOverflowType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- StackOverflowType
helpviewer_keywords:
- StackOverflowType enumeration [.NET Framework hosting]
ms.assetid: dab648ad-972b-479c-b129-b4c1dcbd932e
topic_type:
- apiref
ms.openlocfilehash: d39ccd99331a3e839236f1ede21254edb92b2dfb
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99679363"
---
# <a name="stackoverflowtype-enumeration"></a><span data-ttu-id="534c5-103">Перечисление StackOverflowType</span><span class="sxs-lookup"><span data-stu-id="534c5-103">StackOverflowType Enumeration</span></span>

<span data-ttu-id="534c5-104">Содержит значения, указывающие основную причину события переполнения стека.</span><span class="sxs-lookup"><span data-stu-id="534c5-104">Contains values that indicate the underlying cause of a stack overflow event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="534c5-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="534c5-105">Syntax</span></span>  
  
```cpp  
typedef enum {  
    SO_Managed,  
    SO_ClrEngine,  
    SO_Other  
} StackOverflowType;  
```  
  
## <a name="members"></a><span data-ttu-id="534c5-106">Члены</span><span class="sxs-lookup"><span data-stu-id="534c5-106">Members</span></span>  
  
|<span data-ttu-id="534c5-107">Член</span><span class="sxs-lookup"><span data-stu-id="534c5-107">Member</span></span>|<span data-ttu-id="534c5-108">Описание</span><span class="sxs-lookup"><span data-stu-id="534c5-108">Description</span></span>|  
|------------|-----------------|  
|`SO_ClrEngine`|<span data-ttu-id="534c5-109">Переполнение стека было вызвано подсистемой выполнения.</span><span class="sxs-lookup"><span data-stu-id="534c5-109">The stack overflow was caused by the execution engine.</span></span>|  
|`SO_Managed`|<span data-ttu-id="534c5-110">Переполнение стека было вызвано управляемым кодом.</span><span class="sxs-lookup"><span data-stu-id="534c5-110">The stack overflow was caused by managed code.</span></span>|  
|`SO_Other`|<span data-ttu-id="534c5-111">Переполнение стека было вызвано неуправляемым кодом.</span><span class="sxs-lookup"><span data-stu-id="534c5-111">The stack overflow was caused by unmanaged code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="534c5-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="534c5-112">Remarks</span></span>  

 <span data-ttu-id="534c5-113">Эти сведения передаются на узел посредством вызова метода [иактиононклревент:: oneven](iactiononclrevent-onevent-method.md) .</span><span class="sxs-lookup"><span data-stu-id="534c5-113">This information is passed to the host through a call to the [IActionOnCLREvent::OnEvent](iactiononclrevent-onevent-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="534c5-114">Требования</span><span class="sxs-lookup"><span data-stu-id="534c5-114">Requirements</span></span>  

 <span data-ttu-id="534c5-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="534c5-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="534c5-116">**Заголовок:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="534c5-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="534c5-117">**Библиотека:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="534c5-117">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="534c5-118">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="534c5-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="534c5-119">См. также</span><span class="sxs-lookup"><span data-stu-id="534c5-119">See also</span></span>

- [<span data-ttu-id="534c5-120">Размещение перечислений</span><span class="sxs-lookup"><span data-stu-id="534c5-120">Hosting Enumerations</span></span>](hosting-enumerations.md)
