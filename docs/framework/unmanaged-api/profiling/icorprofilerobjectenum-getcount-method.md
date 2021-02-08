---
description: 'Дополнительные сведения о методе: ICorProfilerObjectEnum:: NOCOUNT'
title: Метод ICorProfilerObjectEnum::GetCount
ms.date: 03/30/2017
api_name:
- ICorProfilerObjectEnum.GetCount
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerObjectEnum::GetCount
helpviewer_keywords:
- ICorProfilerObjectEnum::GetCount method [.NET Framework profiling]
- GetCount method, ICorProfilerObjectEnum interface [.NET Framework profiling]
ms.assetid: 166b0761-ed80-4ccd-9973-dc20e61bf8fa
topic_type:
- apiref
ms.openlocfilehash: b1bedfca913a099f88780807021497d15f75fcd8
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99798944"
---
# <a name="icorprofilerobjectenumgetcount-method"></a><span data-ttu-id="53fc2-103">Метод ICorProfilerObjectEnum::GetCount</span><span class="sxs-lookup"><span data-stu-id="53fc2-103">ICorProfilerObjectEnum::GetCount Method</span></span>

<span data-ttu-id="53fc2-104">Возвращает общее число замороженных объектов в коллекции.</span><span class="sxs-lookup"><span data-stu-id="53fc2-104">Gets the total number of frozen objects in the collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53fc2-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="53fc2-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCount (  
    [out] ULONG   *pcelt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="53fc2-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="53fc2-106">Parameters</span></span>  

 `pcelt`  
 <span data-ttu-id="53fc2-107">заполняет Указатель на число замороженных объектов в коллекции.</span><span class="sxs-lookup"><span data-stu-id="53fc2-107">[out] A pointer to the number of frozen objects in the collection.</span></span>  
  
 <span data-ttu-id="53fc2-108">Этот метод всегда будет возвращать ноль в платформа .NET Framework версии 3,5 с пакетом обновления 1 (SP1) и более поздних версиях.</span><span class="sxs-lookup"><span data-stu-id="53fc2-108">This method will always return zero in the .NET Framework version 3.5 Service Pack 1 (SP1) and later versions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53fc2-109">Требования</span><span class="sxs-lookup"><span data-stu-id="53fc2-109">Requirements</span></span>  

 <span data-ttu-id="53fc2-110">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="53fc2-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53fc2-111">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="53fc2-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="53fc2-112">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="53fc2-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="53fc2-113">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53fc2-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53fc2-114">См. также</span><span class="sxs-lookup"><span data-stu-id="53fc2-114">See also</span></span>

- [<span data-ttu-id="53fc2-115">Интерфейс ICorProfilerObjectEnum</span><span class="sxs-lookup"><span data-stu-id="53fc2-115">ICorProfilerObjectEnum Interface</span></span>](icorprofilerobjectenum-interface.md)
