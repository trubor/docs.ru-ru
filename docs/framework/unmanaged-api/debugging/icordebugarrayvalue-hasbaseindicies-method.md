---
description: 'Дополнительные сведения о методе: ICorDebugArrayValue:: ХасбасеиндиЦиес'
title: Метод ICorDebugArrayValue::HasBaseIndicies
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue.HasBaseIndicies
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue::HasBaseIndicies
helpviewer_keywords:
- HasBaseIndicies method [.NET Framework debugging]
- ICorDebugArrayValue::HasBaseIndicies method [.NET Framework debugging]
ms.assetid: aa26df07-e0a6-4608-bdef-d4afafec89aa
topic_type:
- apiref
ms.openlocfilehash: b251653004801ff2d312dfb34749c413774ddf40
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99722962"
---
# <a name="icordebugarrayvaluehasbaseindicies-method"></a><span data-ttu-id="3e977-103">Метод ICorDebugArrayValue::HasBaseIndicies</span><span class="sxs-lookup"><span data-stu-id="3e977-103">ICorDebugArrayValue::HasBaseIndicies Method</span></span>

<span data-ttu-id="3e977-104">Возвращает значение, указывающее, имеют ли измерения данного массива базовый индекс, отличный от нуля.</span><span class="sxs-lookup"><span data-stu-id="3e977-104">Gets a value that indicates whether any dimensions of this array have a base index of non-zero.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e977-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="3e977-105">Syntax</span></span>  
  
```cpp  
HRESULT HasBaseIndicies (  
    [out] BOOL    *pbHasBaseIndicies  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3e977-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="3e977-106">Parameters</span></span>  

 `pbHasBaseIndicies`  
 <span data-ttu-id="3e977-107">заполняет Указатель на логическое значение, равное, `true` Если одно или несколько измерений этого `ICorDebugArrayValue` объекта имеют базовый индекс ненулевого значения; в противном случае логическое значение равно `false` .</span><span class="sxs-lookup"><span data-stu-id="3e977-107">[out] A pointer to a Boolean value that is `true` if one or more dimensions of this `ICorDebugArrayValue` object have a base index of non-zero; otherwise, the Boolean value is `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e977-108">Требования</span><span class="sxs-lookup"><span data-stu-id="3e977-108">Requirements</span></span>  

 <span data-ttu-id="3e977-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3e977-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e977-110">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3e977-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3e977-111">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3e977-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3e977-112">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e977-112">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>
