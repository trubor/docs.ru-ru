---
description: 'Дополнительные сведения о методе: ICorDebugVariableSymbol:: GetSlotIndex'
title: Метод ICorDebugVariableSymbol::GetSlotIndex
ms.date: 03/30/2017
ms.assetid: 09c19f5f-afc4-4e0c-bffe-cd7147bc7a43
ms.openlocfilehash: 3b5cba06a5e80ffa323d2e6521e9ec4666f6f5f3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790559"
---
# <a name="icordebugvariablesymbolgetslotindex-method"></a><span data-ttu-id="164b5-103">Метод ICorDebugVariableSymbol::GetSlotIndex</span><span class="sxs-lookup"><span data-stu-id="164b5-103">ICorDebugVariableSymbol::GetSlotIndex Method</span></span>

<span data-ttu-id="164b5-104">Возвращает управляемый индекс слота локальной переменной.</span><span class="sxs-lookup"><span data-stu-id="164b5-104">Gets the managed slot index of a local variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="164b5-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="164b5-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSlotIndex(  
   [out] ULONG32 *pSlotIndex  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="164b5-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="164b5-106">Parameters</span></span>  

 `pSlotIndex`  
 <span data-ttu-id="164b5-107">[выходной] Указатель на индекс слота локальной переменной.</span><span class="sxs-lookup"><span data-stu-id="164b5-107">[out] A pointer to the local variable's slot index.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="164b5-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="164b5-108">Return Value</span></span>  

 <span data-ttu-id="164b5-109">`S_OK` в случае успешного выполнения.</span><span class="sxs-lookup"><span data-stu-id="164b5-109">`S_OK` if successful.</span></span> <span data-ttu-id="164b5-110">`E_FAIL`, если переменная является аргументом функции.</span><span class="sxs-lookup"><span data-stu-id="164b5-110">`E_FAIL` if the variable is a function argument.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="164b5-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="164b5-111">Remarks</span></span>  

 <span data-ttu-id="164b5-112">Управляемый индекс слота можно использовать для получения информации о метаданных переменной.</span><span class="sxs-lookup"><span data-stu-id="164b5-112">The managed slot index of a local variable can be used to retrieve the variable's metadata information</span></span>  
  
> [!NOTE]
> <span data-ttu-id="164b5-113">Этот метод доступен только в машинном коде .NET.</span><span class="sxs-lookup"><span data-stu-id="164b5-113">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="164b5-114">Требования</span><span class="sxs-lookup"><span data-stu-id="164b5-114">Requirements</span></span>  

 <span data-ttu-id="164b5-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="164b5-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="164b5-116">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="164b5-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="164b5-117">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="164b5-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="164b5-118">**Платформа .NET Framework версии:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="164b5-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="164b5-119">См. также</span><span class="sxs-lookup"><span data-stu-id="164b5-119">See also</span></span>

- [<span data-ttu-id="164b5-120">Интерфейс ICorDebugVariableSymbol</span><span class="sxs-lookup"><span data-stu-id="164b5-120">ICorDebugVariableSymbol Interface</span></span>](icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="164b5-121">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="164b5-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
