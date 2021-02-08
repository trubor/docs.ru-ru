---
description: 'Дополнительные сведения о методе: ICorDebugInstanceFieldSymbol:: resize'
title: Метод ICorDebugInstanceFieldSymbol::GetSize
ms.date: 03/30/2017
ms.assetid: a4af1e3b-6a9f-4855-95ba-5317565c8e2b
ms.openlocfilehash: fa143620b57ec053ab26ff79b7ea2b2f386431e7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791157"
---
# <a name="icordebuginstancefieldsymbolgetsize-method"></a><span data-ttu-id="30802-103">Метод ICorDebugInstanceFieldSymbol::GetSize</span><span class="sxs-lookup"><span data-stu-id="30802-103">ICorDebugInstanceFieldSymbol::GetSize Method</span></span>

<span data-ttu-id="30802-104">Получает размер поля экземпляра в байтах.</span><span class="sxs-lookup"><span data-stu-id="30802-104">Gets the size in bytes of the instance field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30802-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="30802-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="30802-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="30802-106">Parameters</span></span>  

 `pcbSize`  
 <span data-ttu-id="30802-107">[out] Указатель на длину этого поля.</span><span class="sxs-lookup"><span data-stu-id="30802-107">[out] A pointer to length of the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="30802-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="30802-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="30802-109">Этот метод доступен только в машинном коде .NET.</span><span class="sxs-lookup"><span data-stu-id="30802-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30802-110">Требования</span><span class="sxs-lookup"><span data-stu-id="30802-110">Requirements</span></span>  

 <span data-ttu-id="30802-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="30802-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30802-112">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="30802-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="30802-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="30802-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="30802-114">**Платформа .NET Framework версии:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30802-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="30802-115">См. также</span><span class="sxs-lookup"><span data-stu-id="30802-115">See also</span></span>

- [<span data-ttu-id="30802-116">Интерфейс ICorDebugInstanceFieldSymbol</span><span class="sxs-lookup"><span data-stu-id="30802-116">ICorDebugInstanceFieldSymbol Interface</span></span>](icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="30802-117">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="30802-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
