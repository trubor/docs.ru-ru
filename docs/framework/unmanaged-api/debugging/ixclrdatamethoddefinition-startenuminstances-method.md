---
description: 'Дополнительные сведения о методе: Иксклрдатамесоддефинитион:: Стартенуминстанцес'
title: 'Метод Иксклрдатамесоддефинитион:: Стартенуминстанцес'
ms.date: 01/16/2019
api.name:
- IXCLRDataMethodDefinition::StartEnumInstances Method
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- IXCLRDataMethodDefinition::StartEnumInstances Method
helpviewer.keywords:
- IXCLRDataMethodDefinition::StartEnumInstances Method [.NET Framework debugging]
topic_type:
- apiref
author: cshung
ms.author: andrewau
ms.openlocfilehash: 74de6360c90766cfec17e6b88a495fe2a70858b4
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800829"
---
# <a name="ixclrdatamethoddefinitionstartenuminstances-method"></a><span data-ttu-id="e99ba-103">Метод Иксклрдатамесоддефинитион:: Стартенуминстанцес</span><span class="sxs-lookup"><span data-stu-id="e99ba-103">IXCLRDataMethodDefinition::StartEnumInstances Method</span></span>

<span data-ttu-id="e99ba-104">Предоставляет обработчик для перечисления экземпляров методов для заданного объекта `IXCLRDataAppDomain` .</span><span class="sxs-lookup"><span data-stu-id="e99ba-104">Provides a handle for the enumeration of method instances for a given `IXCLRDataAppDomain`.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="e99ba-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e99ba-105">Syntax</span></span>

```cpp
HRESULT StartEnumInstances(
    [in] IXCLRDataAppDomain* appDomain,
    [out] CLRDATA_ENUM *handle
);
```

## <a name="parameters"></a><span data-ttu-id="e99ba-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="e99ba-106">Parameters</span></span>

`appDomain`\
<span data-ttu-id="e99ba-107">окне Домен приложения для перечисления.</span><span class="sxs-lookup"><span data-stu-id="e99ba-107">[in] An AppDomain for the enumeration.</span></span>

`handle`\
<span data-ttu-id="e99ba-108">заполняет Маркер для перечисления экземпляров.</span><span class="sxs-lookup"><span data-stu-id="e99ba-108">[out] A handle for enumerating the instances.</span></span>

## <a name="remarks"></a><span data-ttu-id="e99ba-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="e99ba-109">Remarks</span></span>

<span data-ttu-id="e99ba-110">Предоставленный метод является частью `IXCLRDataMethodDefinition` интерфейса и соответствует 5-сегменту таблицы виртуального метода.</span><span class="sxs-lookup"><span data-stu-id="e99ba-110">The provided method is part of the `IXCLRDataMethodDefinition` interface and corresponds to the 5th slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="e99ba-111">Требования</span><span class="sxs-lookup"><span data-stu-id="e99ba-111">Requirements</span></span>

<span data-ttu-id="e99ba-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e99ba-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="e99ba-113">**Заголовок:** None</span><span class="sxs-lookup"><span data-stu-id="e99ba-113">**Header:** None</span></span>  
<span data-ttu-id="e99ba-114">**Библиотека:** None</span><span class="sxs-lookup"><span data-stu-id="e99ba-114">**Library:** None</span></span>  
<span data-ttu-id="e99ba-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="e99ba-115">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="e99ba-116">См. также</span><span class="sxs-lookup"><span data-stu-id="e99ba-116">See also</span></span>

- [<span data-ttu-id="e99ba-117">Перечисление Клрдатасаурцетипе</span><span class="sxs-lookup"><span data-stu-id="e99ba-117">CLRDataSourceType Enumeration</span></span>](clrdatasourcetype-enumeration.md)
- [<span data-ttu-id="e99ba-118">Отладка</span><span class="sxs-lookup"><span data-stu-id="e99ba-118">Debugging</span></span>](index.md)
- [<span data-ttu-id="e99ba-119">Интерфейс IXCLRDataMethodDefinition</span><span class="sxs-lookup"><span data-stu-id="e99ba-119">IXCLRDataMethodDefinition Interface</span></span>](ixclrdatamethoddefinition-interface.md)
