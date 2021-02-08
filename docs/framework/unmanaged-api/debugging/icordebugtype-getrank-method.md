---
description: Дополнительные сведения о методе "ICorDebugType::/Rank"
title: Метод ICorDebugType::GetRank
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetRank
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetRank
helpviewer_keywords:
- GetRank method, ICorDebugType interface [.NET Framework debugging]
- ICorDebugType::GetRank method [.NET Framework debugging]
ms.assetid: 72d3d927-f590-4f2d-8f60-448f3dfb96af
topic_type:
- apiref
ms.openlocfilehash: e13416856f900846d2df4b8a39303cf0b6a48ebc
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99800907"
---
# <a name="icordebugtypegetrank-method"></a><span data-ttu-id="8bcf9-103">Метод ICorDebugType::GetRank</span><span class="sxs-lookup"><span data-stu-id="8bcf9-103">ICorDebugType::GetRank Method</span></span>

<span data-ttu-id="8bcf9-104">Возвращает число измерений в типе массива.</span><span class="sxs-lookup"><span data-stu-id="8bcf9-104">Gets the number of dimensions in an array type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8bcf9-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="8bcf9-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRank (  
    [out] ULONG32   *pnRank  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8bcf9-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="8bcf9-106">Parameters</span></span>  

 `pnRank`  
 <span data-ttu-id="8bcf9-107">заполняет Указатель на число измерений.</span><span class="sxs-lookup"><span data-stu-id="8bcf9-107">[out] A pointer to the number of dimensions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8bcf9-108">Требования</span><span class="sxs-lookup"><span data-stu-id="8bcf9-108">Requirements</span></span>  

 <span data-ttu-id="8bcf9-109">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8bcf9-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8bcf9-110">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8bcf9-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8bcf9-111">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8bcf9-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8bcf9-112">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8bcf9-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
