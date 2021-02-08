---
description: 'Дополнительные сведения о методе: ICorDebugThread4:: GetCurrentCustomDebuggerNotification'
title: Метод ICorDebugThread4::GetCurrentCustomDebuggerNotification
ms.date: 03/30/2017
api_name:
- ICorDebugThread4.GetCurrentCustomDebuggerNotification Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread4::GetCurrentCustomDebuggerNotification
helpviewer_keywords:
- GetCurrentCustomDebuggerNotification method [.NET Framework debugging]
- ICorDebugThread4::GetCurrentCustomDebuggerNotification method [.NET Framework debugging]
ms.assetid: 57e0f2d2-5f0e-4e2d-99ec-3f26632eb693
topic_type:
- apiref
ms.openlocfilehash: 20d9449e98b9ab91dbdec84ba026e91514d5b3cc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800946"
---
# <a name="icordebugthread4getcurrentcustomdebuggernotification-method"></a><span data-ttu-id="60df7-103">Метод ICorDebugThread4::GetCurrentCustomDebuggerNotification</span><span class="sxs-lookup"><span data-stu-id="60df7-103">ICorDebugThread4::GetCurrentCustomDebuggerNotification Method</span></span>

<span data-ttu-id="60df7-104">Возвращает текущий объект [ICorDebugManagedCallback3:: CustomNotification](icordebugmanagedcallback3-customnotification-method.md) в текущем потоке.</span><span class="sxs-lookup"><span data-stu-id="60df7-104">Gets the current [ICorDebugManagedCallback3::CustomNotification](icordebugmanagedcallback3-customnotification-method.md) object on the current thread.</span></span>

## <a name="syntax"></a><span data-ttu-id="60df7-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="60df7-105">Syntax</span></span>

```cpp
HRESULT GetCurrentCustomDebuggerNotification(
    [out] ICorDebugValue **ppNotificationObject
    );
```

## <a name="parameters"></a><span data-ttu-id="60df7-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="60df7-106">Parameters</span></span>

`ppNotificationObject`\
<span data-ttu-id="60df7-107">заполняет Указатель на текущий `ICorDebugManagedCallback3::CustomNotification` объект в текущем потоке.</span><span class="sxs-lookup"><span data-stu-id="60df7-107">[out] A pointer to the current `ICorDebugManagedCallback3::CustomNotification` object on the current thread.</span></span>

## <a name="remarks"></a><span data-ttu-id="60df7-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="60df7-108">Remarks</span></span>

<span data-ttu-id="60df7-109">Значение `ppNotificationObject` равно null, если метод не вызывается из `ICorDebugManagedCallback3::CustomNotification` обратного вызова или если текущий объект уведомления не существует.</span><span class="sxs-lookup"><span data-stu-id="60df7-109">The value of `ppNotificationObject` is null if the method is not called from within a `ICorDebugManagedCallback3::CustomNotification` callback, or if no current notification object exists.</span></span>

## <a name="requirements"></a><span data-ttu-id="60df7-110">Требования</span><span class="sxs-lookup"><span data-stu-id="60df7-110">Requirements</span></span>

<span data-ttu-id="60df7-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="60df7-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="60df7-112">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="60df7-112">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="60df7-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="60df7-113">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="60df7-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="60df7-114">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="60df7-115">См. также</span><span class="sxs-lookup"><span data-stu-id="60df7-115">See also</span></span>

- [<span data-ttu-id="60df7-116">Интерфейс ICorDebugThread4</span><span class="sxs-lookup"><span data-stu-id="60df7-116">ICorDebugThread4 Interface</span></span>](icordebugthread4-interface.md)
- [<span data-ttu-id="60df7-117">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="60df7-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="60df7-118">Отладка</span><span class="sxs-lookup"><span data-stu-id="60df7-118">Debugging</span></span>](index.md)
