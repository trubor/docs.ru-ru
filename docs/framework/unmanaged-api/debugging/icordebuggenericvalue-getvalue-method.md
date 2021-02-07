---
description: 'Дополнительные сведения о методе: ICorDebugGenericValue:: GetValue'
title: Метод ICorDebugGenericValue::GetValue
ms.date: 03/30/2017
api_name:
- ICorDebugGenericValue.GetValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGenericValue::GetValue
helpviewer_keywords:
- ICorDebugGenericValue::GetValue method [.NET Framework debugging]
- GetValue method, ICorDebugGenericValue interface [.NET Framework debugging]
ms.assetid: 4e95d7cb-144d-4ccf-8a69-d605f4744be2
topic_type:
- apiref
ms.openlocfilehash: 9c8459ce6a9fb59e934b1ebd355aa091a37b2d7b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99661068"
---
# <a name="icordebuggenericvaluegetvalue-method"></a><span data-ttu-id="11206-103">Метод ICorDebugGenericValue::GetValue</span><span class="sxs-lookup"><span data-stu-id="11206-103">ICorDebugGenericValue::GetValue Method</span></span>

<span data-ttu-id="11206-104">Копирует значение этого универсального объекта в указанный буфер.</span><span class="sxs-lookup"><span data-stu-id="11206-104">Copies the value of this generic into the specified buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="11206-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="11206-105">Syntax</span></span>  
  
```cpp  
HRESULT GetValue (  
    [out] void     *pTo  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="11206-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="11206-106">Parameters</span></span>  

 `pTo`  
 <span data-ttu-id="11206-107">заполняет Указатель на значение, представленное этим объектом ICorDebugGenericValue.</span><span class="sxs-lookup"><span data-stu-id="11206-107">[out] A pointer to the value that is represented by this ICorDebugGenericValue object.</span></span> <span data-ttu-id="11206-108">Значение может быть простым типом или ссылочным типом (т. е. указателем).</span><span class="sxs-lookup"><span data-stu-id="11206-108">The value may be a simple type or a reference type (that is, a pointer).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11206-109">Требования</span><span class="sxs-lookup"><span data-stu-id="11206-109">Requirements</span></span>  

 <span data-ttu-id="11206-110">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="11206-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11206-111">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="11206-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="11206-112">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="11206-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="11206-113">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11206-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
