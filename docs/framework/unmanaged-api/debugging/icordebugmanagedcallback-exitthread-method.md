---
description: 'Дополнительные сведения о методе: ICorDebugManagedCallback:: ExitThread'
title: Метод ICorDebugManagedCallback::ExitThread
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.ExitThread
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::ExitThread
helpviewer_keywords:
- ExitThread method [.NET Framework debugging]
- ICorDebugManagedCallback::ExitThread method [.NET Framework debugging]
ms.assetid: 62db708b-6cf0-45c5-b897-4b5c75bd2505
topic_type:
- apiref
ms.openlocfilehash: 4c9472d6377246833c7c30f072549da9c44f05d8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790949"
---
# <a name="icordebugmanagedcallbackexitthread-method"></a><span data-ttu-id="53a59-103">Метод ICorDebugManagedCallback::ExitThread</span><span class="sxs-lookup"><span data-stu-id="53a59-103">ICorDebugManagedCallback::ExitThread Method</span></span>

<span data-ttu-id="53a59-104">Уведомляет отладчик о том, что поток, который выполнял управляемый код, завершил работу.</span><span class="sxs-lookup"><span data-stu-id="53a59-104">Notifies the debugger that a thread that was executing managed code has exited.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53a59-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="53a59-105">Syntax</span></span>  
  
```cpp  
HRESULT ExitThread (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugThread    *thread  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="53a59-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="53a59-106">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="53a59-107">окне Указатель на объект ICorDebugAppDomain, представляющий домен приложения, содержащий управляемый поток.</span><span class="sxs-lookup"><span data-stu-id="53a59-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain containing the managed thread.</span></span>  
  
 `thread`  
 <span data-ttu-id="53a59-108">окне Указатель на объект ICorDebugThread, представляющий управляемый поток.</span><span class="sxs-lookup"><span data-stu-id="53a59-108">[in] A pointer to an ICorDebugThread object that represents the managed thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="53a59-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="53a59-109">Remarks</span></span>  

 <span data-ttu-id="53a59-110">После `ExitThread` запуска обратного вызова поток больше не будет отображаться в перечислениях потоков.</span><span class="sxs-lookup"><span data-stu-id="53a59-110">Once the `ExitThread` callback is fired, the thread will no longer appear in thread enumerations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53a59-111">Требования</span><span class="sxs-lookup"><span data-stu-id="53a59-111">Requirements</span></span>  

 <span data-ttu-id="53a59-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="53a59-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53a59-113">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="53a59-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="53a59-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="53a59-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="53a59-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53a59-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53a59-116">См. также</span><span class="sxs-lookup"><span data-stu-id="53a59-116">See also</span></span>

- [<span data-ttu-id="53a59-117">Интерфейс ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="53a59-117">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
