---
description: 'Дополнительные сведения о методе: Иксклрдатапроцесс:: Енденуммодулес'
title: 'Метод Иксклрдатапроцесс:: Енденуммодулес'
ms.date: 01/16/2019
api.name:
- IXCLRDataProcess::EndEnumModules Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataProcess::EndEnumModules Method
helpviewer.keywords:
- IXCLRDataProcess::EndEnumModules Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 454d4fa3616f9ba8312dc3d1ac02c228625aa488
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800712"
---
# <a name="ixclrdataprocessendenummodules-method"></a><span data-ttu-id="0c556-103">Метод Иксклрдатапроцесс:: Енденуммодулес</span><span class="sxs-lookup"><span data-stu-id="0c556-103">IXCLRDataProcess::EndEnumModules Method</span></span>

<span data-ttu-id="0c556-104">Освобождает ресурсы, используемые внутренними итераторами, используемыми при перечислении модулей.</span><span class="sxs-lookup"><span data-stu-id="0c556-104">Releases the resources used by internal iterators used during module enumeration.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="0c556-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0c556-105">Syntax</span></span>

```cpp
HRESULT EndEnumModules(
    [in] CLRDATA_ENUM handle
);
```

## <a name="parameters"></a><span data-ttu-id="0c556-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="0c556-106">Parameters</span></span>

`handle`\
<span data-ttu-id="0c556-107">заполняет Маркер для перечисления модулей.</span><span class="sxs-lookup"><span data-stu-id="0c556-107">[out] A handle for enumerating the modules.</span></span>

## <a name="remarks"></a><span data-ttu-id="0c556-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="0c556-108">Remarks</span></span>

<span data-ttu-id="0c556-109">Предоставленный метод является частью `IXCLRDataProcess` интерфейса и соответствует слоту 26th таблицы виртуальных методов.</span><span class="sxs-lookup"><span data-stu-id="0c556-109">The provided method is part of the `IXCLRDataProcess` interface and corresponds to the 26th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="0c556-110">Требования</span><span class="sxs-lookup"><span data-stu-id="0c556-110">Requirements</span></span>

<span data-ttu-id="0c556-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0c556-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>
<span data-ttu-id="0c556-112">**Заголовок:** Нет **библиотеки:** нет **платформа .NET Framework версий:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="0c556-112">**Header:** None **Library:** None **.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="0c556-113">См. также</span><span class="sxs-lookup"><span data-stu-id="0c556-113">See also</span></span>

- [<span data-ttu-id="0c556-114">Отладка</span><span class="sxs-lookup"><span data-stu-id="0c556-114">Debugging</span></span>](index.md)
- [<span data-ttu-id="0c556-115">Интерфейс IXCLRDataProcess</span><span class="sxs-lookup"><span data-stu-id="0c556-115">IXCLRDataProcess Interface</span></span>](ixclrdataprocess-interface.md)
