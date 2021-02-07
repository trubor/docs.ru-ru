---
description: 'Дополнительные сведения о методе: ICorDebugModule:: GetGlobalVariableValue'
title: Метод ICorDebugModule::GetGlobalVariableValue
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetGlobalVariableValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetGlobalVariableValue
helpviewer_keywords:
- ICorDebugModule::GetGlobalVariableValue method [.NET Framework debugging]
- GetGlobalVariableValue method [.NET Framework debugging]
ms.assetid: bbc0881c-6a59-41a0-b5ee-2f3d1b71684c
topic_type:
- apiref
ms.openlocfilehash: a4efe2f56387be7351fd5bc16716bcd1f34f7d7a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99691670"
---
# <a name="icordebugmodulegetglobalvariablevalue-method"></a><span data-ttu-id="16c8e-103">Метод ICorDebugModule::GetGlobalVariableValue</span><span class="sxs-lookup"><span data-stu-id="16c8e-103">ICorDebugModule::GetGlobalVariableValue Method</span></span>

<span data-ttu-id="16c8e-104">Возвращает значение указанной глобальной переменной.</span><span class="sxs-lookup"><span data-stu-id="16c8e-104">Gets the value of the specified global variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16c8e-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="16c8e-105">Syntax</span></span>  
  
```cpp  
HRESULT GetGlobalVariableValue(  
    [in]  mdFieldDef      fieldDef,  
    [out] ICorDebugValue  **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="16c8e-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="16c8e-106">Parameters</span></span>  

 `fieldDef`  
 <span data-ttu-id="16c8e-107">окне `mdFieldDef` Токен, ссылающийся на метаданные, описывающие глобальную переменную.</span><span class="sxs-lookup"><span data-stu-id="16c8e-107">[in] An `mdFieldDef` token that references the metadata describing the global variable.</span></span>  
  
 `ppValue`  
 <span data-ttu-id="16c8e-108">заполняет Указатель на адрес объекта ICorDebugValue, представляющий значение указанной глобальной переменной.</span><span class="sxs-lookup"><span data-stu-id="16c8e-108">[out] A pointer to the address of an ICorDebugValue object that represents the value of the specified global variable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16c8e-109">Требования</span><span class="sxs-lookup"><span data-stu-id="16c8e-109">Requirements</span></span>  

 <span data-ttu-id="16c8e-110">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="16c8e-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16c8e-111">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="16c8e-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="16c8e-112">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="16c8e-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="16c8e-113">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16c8e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
