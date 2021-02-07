---
description: 'Дополнительные сведения о методе: ICorDebugEnum:: Clone'
title: Метод ICorDebugEnum::Clone
ms.date: 03/30/2017
api_name:
- ICorDebugEnum.Clone
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEnum::Clone
helpviewer_keywords:
- Clone method, ICorDebugEnum interface [.NET Framework debugging]
- ICorDebugEnum::Clone method [.NET Framework debugging]
ms.assetid: 57eefaf3-75cf-4496-bc94-88c0706861b7
topic_type:
- apiref
ms.openlocfilehash: 18219757980870dcf9663477d195068a76814de1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99694582"
---
# <a name="icordebugenumclone-method"></a><span data-ttu-id="fa13d-103">Метод ICorDebugEnum::Clone</span><span class="sxs-lookup"><span data-stu-id="fa13d-103">ICorDebugEnum::Clone Method</span></span>

<span data-ttu-id="fa13d-104">Создает копию этого объекта ICorDebugEnum.</span><span class="sxs-lookup"><span data-stu-id="fa13d-104">Creates a copy of this ICorDebugEnum object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa13d-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="fa13d-105">Syntax</span></span>  
  
```cpp  
HRESULT Clone (  
    [out] ICorDebugEnum **ppEnum  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fa13d-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="fa13d-106">Parameters</span></span>  

 `ppEnum`  
 <span data-ttu-id="fa13d-107">заполняет Указатель на адрес `ICorDebugEnum` объекта, который является копией этого `ICorDebugEnum` объекта.</span><span class="sxs-lookup"><span data-stu-id="fa13d-107">[out] A pointer to the address of an `ICorDebugEnum` object that is a copy of this `ICorDebugEnum` object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fa13d-108">Требования</span><span class="sxs-lookup"><span data-stu-id="fa13d-108">Requirements</span></span>  

 <span data-ttu-id="fa13d-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fa13d-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fa13d-110">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fa13d-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fa13d-111">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fa13d-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fa13d-112">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fa13d-112">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
