---
description: 'Дополнительные сведения о методе: Икордебугстатикфиелдсимбол::/Address'
title: Метод ICorDebugStaticFieldSymbol::GetAddress
ms.date: 03/30/2017
ms.assetid: 5a6c9a5a-ec72-4c40-a9c3-cee7baa63687
ms.openlocfilehash: 1944839ff6afc31dc3667111397cbb088b95b412
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801011"
---
# <a name="icordebugstaticfieldsymbolgetaddress-method"></a><span data-ttu-id="d627b-103">Метод ICorDebugStaticFieldSymbol::GetAddress</span><span class="sxs-lookup"><span data-stu-id="d627b-103">ICorDebugStaticFieldSymbol::GetAddress Method</span></span>

<span data-ttu-id="d627b-104">Получает адрес статического поля.</span><span class="sxs-lookup"><span data-stu-id="d627b-104">Gets the address of a static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d627b-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d627b-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAddress(  
   [out] CORDB_ADDRESS *pRVA  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d627b-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="d627b-106">Parameters</span></span>  

 <span data-ttu-id="d627b-107">pRVA</span><span class="sxs-lookup"><span data-stu-id="d627b-107">pRVA</span></span>  
 <span data-ttu-id="d627b-108">[out] Указатель на относительный виртуальный адрес (RVA) статического поля.</span><span class="sxs-lookup"><span data-stu-id="d627b-108">[out] A pointer to the relative virtual address (RVA) of the static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d627b-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="d627b-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d627b-110">Этот метод доступен только в машинном коде .NET.</span><span class="sxs-lookup"><span data-stu-id="d627b-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d627b-111">Требования</span><span class="sxs-lookup"><span data-stu-id="d627b-111">Requirements</span></span>  

 <span data-ttu-id="d627b-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d627b-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d627b-113">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d627b-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d627b-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d627b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d627b-115">**Платформа .NET Framework версии:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d627b-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d627b-116">См. также</span><span class="sxs-lookup"><span data-stu-id="d627b-116">See also</span></span>

- [<span data-ttu-id="d627b-117">Интерфейс ICorDebugStaticFieldSymbol</span><span class="sxs-lookup"><span data-stu-id="d627b-117">ICorDebugStaticFieldSymbol Interface</span></span>](icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="d627b-118">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="d627b-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
