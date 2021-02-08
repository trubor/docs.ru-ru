---
description: 'Дополнительные сведения о методе: Иксклрдатапроцесс:: Стартенуммодулес'
title: 'Метод Иксклрдатапроцесс:: Стартенуммодулес'
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::StartEnumModules Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::StartEnumModules Method
helpviewer.keywords:
- IXCLRDataProcess::StartEnumModules Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 2e90c646ee8815ec10ce0bbd7538f13d7b5dcf8a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800588"
---
# <a name="ixclrdataprocessstartenummodules-method"></a><span data-ttu-id="26f6e-103">Метод Иксклрдатапроцесс:: Стартенуммодулес</span><span class="sxs-lookup"><span data-stu-id="26f6e-103">IXCLRDataProcess::StartEnumModules Method</span></span>

<span data-ttu-id="26f6e-104">Предоставляет описатель для перечисления модулей процесса.</span><span class="sxs-lookup"><span data-stu-id="26f6e-104">Provides a handle to enumerate the modules of a process.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="26f6e-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="26f6e-105">Syntax</span></span>

```cpp
HRESULT StartEnumModules(
    [out] CLRDATA_ENUM *handle
);
```

## <a name="parameters"></a><span data-ttu-id="26f6e-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="26f6e-106">Parameters</span></span>

`handle`\
<span data-ttu-id="26f6e-107">заполняет Маркер для перечисления модулей.</span><span class="sxs-lookup"><span data-stu-id="26f6e-107">[out] A handle for enumerating the modules.</span></span>

## <a name="remarks"></a><span data-ttu-id="26f6e-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="26f6e-108">Remarks</span></span>

<span data-ttu-id="26f6e-109">Предоставленный метод является частью `IXCLRDataProcess` интерфейса и соответствует слоту 24 таблицы виртуальных методов.</span><span class="sxs-lookup"><span data-stu-id="26f6e-109">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 24th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="26f6e-110">Требования</span><span class="sxs-lookup"><span data-stu-id="26f6e-110">Requirements</span></span>

<span data-ttu-id="26f6e-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="26f6e-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="26f6e-112">**Заголовок:** None</span><span class="sxs-lookup"><span data-stu-id="26f6e-112">**Header:** None</span></span>  
<span data-ttu-id="26f6e-113">**Библиотека:** None</span><span class="sxs-lookup"><span data-stu-id="26f6e-113">**Library:** None</span></span>  
<span data-ttu-id="26f6e-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="26f6e-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="26f6e-115">См. также</span><span class="sxs-lookup"><span data-stu-id="26f6e-115">See also</span></span>

- [<span data-ttu-id="26f6e-116">Перечисление Клрдатасаурцетипе</span><span class="sxs-lookup"><span data-stu-id="26f6e-116">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="26f6e-117">Отладка</span><span class="sxs-lookup"><span data-stu-id="26f6e-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="26f6e-118">Интерфейс IXCLRDataProcess</span><span class="sxs-lookup"><span data-stu-id="26f6e-118">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
