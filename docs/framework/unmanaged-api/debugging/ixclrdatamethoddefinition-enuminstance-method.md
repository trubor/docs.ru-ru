---
description: 'Дополнительные сведения о методе: Иксклрдатамесоддефинитион:: Енуминстанце'
title: 'Метод Иксклрдатамесоддефинитион:: Енуминстанце'
ms.date: 01/16/2019
api.name:
- IXCLRDataMethodDefinition::EnumInstance Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodDefinition::EnumInstance Method
helpviewer.keywords:
- IXCLRDataMethodDefinition::EnumInstance Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 4038dc4706b8362acaf9c13abd9c7326cce376a2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790364"
---
# <a name="ixclrdatamethoddefinitionenuminstance-method"></a><span data-ttu-id="704ce-103">Метод Иксклрдатамесоддефинитион:: Енуминстанце</span><span class="sxs-lookup"><span data-stu-id="704ce-103">IXCLRDataMethodDefinition::EnumInstance Method</span></span>

<span data-ttu-id="704ce-104">Перечисляет экземпляры этого определения метода.</span><span class="sxs-lookup"><span data-stu-id="704ce-104">Enumerates the instances of this method definition.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="704ce-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="704ce-105">Syntax</span></span>

```cpp
HRESULT EnumInstance(
    [in, out] CLRDATA_ENUM         *handle,
    [out] IXCLRDataMethodInstance **instance
);
```

## <a name="parameters"></a><span data-ttu-id="704ce-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="704ce-106">Parameters</span></span>

`handle`\
<span data-ttu-id="704ce-107">[вход, выход] Маркер для перечисления экземпляров.</span><span class="sxs-lookup"><span data-stu-id="704ce-107">[in, out] A handle for enumerating the instances.</span></span>

`instance`\
<span data-ttu-id="704ce-108">заполняет Перечислимый экземпляр.</span><span class="sxs-lookup"><span data-stu-id="704ce-108">[out] The enumerated instance.</span></span>

## <a name="remarks"></a><span data-ttu-id="704ce-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="704ce-109">Remarks</span></span>

<span data-ttu-id="704ce-110">Предоставленный метод является частью `IXCLRDataMethodDefinition` интерфейса и соответствует шестому слоту таблицы виртуального метода.</span><span class="sxs-lookup"><span data-stu-id="704ce-110">The provided method is part of the `IXCLRDataMethodDefinition` interface and corresponds to the 6th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="704ce-111">Требования</span><span class="sxs-lookup"><span data-stu-id="704ce-111">Requirements</span></span>

<span data-ttu-id="704ce-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="704ce-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="704ce-113">**Заголовок:** None</span><span class="sxs-lookup"><span data-stu-id="704ce-113">**Header:** None</span></span>  
<span data-ttu-id="704ce-114">**Библиотека:** None</span><span class="sxs-lookup"><span data-stu-id="704ce-114">**Library:** None</span></span>  
<span data-ttu-id="704ce-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="704ce-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="704ce-116">См. также</span><span class="sxs-lookup"><span data-stu-id="704ce-116">See also</span></span>

- [<span data-ttu-id="704ce-117">Перечисление Клрдатасаурцетипе</span><span class="sxs-lookup"><span data-stu-id="704ce-117">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="704ce-118">Отладка</span><span class="sxs-lookup"><span data-stu-id="704ce-118">Debugging</span></span>](index.md)
- [<span data-ttu-id="704ce-119">Интерфейс IXCLRDataMethodDefinition</span><span class="sxs-lookup"><span data-stu-id="704ce-119">IXCLRDataMethodDefinition Interface</span></span>](ixclrdatamethoddefinition-interface.md)
- [<span data-ttu-id="704ce-120">Интерфейс IXCLRDataMethodInstance</span><span class="sxs-lookup"><span data-stu-id="704ce-120">IXCLRDataMethodInstance Interface</span></span>](ixclrdatamethodinstance-interface.md)
