---
description: 'Дополнительные сведения о методе: ICorDebugClass:: module'
title: Метод ICorDebugClass::GetModule
ms.date: 03/30/2017
api_name:
- ICorDebugClass.GetModule
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass::GetModule
helpviewer_keywords:
- GetModule method, ICorDebugClass interface [.NET Framework debugging]
- ICorDebugClass::GetModule method [.NET Framework debugging]
ms.assetid: 87029cc4-e5e1-42d5-8b98-655bb7ece520
topic_type:
- apiref
ms.openlocfilehash: 338ea5aeede4a209f7a3e3ed685ae9bd84105890
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99711548"
---
# <a name="icordebugclassgetmodule-method"></a><span data-ttu-id="2c377-103">Метод ICorDebugClass::GetModule</span><span class="sxs-lookup"><span data-stu-id="2c377-103">ICorDebugClass::GetModule Method</span></span>

<span data-ttu-id="2c377-104">Возвращает модуль, который определяет этот класс.</span><span class="sxs-lookup"><span data-stu-id="2c377-104">Gets the module that defines this class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c377-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="2c377-105">Syntax</span></span>  
  
```cpp  
HRESULT GetModule (  
    [out] ICorDebugModule    **pModule  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2c377-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="2c377-106">Parameters</span></span>  

 `pModule`  
 <span data-ttu-id="2c377-107">заполняет Указатель на адрес объекта ICorDebugModule, который представляет модуль, в котором определен этот класс.</span><span class="sxs-lookup"><span data-stu-id="2c377-107">[out] A pointer to the address of an ICorDebugModule object that represents the module in which this class is defined.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c377-108">Требования</span><span class="sxs-lookup"><span data-stu-id="2c377-108">Requirements</span></span>  

 <span data-ttu-id="2c377-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2c377-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c377-110">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2c377-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2c377-111">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2c377-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2c377-112">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c377-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
