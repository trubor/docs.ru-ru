---
description: 'Дополнительные сведения о методе: ICorDebugAppDomain:: GetId'
title: Метод ICorDebugAppDomain::GetId
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.GetId
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::GetId
helpviewer_keywords:
- GetId method, ICorDebugAppDomain interface [.NET Framework debugging]
- ICorDebugAppDomain::GetId method [.NET Framework debugging]
ms.assetid: 32c27576-71fa-42ee-8230-67b92913ea08
topic_type:
- apiref
ms.openlocfilehash: ea660aa08e93e4ce2d97f1e7ae05b261db91118f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99772486"
---
# <a name="icordebugappdomaingetid-method"></a><span data-ttu-id="a17f3-103">Метод ICorDebugAppDomain::GetId</span><span class="sxs-lookup"><span data-stu-id="a17f3-103">ICorDebugAppDomain::GetId Method</span></span>

<span data-ttu-id="a17f3-104">Возвращает уникальный идентификатор домена приложения.</span><span class="sxs-lookup"><span data-stu-id="a17f3-104">Gets the unique identifier of the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a17f3-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a17f3-105">Syntax</span></span>  
  
```cpp  
HRESULT GetID (  
    [out] ULONG32   *pId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a17f3-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="a17f3-106">Parameters</span></span>  

 `pId`  
 <span data-ttu-id="a17f3-107">заполняет Уникальный идентификатор домена приложения.</span><span class="sxs-lookup"><span data-stu-id="a17f3-107">[out] The unique identifier of the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a17f3-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="a17f3-108">Remarks</span></span>  

 <span data-ttu-id="a17f3-109">Идентификатор домена приложения уникален в пределах содержащего его процесса.</span><span class="sxs-lookup"><span data-stu-id="a17f3-109">The identifier for the application domain is unique within the containing process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a17f3-110">Требования</span><span class="sxs-lookup"><span data-stu-id="a17f3-110">Requirements</span></span>  

 <span data-ttu-id="a17f3-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a17f3-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a17f3-112">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a17f3-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a17f3-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a17f3-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a17f3-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a17f3-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
