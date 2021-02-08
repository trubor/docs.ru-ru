---
description: 'Дополнительные сведения о: интерфейс Иксклрдатамесодинстанце'
title: Интерфейс IXCLRDataMethodInstance
ms.date: 02/01/2019
api.name:
- IXCLRDataMethodInstance Interface
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodInstance Interface
helpviewer.keywords:
- IXCLRDataMethodInstance Interface [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 4e9ad57988420ff14b297c693c31c0dc5b3b181c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800790"
---
# <a name="ixclrdatamethodinstance-interface"></a><span data-ttu-id="6a143-103">Интерфейс IXCLRDataMethodInstance</span><span class="sxs-lookup"><span data-stu-id="6a143-103">IXCLRDataMethodInstance Interface</span></span>

<span data-ttu-id="6a143-104">Предоставляет методы для запроса сведений об экземпляре метода.</span><span class="sxs-lookup"><span data-stu-id="6a143-104">Provides methods for querying information about a method instance.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="methods"></a><span data-ttu-id="6a143-105">Методы</span><span class="sxs-lookup"><span data-stu-id="6a143-105">Methods</span></span>

| <span data-ttu-id="6a143-106">Метод</span><span class="sxs-lookup"><span data-stu-id="6a143-106">Method</span></span>                                                                                                                  | <span data-ttu-id="6a143-107">Описание</span><span class="sxs-lookup"><span data-stu-id="6a143-107">Description</span></span>                                 |
| ----------------------------------------------------------------------------------------------------------------------- | ------------------------------------------- |
| [<span data-ttu-id="6a143-108">GetILAddressMap</span><span class="sxs-lookup"><span data-stu-id="6a143-108">GetILAddressMap</span></span>](ixclrdatamethodinstance-getiladdressmap-method.md) | <span data-ttu-id="6a143-109">Возвращает IL для сопоставления сведений о сопоставлении.</span><span class="sxs-lookup"><span data-stu-id="6a143-109">Gets the IL to address mapping information.</span></span> |
| [<span data-ttu-id="6a143-110">GetRepresentativeEntryAddress</span><span class="sxs-lookup"><span data-stu-id="6a143-110">GetRepresentativeEntryAddress</span></span>](ixclrdatamethodinstance-getrepresentativeentryaddress-method.md) | <span data-ttu-id="6a143-111">Возвращает наиболее репрезентативный адрес точки входа для собственной компиляции всех возможных точек входа для метода.</span><span class="sxs-lookup"><span data-stu-id="6a143-111">Gets the most representative entry point address for the native compilation of all the possible entry points for a method.</span></span> |

## <a name="remarks"></a><span data-ttu-id="6a143-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="6a143-112">Remarks</span></span>

<span data-ttu-id="6a143-113">Этот интерфейс находится внутри среды выполнения и не предоставляется через все файлы заголовков или библиотек.</span><span class="sxs-lookup"><span data-stu-id="6a143-113">This interface lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="6a143-114">Однако это COM-интерфейс, производный от `IUnknown` GUID `ECD73800-22CA-4b0d-AB55-E9BA7E6318A5` , который можно получить с помощью стандартных механизмов com.</span><span class="sxs-lookup"><span data-stu-id="6a143-114">However, it's a COM interface that derives from `IUnknown` with GUID `ECD73800-22CA-4b0d-AB55-E9BA7E6318A5` that can be obtained through the usual COM mechanisms.</span></span>

## <a name="requirements"></a><span data-ttu-id="6a143-115">Требования</span><span class="sxs-lookup"><span data-stu-id="6a143-115">Requirements</span></span>

<span data-ttu-id="6a143-116">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6a143-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="6a143-117">**Заголовок:** None</span><span class="sxs-lookup"><span data-stu-id="6a143-117">**Header:** None</span></span>  
<span data-ttu-id="6a143-118">**Библиотека:** None</span><span class="sxs-lookup"><span data-stu-id="6a143-118">**Library:** None</span></span>  
<span data-ttu-id="6a143-119">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="6a143-119">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="6a143-120">См. также</span><span class="sxs-lookup"><span data-stu-id="6a143-120">See also</span></span>

- [<span data-ttu-id="6a143-121">Отладка</span><span class="sxs-lookup"><span data-stu-id="6a143-121">Debugging</span></span>](index.md)
- [<span data-ttu-id="6a143-122">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="6a143-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
