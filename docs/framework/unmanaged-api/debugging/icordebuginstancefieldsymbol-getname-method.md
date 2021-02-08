---
description: 'Дополнительные сведения о методе: ICorDebugInstanceFieldSymbol:: Name'
title: Метод ICorDebugInstanceFieldSymbol::GetName
ms.date: 03/30/2017
ms.assetid: d9c12b1f-9c1d-4943-8e9e-93b55faf085f
ms.openlocfilehash: 9cc2106d1527aa0b4d9e5c52115b703ffe55037f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791196"
---
# <a name="icordebuginstancefieldsymbolgetname-method"></a><span data-ttu-id="b2b4e-103">Метод ICorDebugInstanceFieldSymbol::GetName</span><span class="sxs-lookup"><span data-stu-id="b2b4e-103">ICorDebugInstanceFieldSymbol::GetName Method</span></span>

<span data-ttu-id="b2b4e-104">Получает имя поля экземпляра.</span><span class="sxs-lookup"><span data-stu-id="b2b4e-104">Gets the name of the instance field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b2b4e-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b2b4e-105">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,
   [out] ULONG32 *pcchName,
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b2b4e-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="b2b4e-106">Parameters</span></span>  

 `cchName`  
 <span data-ttu-id="b2b4e-107">[in] Число символов в буфере `szName`.</span><span class="sxs-lookup"><span data-stu-id="b2b4e-107">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="b2b4e-108">[out] Указатель на число символов, фактически записанных в буфер `szName`.</span><span class="sxs-lookup"><span data-stu-id="b2b4e-108">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="b2b4e-109">[out] Массив символов, в котором хранится возвращаемое имя.</span><span class="sxs-lookup"><span data-stu-id="b2b4e-109">[out] A character array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b2b4e-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="b2b4e-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b2b4e-111">Этот метод доступен только в машинном коде .NET.</span><span class="sxs-lookup"><span data-stu-id="b2b4e-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b2b4e-112">Требования</span><span class="sxs-lookup"><span data-stu-id="b2b4e-112">Requirements</span></span>  

 <span data-ttu-id="b2b4e-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b2b4e-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b2b4e-114">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b2b4e-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b2b4e-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b2b4e-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b2b4e-116">**Платформа .NET Framework версии:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b2b4e-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b2b4e-117">См. также</span><span class="sxs-lookup"><span data-stu-id="b2b4e-117">See also</span></span>

- [<span data-ttu-id="b2b4e-118">Интерфейс ICorDebugInstanceFieldSymbol</span><span class="sxs-lookup"><span data-stu-id="b2b4e-118">ICorDebugInstanceFieldSymbol Interface</span></span>](icordebuginstancefieldsymbol-interface.md)
- [<span data-ttu-id="b2b4e-119">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="b2b4e-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
