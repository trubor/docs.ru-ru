---
description: 'Дополнительные сведения о: интерфейс Иксклрдатапроцесс'
title: Интерфейс IXCLRDataProcess
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess Interface
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess Interface
helpviewer.keywords:
- IXCLRDataProcess Interface [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: b611491e5c9a5957c07a305a3f395b67ad208649
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800647"
---
# <a name="ixclrdataprocess-interface"></a><span data-ttu-id="eb070-103">Интерфейс IXCLRDataProcess</span><span class="sxs-lookup"><span data-stu-id="eb070-103">IXCLRDataProcess Interface</span></span>

<span data-ttu-id="eb070-104">Предоставляет методы для запроса сведений о процессе.</span><span class="sxs-lookup"><span data-stu-id="eb070-104">Provides methods for querying information about a process.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="eb070-105">Методы</span><span class="sxs-lookup"><span data-stu-id="eb070-105">Methods</span></span>

| <span data-ttu-id="eb070-106">Метод</span><span class="sxs-lookup"><span data-stu-id="eb070-106">Method</span></span>                                                                                                                                               | <span data-ttu-id="eb070-107">Описание</span><span class="sxs-lookup"><span data-stu-id="eb070-107">Description</span></span>                                                                                     |
| ---------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------- |
| [<span data-ttu-id="eb070-108">GetRuntimeNameByAddress</span><span class="sxs-lookup"><span data-stu-id="eb070-108">GetRuntimeNameByAddress</span></span>](ixclrdataprocess-getruntimenamebyaddress-method.md)                     | <span data-ttu-id="eb070-109">Возвращает имя для заданного адреса.</span><span class="sxs-lookup"><span data-stu-id="eb070-109">Gets a name for the given address.</span></span>                                                               |
| [<span data-ttu-id="eb070-110">GetAppDomainByUniqueId</span><span class="sxs-lookup"><span data-stu-id="eb070-110">GetAppDomainByUniqueId</span></span>](ixclrdataprocess-getappdomainbyuniqueid-method.md)                       | <span data-ttu-id="eb070-111">Возвращает `AppDomain` в процессе по его уникальному идентификатору.</span><span class="sxs-lookup"><span data-stu-id="eb070-111">Gets an `AppDomain` in a process by its unique id.</span></span>                                              |
| [<span data-ttu-id="eb070-112">StartEnumModules</span><span class="sxs-lookup"><span data-stu-id="eb070-112">StartEnumModules</span></span>](ixclrdataprocess-startenummodules-method.md)                                   | <span data-ttu-id="eb070-113">Предоставляет описатель для перечисления модулей процесса.</span><span class="sxs-lookup"><span data-stu-id="eb070-113">Provides a handle to enumerate the modules of a process.</span></span>                                        |
| [<span data-ttu-id="eb070-114">EnumModule</span><span class="sxs-lookup"><span data-stu-id="eb070-114">EnumModule</span></span>](ixclrdataprocess-enummodule-method.md)                                               | <span data-ttu-id="eb070-115">Перечисляет модули этого процесса.</span><span class="sxs-lookup"><span data-stu-id="eb070-115">Enumerates the modules of this process.</span></span>                                                         |
| [<span data-ttu-id="eb070-116">EndEnumModules</span><span class="sxs-lookup"><span data-stu-id="eb070-116">EndEnumModules</span></span>](ixclrdataprocess-endenummodules-method.md)                                       | <span data-ttu-id="eb070-117">Освобождает ресурсы, используемые внутренними итераторами, используемыми при перечислении модулей.</span><span class="sxs-lookup"><span data-stu-id="eb070-117">Releases the resources used by internal iterators used during module enumeration.</span></span>               |
| [<span data-ttu-id="eb070-118">StartEnumMethodInstancesByAddress</span><span class="sxs-lookup"><span data-stu-id="eb070-118">StartEnumMethodInstancesByAddress</span></span>](ixclrdataprocess-startenummethodinstancesbyaddress-method.md) | <span data-ttu-id="eb070-119">Предоставляет описатель для перечисления экземпляров методов, `AppDomain` начиная с заданного адреса.</span><span class="sxs-lookup"><span data-stu-id="eb070-119">Provides a handle to enumerate the method instances of `AppDomain` starting at a given address.</span></span> |
| [<span data-ttu-id="eb070-120">EnumMethodInstanceByAddress</span><span class="sxs-lookup"><span data-stu-id="eb070-120">EnumMethodInstanceByAddress</span></span>](ixclrdataprocess-enummethodinstancebyaddress-method.md)             | <span data-ttu-id="eb070-121">Перечисляет экземпляры методов этого процесса, начиная с смещения адреса.</span><span class="sxs-lookup"><span data-stu-id="eb070-121">Enumerates the method instances of this process starting at an address offset.</span></span>                  |
| [<span data-ttu-id="eb070-122">EndEnumMethodInstancesByAddress</span><span class="sxs-lookup"><span data-stu-id="eb070-122">EndEnumMethodInstancesByAddress</span></span>](ixclrdataprocess-endenummethodinstancesbyaddress-method.md)     | <span data-ttu-id="eb070-123">Освобождает ресурсы, используемые внутренними итераторами, используемыми при перечислении экземпляров.</span><span class="sxs-lookup"><span data-stu-id="eb070-123">Releases the resources used by internal iterators used during instance enumeration.</span></span>             |

## <a name="remarks"></a><span data-ttu-id="eb070-124">Remarks</span><span class="sxs-lookup"><span data-stu-id="eb070-124">Remarks</span></span>

<span data-ttu-id="eb070-125">Этот интерфейс находится внутри среды выполнения и не предоставляется через все файлы заголовков или библиотек.</span><span class="sxs-lookup"><span data-stu-id="eb070-125">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="eb070-126">Однако это COM-интерфейс, производный от `IUnknown` GUID `5c552ab6-fc09-4cb3-8e36-22fa03c798b7` , который можно получить с помощью стандартных механизмов com.</span><span class="sxs-lookup"><span data-stu-id="eb070-126">However, it's a COM interface that derives from `IUnknown` with GUID `5c552ab6-fc09-4cb3-8e36-22fa03c798b7` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="eb070-127">Требования</span><span class="sxs-lookup"><span data-stu-id="eb070-127">Requirements</span></span>

<span data-ttu-id="eb070-128">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eb070-128">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>
<span data-ttu-id="eb070-129">**Заголовок:** None</span><span class="sxs-lookup"><span data-stu-id="eb070-129">**Header:** None</span></span>  
<span data-ttu-id="eb070-130">**Библиотека:** None</span><span class="sxs-lookup"><span data-stu-id="eb070-130">**Library:** None</span></span>  
<span data-ttu-id="eb070-131">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="eb070-131">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="eb070-132">См. также</span><span class="sxs-lookup"><span data-stu-id="eb070-132">See also</span></span>

- [<span data-ttu-id="eb070-133">Отладка</span><span class="sxs-lookup"><span data-stu-id="eb070-133">Debugging</span></span>](index.md)
- [<span data-ttu-id="eb070-134">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="eb070-134">Debugging Interfaces</span></span>](debugging-interfaces.md)
