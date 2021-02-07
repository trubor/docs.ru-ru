---
description: 'Дополнительные сведения о методе: Икордебугкодинум:: Next'
title: Метод ICorDebugCodeEnum::Next
ms.date: 03/30/2017
api_name:
- ICorDebugCodeEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCodeEnum::Next
helpviewer_keywords:
- ICorDebugCodeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugEnum interface [.NET Framework debugging]
ms.assetid: 644ece86-384d-4c63-9fba-52c789616ff7
topic_type:
- apiref
ms.openlocfilehash: 51d46718891ce3df537c675175eacc4e33b92f79
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99764779"
---
# <a name="icordebugcodeenumnext-method"></a><span data-ttu-id="3a01b-103">Метод ICorDebugCodeEnum::Next</span><span class="sxs-lookup"><span data-stu-id="3a01b-103">ICorDebugCodeEnum::Next Method</span></span>

<span data-ttu-id="3a01b-104">Возвращает указанное число экземпляров ICorDebugCode из перечисления, начиная с текущей позиции.</span><span class="sxs-lookup"><span data-stu-id="3a01b-104">Gets the specified number of "ICorDebugCode" instances from the enumeration, starting at the current position.</span></span>

## <a name="syntax"></a><span data-ttu-id="3a01b-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="3a01b-105">Syntax</span></span>

```cpp
HRESULT Next (
    [in] ULONG  celt,
    [out, size_is(celt), length_is(*pceltFetched)]
        ICorDebugCode *values[],
    [out] ULONG *pceltFetched
);
```

## <a name="parameters"></a><span data-ttu-id="3a01b-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="3a01b-106">Parameters</span></span>

`celt`  
<span data-ttu-id="3a01b-107">окне Число `ICorDebugCode` извлекаемых экземпляров.</span><span class="sxs-lookup"><span data-stu-id="3a01b-107">[in] The number of `ICorDebugCode` instances to be retrieved.</span></span>

`values`  
<span data-ttu-id="3a01b-108">заполняет Массив указателей, каждый из которых указывает на `ICorDebugCode` объект.</span><span class="sxs-lookup"><span data-stu-id="3a01b-108">[out] An array of pointers, each of which points to an `ICorDebugCode` object.</span></span>

`pceltFetched`  
<span data-ttu-id="3a01b-109">заполняет Указатель на число `ICorDebugCode` фактически возвращенных экземпляров.</span><span class="sxs-lookup"><span data-stu-id="3a01b-109">[out] A pointer to the number of `ICorDebugCode` instances actually returned.</span></span> <span data-ttu-id="3a01b-110">Это значение может быть равно NULL `celt` , если равно единице.</span><span class="sxs-lookup"><span data-stu-id="3a01b-110">This value may be null if `celt` is one.</span></span>

## <a name="requirements"></a><span data-ttu-id="3a01b-111">Требования</span><span class="sxs-lookup"><span data-stu-id="3a01b-111">Requirements</span></span>

<span data-ttu-id="3a01b-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3a01b-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="3a01b-113">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3a01b-113">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="3a01b-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3a01b-114">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="3a01b-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a01b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
