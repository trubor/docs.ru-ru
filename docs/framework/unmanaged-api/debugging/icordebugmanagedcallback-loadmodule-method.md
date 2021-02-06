---
description: 'Дополнительные сведения о методе: ICorDebugManagedCallback:: LoadModule'
title: Метод ICorDebugManagedCallback::LoadModule
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.LoadModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LoadModule
helpviewer_keywords:
- ICorDebugManagedCallback::LoadModule method [.NET Framework debugging]
- LoadModule method [.NET Framework debugging]
ms.assetid: 66ec04e9-87cb-42ce-9720-81522abb5d5a
topic_type:
- apiref
ms.openlocfilehash: 9a547d384b3f450054ebc70072664c6dcfb5992f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99660509"
---
# <a name="icordebugmanagedcallbackloadmodule-method"></a><span data-ttu-id="a02a0-103">Метод ICorDebugManagedCallback::LoadModule</span><span class="sxs-lookup"><span data-stu-id="a02a0-103">ICorDebugManagedCallback::LoadModule Method</span></span>

<span data-ttu-id="a02a0-104">Уведомляет отладчик о том, что модуль среды CLR успешно загружен.</span><span class="sxs-lookup"><span data-stu-id="a02a0-104">Notifies the debugger that a common language runtime (CLR) module has been successfully loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a02a0-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a02a0-105">Syntax</span></span>  
  
```cpp  
HRESULT LoadModule (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugModule    *pModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a02a0-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="a02a0-106">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="a02a0-107">окне Указатель на объект ICorDebugAppDomain, представляющий домен приложения, в который был загружен модуль.</span><span class="sxs-lookup"><span data-stu-id="a02a0-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain into which the module has been loaded.</span></span>  
  
 `pModule`  
 <span data-ttu-id="a02a0-108">окне Указатель на объект ICorDebugModule, представляющий модуль CLR.</span><span class="sxs-lookup"><span data-stu-id="a02a0-108">[in] A pointer to an ICorDebugModule object that represents the CLR module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a02a0-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="a02a0-109">Remarks</span></span>  

 <span data-ttu-id="a02a0-110">`LoadModule`Обратный вызов предоставляет подходящее время для проверки метаданных модуля, установки флагов JIT-компилятора или включения или отключения обратных вызовов при загрузке класса для модуля.</span><span class="sxs-lookup"><span data-stu-id="a02a0-110">The `LoadModule` callback provides an appropriate time to examine metadata for the module, set just-in-time (JIT) compiler flags, or enable or disable class loading callbacks for the module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a02a0-111">Требования</span><span class="sxs-lookup"><span data-stu-id="a02a0-111">Requirements</span></span>  

 <span data-ttu-id="a02a0-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a02a0-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a02a0-113">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a02a0-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a02a0-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a02a0-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a02a0-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a02a0-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a02a0-116">См. также</span><span class="sxs-lookup"><span data-stu-id="a02a0-116">See also</span></span>

- [<span data-ttu-id="a02a0-117">Метод UnloadModule</span><span class="sxs-lookup"><span data-stu-id="a02a0-117">UnloadModule Method</span></span>](icordebugmanagedcallback-unloadmodule-method.md)
- [<span data-ttu-id="a02a0-118">Интерфейс ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="a02a0-118">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
