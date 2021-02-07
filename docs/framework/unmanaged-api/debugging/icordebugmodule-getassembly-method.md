---
description: 'Дополнительные сведения о методе: ICorDebugModule:: Assembly'
title: Метод ICorDebugModule::GetAssembly
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetAssembly
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetAssembly
helpviewer_keywords:
- ICorDebugModule::GetAssembly method [.NET Framework debugging]
- GetAssembly method [.NET Framework debugging]
ms.assetid: 989762c4-3d15-4485-b8ee-69e0fa8ec895
topic_type:
- apiref
ms.openlocfilehash: 88bda923cd4c3ebfa5da6b3343e1cead4cebbad9
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99722622"
---
# <a name="icordebugmodulegetassembly-method"></a><span data-ttu-id="d4147-103">Метод ICorDebugModule::GetAssembly</span><span class="sxs-lookup"><span data-stu-id="d4147-103">ICorDebugModule::GetAssembly Method</span></span>

<span data-ttu-id="d4147-104">Возвращает содержащуюся сборку для этого модуля.</span><span class="sxs-lookup"><span data-stu-id="d4147-104">Gets the containing assembly for this module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4147-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d4147-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAssembly(  
    [out] ICorDebugAssembly **ppAssembly  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d4147-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="d4147-106">Parameters</span></span>  

 `ppAssembly`  
 <span data-ttu-id="d4147-107">заполняет Указатель на объект ICorDebugAssembly, представляющий сборку, содержащую этот модуль.</span><span class="sxs-lookup"><span data-stu-id="d4147-107">[out] A pointer to an ICorDebugAssembly object that represents the assembly containing this module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4147-108">Требования</span><span class="sxs-lookup"><span data-stu-id="d4147-108">Requirements</span></span>  

 <span data-ttu-id="d4147-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d4147-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4147-110">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d4147-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d4147-111">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d4147-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d4147-112">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4147-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
