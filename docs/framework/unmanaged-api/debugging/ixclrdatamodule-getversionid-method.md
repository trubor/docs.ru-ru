---
description: 'Дополнительные сведения о методе: Иксклрдатамодуле:: Жетверсионид'
title: 'Метод Иксклрдатамодуле:: Жетверсионид'
ms.date: 01/16/2019
api.name:
- IXCLRDataModule::GetVersionId Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataModule::GetVersionId Method
helpviewer.keywords:
- IXCLRDataModule::GetVersionId Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 1b924757f43d106df555ea028270ac873f8f4558
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800764"
---
# <a name="ixclrdatamodulegetversionid-method"></a><span data-ttu-id="0868a-103">Метод Иксклрдатамодуле:: Жетверсионид</span><span class="sxs-lookup"><span data-stu-id="0868a-103">IXCLRDataModule::GetVersionId Method</span></span>

<span data-ttu-id="0868a-104">Возвращает идентификатор версии модуля.</span><span class="sxs-lookup"><span data-stu-id="0868a-104">Gets the module's version identifier.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="0868a-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0868a-105">Syntax</span></span>

```cpp
HRESULT GetVersionId(
    [out] GUID* vid
);
```

## <a name="parameters"></a><span data-ttu-id="0868a-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="0868a-106">Parameters</span></span>

`vid`\
<span data-ttu-id="0868a-107">заполняет Идентификатор версии модуля.</span><span class="sxs-lookup"><span data-stu-id="0868a-107">[out] The module's version identifier.</span></span>

## <a name="remarks"></a><span data-ttu-id="0868a-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="0868a-108">Remarks</span></span>

<span data-ttu-id="0868a-109">Предоставленный метод является частью `IXCLRDataModule` интерфейса и соответствует слоту й таблицы виртуальных методов.</span><span class="sxs-lookup"><span data-stu-id="0868a-109">The provided method is part of the `IXCLRDataModule` interface and corresponds to the 41st slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="0868a-110">Требования</span><span class="sxs-lookup"><span data-stu-id="0868a-110">Requirements</span></span>

<span data-ttu-id="0868a-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0868a-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="0868a-112">**Заголовок:** None</span><span class="sxs-lookup"><span data-stu-id="0868a-112">**Header:** None</span></span>  
<span data-ttu-id="0868a-113">**Библиотека:** None</span><span class="sxs-lookup"><span data-stu-id="0868a-113">**Library:** None</span></span>  
<span data-ttu-id="0868a-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="0868a-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="0868a-115">См. также</span><span class="sxs-lookup"><span data-stu-id="0868a-115">See also</span></span>

- [<span data-ttu-id="0868a-116">Отладка</span><span class="sxs-lookup"><span data-stu-id="0868a-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="0868a-117">Интерфейс IXCLRDataModule</span><span class="sxs-lookup"><span data-stu-id="0868a-117">IXCLRDataModule Interface</span></span>](ixclrdatamodule-interface.md)
