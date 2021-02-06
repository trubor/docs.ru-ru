---
description: 'Дополнительные сведения о методе: ICorDebugModule:: Исинмемори'
title: Метод ICorDebugModule::IsInMemory
ms.date: 03/30/2017
api_name:
- ICorDebugModule.IsInMemory
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::IsInMemory
helpviewer_keywords:
- IsInMemory method [.NET Framework debugging]
- ICorDebugModule::IsInMemory method [.NET Framework debugging]
ms.assetid: 89940711-98e7-4aa6-bffc-5e39e91e1b7d
topic_type:
- apiref
ms.openlocfilehash: 41454ede15e1d45775af8fb0ab7a6b571d9c0e41
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99660093"
---
# <a name="icordebugmoduleisinmemory-method"></a><span data-ttu-id="f49b7-103">Метод ICorDebugModule::IsInMemory</span><span class="sxs-lookup"><span data-stu-id="f49b7-103">ICorDebugModule::IsInMemory Method</span></span>

<span data-ttu-id="f49b7-104">Возвращает значение, указывающее, существует ли этот модуль только в памяти.</span><span class="sxs-lookup"><span data-stu-id="f49b7-104">Gets a value that indicates whether this module exists only in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f49b7-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f49b7-105">Syntax</span></span>  
  
```cpp  
HRESULT IsInMemory(  
    [out] BOOL *pInMemory  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f49b7-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="f49b7-106">Parameters</span></span>  

 `pInMemory`  
 <span data-ttu-id="f49b7-107">[out] `true` значение, если этот модуль существует только в памяти; в противном случае — `false` .</span><span class="sxs-lookup"><span data-stu-id="f49b7-107">[out] `true` if this module exists only in memory; otherwise, `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f49b7-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="f49b7-108">Remarks</span></span>  

 <span data-ttu-id="f49b7-109">Среда CLR поддерживает загрузку модулей из необработанных потоков байтов.</span><span class="sxs-lookup"><span data-stu-id="f49b7-109">The common language runtime (CLR) supports the loading of modules from raw streams of bytes.</span></span> <span data-ttu-id="f49b7-110">Такие модули называются *модулями в памяти* и не существуют на диске.</span><span class="sxs-lookup"><span data-stu-id="f49b7-110">Such modules are called *in-memory modules* and do not exist on disk.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f49b7-111">Требования</span><span class="sxs-lookup"><span data-stu-id="f49b7-111">Requirements</span></span>  

 <span data-ttu-id="f49b7-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f49b7-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f49b7-113">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f49b7-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f49b7-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f49b7-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f49b7-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f49b7-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f49b7-116">См. также</span><span class="sxs-lookup"><span data-stu-id="f49b7-116">See also</span></span>
