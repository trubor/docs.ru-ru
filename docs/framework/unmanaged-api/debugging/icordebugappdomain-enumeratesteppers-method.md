---
description: 'Дополнительные сведения о методе: ICorDebugAppDomain:: Енумератестепперс'
title: Метод ICorDebugAppDomain::EnumerateSteppers
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.EnumerateSteppers
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::EnumerateSteppers
helpviewer_keywords:
- ICorDebugAppDomain::EnumerateSteppers method [.NET Framework debugging]
- EnumerateSteppers method [.NET Framework debugging]
ms.assetid: 3f3c4503-570e-44c1-ae6a-a3c6b840c732
topic_type:
- apiref
ms.openlocfilehash: a9c7f8b1486522b4740ec18c575c9876512b7d8c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754255"
---
# <a name="icordebugappdomainenumeratesteppers-method"></a><span data-ttu-id="a2817-103">Метод ICorDebugAppDomain::EnumerateSteppers</span><span class="sxs-lookup"><span data-stu-id="a2817-103">ICorDebugAppDomain::EnumerateSteppers Method</span></span>

<span data-ttu-id="a2817-104">Возвращает перечислитель для всех активных шагов в домене приложения.</span><span class="sxs-lookup"><span data-stu-id="a2817-104">Gets an enumerator for all active steppers in the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2817-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a2817-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateSteppers (  
    [out] ICorDebugStepperEnum   **ppSteppers  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a2817-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="a2817-106">Parameters</span></span>  

 `ppSteppers`  
 <span data-ttu-id="a2817-107">заполняет Указатель на адрес объекта Икордебугстепперенум, который является перечислителем для всех активных шагов в домене приложения.</span><span class="sxs-lookup"><span data-stu-id="a2817-107">[out] A pointer to the address of an ICorDebugStepperEnum object that is the enumerator for all active steppers in the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2817-108">Требования</span><span class="sxs-lookup"><span data-stu-id="a2817-108">Requirements</span></span>  

 <span data-ttu-id="a2817-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a2817-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2817-110">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a2817-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a2817-111">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a2817-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a2817-112">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2817-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
