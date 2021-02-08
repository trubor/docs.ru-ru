---
description: 'Дополнительные сведения о методе: ICorDebugInstanceFieldSymbol:: методом offset'
title: Метод ICorDebugInstanceFieldSymbol::GetOffset
ms.date: 03/30/2017
ms.assetid: 7e470150-2b92-4425-989c-315f48964fd2
ms.openlocfilehash: 4a877b2f78adfac5c54694ab306fd7db60f266f0
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791170"
---
# <a name="icordebuginstancefieldsymbolgetoffset-method"></a><span data-ttu-id="92150-103">Метод ICorDebugInstanceFieldSymbol::GetOffset</span><span class="sxs-lookup"><span data-stu-id="92150-103">ICorDebugInstanceFieldSymbol::GetOffset Method</span></span>

<span data-ttu-id="92150-104">Возвращает смещение в байтах этого поля экземпляра в его родительском классе.</span><span class="sxs-lookup"><span data-stu-id="92150-104">Gets the offset in bytes of this instance field in its parent class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92150-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="92150-105">Syntax</span></span>  
  
```cpp  
HRESULT GetOffset(  
   [out] ULONG32 *pcbOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="92150-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="92150-106">Parameters</span></span>  

 `pcbOffset`  
 <span data-ttu-id="92150-107">Указатель на число байтов, на которое это поле экземпляра смещается в своем родительском классе.</span><span class="sxs-lookup"><span data-stu-id="92150-107">A pointer to the number of bytes that this instance field is offset in its parent class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="92150-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="92150-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="92150-109">Этот метод доступен только в машинном коде .NET.</span><span class="sxs-lookup"><span data-stu-id="92150-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92150-110">Требования</span><span class="sxs-lookup"><span data-stu-id="92150-110">Requirements</span></span>  

 <span data-ttu-id="92150-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92150-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92150-112">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="92150-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="92150-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="92150-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="92150-114">**Платформа .NET Framework версии:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92150-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92150-115">См. также</span><span class="sxs-lookup"><span data-stu-id="92150-115">See also</span></span>

- [<span data-ttu-id="92150-116">Интерфейс ICorDebugInstanceFieldSymbol</span><span class="sxs-lookup"><span data-stu-id="92150-116">ICorDebugInstanceFieldSymbol Interface</span></span>](icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="92150-117">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="92150-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
