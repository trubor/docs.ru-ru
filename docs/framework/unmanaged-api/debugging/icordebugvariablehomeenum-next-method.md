---
description: 'Дополнительные сведения о методе: ICorDebugVariableHomeEnum:: Next'
title: 'Метод ICorDebugVariableHomeEnum:: Next'
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHomeEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHomeEnum::Next
helpviewer_keywords:
- ICorDebugVariableHomeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugVariableHomeEnum interface [.NET Framework debugging]
ms.assetid: eb9ea96c-5b58-4655-8104-094fc8b393b8
topic_type:
- apiref
ms.openlocfilehash: 0aa0174e67bceaa724ddfeadc2560d12e112b859
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790611"
---
# <a name="icordebugvariablehomeenumnext-method"></a><span data-ttu-id="40f75-103">Метод ICorDebugVariableHomeEnum:: Next</span><span class="sxs-lookup"><span data-stu-id="40f75-103">ICorDebugVariableHomeEnum::Next Method</span></span>

<span data-ttu-id="40f75-104">Возвращает указанное число экземпляров [ICorDebugVariableHome](icordebugvariablehome-interface.md) , содержащих сведения о локальных переменных и аргументах в функции.</span><span class="sxs-lookup"><span data-stu-id="40f75-104">Gets the specified number of [ICorDebugVariableHome](icordebugvariablehome-interface.md) instances that contain information about the local variables and arguments in a function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40f75-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="40f75-105">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)] ICorDebugVariableHome *homes[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="40f75-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="40f75-106">Parameters</span></span>  

 `celt`  
 <span data-ttu-id="40f75-107">[in] Количество объектов, которые должны быть получены.</span><span class="sxs-lookup"><span data-stu-id="40f75-107">[in] The number of objects to be retrieved.</span></span>  
  
 `homes`  
 <span data-ttu-id="40f75-108">Массив указателей, каждый из которых указывает на объект [ICorDebugVariableHome](icordebugvariablehome-interface.md) , предоставляющий сведения о локальной переменной или аргументе функции.</span><span class="sxs-lookup"><span data-stu-id="40f75-108">An array of pointers, each of which points to a [ICorDebugVariableHome](icordebugvariablehome-interface.md) object that provides information about  a local variable or argument of a function.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="40f75-109">заполняет Число экземпляров, фактически возвращаемых в объектах.</span><span class="sxs-lookup"><span data-stu-id="40f75-109">[out] The number of instances actually returned in objects.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="40f75-110">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="40f75-110">Return Value</span></span>  

 <span data-ttu-id="40f75-111">Метод возвращает следующие значения.</span><span class="sxs-lookup"><span data-stu-id="40f75-111">The method returns the following values.</span></span>  
  
|<span data-ttu-id="40f75-112">HRESULT</span><span class="sxs-lookup"><span data-stu-id="40f75-112">HRESULT</span></span>|<span data-ttu-id="40f75-113">Описание</span><span class="sxs-lookup"><span data-stu-id="40f75-113">Description</span></span>|  
|-------------|-----------------|  
|`S_OK`|<span data-ttu-id="40f75-114">Метод завершился успешно.</span><span class="sxs-lookup"><span data-stu-id="40f75-114">The method completed successfully.</span></span>|  
|`S_FALSE`|<span data-ttu-id="40f75-115">Фактическое число получаемых экземпляров, как показано в `pceltFetched` , меньше числа запрошенных экземпляров.</span><span class="sxs-lookup"><span data-stu-id="40f75-115">The actual number of instances retrieved, as reflected in `pceltFetched`, is less than the number of instances requested.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="40f75-116">Remarks</span><span class="sxs-lookup"><span data-stu-id="40f75-116">Remarks</span></span>  

 <span data-ttu-id="40f75-117">Метод [ICorDebugVariableHomeEnum:: Next](icordebugvariablehomeenum-next-method.md) извлекает максимум  `celt` объектов, начиная с текущей позиции перечислителя.</span><span class="sxs-lookup"><span data-stu-id="40f75-117">The [ICorDebugVariableHomeEnum::Next](icordebugvariablehomeenum-next-method.md) method retrieves a maximum of  `celt` objects starting at the current position of the enumerator.</span></span> <span data-ttu-id="40f75-118">При возврате из метода `pceltFetched` содержит фактическое число извлеченных объектов.</span><span class="sxs-lookup"><span data-stu-id="40f75-118">When the method returns, `pceltFetched` contains the actual number of objects retrieved.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40f75-119">Требования</span><span class="sxs-lookup"><span data-stu-id="40f75-119">Requirements</span></span>  

 <span data-ttu-id="40f75-120">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="40f75-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40f75-121">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="40f75-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="40f75-122">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="40f75-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="40f75-123">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40f75-123">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40f75-124">См. также</span><span class="sxs-lookup"><span data-stu-id="40f75-124">See also</span></span>

- [<span data-ttu-id="40f75-125">Интерфейс ICorDebugVariableHomeEnum</span><span class="sxs-lookup"><span data-stu-id="40f75-125">ICorDebugVariableHomeEnum Interface</span></span>](icordebugvariablehomeenum-interface.md)
- [<span data-ttu-id="40f75-126">Интерфейс ICorDebugVariableHome</span><span class="sxs-lookup"><span data-stu-id="40f75-126">ICorDebugVariableHome Interface</span></span>](icordebugvariablehome-interface.md)
