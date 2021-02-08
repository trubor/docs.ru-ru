---
description: 'Дополнительные сведения о методе: Иксклрдатамодуле:: Жетмесоддефинитионбитокен'
title: 'Метод Иксклрдатамодуле:: Жетмесоддефинитионбитокен'
ms.date: 01/16/2019
api.name:
- IXCLRDataModule::GetMethodDefinitionByToken Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataModule::GetMethodDefinitionByToken Method
helpviewer.keywords:
- IXCLRDataModule::GetMethodDefinitionByToken Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 1eb1187d09183bfff97324a8032d23cbf471f580
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800777"
---
# <a name="ixclrdatamodulegetmethoddefinitionbytoken-method"></a><span data-ttu-id="92fb3-103">Метод Иксклрдатамодуле:: Жетмесоддефинитионбитокен</span><span class="sxs-lookup"><span data-stu-id="92fb3-103">IXCLRDataModule::GetMethodDefinitionByToken Method</span></span>

<span data-ttu-id="92fb3-104">Возвращает определение метода, соответствующее заданному маркеру метаданных.</span><span class="sxs-lookup"><span data-stu-id="92fb3-104">Gets the method definition corresponding to a given metadata token.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="92fb3-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="92fb3-105">Syntax</span></span>

```cpp
HRESULT GetMethodDefinitionByToken(
    [in] mdMethodDef token,
    [out] IXCLRDataMethodDefinition** methodDefinition
);
```

## <a name="parameters"></a><span data-ttu-id="92fb3-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="92fb3-106">Parameters</span></span>

`token`\
<span data-ttu-id="92fb3-107">окне Токен метода.</span><span class="sxs-lookup"><span data-stu-id="92fb3-107">[in] The method token.</span></span>

`methodDefinition`\
<span data-ttu-id="92fb3-108">заполняет Определение метода.</span><span class="sxs-lookup"><span data-stu-id="92fb3-108">[out] The method definition.</span></span>

## <a name="remarks"></a><span data-ttu-id="92fb3-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="92fb3-109">Remarks</span></span>

<span data-ttu-id="92fb3-110">Предоставленный метод является частью `IXCLRDataModule` интерфейса и соответствует слоту 26th таблицы виртуальных методов.</span><span class="sxs-lookup"><span data-stu-id="92fb3-110">The provided method is part of the `IXCLRDataModule` interface and corresponds to the 26th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="92fb3-111">Требования</span><span class="sxs-lookup"><span data-stu-id="92fb3-111">Requirements</span></span>

<span data-ttu-id="92fb3-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92fb3-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="92fb3-113">**Заголовок:** None</span><span class="sxs-lookup"><span data-stu-id="92fb3-113">**Header:** None</span></span>  
<span data-ttu-id="92fb3-114">**Библиотека:** None</span><span class="sxs-lookup"><span data-stu-id="92fb3-114">**Library:** None</span></span>  
<span data-ttu-id="92fb3-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="92fb3-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="92fb3-116">См. также</span><span class="sxs-lookup"><span data-stu-id="92fb3-116">See also</span></span>

- [<span data-ttu-id="92fb3-117">Отладка</span><span class="sxs-lookup"><span data-stu-id="92fb3-117">Debugging</span></span>](index.md)
- [<span data-ttu-id="92fb3-118">Интерфейс IXCLRDataModule</span><span class="sxs-lookup"><span data-stu-id="92fb3-118">IXCLRDataModule Interface</span></span>](ixclrdatamodule-interface.md)
