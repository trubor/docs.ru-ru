---
description: 'Дополнительные сведения о методе: ICorDebugCode2:: Жеткомпилерфлагс'
title: Метод ICorDebugCode2::GetCompilerFlags
ms.date: 03/30/2017
api_name:
- ICorDebugCode2.GetCompilerFlags
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode2::GetCompilerFlags
helpviewer_keywords:
- GetCompilerFlags method [.NET Framework debugging]
- ICorDebugCode2::GetCompilerFlags method [.NET Framework debugging]
ms.assetid: 532e9dfd-d114-4c75-b952-1accce102643
topic_type:
- apiref
ms.openlocfilehash: 820b6d2392b2b91bbfc8a85b165c4d73a2546859
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99711126"
---
# <a name="icordebugcode2getcompilerflags-method"></a><span data-ttu-id="f8a9a-103">Метод ICorDebugCode2::GetCompilerFlags</span><span class="sxs-lookup"><span data-stu-id="f8a9a-103">ICorDebugCode2::GetCompilerFlags Method</span></span>

<span data-ttu-id="f8a9a-104">Возвращает флаги, указывающие условия, при которых этот объект кода был либо JIT-скомпилирован, либо создан с помощью генератора образов в машинном коде (Ngen.exe).</span><span class="sxs-lookup"><span data-stu-id="f8a9a-104">Gets the flags that specify the conditions under which this code object was either just-in-time (JIT) compiled or generated using the native image generator (Ngen.exe).</span></span>

## <a name="syntax"></a><span data-ttu-id="f8a9a-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f8a9a-105">Syntax</span></span>

```cpp
HRESULT GetCompilerFlags (
    [out] DWORD *pdwFlags
);
```

## <a name="parameters"></a><span data-ttu-id="f8a9a-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="f8a9a-106">Parameters</span></span>

`pdwFlags`  
<span data-ttu-id="f8a9a-107">заполняет Указатель на значение перечисления [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) , которое указывает поведение JIT-компилятора или генератора образов в машинном код.</span><span class="sxs-lookup"><span data-stu-id="f8a9a-107">[out] A pointer to a value of the [CorDebugJITCompilerFlags](cordebugjitcompilerflags-enumeration.md) enumeration that specifies the behavior of the JIT compiler or the native image generator.</span></span>

## <a name="requirements"></a><span data-ttu-id="f8a9a-108">Требования</span><span class="sxs-lookup"><span data-stu-id="f8a9a-108">Requirements</span></span>

<span data-ttu-id="f8a9a-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f8a9a-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="f8a9a-110">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f8a9a-110">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="f8a9a-111">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f8a9a-111">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="f8a9a-112">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8a9a-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
