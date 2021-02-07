---
description: 'Дополнительные сведения о методе: ICorDebugEval:: Невобжектноконструктор'
title: Метод ICorDebugEval::NewObjectNoConstructor
ms.date: 03/30/2017
api_name:
- ICorDebugEval.NewObjectNoConstructor
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::NewObjectNoConstructor
helpviewer_keywords:
- NewObjectNoConstructor method [.NET Framework debugging]
- ICorDebugEval::NewObjectNoConstructor method [.NET Framework debugging]
ms.assetid: 80d509ca-b5e3-4c46-9c14-800db73d9bf7
topic_type:
- apiref
ms.openlocfilehash: 4bc8f95da1a554091052dc7e7f49aef4f494578d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99693815"
---
# <a name="icordebugevalnewobjectnoconstructor-method"></a><span data-ttu-id="9eda2-103">Метод ICorDebugEval::NewObjectNoConstructor</span><span class="sxs-lookup"><span data-stu-id="9eda2-103">ICorDebugEval::NewObjectNoConstructor Method</span></span>

<span data-ttu-id="9eda2-104">Выделяет новый экземпляр объекта указанного типа без попытки вызова метода конструктора.</span><span class="sxs-lookup"><span data-stu-id="9eda2-104">Allocates a new object instance of the specified type, without attempting to call a constructor method.</span></span>  
  
 <span data-ttu-id="9eda2-105">Этот метод является устаревшим в платформа .NET Framework версии 2,0.</span><span class="sxs-lookup"><span data-stu-id="9eda2-105">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="9eda2-106">Вместо этого используйте [ICorDebugEval2:: невпараметеризедобжектноконструктор](icordebugeval2-newparameterizedobjectnoconstructor-method.md) .</span><span class="sxs-lookup"><span data-stu-id="9eda2-106">Use [ICorDebugEval2::NewParameterizedObjectNoConstructor](icordebugeval2-newparameterizedobjectnoconstructor-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9eda2-107">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="9eda2-107">Syntax</span></span>  
  
```cpp  
HRESULT NewObjectNoConstructor (  
    [in] ICorDebugClass     *pClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9eda2-108">Параметры</span><span class="sxs-lookup"><span data-stu-id="9eda2-108">Parameters</span></span>  

 `pClass`  
 <span data-ttu-id="9eda2-109">окне Указатель на объект ICorDebugClass, представляющий тип объекта, для которого создается экземпляр.</span><span class="sxs-lookup"><span data-stu-id="9eda2-109">[in] Pointer to an ICorDebugClass object that represents the type of object to be instantiated.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9eda2-110">Требования</span><span class="sxs-lookup"><span data-stu-id="9eda2-110">Requirements</span></span>  

 <span data-ttu-id="9eda2-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9eda2-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9eda2-112">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9eda2-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9eda2-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9eda2-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9eda2-114">**Платформа .NET Framework версии:** 1,1, 1,0</span><span class="sxs-lookup"><span data-stu-id="9eda2-114">**.NET Framework Versions:** 1.1, 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9eda2-115">См. также</span><span class="sxs-lookup"><span data-stu-id="9eda2-115">See also</span></span>

- [<span data-ttu-id="9eda2-116">Метод NewParameterizedObjectNoConstructor</span><span class="sxs-lookup"><span data-stu-id="9eda2-116">NewParameterizedObjectNoConstructor Method</span></span>](icordebugeval2-newparameterizedobjectnoconstructor-method.md)
