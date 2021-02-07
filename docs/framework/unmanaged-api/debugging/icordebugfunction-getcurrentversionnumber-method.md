---
description: 'Дополнительные сведения: метод ICorDebugFunction:: GetCurrentVersionNumber'
title: Метод ICorDebugFunction::GetCurrentVersionNumber
ms.date: 03/30/2017
api_name:
- ICorDebugFunction.GetCurrentVersionNumber
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction::GetCurrentVersionNumber
helpviewer_keywords:
- GetCurrentVersionNumber method [.NET Framework debugging]
- ICorDebugFunction::GetCurrentVersionNumber method [.NET Framework debugging]
ms.assetid: c3af1575-cbe6-457a-bc08-c53460edcbc8
topic_type:
- apiref
ms.openlocfilehash: ccc96755ac74624a00b806e3f569f39f2d6059f5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99692541"
---
# <a name="icordebugfunctiongetcurrentversionnumber-method"></a><span data-ttu-id="5431a-103">Метод ICorDebugFunction::GetCurrentVersionNumber</span><span class="sxs-lookup"><span data-stu-id="5431a-103">ICorDebugFunction::GetCurrentVersionNumber Method</span></span>

<span data-ttu-id="5431a-104">Возвращает номер версии последнего изменения, внесенного в функцию, представленную этим объектом ICorDebugFunction.</span><span class="sxs-lookup"><span data-stu-id="5431a-104">Gets the version number of the latest edit made to the function represented by this ICorDebugFunction object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5431a-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="5431a-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentVersionNumber (  
    [out] ULONG32 *pnCurrentVersion  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5431a-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="5431a-106">Parameters</span></span>  

 `pnCurrentVersion`  
 <span data-ttu-id="5431a-107">заполняет Указатель на целочисленное значение, которое является номером версии последнего изменения, внесенного в эту функцию.</span><span class="sxs-lookup"><span data-stu-id="5431a-107">[out] A pointer to an integer value that is the version number of the latest edit made to this function.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5431a-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="5431a-108">Remarks</span></span>  

 <span data-ttu-id="5431a-109">Номер версии последнего изменения, внесенного в эту функцию, может быть больше номера версии самой функции.</span><span class="sxs-lookup"><span data-stu-id="5431a-109">The version number of the latest edit made to this function may be greater than the version number of the function itself.</span></span> <span data-ttu-id="5431a-110">Для получения номера версии функции используйте метод [ICorDebugFunction2:: жетверсионнумбер](icordebugfunction2-getversionnumber-method.md) или метод [ICorDebugCode:: жетверсионнумбер](icordebugcode-getversionnumber-method.md) .</span><span class="sxs-lookup"><span data-stu-id="5431a-110">Use either the [ICorDebugFunction2::GetVersionNumber](icordebugfunction2-getversionnumber-method.md) method or the [ICorDebugCode::GetVersionNumber](icordebugcode-getversionnumber-method.md) method to retrieve the version number of the function.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5431a-111">Требования</span><span class="sxs-lookup"><span data-stu-id="5431a-111">Requirements</span></span>  

 <span data-ttu-id="5431a-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5431a-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5431a-113">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5431a-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5431a-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5431a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5431a-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5431a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
