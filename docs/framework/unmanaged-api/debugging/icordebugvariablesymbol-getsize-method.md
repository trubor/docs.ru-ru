---
description: 'Дополнительные сведения о методе: ICorDebugVariableSymbol:: resize'
title: Метод ICorDebugVariableSymbol::GetSize
ms.date: 03/30/2017
ms.assetid: add0cd9d-9a29-49b1-ae07-d9d3786b4ccd
ms.openlocfilehash: f4098bf5e053ab66dd7966d4b665cfad4dee01d5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790585"
---
# <a name="icordebugvariablesymbolgetsize-method"></a><span data-ttu-id="49b67-103">Метод ICorDebugVariableSymbol::GetSize</span><span class="sxs-lookup"><span data-stu-id="49b67-103">ICorDebugVariableSymbol::GetSize Method</span></span>

<span data-ttu-id="49b67-104">Получает размер переменной в байтах.</span><span class="sxs-lookup"><span data-stu-id="49b67-104">Gets the size of a variable in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49b67-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="49b67-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="49b67-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="49b67-106">Parameters</span></span>  

 `pcbValue`  
 <span data-ttu-id="49b67-107">Указатель на 32-разрядное целое число без знака, содержащее размер переменной.</span><span class="sxs-lookup"><span data-stu-id="49b67-107">A pointer to a 32-bit unsigned integer containing the size of the variable.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="49b67-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="49b67-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="49b67-109">Этот метод доступен только в машинном коде .NET.</span><span class="sxs-lookup"><span data-stu-id="49b67-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="49b67-110">Требования</span><span class="sxs-lookup"><span data-stu-id="49b67-110">Requirements</span></span>  

 <span data-ttu-id="49b67-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="49b67-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="49b67-112">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="49b67-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="49b67-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="49b67-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="49b67-114">**Платформа .NET Framework версии:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="49b67-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49b67-115">См. также</span><span class="sxs-lookup"><span data-stu-id="49b67-115">See also</span></span>

- [<span data-ttu-id="49b67-116">Интерфейс ICorDebugVariableSymbol</span><span class="sxs-lookup"><span data-stu-id="49b67-116">ICorDebugVariableSymbol Interface</span></span>](icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="49b67-117">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="49b67-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
