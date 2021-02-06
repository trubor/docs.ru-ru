---
description: 'Дополнительные сведения о методе: метод icordebugsymbolprovider:: GetInstanceFieldSymbols'
title: Метод ICorDebugSymbolProvider::GetInstanceFieldSymbols
ms.date: 03/30/2017
ms.assetid: a29b9233-ee67-4b53-b8bc-c00b281e7edb
ms.openlocfilehash: 379d943743bb1fe21edbcca2265b4d8613d4f4b8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99659898"
---
# <a name="icordebugsymbolprovidergetinstancefieldsymbols-method"></a><span data-ttu-id="a69ea-103">Метод ICorDebugSymbolProvider::GetInstanceFieldSymbols</span><span class="sxs-lookup"><span data-stu-id="a69ea-103">ICorDebugSymbolProvider::GetInstanceFieldSymbols Method</span></span>

<span data-ttu-id="a69ea-104">Получает символы поля экземпляра, которые соответствуют сигнатуре TypeSpec.</span><span class="sxs-lookup"><span data-stu-id="a69ea-104">Gets the instance field symbols that correspond to a typespec signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a69ea-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a69ea-105">Syntax</span></span>  
  
```cpp  
HRESULT GetInstanceFieldSymbols(  
   [in] ULONG32 cbSignature,  
   [in, size_is(cbSignature)]  BYTE typeSig[],  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugInstanceFieldSymbol *pSymbols[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a69ea-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="a69ea-106">Parameters</span></span>  

 `cbSignature`  
 <span data-ttu-id="a69ea-107">[in] Число байтов в массиве `typeSig`.</span><span class="sxs-lookup"><span data-stu-id="a69ea-107">[in] The number of bytes in the `typeSig` array.</span></span>  
  
 `typeSig`  
 <span data-ttu-id="a69ea-108">[in] Массив байтов, содержащий сигнатуру `typespec`.</span><span class="sxs-lookup"><span data-stu-id="a69ea-108">[in] A byte array that contains the `typespec` signature.</span></span>  
  
 `cRequestedSymbols`  
 <span data-ttu-id="a69ea-109">[in] Количество запрошенных символов.</span><span class="sxs-lookup"><span data-stu-id="a69ea-109">[in] The number of symbols requested.</span></span>  
  
 `pcFetchedSymbols`  
 <span data-ttu-id="a69ea-110">[out] Указатель на число  символов, полученных при помощи метода.</span><span class="sxs-lookup"><span data-stu-id="a69ea-110">[out] A pointer to the number of symbols retrieved by the method.</span></span>  
  
 `pSymbols`  
 <span data-ttu-id="a69ea-111">заполняет Указатель на массив [икордебугстатикфиелдсимбол](icordebugstaticfieldsymbol-interface.md) , содержащий запрошенные символы поля экземпляра.</span><span class="sxs-lookup"><span data-stu-id="a69ea-111">[out] A pointer to an [ICorDebugStaticFieldSymbol](icordebugstaticfieldsymbol-interface.md) array that contains the requested instance field symbols.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a69ea-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="a69ea-112">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a69ea-113">Этот метод доступен только в машинном коде .NET.</span><span class="sxs-lookup"><span data-stu-id="a69ea-113">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a69ea-114">Требования</span><span class="sxs-lookup"><span data-stu-id="a69ea-114">Requirements</span></span>  

 <span data-ttu-id="a69ea-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a69ea-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a69ea-116">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a69ea-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a69ea-117">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a69ea-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a69ea-118">**Платформа .NET Framework версии:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a69ea-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a69ea-119">См. также</span><span class="sxs-lookup"><span data-stu-id="a69ea-119">See also</span></span>

- [<span data-ttu-id="a69ea-120">Метод GetStaticFieldSymbols</span><span class="sxs-lookup"><span data-stu-id="a69ea-120">GetStaticFieldSymbols Method</span></span>](icordebugsymbolprovider-getstaticfieldsymbols-method.md)
- [<span data-ttu-id="a69ea-121">Интерфейс ICorDebugSymbolProvider</span><span class="sxs-lookup"><span data-stu-id="a69ea-121">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="a69ea-122">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="a69ea-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
