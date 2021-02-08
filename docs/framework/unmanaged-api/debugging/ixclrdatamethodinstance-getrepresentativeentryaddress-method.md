---
description: 'Дополнительные сведения о методе: Иксклрдатамесодинстанце:: Жетрепресентативинтряддресс'
title: 'Метод Иксклрдатамесодинстанце:: Жетрепресентативинтряддресс'
ms.date: 02/01/2019
api.name:
- IXCLRDataMethodInstance::GetRepresentativeEntryAddress
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodInstance::GetRepresentativeEntryAddress
helpviewer.keywords:
- IXCLRDataMethodInstance::GetRepresentativeEntryAddress Method [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: 21cc6c50ab460c0e3a3a92c11fcfe51d4a2a4606
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800803"
---
# <a name="ixclrdatamethodinstancegetrepresentativeentryaddress-method"></a><span data-ttu-id="27f2e-103">Метод Иксклрдатамесодинстанце:: Жетрепресентативинтряддресс</span><span class="sxs-lookup"><span data-stu-id="27f2e-103">IXCLRDataMethodInstance::GetRepresentativeEntryAddress Method</span></span>

<span data-ttu-id="27f2e-104">Возвращает наиболее репрезентативный адрес точки входа для собственной компиляции всех возможных точек входа для метода.</span><span class="sxs-lookup"><span data-stu-id="27f2e-104">Gets the most representative entry point address for the native compilation of all the possible entry points for a method.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="27f2e-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="27f2e-105">Syntax</span></span>

```cpp
HRESULT GetRepresentativeEntryAddress(
    [out] CLRDATA_ADDRESS* addr
);
```

## <a name="parameters"></a><span data-ttu-id="27f2e-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="27f2e-106">Parameters</span></span>

`addr`\
<span data-ttu-id="27f2e-107">заполняет Адрес наиболее репрезентативной собственной точки входа для метода.</span><span class="sxs-lookup"><span data-stu-id="27f2e-107">[out] The address of the most representative native entry point for the method.</span></span>

## <a name="remarks"></a><span data-ttu-id="27f2e-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="27f2e-108">Remarks</span></span>

<span data-ttu-id="27f2e-109">Предоставленный метод является частью [ `IXCLRDataMethodInstance` интерфейса](ixclrdatamethodinstance-interface.md) и соответствует слоту 20 таблицы виртуальных методов.</span><span class="sxs-lookup"><span data-stu-id="27f2e-109">The provided method is part of the [`IXCLRDataMethodInstance` interface](ixclrdatamethodinstance-interface.md) and corresponds to the 20th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="27f2e-110">Требования</span><span class="sxs-lookup"><span data-stu-id="27f2e-110">Requirements</span></span>

<span data-ttu-id="27f2e-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="27f2e-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="27f2e-112">**Заголовок:** None</span><span class="sxs-lookup"><span data-stu-id="27f2e-112">**Header:** None</span></span>  
<span data-ttu-id="27f2e-113">**Библиотека:** None</span><span class="sxs-lookup"><span data-stu-id="27f2e-113">**Library:** None</span></span>  
<span data-ttu-id="27f2e-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="27f2e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="27f2e-115">См. также</span><span class="sxs-lookup"><span data-stu-id="27f2e-115">See also</span></span>

- [<span data-ttu-id="27f2e-116">Отладка</span><span class="sxs-lookup"><span data-stu-id="27f2e-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="27f2e-117">Интерфейс IXCLRDataMethodInstance</span><span class="sxs-lookup"><span data-stu-id="27f2e-117">IXCLRDataMethodInstance Interface</span></span>](ixclrdatamethodinstance-interface.md)
