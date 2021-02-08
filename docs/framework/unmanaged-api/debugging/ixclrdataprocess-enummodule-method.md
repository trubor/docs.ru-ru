---
description: 'Дополнительные сведения о методе: Иксклрдатапроцесс:: Енуммодуле'
title: 'Метод Иксклрдатапроцесс:: Енуммодуле'
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::EnumModule Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::EnumModule Method
helpviewer.keywords:
- IXCLRDataProcess::EnumModule Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 33b15da6939a0fb78a4eeafcf75e1a2b2f0d0ab1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800686"
---
# <a name="ixclrdataprocessenummodule-method"></a><span data-ttu-id="ed70e-103">Метод Иксклрдатапроцесс:: Енуммодуле</span><span class="sxs-lookup"><span data-stu-id="ed70e-103">IXCLRDataProcess::EnumModule Method</span></span>

<span data-ttu-id="ed70e-104">Перечисляет модули этого процесса.</span><span class="sxs-lookup"><span data-stu-id="ed70e-104">Enumerates the modules of this process.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="ed70e-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ed70e-105">Syntax</span></span>

```cpp
HRESULT EnumModule(
    [in, out] CLRDATA_ENUM  *handle,
    [out] IXCLRDataModule  **mod
);
```

## <a name="parameters"></a><span data-ttu-id="ed70e-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="ed70e-106">Parameters</span></span>

`handle`\
<span data-ttu-id="ed70e-107">[вход, выход] Маркер для перечисления модулей.</span><span class="sxs-lookup"><span data-stu-id="ed70e-107">[in, out] A handle for enumerating the modules.</span></span>

`mod`\
<span data-ttu-id="ed70e-108">заполняет Перечисленный модуль.</span><span class="sxs-lookup"><span data-stu-id="ed70e-108">[out] The enumerated module.</span></span>

## <a name="remarks"></a><span data-ttu-id="ed70e-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="ed70e-109">Remarks</span></span>

<span data-ttu-id="ed70e-110">Предоставленный метод является частью `IXCLRDataProcess` интерфейса и соответствует 25-е слоту таблицы виртуального метода.</span><span class="sxs-lookup"><span data-stu-id="ed70e-110">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 25th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="ed70e-111">Требования</span><span class="sxs-lookup"><span data-stu-id="ed70e-111">Requirements</span></span>

<span data-ttu-id="ed70e-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ed70e-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="ed70e-113">**Заголовок:** None</span><span class="sxs-lookup"><span data-stu-id="ed70e-113">**Header:** None</span></span>  
<span data-ttu-id="ed70e-114">**Библиотека:** None</span><span class="sxs-lookup"><span data-stu-id="ed70e-114">**Library:** None</span></span>  
<span data-ttu-id="ed70e-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="ed70e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="ed70e-116">См. также</span><span class="sxs-lookup"><span data-stu-id="ed70e-116">See also</span></span>

- [<span data-ttu-id="ed70e-117">Перечисление Клрдатасаурцетипе</span><span class="sxs-lookup"><span data-stu-id="ed70e-117">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="ed70e-118">Отладка</span><span class="sxs-lookup"><span data-stu-id="ed70e-118">Debugging</span></span>](index.md)
- [<span data-ttu-id="ed70e-119">Интерфейс IXCLRDataModule</span><span class="sxs-lookup"><span data-stu-id="ed70e-119">IXCLRDataModule Interface</span></span>](ixclrdatamodule-interface.md)
- [<span data-ttu-id="ed70e-120">Интерфейс IXCLRDataProcess</span><span class="sxs-lookup"><span data-stu-id="ed70e-120">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
