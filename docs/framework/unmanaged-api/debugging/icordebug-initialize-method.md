---
description: 'Дополнительные сведения о методе ICorDebug:: Initialize'
title: Метод ICorDebug::Initialize
ms.date: 03/30/2017
api_name:
- ICorDebug.Initialize
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::Initialize
helpviewer_keywords:
- Initialize method, ICorDebug interface [.NET Framework debugging]
- ICorDebug::Initialize method [.NET Framework debugging]
ms.assetid: 6fae3b23-5c9f-47c0-85d8-6bb75e050786
topic_type:
- apiref
ms.openlocfilehash: 6b6ddd8c1c21470477420909bcf75906b5731ee6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791599"
---
# <a name="icordebuginitialize-method"></a><span data-ttu-id="5fb96-103">Метод ICorDebug::Initialize</span><span class="sxs-lookup"><span data-stu-id="5fb96-103">ICorDebug::Initialize Method</span></span>

<span data-ttu-id="5fb96-104">Выполняет инициализацию объекта `ICorDebug`.</span><span class="sxs-lookup"><span data-stu-id="5fb96-104">Initializes the `ICorDebug` object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5fb96-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="5fb96-105">Syntax</span></span>  
  
```cpp  
HRESULT Initialize ();  
```  
  
## <a name="remarks"></a><span data-ttu-id="5fb96-106">Remarks</span><span class="sxs-lookup"><span data-stu-id="5fb96-106">Remarks</span></span>  

 <span data-ttu-id="5fb96-107">Отладчик должен вызвать `Initialize` во время создания, чтобы инициализировать службы отладки.</span><span class="sxs-lookup"><span data-stu-id="5fb96-107">The debugger must call `Initialize` at creation time to initialize the debugging services.</span></span> <span data-ttu-id="5fb96-108">Этот метод должен вызываться до вызова любого другого метода `ICorDebug` .</span><span class="sxs-lookup"><span data-stu-id="5fb96-108">This method must be called before any other method on `ICorDebug` is called.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5fb96-109">Требования</span><span class="sxs-lookup"><span data-stu-id="5fb96-109">Requirements</span></span>  

 <span data-ttu-id="5fb96-110">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5fb96-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5fb96-111">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5fb96-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5fb96-112">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5fb96-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5fb96-113">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5fb96-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fb96-114">См. также</span><span class="sxs-lookup"><span data-stu-id="5fb96-114">See also</span></span>

- [<span data-ttu-id="5fb96-115">Интерфейс ICorDebug</span><span class="sxs-lookup"><span data-stu-id="5fb96-115">ICorDebug Interface</span></span>](icordebug-interface.md)
