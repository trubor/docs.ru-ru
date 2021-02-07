---
description: 'Дополнительные сведения: метод ICorDebugCode:: ИСИЛ'
title: Метод ICorDebugCode::IsIL
ms.date: 03/30/2017
api_name:
- ICorDebugCode.IsIL
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::IsIL
helpviewer_keywords:
- ICorDebugCode::IsIL method [.NET Framework debugging]
- IsIL method [.NET Framework debugging]
ms.assetid: 132ef8cc-d938-43f3-b8f2-e3b97c0ceb33
topic_type:
- apiref
ms.openlocfilehash: db41f9ebaa6a6403b21e10d1daa0e8b167c7cb96
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99711132"
---
# <a name="icordebugcodeisil-method"></a><span data-ttu-id="6a4fc-103">Метод ICorDebugCode::IsIL</span><span class="sxs-lookup"><span data-stu-id="6a4fc-103">ICorDebugCode::IsIL Method</span></span>

<span data-ttu-id="6a4fc-104">Возвращает значение, указывающее, представляет ли этот "ICorDebugCode" код, скомпилированный на языке MSIL.</span><span class="sxs-lookup"><span data-stu-id="6a4fc-104">Gets a value that indicates whether this "ICorDebugCode" represents code that was compiled in Microsoft intermediate language (MSIL).</span></span>

## <a name="syntax"></a><span data-ttu-id="6a4fc-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="6a4fc-105">Syntax</span></span>

```cpp
HRESULT IsIL (
    [out] BOOL       *pbIL
);
```

## <a name="parameters"></a><span data-ttu-id="6a4fc-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="6a4fc-106">Parameters</span></span>

`pbIL`  
<span data-ttu-id="6a4fc-107">[out] `true` , если `ICorDebugCode` представляет код, скомпилированный в MSIL; в противном случае — `false` .</span><span class="sxs-lookup"><span data-stu-id="6a4fc-107">[out] `true` if this `ICorDebugCode` represents code that was compiled in MSIL; otherwise, `false`.</span></span>

## <a name="requirements"></a><span data-ttu-id="6a4fc-108">Требования</span><span class="sxs-lookup"><span data-stu-id="6a4fc-108">Requirements</span></span>

<span data-ttu-id="6a4fc-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6a4fc-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="6a4fc-110">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6a4fc-110">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="6a4fc-111">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6a4fc-111">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="6a4fc-112">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6a4fc-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
