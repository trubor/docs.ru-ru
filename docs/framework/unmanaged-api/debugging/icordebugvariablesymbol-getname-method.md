---
description: 'Дополнительные сведения о методе: ICorDebugVariableSymbol:: Name'
title: Метод ICorDebugVariableSymbol::GetName
ms.date: 03/30/2017
ms.assetid: c922b7d4-44e5-45e4-aef3-cc9c35a0be80
ms.openlocfilehash: 4a3ba1dfebd256dcbb8374634a52f1feca5d9611
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790598"
---
# <a name="icordebugvariablesymbolgetname-method"></a><span data-ttu-id="ad773-103">Метод ICorDebugVariableSymbol::GetName</span><span class="sxs-lookup"><span data-stu-id="ad773-103">ICorDebugVariableSymbol::GetName Method</span></span>

<span data-ttu-id="ad773-104">Получает имя переменной.</span><span class="sxs-lookup"><span data-stu-id="ad773-104">Gets the name of a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad773-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ad773-105">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,
   [out] ULONG32 *pcchName,
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ad773-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="ad773-106">Parameters</span></span>  

 `cchName`  
 <span data-ttu-id="ad773-107">[in] Число символов в буфере `szName`.</span><span class="sxs-lookup"><span data-stu-id="ad773-107">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="ad773-108">[out] Указатель на число символов, фактически записанных в буфер `szName`.</span><span class="sxs-lookup"><span data-stu-id="ad773-108">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="ad773-109">Указатель на массив символов, содержащий имя переменной.</span><span class="sxs-lookup"><span data-stu-id="ad773-109">A pointer to a character array that contains the variable name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ad773-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="ad773-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ad773-111">Этот метод доступен только в машинном коде .NET.</span><span class="sxs-lookup"><span data-stu-id="ad773-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad773-112">Требования</span><span class="sxs-lookup"><span data-stu-id="ad773-112">Requirements</span></span>  

 <span data-ttu-id="ad773-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad773-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad773-114">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ad773-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ad773-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ad773-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ad773-116">**Платформа .NET Framework версии:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad773-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad773-117">См. также</span><span class="sxs-lookup"><span data-stu-id="ad773-117">See also</span></span>

- [<span data-ttu-id="ad773-118">Интерфейс ICorDebugVariableSymbol</span><span class="sxs-lookup"><span data-stu-id="ad773-118">ICorDebugVariableSymbol Interface</span></span>](icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="ad773-119">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="ad773-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
