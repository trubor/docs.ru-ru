---
description: 'Дополнительные сведения о методе: ICorProfilerInfo2:: Жетрвастатикаддресс'
title: Метод ICorProfilerInfo2::GetRVAStaticAddress
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetRVAStaticAddress
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetRVAStaticAddress
helpviewer_keywords:
- GetRVAStaticAddress method [.NET Framework profiling]
- ICorProfilerInfo2::GetRVAStaticAddress method [.NET Framework profiling]
ms.assetid: a25a8f8b-5cfa-440d-9376-a1a1c3a9fc11
topic_type:
- apiref
ms.openlocfilehash: e72a136ca0d8462d19c57da021e9429528555dac
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99716410"
---
# <a name="icorprofilerinfo2getrvastaticaddress-method"></a><span data-ttu-id="fae2f-103">Метод ICorProfilerInfo2::GetRVAStaticAddress</span><span class="sxs-lookup"><span data-stu-id="fae2f-103">ICorProfilerInfo2::GetRVAStaticAddress Method</span></span>

<span data-ttu-id="fae2f-104">Возвращает адрес указанного статического поля с относительным виртуальным адресом (RVA).</span><span class="sxs-lookup"><span data-stu-id="fae2f-104">Gets the address of the specified relative virtual address (RVA) static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fae2f-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="fae2f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRVAStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [out] void **ppAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fae2f-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="fae2f-106">Parameters</span></span>  

 `classId`  
 <span data-ttu-id="fae2f-107">окне Идентификатор класса, содержащего запрошенное статическое поле для параметра RVA.</span><span class="sxs-lookup"><span data-stu-id="fae2f-107">[in] The ID of the class that contains the requested RVA-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="fae2f-108">окне Токен метаданных для запрошенного статического поля.</span><span class="sxs-lookup"><span data-stu-id="fae2f-108">[in] Metadata token for the requested RVA-static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="fae2f-109">заполняет Указатель на адрес поля static-RVA.</span><span class="sxs-lookup"><span data-stu-id="fae2f-109">[out] A pointer to the address of the RVA-static field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fae2f-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="fae2f-110">Remarks</span></span>  

 <span data-ttu-id="fae2f-111">`GetRVAStaticAddress`Метод может вернуть одно из следующих данных:</span><span class="sxs-lookup"><span data-stu-id="fae2f-111">The `GetRVAStaticAddress` method may return one of the following:</span></span>  
  
- <span data-ttu-id="fae2f-112">CORPROF_E_DATAINCOMPLETE HRESULT, если заданному статическому полю не назначен адрес в указанном контексте.</span><span class="sxs-lookup"><span data-stu-id="fae2f-112">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
- <span data-ttu-id="fae2f-113">Адреса объектов, которые могут находиться в куче сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="fae2f-113">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="fae2f-114">Эти адреса могут стать недействительными после сборки мусора, поэтому после сборки мусора профилировщики не должны считать, что они являются допустимыми.</span><span class="sxs-lookup"><span data-stu-id="fae2f-114">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="fae2f-115">Перед завершением конструктора класса класса возвратит `GetRVAStaticAddress` CORPROF_E_DATAINCOMPLETE для всех его статических полей, хотя некоторые статические поля уже могут быть инициализированы и могут быть корневыми объектами сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="fae2f-115">Before a class’s class constructor is completed, `GetRVAStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and may be rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fae2f-116">Требования</span><span class="sxs-lookup"><span data-stu-id="fae2f-116">Requirements</span></span>  

 <span data-ttu-id="fae2f-117">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fae2f-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fae2f-118">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="fae2f-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fae2f-119">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fae2f-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fae2f-120">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fae2f-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fae2f-121">См. также</span><span class="sxs-lookup"><span data-stu-id="fae2f-121">See also</span></span>

- [<span data-ttu-id="fae2f-122">Интерфейс ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="fae2f-122">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="fae2f-123">Интерфейс ICorProfilerInfo2</span><span class="sxs-lookup"><span data-stu-id="fae2f-123">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
