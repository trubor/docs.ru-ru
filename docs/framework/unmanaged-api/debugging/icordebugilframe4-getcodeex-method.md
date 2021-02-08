---
description: 'Дополнительные сведения о методе: ICorDebugILFrame4:: GetCodeEx'
title: Метод ICorDebugILFrame4::GetCodeEx
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorDebugILFrame4.GetLocalVariableEx
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: aeda0e42-29ee-4ca8-9f21-ac4641677a62
topic_type:
- apiref
ms.openlocfilehash: 1d17dfa531354b8a4b0dd3c0d3d2eb47206900cc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99791235"
---
# <a name="icordebugilframe4getcodeex-method"></a><span data-ttu-id="4bb6c-103">Метод ICorDebugILFrame4::GetCodeEx</span><span class="sxs-lookup"><span data-stu-id="4bb6c-103">ICorDebugILFrame4::GetCodeEx Method</span></span>

<span data-ttu-id="4bb6c-104">[Поддерживается в .NET Framework 4.5.2 и более поздних версиях.]</span><span class="sxs-lookup"><span data-stu-id="4bb6c-104">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="4bb6c-105">Получает указатель на код, который выполняется этим кадром стека.</span><span class="sxs-lookup"><span data-stu-id="4bb6c-105">Gets a pointer to the code that this stack frame is executing.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4bb6c-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="4bb6c-106">Syntax</span></span>  
  
```cpp
HRESULT GetCodeEx(  
   [in] ILCodeKind flags,
   [out] ICorDebugCode **ppCode  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4bb6c-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="4bb6c-107">Parameters</span></span>  

 `flags`  
 <span data-ttu-id="4bb6c-108">окне Элемент перечисления [ILCodeKind](ilcodekind-enumeration.md) , указывающий, включается ли в кадр промежуточный язык (IL), определенный в запросе ReJIT профилировщика.</span><span class="sxs-lookup"><span data-stu-id="4bb6c-108">[in] An [ILCodeKind](ilcodekind-enumeration.md) enumeration member that specifies whether the intermediate language (IL) defined by the profiler's ReJIT request is included in the frame.</span></span>  
  
 `ppCode`  
 <span data-ttu-id="4bb6c-109">заполняет Указатель на адрес объекта ICorDebugCode, который представляет код, который исполняется этим кадром стека.</span><span class="sxs-lookup"><span data-stu-id="4bb6c-109">[out] A pointer to the address of an "ICorDebugCode" object that represents the code that this stack frame is executing.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4bb6c-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="4bb6c-110">Remarks</span></span>  

 <span data-ttu-id="4bb6c-111">Этот метод аналогичен методу [ICorDebugFrame::-Code](icordebugframe-getcode-method.md) , за исключением того, что он дополнительно получает доступ к коду, определенному в запросе ReJIT профилировщика.</span><span class="sxs-lookup"><span data-stu-id="4bb6c-111">This method is similar to the [ICorDebugFrame::GetCode](icordebugframe-getcode-method.md) method, except that it optionally accesses code defined by the profiler's ReJIT request.</span></span> <span data-ttu-id="4bb6c-112">Вызов этого метода со `flags` значением `ILCODE_ORIGINAL_IL` эквивалентен вызову метода " [.](icordebugframe-getcode-method.md)" Если метод инструментирован, его Il будет недоступен.</span><span class="sxs-lookup"><span data-stu-id="4bb6c-112">Calling this method with a `flags` value of `ILCODE_ORIGINAL_IL` is equivalent to calling [GetCode](icordebugframe-getcode-method.md); if the method is instrumented, its IL will not be accessible.</span></span> <span data-ttu-id="4bb6c-113">`ILCODE_REJIT_IL` позволяет отладчику получить доступ к промежуточному языку, определенному запросом ReJIT профилировщика.</span><span class="sxs-lookup"><span data-stu-id="4bb6c-113">`ILCODE_REJIT_IL` allows the debugger to access the IL defined by the profiler's ReJIT request.</span></span> <span data-ttu-id="4bb6c-114">Если IL не инструментирован, `ppCode` имеет **значение NULL** и метод возвращает `S_OK` .</span><span class="sxs-lookup"><span data-stu-id="4bb6c-114">If the IL is not instrumented, `ppCode` is **null**, and the method returns `S_OK`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4bb6c-115">Требования</span><span class="sxs-lookup"><span data-stu-id="4bb6c-115">Requirements</span></span>  

 <span data-ttu-id="4bb6c-116">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4bb6c-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4bb6c-117">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4bb6c-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4bb6c-118">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4bb6c-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4bb6c-119">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4bb6c-119">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4bb6c-120">См. также</span><span class="sxs-lookup"><span data-stu-id="4bb6c-120">See also</span></span>

- [<span data-ttu-id="4bb6c-121">Интерфейс ICorDebugILFrame4</span><span class="sxs-lookup"><span data-stu-id="4bb6c-121">ICorDebugILFrame4 Interface</span></span>](icordebugilframe4-interface.md)
- [<span data-ttu-id="4bb6c-122">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="4bb6c-122">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="4bb6c-123">ReJIT: руководство по How-To</span><span class="sxs-lookup"><span data-stu-id="4bb6c-123">ReJIT: A How-To Guide</span></span>](/archive/blogs/davbr/rejit-a-how-to-guide)
