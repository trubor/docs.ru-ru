---
description: 'Дополнительные сведения о методе: Иксклрдатамесоддефинитион:: Енденуминстанцес'
title: 'Метод Иксклрдатамесоддефинитион:: Енденуминстанцес'
ms.date: 01/16/2019
api.name:
- IXCLRDataMethodDefinition::EndEnumInstances Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodDefinition::EndEnumInstances Method
helpviewer.keywords:
- IXCLRDataMethodDefinition::EndEnumInstances Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: bfdcb9046b4983e6686410bf2ceadf7119b89e74
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790377"
---
# <a name="ixclrdatamethoddefinitionendenuminstances-method"></a><span data-ttu-id="46e91-103">Метод Иксклрдатамесоддефинитион:: Енденуминстанцес</span><span class="sxs-lookup"><span data-stu-id="46e91-103">IXCLRDataMethodDefinition::EndEnumInstances Method</span></span>

<span data-ttu-id="46e91-104">Освобождает ресурсы, используемые внутренними итераторами, используемыми при перечислении экземпляров.</span><span class="sxs-lookup"><span data-stu-id="46e91-104">Releases the resources used by internal iterators used during instance enumeration.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="46e91-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="46e91-105">Syntax</span></span>

```cpp
HRESULT EndEnumInstances(
    [in] CLRDATA_ENUM handle
);
```

## <a name="parameters"></a><span data-ttu-id="46e91-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="46e91-106">Parameters</span></span>

`handle`\
<span data-ttu-id="46e91-107">заполняет Маркер для перечисления экземпляров.</span><span class="sxs-lookup"><span data-stu-id="46e91-107">[out] A handle for enumerating the instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="46e91-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="46e91-108">Remarks</span></span>

<span data-ttu-id="46e91-109">Предоставленный метод является частью `IXCLRDataMethodDefinition` интерфейса и соответствует седьмому слоту таблицы виртуального метода.</span><span class="sxs-lookup"><span data-stu-id="46e91-109">The provided method is part of the `IXCLRDataMethodDefinition` interface and corresponds to the 7th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="46e91-110">Требования</span><span class="sxs-lookup"><span data-stu-id="46e91-110">Requirements</span></span>

<span data-ttu-id="46e91-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="46e91-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="46e91-112">**Заголовок:** None</span><span class="sxs-lookup"><span data-stu-id="46e91-112">**Header:** None</span></span>  
<span data-ttu-id="46e91-113">**Библиотека:** None</span><span class="sxs-lookup"><span data-stu-id="46e91-113">**Library:** None</span></span>  
<span data-ttu-id="46e91-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="46e91-114">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="46e91-115">См. также</span><span class="sxs-lookup"><span data-stu-id="46e91-115">See also</span></span>

- [<span data-ttu-id="46e91-116">Отладка</span><span class="sxs-lookup"><span data-stu-id="46e91-116">Debugging</span></span>](index.md)
- [<span data-ttu-id="46e91-117">Интерфейс IXCLRDataMethodDefinition</span><span class="sxs-lookup"><span data-stu-id="46e91-117">IXCLRDataMethodDefinition Interface</span></span>](ixclrdatamethoddefinition-interface.md)
