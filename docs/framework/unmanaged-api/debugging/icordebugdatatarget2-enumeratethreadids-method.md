---
description: 'Дополнительные сведения о методе: метод icordebugdatatarget2:: Енумератесреадидс'
title: Метод ICorDebugDataTarget2::EnumerateThreadIDs
ms.date: 03/30/2017
ms.assetid: af02460f-2a45-496e-bc4e-a1ac4f80fe11
ms.openlocfilehash: 5bbda67e6c6de81e9de566a68f772f324d79b92f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710560"
---
# <a name="icordebugdatatarget2enumeratethreadids-method"></a><span data-ttu-id="839b7-103">Метод ICorDebugDataTarget2::EnumerateThreadIDs</span><span class="sxs-lookup"><span data-stu-id="839b7-103">ICorDebugDataTarget2::EnumerateThreadIDs Method</span></span>

<span data-ttu-id="839b7-104">Возвращает список идентификаторов активных потоков.</span><span class="sxs-lookup"><span data-stu-id="839b7-104">Returns a list of active thread IDs.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="839b7-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="839b7-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateThreadIDs(  
    [in] ULONG32 cThreadIds,
    [out] ULONG32 *pcThreadIds,
    [out, size_is(cThreadIds), length_is(*pcThreadIds)] ULONG32 pThreadIds[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="839b7-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="839b7-106">Parameters</span></span>  

 <span data-ttu-id="839b7-107">cThreadIDs</span><span class="sxs-lookup"><span data-stu-id="839b7-107">cThreadIDs</span></span>  
 <span data-ttu-id="839b7-108">[входной] Максимальное число потоков, идентификаторы которых могут быть возвращены.</span><span class="sxs-lookup"><span data-stu-id="839b7-108">[in] The maximum number of threads whose IDs can be returned.</span></span>  
  
 <span data-ttu-id="839b7-109">pcThreadIds</span><span class="sxs-lookup"><span data-stu-id="839b7-109">pcThreadIds</span></span>  
 <span data-ttu-id="839b7-110">[выходной] Указатель на `ULONG32`, который указывает фактическое количество идентификаторов потоков, записанных в массив `pThreadIds`.</span><span class="sxs-lookup"><span data-stu-id="839b7-110">[out] A pointer to a `ULONG32` that indicates the actual number of thread IDs written to the `pThreadIds` array.</span></span>  
  
 <span data-ttu-id="839b7-111">pThreadIDs</span><span class="sxs-lookup"><span data-stu-id="839b7-111">pThreadIDs</span></span>  
 <span data-ttu-id="839b7-112">Массив идентификаторов потоков.</span><span class="sxs-lookup"><span data-stu-id="839b7-112">An array of thread identifiers.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="839b7-113">Remarks</span><span class="sxs-lookup"><span data-stu-id="839b7-113">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="839b7-114">Этот метод доступен только в машинном коде .NET.</span><span class="sxs-lookup"><span data-stu-id="839b7-114">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="839b7-115">Требования</span><span class="sxs-lookup"><span data-stu-id="839b7-115">Requirements</span></span>  

 <span data-ttu-id="839b7-116">**Платформы:** См. раздел [требования к системе](../../get-started/system-requirements.md). **Заголовок:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="839b7-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="839b7-117">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="839b7-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="839b7-118">**Платформа .NET Framework версии:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="839b7-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="839b7-119">См. также</span><span class="sxs-lookup"><span data-stu-id="839b7-119">See also</span></span>

- [<span data-ttu-id="839b7-120">Интерфейс ICorDebugDataTarget2</span><span class="sxs-lookup"><span data-stu-id="839b7-120">ICorDebugDataTarget2 Interface</span></span>](icordebugdatatarget2-interface.md)
- [<span data-ttu-id="839b7-121">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="839b7-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
