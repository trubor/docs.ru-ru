---
description: 'Дополнительные сведения о методе: ICorDebugProcess2:: метода Version'
title: Метод ICorDebugProcess2::GetVersion
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.GetVersion
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::GetVersion
helpviewer_keywords:
- GetVersion method, ICorDebugProcess2 interface [.NET Framework debugging]
- ICorDebugProcess2::GetVersion method [.NET Framework debugging]
ms.assetid: e11d5a75-61d9-4548-aedf-79c26079bd17
topic_type:
- apiref
ms.openlocfilehash: 8472e811ea4df1f99fb4e27b55f3561fae0c8a21
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99650107"
---
# <a name="icordebugprocess2getversion-method"></a><span data-ttu-id="abffe-103">Метод ICorDebugProcess2::GetVersion</span><span class="sxs-lookup"><span data-stu-id="abffe-103">ICorDebugProcess2::GetVersion Method</span></span>

<span data-ttu-id="abffe-104">Возвращает номер версии среды CLR, которая выполняется в этом процессе.</span><span class="sxs-lookup"><span data-stu-id="abffe-104">Gets the version number of the common language runtime (CLR) that is running in this process.</span></span>

## <a name="syntax"></a><span data-ttu-id="abffe-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="abffe-105">Syntax</span></span>

```cpp
HRESULT GetVersion (
    [out] COR_VERSION     *version
);
```

## <a name="parameters"></a><span data-ttu-id="abffe-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="abffe-106">Parameters</span></span>

`version`\
<span data-ttu-id="abffe-107">заполняет Указатель на структуру COR_VERSION, в которой хранится номер версии среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="abffe-107">[out] A pointer to a COR_VERSION structure that stores the version number of the runtime.</span></span>

## <a name="remarks"></a><span data-ttu-id="abffe-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="abffe-108">Remarks</span></span>

<span data-ttu-id="abffe-109">`GetVersion`Метод возвращает код ошибки, если в процессе не была загружена среда выполнения.</span><span class="sxs-lookup"><span data-stu-id="abffe-109">The `GetVersion` method returns an error code if no runtime has been loaded in the process.</span></span>

## <a name="requirements"></a><span data-ttu-id="abffe-110">Требования</span><span class="sxs-lookup"><span data-stu-id="abffe-110">Requirements</span></span>

<span data-ttu-id="abffe-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="abffe-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="abffe-112">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="abffe-112">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="abffe-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="abffe-113">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="abffe-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="abffe-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
