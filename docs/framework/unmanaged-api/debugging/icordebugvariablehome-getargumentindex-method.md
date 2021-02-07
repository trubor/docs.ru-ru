---
description: 'Дополнительные сведения о методе: ICorDebugVariableHome:: Жетаргументиндекс'
title: 'Метод ICorDebugVariableHome:: Жетаргументиндекс'
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetArgumentIndex
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetArgumentIndex
helpviewer_keywords:
- ICorDebugVariableHome::GetArgumentIndex method [.NET Framework debugging]
- GetArgumentIndex method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: e86fcc72-388d-4009-ab21-8f9c3323e9a3
topic_type:
- apiref
ms.openlocfilehash: 827ef55d3e3509cbfbfc8213ef5b53fbe2e2220e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99690045"
---
# <a name="icordebugvariablehomegetargumentindex-method"></a><span data-ttu-id="d36ea-103">Метод ICorDebugVariableHome:: Жетаргументиндекс</span><span class="sxs-lookup"><span data-stu-id="d36ea-103">ICorDebugVariableHome::GetArgumentIndex Method</span></span>

<span data-ttu-id="d36ea-104">Возвращает индекс аргумента функции.</span><span class="sxs-lookup"><span data-stu-id="d36ea-104">Gets the index of a function argument.</span></span>

## <a name="syntax"></a><span data-ttu-id="d36ea-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d36ea-105">Syntax</span></span>

```cpp
HRESULT GetArgumentIndex(
    [out] ULONG32* pArgumentIndex
);
```

## <a name="parameters"></a><span data-ttu-id="d36ea-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="d36ea-106">Parameters</span></span>

`pArgumentIndex`\
<span data-ttu-id="d36ea-107">заполняет Указатель на индекс аргумента.</span><span class="sxs-lookup"><span data-stu-id="d36ea-107">[out] A pointer to the argument index.</span></span>

## <a name="return-value"></a><span data-ttu-id="d36ea-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="d36ea-108">Return Value</span></span>

<span data-ttu-id="d36ea-109">Метод возвращает следующие значения.</span><span class="sxs-lookup"><span data-stu-id="d36ea-109">The method returns the following values.</span></span>

|<span data-ttu-id="d36ea-110">Значение</span><span class="sxs-lookup"><span data-stu-id="d36ea-110">Value</span></span>|<span data-ttu-id="d36ea-111">Описание</span><span class="sxs-lookup"><span data-stu-id="d36ea-111">Description</span></span>|
|-----------|-----------------|
|`S_OK`|<span data-ttu-id="d36ea-112">Вызов метода вернул допустимый индекс аргумента.</span><span class="sxs-lookup"><span data-stu-id="d36ea-112">The method call returned a valid argument index.</span></span>|
|`E_FAIL`|<span data-ttu-id="d36ea-113">Текущий экземпляр [ICorDebugVariableHome](icordebugvariablehome-interface.md) представляет локальную переменную.</span><span class="sxs-lookup"><span data-stu-id="d36ea-113">The current [ICorDebugVariableHome](icordebugvariablehome-interface.md) instance represents a local variable.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d36ea-114">Remarks</span><span class="sxs-lookup"><span data-stu-id="d36ea-114">Remarks</span></span>

<span data-ttu-id="d36ea-115">Индекс аргумента можно использовать для получения метаданных для этого аргумента.</span><span class="sxs-lookup"><span data-stu-id="d36ea-115">The argument index can be used to retrieve metadata for this argument.</span></span>

## <a name="requirements"></a><span data-ttu-id="d36ea-116">Требования</span><span class="sxs-lookup"><span data-stu-id="d36ea-116">Requirements</span></span>

<span data-ttu-id="d36ea-117">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d36ea-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="d36ea-118">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d36ea-118">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="d36ea-119">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d36ea-119">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="d36ea-120">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d36ea-120">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="d36ea-121">См. также</span><span class="sxs-lookup"><span data-stu-id="d36ea-121">See also</span></span>

- [<span data-ttu-id="d36ea-122">Интерфейс ICorDebugVariableHome</span><span class="sxs-lookup"><span data-stu-id="d36ea-122">ICorDebugVariableHome Interface</span></span>](icordebugvariablehome-interface.md)
