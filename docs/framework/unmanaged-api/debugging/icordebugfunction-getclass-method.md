---
description: 'Дополнительные сведения о методе ICorDebugFunction:: coclass'
title: Метод ICorDebugFunction::GetClass
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetClass
helpviewer_keywords:
- GetClass method, ICorDebugFunction interface [.NET Framework debugging]
- ICorDebugFunction::GetClass method [.NET Framework debugging]
ms.assetid: 27967230-144f-40d3-9e23-961d0241abd9
topic_type:
- apiref
ms.openlocfilehash: 09049962082bc51cc47a56b0de591a26c2ef93fc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99692593"
---
# <a name="icordebugfunctiongetclass-method"></a><span data-ttu-id="eccb3-103">Метод ICorDebugFunction::GetClass</span><span class="sxs-lookup"><span data-stu-id="eccb3-103">ICorDebugFunction::GetClass Method</span></span>

<span data-ttu-id="eccb3-104">Возвращает объект ICorDebugClass, представляющий класс, членом которого является эта функция.</span><span class="sxs-lookup"><span data-stu-id="eccb3-104">Gets an ICorDebugClass object that represents the class this function is a member of.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eccb3-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="eccb3-105">Syntax</span></span>  
  
```cpp  
HRESULT GetClass (  
    [out] ICorDebugClass **ppClass  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="eccb3-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="eccb3-106">Parameters</span></span>  

 `ppClass`  
 <span data-ttu-id="eccb3-107">заполняет Указатель на адрес `ICorDebugClass` объекта, представляющий класс, или значение null, если эта функция не является членом класса.</span><span class="sxs-lookup"><span data-stu-id="eccb3-107">[out] A pointer to the address of the `ICorDebugClass` object that represents the class, or null, if this function is not a member of a class.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="eccb3-108">Требования</span><span class="sxs-lookup"><span data-stu-id="eccb3-108">Requirements</span></span>  

 <span data-ttu-id="eccb3-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="eccb3-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="eccb3-110">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="eccb3-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="eccb3-111">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="eccb3-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="eccb3-112">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="eccb3-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
