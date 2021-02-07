---
description: 'Дополнительные сведения о методе: ICorDebugEval:: NewObject'
title: Метод ICorDebugEval::NewObject
ms.date: 03/30/2017
api_name:
- ICorDebugEval.NewObject
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::NewObject
helpviewer_keywords:
- NewObject method [.NET Framework debugging]
- ICorDebugEval::NewObject method [.NET Framework debugging]
ms.assetid: ce3025e8-defa-4c5e-8298-f49d71fa5736
topic_type:
- apiref
ms.openlocfilehash: 0f7feb53d061e5dbc453015772b97f2a5a59bbb3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693958"
---
# <a name="icordebugevalnewobject-method"></a><span data-ttu-id="044c3-103">Метод ICorDebugEval::NewObject</span><span class="sxs-lookup"><span data-stu-id="044c3-103">ICorDebugEval::NewObject Method</span></span>

<span data-ttu-id="044c3-104">Выделяет новый экземпляр объекта и вызывает указанный метод конструктора.</span><span class="sxs-lookup"><span data-stu-id="044c3-104">Allocates a new object instance and calls the specified constructor method.</span></span>  
  
 <span data-ttu-id="044c3-105">Этот метод является устаревшим в платформа .NET Framework версии 2,0.</span><span class="sxs-lookup"><span data-stu-id="044c3-105">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="044c3-106">Вместо этого используйте [ICorDebugEval2:: невпараметеризедобжект](icordebugeval2-newparameterizedobject-method.md) .</span><span class="sxs-lookup"><span data-stu-id="044c3-106">Use [ICorDebugEval2::NewParameterizedObject](icordebugeval2-newparameterizedobject-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="044c3-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="044c3-107">Syntax</span></span>  
  
```cpp  
HRESULT NewObject (  
    [in] ICorDebugFunction  *pConstructor,  
    [in] ULONG32            nArgs,  
    [in, size_is(nArgs)] ICorDebugValue *ppArgs[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="044c3-108">Параметры</span><span class="sxs-lookup"><span data-stu-id="044c3-108">Parameters</span></span>  

 `pConstructor`  
 <span data-ttu-id="044c3-109">окне Вызываемый конструктор.</span><span class="sxs-lookup"><span data-stu-id="044c3-109">[in] The constructor to be called.</span></span>  
  
 `nArgs`  
 <span data-ttu-id="044c3-110">[in] Размер массива `ppArgs`.</span><span class="sxs-lookup"><span data-stu-id="044c3-110">[in] The size of the `ppArgs` array.</span></span>  
  
 `ppArgs`  
 <span data-ttu-id="044c3-111">окне Массив объектов ICorDebugValue, каждый из которых представляет аргумент, передаваемый конструктору.</span><span class="sxs-lookup"><span data-stu-id="044c3-111">[in] An array of ICorDebugValue objects, each of which represents an argument to be passed to the constructor.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="044c3-112">Требования</span><span class="sxs-lookup"><span data-stu-id="044c3-112">Requirements</span></span>  

 <span data-ttu-id="044c3-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="044c3-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="044c3-114">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="044c3-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="044c3-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="044c3-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="044c3-116">**Платформа .NET Framework версии:** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="044c3-116">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="044c3-117">См. также</span><span class="sxs-lookup"><span data-stu-id="044c3-117">See also</span></span>

- [<span data-ttu-id="044c3-118">Метод NewParameterizedObject</span><span class="sxs-lookup"><span data-stu-id="044c3-118">NewParameterizedObject Method</span></span>](icordebugeval2-newparameterizedobject-method.md)
