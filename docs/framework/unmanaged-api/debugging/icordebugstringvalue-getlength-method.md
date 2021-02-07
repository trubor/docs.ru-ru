---
description: 'Дополнительные сведения о методе: ICorDebugStringValue:: DATALENGTH'
title: Метод ICorDebugStringValue::GetLength
ms.date: 03/30/2017
api_name:
- ICorDebugStringValue.GetLength
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStringValue::GetLength
helpviewer_keywords:
- ICorDebugStringValue::GetLength method [.NET Framework debugging]
- GetLength method [.NET Framework debugging]
ms.assetid: a1ebfc69-46a6-4225-8788-b7cfb2f15e1d
topic_type:
- apiref
ms.openlocfilehash: ae4d42b5b65e5f80e884415a5acfc7f894ffe11e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99717385"
---
# <a name="icordebugstringvaluegetlength-method"></a><span data-ttu-id="29b1c-103">Метод ICorDebugStringValue::GetLength</span><span class="sxs-lookup"><span data-stu-id="29b1c-103">ICorDebugStringValue::GetLength Method</span></span>

<span data-ttu-id="29b1c-104">Возвращает число символов в строке, на которую ссылается этот ICorDebugStringValue.</span><span class="sxs-lookup"><span data-stu-id="29b1c-104">Gets the number of characters in the string referenced by this ICorDebugStringValue.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29b1c-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="29b1c-105">Syntax</span></span>  
  
```cpp  
HRESULT GetLength (  
    [out] ULONG32   *pcchString  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="29b1c-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="29b1c-106">Parameters</span></span>  

 `pcchString`  
 <span data-ttu-id="29b1c-107">заполняет Указатель на значение, указывающее длину строки, на которую ссылается этот `ICorDebugStringValue` объект.</span><span class="sxs-lookup"><span data-stu-id="29b1c-107">[out] A pointer to a value that specifies the length of the string referenced by this `ICorDebugStringValue` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29b1c-108">Требования</span><span class="sxs-lookup"><span data-stu-id="29b1c-108">Requirements</span></span>  

 <span data-ttu-id="29b1c-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="29b1c-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29b1c-110">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="29b1c-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="29b1c-111">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="29b1c-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="29b1c-112">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29b1c-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
