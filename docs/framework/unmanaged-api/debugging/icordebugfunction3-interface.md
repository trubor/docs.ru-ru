---
description: 'Дополнительные сведения о: интерфейс ICorDebugFunction3'
title: Интерфейс ICorDebugFunction3
ms.date: 03/30/2017
api_name:
- ICorDebugFunction3
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: b22717b9-ead5-4eea-887e-789b52d613dc
topic_type:
- apiref
ms.openlocfilehash: f6f3ce78fbb0ca7efb6ba6a95da20f8c698b923c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99692073"
---
# <a name="icordebugfunction3-interface"></a><span data-ttu-id="4ff38-103">Интерфейс ICorDebugFunction3</span><span class="sxs-lookup"><span data-stu-id="4ff38-103">ICorDebugFunction3 Interface</span></span>

<span data-ttu-id="4ff38-104">[Поддерживается в .NET Framework 4.5.2 и более поздних версиях.]</span><span class="sxs-lookup"><span data-stu-id="4ff38-104">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="4ff38-105">Логически расширяет интерфейс ICorDebugFunction для предоставления доступа к коду из запроса ReJIT.</span><span class="sxs-lookup"><span data-stu-id="4ff38-105">Logically extends the ICorDebugFunction interface to provide access to code from a ReJIT request.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4ff38-106">Методы</span><span class="sxs-lookup"><span data-stu-id="4ff38-106">Methods</span></span>  
  
|<span data-ttu-id="4ff38-107">Метод</span><span class="sxs-lookup"><span data-stu-id="4ff38-107">Method</span></span>|<span data-ttu-id="4ff38-108">Описание</span><span class="sxs-lookup"><span data-stu-id="4ff38-108">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4ff38-109">Метод GetActiveReJitRequestILCode</span><span class="sxs-lookup"><span data-stu-id="4ff38-109">GetActiveReJitRequestILCode Method</span></span>](icordebugfunction3-getactiverejitrequestilcode-method.md)|<span data-ttu-id="4ff38-110">Возвращает указатель интерфейса на [икордебугилкоде](icordebugilcode-interface.md) , содержащий Il из активного запроса ReJIT.</span><span class="sxs-lookup"><span data-stu-id="4ff38-110">Gets an interface pointer to an [ICorDebugILCode](icordebugilcode-interface.md) that contains the IL from an active ReJIT request.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4ff38-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="4ff38-111">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4ff38-112">Требования</span><span class="sxs-lookup"><span data-stu-id="4ff38-112">Requirements</span></span>  

 <span data-ttu-id="4ff38-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4ff38-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4ff38-114">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4ff38-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4ff38-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4ff38-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4ff38-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4ff38-116">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ff38-117">См. также</span><span class="sxs-lookup"><span data-stu-id="4ff38-117">See also</span></span>

- [<span data-ttu-id="4ff38-118">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="4ff38-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="4ff38-119">Отладка</span><span class="sxs-lookup"><span data-stu-id="4ff38-119">Debugging</span></span>](index.md)
- [<span data-ttu-id="4ff38-120">ReJIT: руководство по How-To</span><span class="sxs-lookup"><span data-stu-id="4ff38-120">ReJIT: A How-To Guide</span></span>](/archive/blogs/davbr/rejit-a-how-to-guide)
