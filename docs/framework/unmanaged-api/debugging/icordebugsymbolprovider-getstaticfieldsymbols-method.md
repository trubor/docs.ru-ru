---
description: 'Дополнительные сведения о методе: метод icordebugsymbolprovider:: Жетстатикфиелдсимболс'
title: Метод ICorDebugSymbolProvider::GetStaticFieldSymbols
ms.date: 03/30/2017
ms.assetid: b178367f-a6e4-413c-b06f-daf3804b456b
ms.openlocfilehash: e95f77be86ef88a73ca4c833b242617a0d405e21
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99659714"
---
# <a name="icordebugsymbolprovidergetstaticfieldsymbols-method"></a><span data-ttu-id="832f0-103">Метод ICorDebugSymbolProvider::GetStaticFieldSymbols</span><span class="sxs-lookup"><span data-stu-id="832f0-103">ICorDebugSymbolProvider::GetStaticFieldSymbols Method</span></span>

<span data-ttu-id="832f0-104">Получает символы статического поля, которые соответствуют сигнатуре TypeSpec.</span><span class="sxs-lookup"><span data-stu-id="832f0-104">Gets the static field symbols that correspond to a typespec signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="832f0-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="832f0-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStaticFieldSymbols(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugStaticFieldSymbol *pSymbols[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="832f0-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="832f0-106">Parameters</span></span>  

 `cbSignature`  
 <span data-ttu-id="832f0-107">[in] Число байтов в массиве `typeSig`.</span><span class="sxs-lookup"><span data-stu-id="832f0-107">[in] The number of bytes in the `typeSig` array.</span></span>  
  
 `typeSig`  
 <span data-ttu-id="832f0-108">[in] Массив байтов, содержащий сигнатуру `typespec`.</span><span class="sxs-lookup"><span data-stu-id="832f0-108">[in] A byte array that contains the `typespec` signature.</span></span>  
  
 `cRequestedSymbols`  
 <span data-ttu-id="832f0-109">[in] Количество запрошенных символов.</span><span class="sxs-lookup"><span data-stu-id="832f0-109">[in] The number of symbols requested.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="832f0-110">[out] Указатель на число  символов, полученных при помощи метода.</span><span class="sxs-lookup"><span data-stu-id="832f0-110">[out] A pointer to the number of symbols retrieved by the method.</span></span>  
  
 `pSymbols`  
 <span data-ttu-id="832f0-111">заполняет Указатель на массив [икордебугстатикфиелдсимбол](icordebugstaticfieldsymbol-interface.md) , содержащий запрошенные символы статического поля.</span><span class="sxs-lookup"><span data-stu-id="832f0-111">[out] A pointer to an [ICorDebugStaticFieldSymbol](icordebugstaticfieldsymbol-interface.md) array that contains the requested static field symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="832f0-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="832f0-112">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="832f0-113">Этот метод доступен только в машинном коде .NET.</span><span class="sxs-lookup"><span data-stu-id="832f0-113">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="832f0-114">Требования</span><span class="sxs-lookup"><span data-stu-id="832f0-114">Requirements</span></span>  

 <span data-ttu-id="832f0-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="832f0-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="832f0-116">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="832f0-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="832f0-117">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="832f0-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="832f0-118">**Платформа .NET Framework версии:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="832f0-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="832f0-119">См. также</span><span class="sxs-lookup"><span data-stu-id="832f0-119">See also</span></span>

- [<span data-ttu-id="832f0-120">Метод GetInstanceFieldSymbols</span><span class="sxs-lookup"><span data-stu-id="832f0-120">GetInstanceFieldSymbols Method</span></span>](icordebugsymbolprovider-getinstancefieldsymbols-method.md)
- [<span data-ttu-id="832f0-121">Интерфейс ICorDebugSymbolProvider</span><span class="sxs-lookup"><span data-stu-id="832f0-121">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="832f0-122">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="832f0-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
