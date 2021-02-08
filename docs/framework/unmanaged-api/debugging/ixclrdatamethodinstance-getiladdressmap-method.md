---
description: 'Дополнительные сведения о методе: Иксклрдатамесодинстанце:: Жетиладдрессмап'
title: 'Метод Иксклрдатамесодинстанце:: Жетиладдрессмап'
ms.date: 01/16/2019
api.name:
- IXCLRDataMethodInstance::GetILAddressMap Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodInstance::GetILAddressMap Method
helpviewer.keywords:
- IXCLRDataMethodInstance::GetILAddressMap Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: ddddf593c3c18f2b4cd1682b5d6f7c8ff1985ac6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800816"
---
# <a name="ixclrdatamethodinstancegetiladdressmap-method"></a><span data-ttu-id="1c3ea-103">Метод Иксклрдатамесодинстанце:: Жетиладдрессмап</span><span class="sxs-lookup"><span data-stu-id="1c3ea-103">IXCLRDataMethodInstance::GetILAddressMap Method</span></span>

<span data-ttu-id="1c3ea-104">Возвращает IL для сопоставления сведений о сопоставлении.</span><span class="sxs-lookup"><span data-stu-id="1c3ea-104">Gets the IL to address mapping information.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="1c3ea-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="1c3ea-105">Syntax</span></span>

```cpp
HRESULT GetILAddressMap(
    [in] ULONG32                                   mapLen,
    [out] ULONG32                                 *mapNeeded,
    [out, size_is(mapLen)] CLRDATA_IL_ADDRESS_MAP  maps[]
);
```

## <a name="parameters"></a><span data-ttu-id="1c3ea-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="1c3ea-106">Parameters</span></span>

`mapLen`\
<span data-ttu-id="1c3ea-107">окне Длина указанного массива сопоставлений.</span><span class="sxs-lookup"><span data-stu-id="1c3ea-107">[in] The length of the provided maps array.</span></span>

`mapNeeded`\
<span data-ttu-id="1c3ea-108">заполняет Количество записей карт, необходимых методу.</span><span class="sxs-lookup"><span data-stu-id="1c3ea-108">[out] The number of map entries that the method needs.</span></span>

`maps`\
<span data-ttu-id="1c3ea-109">[out, size_is (Маплен)] Массив для хранения записей сопоставлений.</span><span class="sxs-lookup"><span data-stu-id="1c3ea-109">[out, size_is(mapLen)] The array for storing the map entries.</span></span>

## <a name="remarks"></a><span data-ttu-id="1c3ea-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="1c3ea-110">Remarks</span></span>

<span data-ttu-id="1c3ea-111">Предоставленный метод является частью `IXCLRDataMethodInstance` интерфейса и соответствует 15-слоту таблицы виртуального метода.</span><span class="sxs-lookup"><span data-stu-id="1c3ea-111">The provided method is part of the `IXCLRDataMethodInstance` interface and corresponds to the 15th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="1c3ea-112">Требования</span><span class="sxs-lookup"><span data-stu-id="1c3ea-112">Requirements</span></span>

<span data-ttu-id="1c3ea-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1c3ea-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="1c3ea-114">**Заголовок:** None</span><span class="sxs-lookup"><span data-stu-id="1c3ea-114">**Header:** None</span></span>  
<span data-ttu-id="1c3ea-115">**Библиотека:** None</span><span class="sxs-lookup"><span data-stu-id="1c3ea-115">**Library:** None</span></span>  
<span data-ttu-id="1c3ea-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="1c3ea-116">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="1c3ea-117">См. также</span><span class="sxs-lookup"><span data-stu-id="1c3ea-117">See also</span></span>

- [<span data-ttu-id="1c3ea-118">Отладка</span><span class="sxs-lookup"><span data-stu-id="1c3ea-118">Debugging</span></span>](index.md)
- [<span data-ttu-id="1c3ea-119">Интерфейс IXCLRDataMethodInstance</span><span class="sxs-lookup"><span data-stu-id="1c3ea-119">IXCLRDataMethodInstance Interface</span></span>](ixclrdatamethodinstance-interface.md)
