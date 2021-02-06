---
description: 'Дополнительные сведения о методе: ICorDebugManagedCallback:: UnloadAssembly'
title: Метод ICorDebugManagedCallback::UnloadAssembly
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback.UnloadAssembly
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback::UnloadAssembly
helpviewer_keywords:
- ICorDebugManagedCallback::UnloadAssembly method [.NET Framework debugging]
- UnloadAssembly method [.NET Framework debugging]
ms.assetid: 6734321c-c8a9-401f-a558-cad715ec4a77
topic_type:
- apiref
ms.openlocfilehash: b1860e90ba2bab1428a0f8559d18801136bbbb39
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99660340"
---
# <a name="icordebugmanagedcallbackunloadassembly-method"></a><span data-ttu-id="023d9-103">Метод ICorDebugManagedCallback::UnloadAssembly</span><span class="sxs-lookup"><span data-stu-id="023d9-103">ICorDebugManagedCallback::UnloadAssembly Method</span></span>

<span data-ttu-id="023d9-104">Уведомляет отладчик о том, что сборка среды CLR была выгружена.</span><span class="sxs-lookup"><span data-stu-id="023d9-104">Notifies the debugger that a common language runtime assembly has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="023d9-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="023d9-105">Syntax</span></span>  
  
```cpp  
HRESULT UnloadAssembly (  
    [in] IcorDebugAppDomain  *pAppDomain,  
    [in] ICorDebugAssembly   *pAssembly  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="023d9-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="023d9-106">Parameters</span></span>  

 `pAppDomain`  
 <span data-ttu-id="023d9-107">окне Указатель на объект ICorDebugAppDomain, представляющий домен приложения, содержащий сборку.</span><span class="sxs-lookup"><span data-stu-id="023d9-107">[in] A pointer to an ICorDebugAppDomain object that represents the application domain that contained the assembly.</span></span>  
  
 `pAssembly`  
 <span data-ttu-id="023d9-108">окне Указатель на объект ICorDebugAssembly, представляющий сборку.</span><span class="sxs-lookup"><span data-stu-id="023d9-108">[in] A pointer to an ICorDebugAssembly object that represents the assembly.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="023d9-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="023d9-109">Remarks</span></span>  

 <span data-ttu-id="023d9-110">Сборка не должна использоваться после этого обратного вызова.</span><span class="sxs-lookup"><span data-stu-id="023d9-110">The assembly should not be used after this callback.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="023d9-111">Требования</span><span class="sxs-lookup"><span data-stu-id="023d9-111">Requirements</span></span>  

 <span data-ttu-id="023d9-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="023d9-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="023d9-113">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="023d9-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="023d9-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="023d9-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="023d9-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="023d9-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="023d9-116">См. также</span><span class="sxs-lookup"><span data-stu-id="023d9-116">See also</span></span>

- [<span data-ttu-id="023d9-117">Метод LoadAssembly</span><span class="sxs-lookup"><span data-stu-id="023d9-117">LoadAssembly Method</span></span>](icordebugmanagedcallback-loadassembly-method.md)
- [<span data-ttu-id="023d9-118">Интерфейс ICorDebugManagedCallback</span><span class="sxs-lookup"><span data-stu-id="023d9-118">ICorDebugManagedCallback Interface</span></span>](icordebugmanagedcallback-interface.md)
