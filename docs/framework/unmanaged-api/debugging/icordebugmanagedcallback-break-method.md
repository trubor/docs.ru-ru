---
description: 'Дополнительные сведения о методе: ICorDebugManagedCallback:: break'
title: Метод ICorDebugManagedCallback::Break
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.Break
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::Break
helpviewer_keywords:
- Break method [.NET Framework debugging]
- ICorDebugManagedCallback::Break method [.NET Framework debugging]
ms.assetid: 7d78a301-82b3-43b2-9d65-3cda3285ae97
topic_type:
- apiref
ms.openlocfilehash: 2ef273a693291685c4c3a0ce2b20ed45613e3376
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801219"
---
# <a name="icordebugmanagedcallbackbreak-method"></a><span data-ttu-id="3915e-103">Метод ICorDebugManagedCallback::Break</span><span class="sxs-lookup"><span data-stu-id="3915e-103">ICorDebugManagedCallback::Break Method</span></span>

<span data-ttu-id="3915e-104">Уведомляет отладчик о <xref:System.Reflection.Emit.OpCodes.Break> выполнении инструкции в потоке кода.</span><span class="sxs-lookup"><span data-stu-id="3915e-104">Notifies the debugger when a <xref:System.Reflection.Emit.OpCodes.Break> instruction in the code stream is executed.</span></span>

## <a name="syntax"></a><span data-ttu-id="3915e-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="3915e-105">Syntax</span></span>

```cpp
HRESULT Break (
    [in] ICorDebugAppDomain *pAppDomain,
    [in] ICorDebugThread    *thread
);
```

## <a name="parameters"></a><span data-ttu-id="3915e-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="3915e-106">Parameters</span></span>

`pAppDomain`\
<span data-ttu-id="3915e-107">окне Указатель на объект ICorDebugAppDomain, представляющий домен приложения, содержащий инструкцию Break.</span><span class="sxs-lookup"><span data-stu-id="3915e-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contains the break instruction.</span></span>

`thread`\
<span data-ttu-id="3915e-108">окне Указатель на объект ICorDebugThread, представляющий поток, содержащий инструкцию Break.</span><span class="sxs-lookup"><span data-stu-id="3915e-108">[in] A pointer to an ICorDebugThread object that represents the thread that contains the break instruction.</span></span>

## <a name="requirements"></a><span data-ttu-id="3915e-109">Требования</span><span class="sxs-lookup"><span data-stu-id="3915e-109">Requirements</span></span>

<span data-ttu-id="3915e-110">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3915e-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="3915e-111">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3915e-111">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="3915e-112">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3915e-112">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="3915e-113">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3915e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="3915e-114">См. также</span><span class="sxs-lookup"><span data-stu-id="3915e-114">See also</span></span>

- [<span data-ttu-id="3915e-115">Интерфейс ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="3915e-115">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
