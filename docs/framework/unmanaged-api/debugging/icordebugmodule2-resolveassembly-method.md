---
description: 'Дополнительные сведения о методе: ICorDebugModule2:: Ресолвеассембли'
title: Метод ICorDebugModule2::ResolveAssembly
ms.date: 03/30/2017
api_name:
- ICorDebugModule2.ResolveAssembly
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule2::ResolveAssembly
helpviewer_keywords:
- ICorDebugModule2::ResolveAssembly method [.NET Framework debugging]
- ResolveAssembly method [.NET Framework debugging]
ms.assetid: ddf9085c-7161-44bd-9609-cd2732b9009f
topic_type:
- apiref
ms.openlocfilehash: fba53b8ff76e4d3deb1876d2a20a7a2edc20bd06
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99722598"
---
# <a name="icordebugmodule2resolveassembly-method"></a><span data-ttu-id="0e997-103">Метод ICorDebugModule2::ResolveAssembly</span><span class="sxs-lookup"><span data-stu-id="0e997-103">ICorDebugModule2::ResolveAssembly Method</span></span>

<span data-ttu-id="0e997-104">Разрешает сборку, на которую ссылается указанный токен метаданных.</span><span class="sxs-lookup"><span data-stu-id="0e997-104">Resolves the assembly referenced by the specified metadata token.</span></span>

## <a name="syntax"></a><span data-ttu-id="0e997-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0e997-105">Syntax</span></span>

```cpp
HRESULT ResolveAssembly (
    [in]  mdToken             tkAssemblyRef,
    [out] ICorDebugAssembly   **ppAssembly
);
```

## <a name="parameters"></a><span data-ttu-id="0e997-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="0e997-106">Parameters</span></span>

`tkAssemblyRef`\
<span data-ttu-id="0e997-107">окне `mdToken` Значение, которое ссылается на сборку.</span><span class="sxs-lookup"><span data-stu-id="0e997-107">[in] An `mdToken` value that references the assembly.</span></span>

`ppAssembly`\
<span data-ttu-id="0e997-108">заполняет Указатель на адрес объекта ICorDebugAssembly, который представляет сборку.</span><span class="sxs-lookup"><span data-stu-id="0e997-108">[out] A pointer to the address of an ICorDebugAssembly object that represents the assembly.</span></span>

## <a name="remarks"></a><span data-ttu-id="0e997-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="0e997-109">Remarks</span></span>

<span data-ttu-id="0e997-110">Если сборка еще не загружена при `ResolveAssembly` вызове метода, возвращается значение HRESULT, равное CORDBG_E_CANNOT_RESOLVE_ASSEMBLY.</span><span class="sxs-lookup"><span data-stu-id="0e997-110">If the assembly is not already loaded when `ResolveAssembly` is called, an HRESULT value of CORDBG_E_CANNOT_RESOLVE_ASSEMBLY is returned.</span></span>

## <a name="requirements"></a><span data-ttu-id="0e997-111">Требования</span><span class="sxs-lookup"><span data-stu-id="0e997-111">Requirements</span></span>

<span data-ttu-id="0e997-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0e997-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="0e997-113">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0e997-113">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="0e997-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0e997-114">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="0e997-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0e997-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
