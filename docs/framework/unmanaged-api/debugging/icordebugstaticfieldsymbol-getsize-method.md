---
description: 'Дополнительные сведения о методе: Икордебугстатикфиелдсимбол:: resize'
title: Метод ICorDebugStaticFieldSymbol::GetSize
ms.date: 03/30/2017
ms.assetid: 72389860-7e37-4656-ba46-b6aeee1860f8
ms.openlocfilehash: f6fd2fe60d7cb8a77dcff5ca259d05ae1ef195ed
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794693"
---
# <a name="icordebugstaticfieldsymbolgetsize-method"></a><span data-ttu-id="d4894-103">Метод ICorDebugStaticFieldSymbol::GetSize</span><span class="sxs-lookup"><span data-stu-id="d4894-103">ICorDebugStaticFieldSymbol::GetSize Method</span></span>

<span data-ttu-id="d4894-104">Получает размер статического поля в байтах.</span><span class="sxs-lookup"><span data-stu-id="d4894-104">Gets the size in bytes of the static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4894-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d4894-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d4894-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="d4894-106">Parameters</span></span>  

 `pcbSize`  
 <span data-ttu-id="d4894-107">[out] Указатель на длину этого поля.</span><span class="sxs-lookup"><span data-stu-id="d4894-107">[out] A pointer to length of the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d4894-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="d4894-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d4894-109">Этот метод доступен только в машинном коде .NET.</span><span class="sxs-lookup"><span data-stu-id="d4894-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d4894-110">Требования</span><span class="sxs-lookup"><span data-stu-id="d4894-110">Requirements</span></span>  

 <span data-ttu-id="d4894-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d4894-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d4894-112">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d4894-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d4894-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d4894-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d4894-114">**Платформа .NET Framework версии:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d4894-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4894-115">См. также</span><span class="sxs-lookup"><span data-stu-id="d4894-115">See also</span></span>

- [<span data-ttu-id="d4894-116">Интерфейс ICorDebugStaticFieldSymbol</span><span class="sxs-lookup"><span data-stu-id="d4894-116">ICorDebugStaticFieldSymbol Interface</span></span>](icordebugstaticfieldsymbol-interface.md)
- [<span data-ttu-id="d4894-117">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="d4894-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
