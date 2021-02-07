---
description: 'Дополнительные сведения о методе: Икордебугчаиненум:: Next'
title: Метод ICorDebugChainEnum::Next
ms.date: 03/30/2017
api_name:
- ICorDebugChainEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChainEnum::Next
helpviewer_keywords:
- ICorDebugChainEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugChainEnum interface [.NET Framework debugging]
ms.assetid: 6b791351-bcc5-4ddd-9cab-eff2f7dd5142
topic_type:
- apiref
ms.openlocfilehash: 5ab6665eb5af6d9f145f9aab67aeb75b4769e7e3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99711574"
---
# <a name="icordebugchainenumnext-method"></a><span data-ttu-id="53015-103">Метод ICorDebugChainEnum::Next</span><span class="sxs-lookup"><span data-stu-id="53015-103">ICorDebugChainEnum::Next Method</span></span>

<span data-ttu-id="53015-104">Возвращает указанное число экземпляров ICorDebugChain из перечисления, начиная с текущей позиции.</span><span class="sxs-lookup"><span data-stu-id="53015-104">Gets the specified number of ICorDebugChain instances from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53015-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="53015-105">Syntax</span></span>  
  
```cpp  
HRESULT Next (  
    [in] ULONG  celt,  
    [out, size_is(celt), length_is(*pceltFetched)]  
        ICorDebugChain *chains[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="53015-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="53015-106">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="53015-107">окне Число `ICorDebugChain` извлекаемых экземпляров.</span><span class="sxs-lookup"><span data-stu-id="53015-107">[in] The number of `ICorDebugChain` instances to be retrieved.</span></span>  
  
 `chains`  
 <span data-ttu-id="53015-108">заполняет Массив указателей, каждый из которых указывает на `ICorDebugChain` объект, представляющий цепочку.</span><span class="sxs-lookup"><span data-stu-id="53015-108">[out] An array of pointers, each of which points to an `ICorDebugChain` object that represents a chain.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="53015-109">заполняет Указатель на число `ICorDebugChain` фактически возвращенных экземпляров.</span><span class="sxs-lookup"><span data-stu-id="53015-109">[out] A pointer to the number of `ICorDebugChain` instances actually returned.</span></span> <span data-ttu-id="53015-110">Это значение может быть равно NULL `celt` , если равно единице.</span><span class="sxs-lookup"><span data-stu-id="53015-110">This value may be null if `celt` is one.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53015-111">Требования</span><span class="sxs-lookup"><span data-stu-id="53015-111">Requirements</span></span>  

 <span data-ttu-id="53015-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="53015-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53015-113">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="53015-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="53015-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="53015-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="53015-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53015-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
