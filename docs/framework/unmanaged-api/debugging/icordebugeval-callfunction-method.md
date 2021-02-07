---
description: 'Дополнительные сведения о методе: ICorDebugEval:: CallFunction'
title: Метод ICorDebugEval::CallFunction
ms.date: 03/30/2017
api_name:
- ICorDebugEval.CallFunction
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::CallFunction
helpviewer_keywords:
- ICorDebugEval::CallFunction method [.NET Framework debugging]
- CallFunction method [.NET Framework debugging]
ms.assetid: 7f470c5c-e1c0-4d8d-aad8-830f113ae751
topic_type:
- apiref
ms.openlocfilehash: c0978ab3bdffc83e3eb5e3a6553e7f374ab6d5da
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99694192"
---
# <a name="icordebugevalcallfunction-method"></a><span data-ttu-id="b689c-103">Метод ICorDebugEval::CallFunction</span><span class="sxs-lookup"><span data-stu-id="b689c-103">ICorDebugEval::CallFunction Method</span></span>

<span data-ttu-id="b689c-104">Настраивает вызов указанной функции.</span><span class="sxs-lookup"><span data-stu-id="b689c-104">Sets up a call to the specified function.</span></span>

<span data-ttu-id="b689c-105">Этот метод является устаревшим в платформа .NET Framework версии 2,0.</span><span class="sxs-lookup"><span data-stu-id="b689c-105">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="b689c-106">Вместо этого используйте [ICorDebugEval2:: каллпараметеризедфунктион](icordebugeval2-callparameterizedfunction-method.md) .</span><span class="sxs-lookup"><span data-stu-id="b689c-106">Use [ICorDebugEval2::CallParameterizedFunction](icordebugeval2-callparameterizedfunction-method.md) instead.</span></span>

## <a name="syntax"></a><span data-ttu-id="b689c-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b689c-107">Syntax</span></span>

```cpp
HRESULT CallFunction (
    [in] ICorDebugFunction  *pFunction,
    [in] ULONG32            nArgs,
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]
);
```

## <a name="parameters"></a><span data-ttu-id="b689c-108">Параметры</span><span class="sxs-lookup"><span data-stu-id="b689c-108">Parameters</span></span>

`pFunction`\
<span data-ttu-id="b689c-109">окне Указатель на объект ICorDebugFunction, указывающий вызываемую функцию.</span><span class="sxs-lookup"><span data-stu-id="b689c-109">[in] Pointer to an ICorDebugFunction object that specifies the function to be called.</span></span>

`nArgs`\
<span data-ttu-id="b689c-110">окне Число аргументов для функции.</span><span class="sxs-lookup"><span data-stu-id="b689c-110">[in] The number of arguments for the function.</span></span>

`ppArgs`\
<span data-ttu-id="b689c-111">окне Массив указателей, каждый из которых указывает на объект ICorDebugValue, указывающий аргумент, передаваемый в функцию.</span><span class="sxs-lookup"><span data-stu-id="b689c-111">[in] An array of pointers, each of which points to an ICorDebugValue object that specifies an argument to be passed to the function.</span></span>

## <a name="remarks"></a><span data-ttu-id="b689c-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="b689c-112">Remarks</span></span>

<span data-ttu-id="b689c-113">Если функция является виртуальной, выполняет `CallFunction` виртуальную диспетчеризацию.</span><span class="sxs-lookup"><span data-stu-id="b689c-113">If the function is virtual, `CallFunction` will perform virtual dispatch.</span></span> <span data-ttu-id="b689c-114">Если функция находится в другом домене приложения, произойдет переход, если все аргументы также находятся в этом домене приложения.</span><span class="sxs-lookup"><span data-stu-id="b689c-114">If the function is in a different application domain, a transition will occur as long as all arguments are also in that application domain.</span></span>

## <a name="requirements"></a><span data-ttu-id="b689c-115">Требования</span><span class="sxs-lookup"><span data-stu-id="b689c-115">Requirements</span></span>

<span data-ttu-id="b689c-116">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b689c-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="b689c-117">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b689c-117">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="b689c-118">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b689c-118">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="b689c-119">**Платформа .NET Framework версии:** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="b689c-119">**.NET Framework Versions:** 1.1, 1.0</span></span>

## <a name="see-also"></a><span data-ttu-id="b689c-120">См. также</span><span class="sxs-lookup"><span data-stu-id="b689c-120">See also</span></span>

- [<span data-ttu-id="b689c-121">Метод CallParameterizedFunction</span><span class="sxs-lookup"><span data-stu-id="b689c-121">CallParameterizedFunction Method</span></span>](icordebugeval2-callparameterizedfunction-method.md)
