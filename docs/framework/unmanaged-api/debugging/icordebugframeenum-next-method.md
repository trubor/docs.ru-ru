---
description: 'Дополнительные сведения о методе: ICorDebugFrameEnum:: Next'
title: Метод ICorDebugFrameEnum::Next
ms.date: 03/30/2017
api_name:
- ICorDebugFrameEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrameEnum::Next
helpviewer_keywords:
- ICorDebugFrameEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugFrameEnum interface [.NET Framework debugging]
ms.assetid: 0bc96acb-6179-4328-a447-cda562ce9e98
topic_type:
- apiref
ms.openlocfilehash: 67b7dd0282c07358f942990f8915150d6449fd32
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99692671"
---
# <a name="icordebugframeenumnext-method"></a><span data-ttu-id="d0836-103">Метод ICorDebugFrameEnum::Next</span><span class="sxs-lookup"><span data-stu-id="d0836-103">ICorDebugFrameEnum::Next Method</span></span>

<span data-ttu-id="d0836-104">Возвращает указанное число экземпляров ICorDebugFrame, начиная с текущей позиции.</span><span class="sxs-lookup"><span data-stu-id="d0836-104">Gets the specified number of ICorDebugFrame instances, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0836-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d0836-105">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugFrame *frames[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d0836-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="d0836-106">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="d0836-107">окне Число `ICorDebugFrame` извлекаемых экземпляров.</span><span class="sxs-lookup"><span data-stu-id="d0836-107">[in] The number of `ICorDebugFrame` instances to be retrieved.</span></span>  
  
 `frames`  
 <span data-ttu-id="d0836-108">заполняет Массив указателей, каждый из которых указывает на `ICorDebugFrame` объект.</span><span class="sxs-lookup"><span data-stu-id="d0836-108">[out] An array of pointers, each of which points to an `ICorDebugFrame` object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="d0836-109">заполняет Указатель на число `ICorDebugFrame` фактически возвращенных экземпляров.</span><span class="sxs-lookup"><span data-stu-id="d0836-109">[out] A pointer to the number of `ICorDebugFrame` instances actually returned.</span></span> <span data-ttu-id="d0836-110">Это значение может быть равно NULL `celt` , если равно единице.</span><span class="sxs-lookup"><span data-stu-id="d0836-110">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0836-111">Требования</span><span class="sxs-lookup"><span data-stu-id="d0836-111">Requirements</span></span>  

 <span data-ttu-id="d0836-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d0836-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0836-113">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d0836-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d0836-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d0836-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d0836-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0836-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
