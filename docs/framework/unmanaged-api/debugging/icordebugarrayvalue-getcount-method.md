---
description: 'Дополнительные сведения о методе: ICorDebugArrayValue:: NOCOUNT'
title: Метод ICorDebugArrayValue::GetCount
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.GetCount
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::GetCount
helpviewer_keywords:
- ICorDebugArrayValue::GetCount method [.NET Framework debugging]
- GetCount method, ICorDebugArrayValue interface [.NET Framework debugging]
ms.assetid: 44cd98cf-2127-4d46-8c6a-da4e857bb6b0
topic_type:
- apiref
ms.openlocfilehash: 7b1422714ed9c6f89c65c310165b8cdaa6566360
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99723131"
---
# <a name="icordebugarrayvaluegetcount-method"></a><span data-ttu-id="30d22-103">Метод ICorDebugArrayValue::GetCount</span><span class="sxs-lookup"><span data-stu-id="30d22-103">ICorDebugArrayValue::GetCount Method</span></span>

<span data-ttu-id="30d22-104">Возвращает общее число элементов в массиве.</span><span class="sxs-lookup"><span data-stu-id="30d22-104">Gets the total number of elements in the array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30d22-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="30d22-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCount (  
    [out] ULONG32 *pnCount  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="30d22-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="30d22-106">Parameters</span></span>  

 `pnCount`  
 <span data-ttu-id="30d22-107">заполняет Указатель на общее число элементов в массиве.</span><span class="sxs-lookup"><span data-stu-id="30d22-107">[out] A pointer to the total number of elements in the array.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="30d22-108">Требования</span><span class="sxs-lookup"><span data-stu-id="30d22-108">Requirements</span></span>  

 <span data-ttu-id="30d22-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="30d22-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="30d22-110">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="30d22-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="30d22-111">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="30d22-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="30d22-112">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="30d22-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
