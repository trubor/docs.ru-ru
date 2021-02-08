---
description: 'Дополнительные сведения о методе: Иксклрдатапроцесс:: Енденуммесодинстанцесбяддресс'
title: 'Метод Иксклрдатапроцесс:: Енденуммесодинстанцесбяддресс'
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::EndEnumMethodInstancesByAddress Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::EndEnumMethodInstancesByAddress Method
helpviewer.keywords:
- IXCLRDataProcess::EndEnumMethodInstancesByAddress Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 2e01fe0737319a7b336d9f6992bf81b2c57f9e70
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800725"
---
# <a name="ixclrdataprocessendenummethodinstancesbyaddress-method"></a><span data-ttu-id="2d200-103">Метод Иксклрдатапроцесс:: Енденуммесодинстанцесбяддресс</span><span class="sxs-lookup"><span data-stu-id="2d200-103">IXCLRDataProcess::EndEnumMethodInstancesByAddress Method</span></span>

<span data-ttu-id="2d200-104">Освобождает ресурсы, используемые внутренними итераторами, используемыми при перечислении экземпляров.</span><span class="sxs-lookup"><span data-stu-id="2d200-104">Releases the resources used by internal iterators used during instance enumeration.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="2d200-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="2d200-105">Syntax</span></span>

```cpp
HRESULT EndEnumMethodInstancesByAddress(
    [in] CLRDATA_ENUM handle
);
```

## <a name="parameters"></a><span data-ttu-id="2d200-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="2d200-106">Parameters</span></span>

`handle`\
<span data-ttu-id="2d200-107">заполняет Описатель для перечисления экземпляров методов.</span><span class="sxs-lookup"><span data-stu-id="2d200-107">[out] A handle for enumerating the method instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="2d200-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="2d200-108">Remarks</span></span>

<span data-ttu-id="2d200-109">Предоставленный метод является частью `IXCLRDataProcess` интерфейса и соответствует 30-му слоту таблицы виртуального метода.</span><span class="sxs-lookup"><span data-stu-id="2d200-109">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 30th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="2d200-110">Требования</span><span class="sxs-lookup"><span data-stu-id="2d200-110">Requirements</span></span>

<span data-ttu-id="2d200-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2d200-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="2d200-112">**Заголовок:** None</span><span class="sxs-lookup"><span data-stu-id="2d200-112">**Header:** None</span></span>  
<span data-ttu-id="2d200-113">**Библиотека:** None</span><span class="sxs-lookup"><span data-stu-id="2d200-113">**Library:** None</span></span>  
<span data-ttu-id="2d200-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="2d200-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="2d200-115">См. также</span><span class="sxs-lookup"><span data-stu-id="2d200-115">See also</span></span>

- [<span data-ttu-id="2d200-116">Перечисление Клрдатасаурцетипе</span><span class="sxs-lookup"><span data-stu-id="2d200-116">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="2d200-117">Отладка</span><span class="sxs-lookup"><span data-stu-id="2d200-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="2d200-118">Интерфейс IXCLRDataProcess</span><span class="sxs-lookup"><span data-stu-id="2d200-118">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
