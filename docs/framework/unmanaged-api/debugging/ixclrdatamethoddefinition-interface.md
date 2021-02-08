---
description: 'Дополнительные сведения о: интерфейс Иксклрдатамесоддефинитион'
title: Интерфейс IXCLRDataMethodDefinition
ms.date: 01/16/2019
api.name:
- IXCLRDataMethodDefinition Interface
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodDefinition Interface
helpviewer.keywords:
- IXCLRDataMethodDefinition Interface [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: d73246b42a0bfb982c87b04d5490e945f7caa745
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790351"
---
# <a name="ixclrdatamethoddefinition-interface"></a><span data-ttu-id="1ad2b-103">Интерфейс IXCLRDataMethodDefinition</span><span class="sxs-lookup"><span data-stu-id="1ad2b-103">IXCLRDataMethodDefinition Interface</span></span>

<span data-ttu-id="1ad2b-104">Предоставляет методы для запроса сведений об определении метода.</span><span class="sxs-lookup"><span data-stu-id="1ad2b-104">Provides methods for querying information about a method definition.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="1ad2b-105">Методы</span><span class="sxs-lookup"><span data-stu-id="1ad2b-105">Methods</span></span>

<span data-ttu-id="1ad2b-106">Ниже перечислены методы, доступные в интерфейсе.</span><span class="sxs-lookup"><span data-stu-id="1ad2b-106">The following methods are some of the methods available in the interface.</span></span>

| <span data-ttu-id="1ad2b-107">Метод</span><span class="sxs-lookup"><span data-stu-id="1ad2b-107">Method</span></span>                                                                                                                          | <span data-ttu-id="1ad2b-108">Описание</span><span class="sxs-lookup"><span data-stu-id="1ad2b-108">Description</span></span>                                                                                 |
| ------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------- |
| [<span data-ttu-id="1ad2b-109">StartEnumInstances</span><span class="sxs-lookup"><span data-stu-id="1ad2b-109">StartEnumInstances</span></span>](ixclrdatamethoddefinition-startenuminstances-method.md) | <span data-ttu-id="1ad2b-110">Предоставляет обработчик для перечисления экземпляров методов для заданного объекта `IXCLRDataAppDomain` .</span><span class="sxs-lookup"><span data-stu-id="1ad2b-110">Provides a handle for the enumeration of method instances for a given `IXCLRDataAppDomain`.</span></span> |
| [<span data-ttu-id="1ad2b-111">EnumInstance</span><span class="sxs-lookup"><span data-stu-id="1ad2b-111">EnumInstance</span></span>](ixclrdatamethoddefinition-enuminstance-method.md)             | <span data-ttu-id="1ad2b-112">Перечисляет экземпляры этого определения метода.</span><span class="sxs-lookup"><span data-stu-id="1ad2b-112">Enumerates the instances of this method definition.</span></span>                                         |
| [<span data-ttu-id="1ad2b-113">EnumInstance</span><span class="sxs-lookup"><span data-stu-id="1ad2b-113">EndEnumInstances</span></span>](ixclrdatamethoddefinition-endenuminstances-method.md)     | <span data-ttu-id="1ad2b-114">Освобождает ресурсы, используемые внутренними итераторами, используемыми при перечислении экземпляров.</span><span class="sxs-lookup"><span data-stu-id="1ad2b-114">Releases the resources used by internal iterators used during instance enumeration.</span></span>         |

## <a name="remarks"></a><span data-ttu-id="1ad2b-115">Remarks</span><span class="sxs-lookup"><span data-stu-id="1ad2b-115">Remarks</span></span>

<span data-ttu-id="1ad2b-116">Этот интерфейс находится внутри среды выполнения и не предоставляется через все файлы заголовков или библиотек.</span><span class="sxs-lookup"><span data-stu-id="1ad2b-116">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="1ad2b-117">Однако это COM-интерфейс, производный от `IUnknown` GUID `AAF60008-FB2C-420b-8FB1-42D244A54A97` , который можно получить с помощью стандартных механизмов com.</span><span class="sxs-lookup"><span data-stu-id="1ad2b-117">However, it's a COM interface that derives from `IUnknown` with GUID `AAF60008-FB2C-420b-8FB1-42D244A54A97` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="1ad2b-118">Требования</span><span class="sxs-lookup"><span data-stu-id="1ad2b-118">Requirements</span></span>

<span data-ttu-id="1ad2b-119">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1ad2b-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="1ad2b-120">**Заголовок:** None</span><span class="sxs-lookup"><span data-stu-id="1ad2b-120">**Header:** None</span></span>  
<span data-ttu-id="1ad2b-121">**Библиотека:** None</span><span class="sxs-lookup"><span data-stu-id="1ad2b-121">**Library:** None</span></span>  
<span data-ttu-id="1ad2b-122">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="1ad2b-122">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="1ad2b-123">См. также</span><span class="sxs-lookup"><span data-stu-id="1ad2b-123">See also</span></span>

- [<span data-ttu-id="1ad2b-124">Отладка</span><span class="sxs-lookup"><span data-stu-id="1ad2b-124">Debugging</span></span>](index.md)
- [<span data-ttu-id="1ad2b-125">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="1ad2b-125">Debugging Interfaces</span></span>](debugging-interfaces.md)
