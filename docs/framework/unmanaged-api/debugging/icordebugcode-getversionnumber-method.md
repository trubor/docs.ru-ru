---
description: 'Дополнительные сведения: метод ICorDebugCode:: Жетверсионнумбер'
title: Метод ICorDebugCode::GetVersionNumber
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetVersionNumber
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetVersionNumber
helpviewer_keywords:
- GetVersionNumber method, ICorDebugCode interface [.NET Framework debugging]
- ICorDebugCode::GetVersionNumber method [.NET Framework debugging]
ms.assetid: c8e02518-679f-4e9f-8a28-ba4a89a3876f
topic_type:
- apiref
ms.openlocfilehash: 901342333bea3d455407602dde78bdccd0140d77
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99764909"
---
# <a name="icordebugcodegetversionnumber-method"></a><span data-ttu-id="f7125-103">Метод ICorDebugCode::GetVersionNumber</span><span class="sxs-lookup"><span data-stu-id="f7125-103">ICorDebugCode::GetVersionNumber Method</span></span>

<span data-ttu-id="f7125-104">Возвращает номер, отсчитываемый от единицы, определяющий версию кода, который представляет этот "ICorDebugCode".</span><span class="sxs-lookup"><span data-stu-id="f7125-104">Gets the one-based number that identifies the version of the code that this "ICorDebugCode" represents.</span></span>

## <a name="syntax"></a><span data-ttu-id="f7125-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f7125-105">Syntax</span></span>

```cpp
HRESULT GetVersionNumber (
    [out] ULONG32    *nVersion
);
```

## <a name="parameters"></a><span data-ttu-id="f7125-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="f7125-106">Parameters</span></span>

 `nVersion`  
 <span data-ttu-id="f7125-107">заполняет Указатель на номер версии кода.</span><span class="sxs-lookup"><span data-stu-id="f7125-107">[out] A pointer to the version number of the code.</span></span>

## <a name="remarks"></a><span data-ttu-id="f7125-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="f7125-108">Remarks</span></span>

 <span data-ttu-id="f7125-109">Номер версии увеличивается каждый раз, когда в коде выполняется операция "изменить и продолжить" (EnC).</span><span class="sxs-lookup"><span data-stu-id="f7125-109">The version number is incremented each time an edit-and-continue (EnC) operation is performed on the code.</span></span>

## <a name="requirements"></a><span data-ttu-id="f7125-110">Требования</span><span class="sxs-lookup"><span data-stu-id="f7125-110">Requirements</span></span>

 <span data-ttu-id="f7125-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f7125-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7125-112">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f7125-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f7125-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f7125-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f7125-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7125-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
