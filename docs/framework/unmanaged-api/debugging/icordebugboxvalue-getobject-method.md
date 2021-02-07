---
description: 'Дополнительные сведения о методе: Икордебугбоксвалуе:: GetObject'
title: Метод ICorDebugBoxValue::GetObject
ms.date: 03/30/2017
api_name:
- ICorDebugBoxValue.GetObject
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBoxValue::GetObject
helpviewer_keywords:
- ICorDebugBoxValue::GetObject method [.NET Framework debugging]
- GetObject method, ICorDebugBoxValue interface [.NET Framework debugging]
ms.assetid: 3a867a5b-bf94-493f-a4f5-b28685cf5325
topic_type:
- apiref
ms.openlocfilehash: fc5376fa7ddbbeae3464427b34caf991d0a2f59a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99711867"
---
# <a name="icordebugboxvaluegetobject-method"></a><span data-ttu-id="0710b-103">Метод ICorDebugBoxValue::GetObject</span><span class="sxs-lookup"><span data-stu-id="0710b-103">ICorDebugBoxValue::GetObject Method</span></span>

<span data-ttu-id="0710b-104">Возвращает упакованное значение.</span><span class="sxs-lookup"><span data-stu-id="0710b-104">Gets the boxed value.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0710b-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="0710b-105">Syntax</span></span>  
  
```cpp  
HRESULT GetObject (  
    [out] ICorDebugObjectValue **ppObject  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0710b-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="0710b-106">Parameters</span></span>  

 `ppObject`  
 <span data-ttu-id="0710b-107">заполняет Указатель на адрес объекта ICorDebugObjectValue, который представляет упакованное значение.</span><span class="sxs-lookup"><span data-stu-id="0710b-107">[out] A pointer to the address of an ICorDebugObjectValue object that represents the boxed value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0710b-108">Требования</span><span class="sxs-lookup"><span data-stu-id="0710b-108">Requirements</span></span>  

 <span data-ttu-id="0710b-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0710b-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0710b-110">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0710b-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0710b-111">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0710b-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0710b-112">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0710b-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
