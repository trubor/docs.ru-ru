---
description: 'Дополнительные сведения о методе: ICorDebugReferenceValue:: IsNull'
title: Метод ICorDebugReferenceValue::IsNull
ms.date: 03/30/2017
api_name:
- ICorDebugReferenceValue.IsNull
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugReferenceValue::IsNull
helpviewer_keywords:
- IsNull method, ICorDebugReferenceValue interface [.NET Framework debugging]
- ICorDebugReferenceValue::IsNull method [.NET Framework debugging]
ms.assetid: 99e8c8d7-a1c0-47c8-9dbd-03e0b2bcb4d5
topic_type:
- apiref
ms.openlocfilehash: 9fffc869e20d1d3aa3a347ff2e026e6b55e6bd4f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99691033"
---
# <a name="icordebugreferencevalueisnull-method"></a><span data-ttu-id="a1ebf-103">Метод ICorDebugReferenceValue::IsNull</span><span class="sxs-lookup"><span data-stu-id="a1ebf-103">ICorDebugReferenceValue::IsNull Method</span></span>

<span data-ttu-id="a1ebf-104">Возвращает значение, указывающее, является ли ICorDebugReferenceValue значением NULL, в этом случае параметр не `ICorDebugReferenceValue` указывает на объект.</span><span class="sxs-lookup"><span data-stu-id="a1ebf-104">Gets a value that indicates whether this ICorDebugReferenceValue is a null value, in which case the `ICorDebugReferenceValue` does not point to an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1ebf-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a1ebf-105">Syntax</span></span>  
  
```cpp  
HRESULT IsNull (  
    [out] BOOL   *pbNull  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a1ebf-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="a1ebf-106">Parameters</span></span>  

 `pbNull`  
 <span data-ttu-id="a1ebf-107">заполняет Указатель на логическое значение, равное, `true` Если этот `ICorDebugReferenceValue` объект имеет значение NULL; в противном случае `pbNull` — `false` .</span><span class="sxs-lookup"><span data-stu-id="a1ebf-107">[out] A pointer to a Boolean value that is `true` if this `ICorDebugReferenceValue` object is null; otherwise, `pbNull` is `false`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1ebf-108">Требования</span><span class="sxs-lookup"><span data-stu-id="a1ebf-108">Requirements</span></span>  

 <span data-ttu-id="a1ebf-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a1ebf-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1ebf-110">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a1ebf-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a1ebf-111">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a1ebf-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a1ebf-112">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1ebf-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
