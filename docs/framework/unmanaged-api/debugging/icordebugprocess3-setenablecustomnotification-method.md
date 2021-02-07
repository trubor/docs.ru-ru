---
description: 'Дополнительные сведения о методе: ICorDebugProcess3:: SetEnableCustomNotification'
title: Метод ICorDebugProcess3::SetEnableCustomNotification
ms.date: 03/30/2017
api_name:
- ICorDebugProcess3.SetEnableCustomNotification Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess3::SetEnableCustomNotification
helpviewer_keywords:
- ICorDebugProcess3::SetEnableCustomNotification method [.NET Framework debugging]
- SetEnableCustomNotification method [.NET Framework debugging]
ms.assetid: afd88ee9-2589-4461-a75a-9b6fe55a2525
topic_type:
- apiref
ms.openlocfilehash: 71d1d23b1fa4ba16b26b7c9bacf7fb5cec5e5074
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99746479"
---
# <a name="icordebugprocess3setenablecustomnotification-method"></a><span data-ttu-id="92918-103">Метод ICorDebugProcess3::SetEnableCustomNotification</span><span class="sxs-lookup"><span data-stu-id="92918-103">ICorDebugProcess3::SetEnableCustomNotification Method</span></span>

<span data-ttu-id="92918-104">Включает и отключает настраиваемые уведомления отладчика указанного типа.</span><span class="sxs-lookup"><span data-stu-id="92918-104">Enables and disables custom debugger notifications of the specified type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92918-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="92918-105">Syntax</span></span>  
  
```cpp  
HRESULT SetEnableCustomNotification(ICorDebugClass * pClass,  
                                    BOOL fEnable);  
```  
  
## <a name="parameters"></a><span data-ttu-id="92918-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="92918-106">Parameters</span></span>  

 `pClass`  
 <span data-ttu-id="92918-107">окне Тип, указывающий пользовательские уведомления отладчика.</span><span class="sxs-lookup"><span data-stu-id="92918-107">[in] The type that specifies custom debugger notifications.</span></span>  
  
 `fEnable`  
 <span data-ttu-id="92918-108">[входные] `true` для включения настраиваемых уведомлений отладчика; `false` для отключения уведомлений.</span><span class="sxs-lookup"><span data-stu-id="92918-108">[in] `true` to enable custom debugger notifications; `false` to disable notifications.</span></span> <span data-ttu-id="92918-109">Значение по умолчанию — `false`.</span><span class="sxs-lookup"><span data-stu-id="92918-109">The default value is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="92918-110">Примечания</span><span class="sxs-lookup"><span data-stu-id="92918-110">Remarks</span></span>  

 <span data-ttu-id="92918-111">Если параметр `fEnable` имеет значение `true` , вызовы <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> метода активируют обратный вызов [ICorDebugManagedCallback3:: CustomNotification](icordebugmanagedcallback3-customnotification-method.md) .</span><span class="sxs-lookup"><span data-stu-id="92918-111">When `fEnable` is set to `true`, calls to the <xref:System.Diagnostics.Debugger.NotifyOfCrossThreadDependency%2A?displayProperty=nameWithType> method trigger an [ICorDebugManagedCallback3::CustomNotification](icordebugmanagedcallback3-customnotification-method.md) callback.</span></span> <span data-ttu-id="92918-112">По умолчанию уведомления отключены. Поэтому в отладчике должны быть указаны все типы уведомлений, о которых он знает, и требуется его обработку.</span><span class="sxs-lookup"><span data-stu-id="92918-112">Notifications are disabled by default; therefore, the debugger must specify any notification types it knows about and wants to handle.</span></span> <span data-ttu-id="92918-113">Так как класс [ICorDebugClass](icordebug-interface.md) ограничивается доменом приложения, отладчик должен вызвать `SetEnableCustomNotification` для каждого домена приложения в процессе, если он хочет получить уведомление во всем процессе.</span><span class="sxs-lookup"><span data-stu-id="92918-113">Because the [ICorDebugClass](icordebug-interface.md) class is scoped by application domain, the debugger must call `SetEnableCustomNotification` for every application domain in the process if it wants to receive the notification across the entire process.</span></span>  
  
 <span data-ttu-id="92918-114">Начиная с платформа .NET Framework 4, единственным поддерживаемым уведомлением является уведомление о зависимости между потоками.</span><span class="sxs-lookup"><span data-stu-id="92918-114">Starting with the .NET Framework 4, the only supported notification is a cross-thread dependency notification.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92918-115">Требования</span><span class="sxs-lookup"><span data-stu-id="92918-115">Requirements</span></span>  

 <span data-ttu-id="92918-116">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92918-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92918-117">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="92918-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="92918-118">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="92918-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="92918-119">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92918-119">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92918-120">См. также</span><span class="sxs-lookup"><span data-stu-id="92918-120">See also</span></span>

- [<span data-ttu-id="92918-121">Интерфейс ICorDebugProcess3</span><span class="sxs-lookup"><span data-stu-id="92918-121">ICorDebugProcess3 Interface</span></span>](icordebugprocess3-interface.md)
- [<span data-ttu-id="92918-122">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="92918-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="92918-123">Отладка</span><span class="sxs-lookup"><span data-stu-id="92918-123">Debugging</span></span>](index.md)
