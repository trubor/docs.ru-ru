---
description: 'Дополнительные сведения о методе: ICorDebugManagedCallback:: LoadAssembly'
title: Метод ICorDebugManagedCallback::LoadAssembly
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.LoadAssembly
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::LoadAssembly
helpviewer_keywords:
- LoadAssembly method [.NET Framework debugging]
- ICorDebugManagedCallback::LoadAssembly method [.NET Framework debugging]
ms.assetid: 55cb673a-e240-43a6-a406-6912e7c0fe66
topic_type:
- apiref
ms.openlocfilehash: b90391f3c6286323db11dadae841db38f9b785a7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99722806"
---
# <a name="icordebugmanagedcallbackloadassembly-method"></a><span data-ttu-id="dad82-103">Метод ICorDebugManagedCallback::LoadAssembly</span><span class="sxs-lookup"><span data-stu-id="dad82-103">ICorDebugManagedCallback::LoadAssembly Method</span></span>

<span data-ttu-id="dad82-104">Уведомляет отладчик о том, что сборка среды CLR была успешно загружена.</span><span class="sxs-lookup"><span data-stu-id="dad82-104">Notifies the debugger that a common language runtime (CLR) assembly has been successfully loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dad82-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="dad82-105">Syntax</span></span>  
  
```cpp  
HRESULT LoadAssembly (  
    [in] ICorDebugAppDomain *pAppDomain,  
    [in] ICorDebugAssembly  *pAssembly  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="dad82-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="dad82-106">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="dad82-107">окне Указатель на объект ICorDebugAppDomain, представляющий домен приложения, в который была загружена сборка.</span><span class="sxs-lookup"><span data-stu-id="dad82-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain into which the assembly has been loaded.</span></span>  
  
 `pAssembly`  
 <span data-ttu-id="dad82-108">окне Указатель на объект ICorDebugAssembly, представляющий сборку.</span><span class="sxs-lookup"><span data-stu-id="dad82-108">[in] A pointer to an ICorDebugAssembly object that represents the assembly.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dad82-109">Требования</span><span class="sxs-lookup"><span data-stu-id="dad82-109">Requirements</span></span>  

 <span data-ttu-id="dad82-110">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dad82-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dad82-111">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dad82-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dad82-112">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dad82-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dad82-113">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dad82-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dad82-114">См. также</span><span class="sxs-lookup"><span data-stu-id="dad82-114">See also</span></span>

- [<span data-ttu-id="dad82-115">Метод UnloadAssembly</span><span class="sxs-lookup"><span data-stu-id="dad82-115">UnloadAssembly Method</span></span>](icordebugmanagedcallback-unloadassembly-method.md)
- [<span data-ttu-id="dad82-116">Интерфейс ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="dad82-116">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
