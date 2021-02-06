---
description: 'Дополнительные сведения о методе: метод icordebugsymbolprovider:: Жетобжектсизе'
title: Метод ICorDebugSymbolProvider::GetObjectSize
ms.date: 03/30/2017
ms.assetid: 3c564396-ac64-4ef3-b4f6-df96f1d46fc7
ms.openlocfilehash: 72720a1af9958fd0ab91276b3967733cec77fee7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99659713"
---
# <a name="icordebugsymbolprovidergetobjectsize-method"></a><span data-ttu-id="d8304-103">Метод ICorDebugSymbolProvider::GetObjectSize</span><span class="sxs-lookup"><span data-stu-id="d8304-103">ICorDebugSymbolProvider::GetObjectSize Method</span></span>

<span data-ttu-id="d8304-104">Возвращает размер объекта для объекта на основе его сигнатуры TypeSpec.</span><span class="sxs-lookup"><span data-stu-id="d8304-104">Returns the object size for an object based on its typespec signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8304-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d8304-105">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectSize(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [out] ULONG32 *pObjectSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d8304-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="d8304-106">Parameters</span></span>  

 `cbSignature`  
 <span data-ttu-id="d8304-107">[in] Число байтов в сигнатуре TypeSpec.</span><span class="sxs-lookup"><span data-stu-id="d8304-107">[in] The number of bytes in the typespec signature.</span></span>  
  
 <span data-ttu-id="d8304-108">typeSig</span><span class="sxs-lookup"><span data-stu-id="d8304-108">typeSig</span></span>  
 <span data-ttu-id="d8304-109">[в] Сигнатура TypeSpec.</span><span class="sxs-lookup"><span data-stu-id="d8304-109">[in] The typespec signature.</span></span>  
  
 `pObjectSize`  
 <span data-ttu-id="d8304-110">[out] Указатель на размер объекта.</span><span class="sxs-lookup"><span data-stu-id="d8304-110">[out] A pointer to the size of the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d8304-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="d8304-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d8304-112">Этот метод доступен только в машинном коде .NET.</span><span class="sxs-lookup"><span data-stu-id="d8304-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d8304-113">Требования</span><span class="sxs-lookup"><span data-stu-id="d8304-113">Requirements</span></span>  

 <span data-ttu-id="d8304-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d8304-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d8304-115">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d8304-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d8304-116">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d8304-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d8304-117">**Платформа .NET Framework версии:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d8304-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8304-118">См. также</span><span class="sxs-lookup"><span data-stu-id="d8304-118">See also</span></span>

- [<span data-ttu-id="d8304-119">Интерфейс ICorDebugSymbolProvider</span><span class="sxs-lookup"><span data-stu-id="d8304-119">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="d8304-120">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="d8304-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
