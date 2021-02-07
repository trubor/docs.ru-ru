---
description: 'Дополнительные сведения о методе: ICorDebugVariableHome:: Жетлокатионтипе'
title: 'Метод ICorDebugVariableHome:: Жетлокатионтипе'
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetLocationType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetLocationType
helpviewer_keywords:
- ICorDebugVariableHome::GetLocationType method [.NET Framework debugging]
- GetLocationType method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: 88027c55-8ec6-4f1e-a55b-7eefdbbc3515
topic_type:
- apiref
ms.openlocfilehash: 6efe9c045641d162be820961ca75c21a2b8fc14b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99728799"
---
# <a name="icordebugvariablehomegetlocationtype-method"></a><span data-ttu-id="c0a5b-103">Метод ICorDebugVariableHome:: Жетлокатионтипе</span><span class="sxs-lookup"><span data-stu-id="c0a5b-103">ICorDebugVariableHome::GetLocationType Method</span></span>

<span data-ttu-id="c0a5b-104">Возвращает тип собственного расположения переменной.</span><span class="sxs-lookup"><span data-stu-id="c0a5b-104">Gets the type of the variable's native location.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0a5b-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="c0a5b-105">Syntax</span></span>  
  
```cpp  
HRESULT GetLocationType(  
    [out] VariableLocationType *pLocationType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c0a5b-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="c0a5b-106">Parameters</span></span>  

 `pLocationType`  
 <span data-ttu-id="c0a5b-107">заполняет Указатель на тип собственного расположения переменной.</span><span class="sxs-lookup"><span data-stu-id="c0a5b-107">[out] A pointer to the type of the variable's native location.</span></span>  <span data-ttu-id="c0a5b-108">Дополнительные сведения см. в описании перечисления [вариаблелокатионтипе](variablelocationtype-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="c0a5b-108">See the [VariableLocationType](variablelocationtype-enumeration.md) enumeration for more information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c0a5b-109">Требования</span><span class="sxs-lookup"><span data-stu-id="c0a5b-109">Requirements</span></span>  

 <span data-ttu-id="c0a5b-110">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c0a5b-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c0a5b-111">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c0a5b-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c0a5b-112">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c0a5b-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c0a5b-113">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c0a5b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0a5b-114">См. также</span><span class="sxs-lookup"><span data-stu-id="c0a5b-114">See also</span></span>

- [<span data-ttu-id="c0a5b-115">Интерфейс ICorDebugVariableHome</span><span class="sxs-lookup"><span data-stu-id="c0a5b-115">ICorDebugVariableHome Interface</span></span>](icordebugvariablehome-interface.md)
- [<span data-ttu-id="c0a5b-116">Перечисление VariableLocationType</span><span class="sxs-lookup"><span data-stu-id="c0a5b-116">VariableLocationType Enumeration</span></span>](variablelocationtype-enumeration.md)
