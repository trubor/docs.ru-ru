---
description: 'Дополнительные сведения о: интерфейс IMethodMalloc'
title: Интерфейс IMethodMalloc
ms.date: 03/30/2017
api_name:
- IMethodMalloc
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- IMethodMalloc
helpviewer_keywords:
- IMethodMalloc interface [.NET Framework profiling]
ms.assetid: 8c8ab5dc-557c-473a-82f2-6e403eca7dac
topic_type:
- apiref
ms.openlocfilehash: 6b84ac0ddb49718d24b2cad174613bc311dc509b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99736964"
---
# <a name="imethodmalloc-interface"></a><span data-ttu-id="07ae3-103">Интерфейс IMethodMalloc</span><span class="sxs-lookup"><span data-stu-id="07ae3-103">IMethodMalloc Interface</span></span>

<span data-ttu-id="07ae3-104">Предоставляет метод для выделения памяти для нового текста функции MSIL.</span><span class="sxs-lookup"><span data-stu-id="07ae3-104">Provides a method to allocate memory for a new Microsoft intermediate language (MSIL) function body.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="07ae3-105">`IMethodMalloc`Интерфейс — это простой механизм выделения памяти.</span><span class="sxs-lookup"><span data-stu-id="07ae3-105">The `IMethodMalloc` interface is a simple memory allocator.</span></span> <span data-ttu-id="07ae3-106">Она позволяет выделить память, но не освобождает ее.</span><span class="sxs-lookup"><span data-stu-id="07ae3-106">It allows you to allocate memory, but not to free it.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="07ae3-107">Методы</span><span class="sxs-lookup"><span data-stu-id="07ae3-107">Methods</span></span>  
  
|<span data-ttu-id="07ae3-108">Метод</span><span class="sxs-lookup"><span data-stu-id="07ae3-108">Method</span></span>|<span data-ttu-id="07ae3-109">Описание</span><span class="sxs-lookup"><span data-stu-id="07ae3-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="07ae3-110">Метод Alloc</span><span class="sxs-lookup"><span data-stu-id="07ae3-110">Alloc Method</span></span>](imethodmalloc-alloc-method.md)|<span data-ttu-id="07ae3-111">Пытается выделить указанный объем памяти для нового текста функции MSIL.</span><span class="sxs-lookup"><span data-stu-id="07ae3-111">Attempts to allocate a specified amount of memory for a new MSIL function body.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="07ae3-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="07ae3-112">Remarks</span></span>  

 <span data-ttu-id="07ae3-113">Каждый распределитель зависит от конкретного модуля и гарантирует, что текст функции будет иметь положительное смещение от базового модуля.</span><span class="sxs-lookup"><span data-stu-id="07ae3-113">Each allocator is module-specific and ensures that the function body will be at a positive offset from the base of the module.</span></span> <span data-ttu-id="07ae3-114">Память над базовым модулем может быть ценной, поэтому распределитель должен использоваться для выделения памяти только для тела функции.</span><span class="sxs-lookup"><span data-stu-id="07ae3-114">Memory above the base of a module can be precious, so the allocator should be used to allocate memory only for a function body.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="07ae3-115">Требования</span><span class="sxs-lookup"><span data-stu-id="07ae3-115">Requirements</span></span>  

 <span data-ttu-id="07ae3-116">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="07ae3-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07ae3-117">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="07ae3-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="07ae3-118">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="07ae3-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="07ae3-119">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="07ae3-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07ae3-120">См. также</span><span class="sxs-lookup"><span data-stu-id="07ae3-120">See also</span></span>

- [<span data-ttu-id="07ae3-121">Профилирующие интерфейсы</span><span class="sxs-lookup"><span data-stu-id="07ae3-121">Profiling Interfaces</span></span>](profiling-interfaces.md)
