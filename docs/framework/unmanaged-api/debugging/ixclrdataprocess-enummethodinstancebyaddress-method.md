---
description: 'Дополнительные сведения о методе: Иксклрдатапроцесс:: Енуммесодинстанцебяддресс'
title: 'Метод Иксклрдатапроцесс:: Енуммесодинстанцебяддресс'
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::EnumMethodInstanceByAddress Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::EnumMethodInstanceByAddress Method
helpviewer.keywords:
- IXCLRDataProcess::EnumMethodInstanceByAddress Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: a0d59956288e39be188628d10c63a52d09d17638
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800699"
---
# <a name="ixclrdataprocessenummethodinstancebyaddress-method"></a><span data-ttu-id="deca5-103">Метод Иксклрдатапроцесс:: Енуммесодинстанцебяддресс</span><span class="sxs-lookup"><span data-stu-id="deca5-103">IXCLRDataProcess::EnumMethodInstanceByAddress Method</span></span>

<span data-ttu-id="deca5-104">Перечисляет экземпляры методов этого процесса, начиная с смещения адреса.</span><span class="sxs-lookup"><span data-stu-id="deca5-104">Enumerates the method instances of this process starting at an address offset.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="deca5-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="deca5-105">Syntax</span></span>

```cpp
HRESULT EnumMethodInstanceByAddress(
    [in] CLRDATA_ENUM              *handle,
    [out] IXCLRDataMethodInstance **method
);
```

## <a name="parameters"></a><span data-ttu-id="deca5-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="deca5-106">Parameters</span></span>

`handle`\
<span data-ttu-id="deca5-107">окне Описатель для перечисления экземпляров методов.</span><span class="sxs-lookup"><span data-stu-id="deca5-107">[in] A handle for enumerating the method instances.</span></span>

`mod`\
<span data-ttu-id="deca5-108">заполняет Экземпляр перечисленного метода.</span><span class="sxs-lookup"><span data-stu-id="deca5-108">[out] The enumerated method instance.</span></span>

## <a name="remarks"></a><span data-ttu-id="deca5-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="deca5-109">Remarks</span></span>

<span data-ttu-id="deca5-110">Предоставленный метод является частью `IXCLRDataProcess` интерфейса и соответствует слоту 29 таблицы виртуальных методов.</span><span class="sxs-lookup"><span data-stu-id="deca5-110">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 29th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="deca5-111">Требования</span><span class="sxs-lookup"><span data-stu-id="deca5-111">Requirements</span></span>

<span data-ttu-id="deca5-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="deca5-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>
<span data-ttu-id="deca5-113">**Заголовок:** Нет **библиотеки:** нет **платформа .NET Framework версий:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="deca5-113">**Header:** None **Library:** None **.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="deca5-114">См. также</span><span class="sxs-lookup"><span data-stu-id="deca5-114">See also</span></span>

- [<span data-ttu-id="deca5-115">Перечисление Клрдатасаурцетипе</span><span class="sxs-lookup"><span data-stu-id="deca5-115">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="deca5-116">Отладка</span><span class="sxs-lookup"><span data-stu-id="deca5-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="deca5-117">Интерфейс IXCLRDataProcess</span><span class="sxs-lookup"><span data-stu-id="deca5-117">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
