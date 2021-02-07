---
description: 'Дополнительные сведения о методе: ICorDebugStringValue:: GetString'
title: Метод ICorDebugStringValue::GetString
ms.date: 03/30/2017
api_name:
- ICorDebugStringValue.GetString
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStringValue::GetString
helpviewer_keywords:
- ICorDebugStringValue::GetString method [.NET Framework debugging]
- GetString method, ICorDebugStringValue interface [.NET Framework debugging]
ms.assetid: 2b94bda7-09ee-435d-91b9-c4e31af1896c
topic_type:
- apiref
ms.openlocfilehash: 06e8e039c8b0afb7753a398302a9b32eb3ba7213
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99717346"
---
# <a name="icordebugstringvaluegetstring-method"></a><span data-ttu-id="002fd-103">Метод ICorDebugStringValue::GetString</span><span class="sxs-lookup"><span data-stu-id="002fd-103">ICorDebugStringValue::GetString Method</span></span>

<span data-ttu-id="002fd-104">Возвращает строку, на которую ссылается этот ICorDebugStringValue.</span><span class="sxs-lookup"><span data-stu-id="002fd-104">Gets the string referenced by this ICorDebugStringValue.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="002fd-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="002fd-105">Syntax</span></span>  
  
```cpp  
HRESULT GetString (  
    [in] ULONG32    cchString,  
    [out] ULONG32   *pcchString,  
    [out, size_is(cchString), length_is(*pcchString)]
        WCHAR       szString[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="002fd-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="002fd-106">Parameters</span></span>  

 `cchString`  
 <span data-ttu-id="002fd-107">[in] Размер массива `szString`.</span><span class="sxs-lookup"><span data-stu-id="002fd-107">[in] The size of the `szString` array.</span></span>  
  
 `pcchString`  
 <span data-ttu-id="002fd-108">заполняет Указатель на число символов, возвращаемых в `szString` массиве.</span><span class="sxs-lookup"><span data-stu-id="002fd-108">[out] A pointer to the number of characters returned in the `szString` array.</span></span>  
  
 `szString`  
 <span data-ttu-id="002fd-109">заполняет Массив, в котором хранится извлеченная строка.</span><span class="sxs-lookup"><span data-stu-id="002fd-109">[out] An array that stores the retrieved string.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="002fd-110">Требования</span><span class="sxs-lookup"><span data-stu-id="002fd-110">Requirements</span></span>  

 <span data-ttu-id="002fd-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="002fd-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="002fd-112">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="002fd-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="002fd-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="002fd-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="002fd-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="002fd-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
