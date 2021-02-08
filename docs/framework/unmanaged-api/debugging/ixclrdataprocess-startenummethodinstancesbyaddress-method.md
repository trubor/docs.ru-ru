---
description: 'Дополнительные сведения о методе: Иксклрдатапроцесс:: Стартенуммесодинстанцесбяддресс'
title: 'Метод Иксклрдатапроцесс:: Стартенуммесодинстанцесбяддресс'
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::StartEnumMethodInstancesByAddress Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::StartEnumMethodInstancesByAddress Method
helpviewer.keywords:
- IXCLRDataProcess::StartEnumMethodInstancesByAddress Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 155d09192b60b8671435abb439f07dfbb290bc87
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800595"
---
# <a name="ixclrdataprocessstartenummethodinstancesbyaddress-method"></a><span data-ttu-id="0322b-103">Метод Иксклрдатапроцесс:: Стартенуммесодинстанцесбяддресс</span><span class="sxs-lookup"><span data-stu-id="0322b-103">IXCLRDataProcess::StartEnumMethodInstancesByAddress Method</span></span>

<span data-ttu-id="0322b-104">Предоставляет описатель для перечисления экземпляров методов, `AppDomain` начиная с заданного адреса.</span><span class="sxs-lookup"><span data-stu-id="0322b-104">Provides a handle to enumerate the method instances of `AppDomain` starting at a given address.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="0322b-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0322b-105">Syntax</span></span>

```cpp
HRESULT StartEnumMethodInstancesByAddress(
    [in] CLRDATA_ADDRESS     address,
    [in] IXCLRDataAppDomain *appDomain,
    [out] CLRDATA_ENUM      *handle
);
```

## <a name="parameters"></a><span data-ttu-id="0322b-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="0322b-106">Parameters</span></span>

`address`\
<span data-ttu-id="0322b-107">окне Адрес первого экземпляра метода.</span><span class="sxs-lookup"><span data-stu-id="0322b-107">[in] The address of the first method instance.</span></span>

`appDomain`\
<span data-ttu-id="0322b-108">окне AppDomain экземпляров метода.</span><span class="sxs-lookup"><span data-stu-id="0322b-108">[in] The AppDomain of the method instances.</span></span>

`handle`\
<span data-ttu-id="0322b-109">заполняет Описатель для перечисления экземпляров методов.</span><span class="sxs-lookup"><span data-stu-id="0322b-109">[out] A handle for enumerating the method instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="0322b-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="0322b-110">Remarks</span></span>

<span data-ttu-id="0322b-111">Предоставленный метод является частью `IXCLRDataProcess` интерфейса и соответствует 28-го слоту таблицы виртуального метода.</span><span class="sxs-lookup"><span data-stu-id="0322b-111">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 28th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="0322b-112">Требования</span><span class="sxs-lookup"><span data-stu-id="0322b-112">Requirements</span></span>

<span data-ttu-id="0322b-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0322b-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="0322b-114">**Заголовок:** None</span><span class="sxs-lookup"><span data-stu-id="0322b-114">**Header:** None</span></span>  
<span data-ttu-id="0322b-115">**Библиотека:** None</span><span class="sxs-lookup"><span data-stu-id="0322b-115">**Library:** None</span></span>  
<span data-ttu-id="0322b-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="0322b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="0322b-117">См. также</span><span class="sxs-lookup"><span data-stu-id="0322b-117">See also</span></span>

- [<span data-ttu-id="0322b-118">Перечисление Клрдатасаурцетипе</span><span class="sxs-lookup"><span data-stu-id="0322b-118">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="0322b-119">Отладка</span><span class="sxs-lookup"><span data-stu-id="0322b-119">Debugging</span></span>](index.md)
- [<span data-ttu-id="0322b-120">Интерфейс IXCLRDataProcess</span><span class="sxs-lookup"><span data-stu-id="0322b-120">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
