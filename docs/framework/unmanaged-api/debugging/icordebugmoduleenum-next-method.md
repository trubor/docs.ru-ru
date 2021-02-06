---
description: 'Дополнительные сведения о методе: Икордебугмодулинум:: Next'
title: Метод ICorDebugModuleEnum::Next
ms.date: 03/30/2017
api_name:
- ICorDebugModuleEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModuleEnum::Next
helpviewer_keywords:
- ICorDebugModuleEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugModuleEnum interface [.NET Framework debugging]
ms.assetid: 9ff3fcd6-38fe-41f8-bfd3-f0ab6c7d77ca
topic_type:
- apiref
ms.openlocfilehash: ed9558edad80c67e7bf3febb10c3adcd027e180a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99650278"
---
# <a name="icordebugmoduleenumnext-method"></a><span data-ttu-id="4a508-103">Метод ICorDebugModuleEnum::Next</span><span class="sxs-lookup"><span data-stu-id="4a508-103">ICorDebugModuleEnum::Next Method</span></span>

<span data-ttu-id="4a508-104">Возвращает количество экземпляров ICorDebugModule, заданных `celt` из перечисления, начиная с текущей позиции.</span><span class="sxs-lookup"><span data-stu-id="4a508-104">Gets the number of "ICorDebugModule" instances specified by `celt` from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a508-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="4a508-105">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in]  ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugModule *modules[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4a508-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="4a508-106">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="4a508-107">окне Число `ICorDebugModule` извлекаемых экземпляров.</span><span class="sxs-lookup"><span data-stu-id="4a508-107">[in] The number of `ICorDebugModule` instances to be retrieved.</span></span>  
  
 `modules`  
 <span data-ttu-id="4a508-108">заполняет Массив указателей, каждый из которых указывает на `ICorDebugModule` объект.</span><span class="sxs-lookup"><span data-stu-id="4a508-108">[out] An array of pointers, each of which points to an `ICorDebugModule` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="4a508-109">заполняет Указатель на число `ICorDebugModule` фактически возвращенных экземпляров.</span><span class="sxs-lookup"><span data-stu-id="4a508-109">[out] Pointer to the number of `ICorDebugModule` instances actually returned.</span></span> <span data-ttu-id="4a508-110">Это значение может быть равно NULL `celt` , если равно единице.</span><span class="sxs-lookup"><span data-stu-id="4a508-110">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a508-111">Требования</span><span class="sxs-lookup"><span data-stu-id="4a508-111">Requirements</span></span>  

 <span data-ttu-id="4a508-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4a508-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a508-113">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4a508-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4a508-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4a508-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4a508-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a508-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a508-116">См. также</span><span class="sxs-lookup"><span data-stu-id="4a508-116">See also</span></span>
