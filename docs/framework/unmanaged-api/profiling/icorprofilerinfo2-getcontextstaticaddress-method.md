---
description: 'Дополнительные сведения о методе: ICorProfilerInfo2:: Жетконтекстстатикаддресс'
title: Метод ICorProfilerInfo2::GetContextStaticAddress
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetContextStaticAddress
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetContextStaticAddress
helpviewer_keywords:
- GetContextStaticAddress method [.NET Framework profiling]
- ICorProfilerInfo2::GetContextStaticAddress method [.NET Framework profiling]
ms.assetid: 2b374116-0972-416a-8cf5-79213129be9a
topic_type:
- apiref
ms.openlocfilehash: 7ea8b81c8b1dba4577e070eda68e760cc39f9131
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99760517"
---
# <a name="icorprofilerinfo2getcontextstaticaddress-method"></a><span data-ttu-id="08662-103">Метод ICorProfilerInfo2::GetContextStaticAddress</span><span class="sxs-lookup"><span data-stu-id="08662-103">ICorProfilerInfo2::GetContextStaticAddress Method</span></span>

<span data-ttu-id="08662-104">Возвращает адрес для указанного статического поля контекста, которое находится в области заданного контекста.</span><span class="sxs-lookup"><span data-stu-id="08662-104">Gets the address for the specified context-static field that is in the scope of the specified context.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08662-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="08662-105">Syntax</span></span>  
  
```cpp  
HRESULT GetContextStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [in] ContextID contextId,  
    [out] void **ppAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="08662-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="08662-106">Parameters</span></span>  

 `classId`  
 <span data-ttu-id="08662-107">окне Идентификатор класса, содержащего запрошенное статическое поле контекста.</span><span class="sxs-lookup"><span data-stu-id="08662-107">[in] The ID of the class that contains the requested context-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="08662-108">окне Токен метаданных для запрошенного статического поля контекста.</span><span class="sxs-lookup"><span data-stu-id="08662-108">[in] The metadata token for the requested context-static field.</span></span>  
  
 `contextId`  
 <span data-ttu-id="08662-109">окне Идентификатор контекста, который является областью для запрошенного статического поля контекста.</span><span class="sxs-lookup"><span data-stu-id="08662-109">[in] The ID of the context that is the scope for the requested context-static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="08662-110">заполняет Указатель на адрес статического поля в заданном контексте.</span><span class="sxs-lookup"><span data-stu-id="08662-110">[out] A pointer to the address of the static field that is within the specified context.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="08662-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="08662-111">Remarks</span></span>  

 <span data-ttu-id="08662-112">`GetContextStaticAddress`Метод может вернуть одно из следующих данных:</span><span class="sxs-lookup"><span data-stu-id="08662-112">The `GetContextStaticAddress` method may return one of the following:</span></span>  
  
- <span data-ttu-id="08662-113">CORPROF_E_DATAINCOMPLETE HRESULT, если заданному статическому полю не назначен адрес в указанном контексте.</span><span class="sxs-lookup"><span data-stu-id="08662-113">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
- <span data-ttu-id="08662-114">Адреса объектов, которые могут находиться в куче сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="08662-114">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="08662-115">Эти адреса могут стать недействительными после сборки мусора, поэтому после сборки мусора профилировщики не должны считать, что они являются допустимыми.</span><span class="sxs-lookup"><span data-stu-id="08662-115">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="08662-116">Перед завершением конструктора класса класса возвратит `GetContextStaticAddress` CORPROF_E_DATAINCOMPLETE для всех его статических полей, хотя некоторые статические поля уже могут быть инициализированы и корневыми объектами сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="08662-116">Before a class’s class constructor is completed, `GetContextStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08662-117">Требования</span><span class="sxs-lookup"><span data-stu-id="08662-117">Requirements</span></span>  

 <span data-ttu-id="08662-118">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="08662-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="08662-119">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="08662-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="08662-120">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="08662-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="08662-121">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="08662-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08662-122">См. также</span><span class="sxs-lookup"><span data-stu-id="08662-122">See also</span></span>

- [<span data-ttu-id="08662-123">Интерфейс ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="08662-123">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="08662-124">Интерфейс ICorProfilerInfo2</span><span class="sxs-lookup"><span data-stu-id="08662-124">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
