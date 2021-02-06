---
description: 'Дополнительные сведения о методе: Икордебугилкоде:: GetEHClauses'
title: Метод ICorDebugILCode::GetEHClauses
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILCode.GetEHClauses
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: cf7a0e00-06ae-47a5-8037-598b26196802
topic_type:
- apiref
ms.openlocfilehash: e790f0f1f69a38d3a1be9e98eacfc5e37be0fd05
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99660665"
---
# <a name="icordebugilcodegetehclauses-method"></a><span data-ttu-id="c05cc-103">Метод ICorDebugILCode::GetEHClauses</span><span class="sxs-lookup"><span data-stu-id="c05cc-103">ICorDebugILCode::GetEHClauses Method</span></span>

<span data-ttu-id="c05cc-104">[Поддерживается в .NET Framework 4.5.2 и более поздних версиях.]</span><span class="sxs-lookup"><span data-stu-id="c05cc-104">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="c05cc-105">Возвращает указатель на список предложений обработки исключений, определенных для этого промежуточного языка.</span><span class="sxs-lookup"><span data-stu-id="c05cc-105">Returns a pointer to a list of exception handling (EH) clauses that are defined for this intermediate language (IL).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c05cc-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c05cc-106">Syntax</span></span>  
  
```cpp
HRESULT GetEHClauses(  
   [in] ULONG32 cClauses,  
   [out] ULONG32 * pcClauses,  
   [out, size_is(cClauses), length_is(*pcClauses)] CorDebugEHClause clauses[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c05cc-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="c05cc-107">Parameters</span></span>  

 `cClauses`  
 <span data-ttu-id="c05cc-108">[в] Емкость хранилища массива `clauses`.</span><span class="sxs-lookup"><span data-stu-id="c05cc-108">[in] The storage capacity of the `clauses` array.</span></span> <span data-ttu-id="c05cc-109">Дополнительные сведения см. в разделе "Примечания".</span><span class="sxs-lookup"><span data-stu-id="c05cc-109">See the Remarks section for more information.</span></span>  
  
 `pcClauses`  
 <span data-ttu-id="c05cc-110">[из] Количество предложений, информация о которых записывается в массив `clauses`.</span><span class="sxs-lookup"><span data-stu-id="c05cc-110">[out] The number of clauses about which information is written to the `clauses` array.</span></span>  
  
 <span data-ttu-id="c05cc-111">предложения</span><span class="sxs-lookup"><span data-stu-id="c05cc-111">clauses</span></span>  
 <span data-ttu-id="c05cc-112">заполняет Массив объектов [кордебужехклаусе](cordebugehclause-structure.md) , содержащих сведения о предложениях обработки исключений, определенных для этого IL.</span><span class="sxs-lookup"><span data-stu-id="c05cc-112">[out] An array of [CorDebugEHClause](cordebugehclause-structure.md) objects that contain information on exception handling clauses defined for this IL.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c05cc-113">Remarks</span><span class="sxs-lookup"><span data-stu-id="c05cc-113">Remarks</span></span>  

 <span data-ttu-id="c05cc-114">Если значение `cClauses` равно 0 и `pcClauses` не равно **null**, то параметру присваивается `pcClauses` число доступных предложений обработки исключений.</span><span class="sxs-lookup"><span data-stu-id="c05cc-114">If `cClauses` is 0 and `pcClauses` is non-**null**, `pcClauses` is set to the number of available exception handling clauses.</span></span> <span data-ttu-id="c05cc-115">Если значение `cClauses` не равно 0, оно обозначает емкость хранилища массива `clauses`.</span><span class="sxs-lookup"><span data-stu-id="c05cc-115">If `cClauses` is non-zero, it represents the storage capacity of the `clauses` array.</span></span> <span data-ttu-id="c05cc-116">Когда метод возвращает не пустое значение, `clauses` содержит максимум элементов `cClauses`, а значению `pcClauses` присваивается количество предложений, записанных в массив `clauses` на данный момент.</span><span class="sxs-lookup"><span data-stu-id="c05cc-116">When the method returns, `clauses` contains a maximum of `cClauses` items, and `pcClauses` is set to the number of clauses actually written to the `clauses` array.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c05cc-117">Требования</span><span class="sxs-lookup"><span data-stu-id="c05cc-117">Requirements</span></span>  

 <span data-ttu-id="c05cc-118">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c05cc-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c05cc-119">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c05cc-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c05cc-120">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c05cc-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c05cc-121">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c05cc-121">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c05cc-122">См. также</span><span class="sxs-lookup"><span data-stu-id="c05cc-122">See also</span></span>

- [<span data-ttu-id="c05cc-123">Интерфейс ICorDebugILCode</span><span class="sxs-lookup"><span data-stu-id="c05cc-123">ICorDebugILCode Interface</span></span>](icordebugilcode-interface.md)
- [<span data-ttu-id="c05cc-124">Структура CorDebugEHClause</span><span class="sxs-lookup"><span data-stu-id="c05cc-124">CorDebugEHClause Structure</span></span>](cordebugehclause-structure.md)
- [<span data-ttu-id="c05cc-125">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="c05cc-125">Debugging Interfaces</span></span>](debugging-interfaces.md)
