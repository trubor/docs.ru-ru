---
description: 'Дополнительные сведения о методе: ICorProfilerInfo2:: Жетсреадстатикаддресс'
title: Метод ICorProfilerInfo2::GetThreadStaticAddress
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetThreadStaticAddress
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetThreadStaticAddress
helpviewer_keywords:
- GetThreadStaticAddress method [.NET Framework profiling]
- ICorProfilerInfo2::GetThreadStaticAddress method [.NET Framework profiling]
ms.assetid: 8e7dbf14-98a2-4384-a950-58a7640e59df
topic_type:
- apiref
ms.openlocfilehash: bab4190f3751967031806dccbea2fdf6add73f6e
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99647058"
---
# <a name="icorprofilerinfo2getthreadstaticaddress-method"></a><span data-ttu-id="f8b56-103">Метод ICorProfilerInfo2::GetThreadStaticAddress</span><span class="sxs-lookup"><span data-stu-id="f8b56-103">ICorProfilerInfo2::GetThreadStaticAddress Method</span></span>

<span data-ttu-id="f8b56-104">Возвращает адрес указанного статического поля потока, который находится в области заданного потока.</span><span class="sxs-lookup"><span data-stu-id="f8b56-104">Gets the address of the specified thread-static field that is in the scope of the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8b56-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f8b56-105">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadStaticAddress(  
    [in] ClassID     classId,  
    [in] mdFieldDef  fieldToken,  
    [in] ThreadID    threadId,  
    [out] void       **ppAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f8b56-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="f8b56-106">Parameters</span></span>  

 `classId`  
 <span data-ttu-id="f8b56-107">окне Идентификатор класса, содержащего запрошенное статическое поле потока.</span><span class="sxs-lookup"><span data-stu-id="f8b56-107">[in] The ID of the class that contains the requested thread-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="f8b56-108">окне Токен метаданных для запрошенного статического поля потока.</span><span class="sxs-lookup"><span data-stu-id="f8b56-108">[in] The metadata token for the requested thread-static field.</span></span>  
  
 `threadId`  
 <span data-ttu-id="f8b56-109">окне Идентификатор потока, который является областью для запрошенного статического поля.</span><span class="sxs-lookup"><span data-stu-id="f8b56-109">[in] The ID of the thread that is the scope for the requested static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="f8b56-110">заполняет Указатель на адрес статического поля, находящихся в указанном потоке.</span><span class="sxs-lookup"><span data-stu-id="f8b56-110">[out] A pointer to the address of the static field that is within the specified thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f8b56-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="f8b56-111">Remarks</span></span>  

 <span data-ttu-id="f8b56-112">`GetThreadStaticAddress`Метод может вернуть одно из следующих данных:</span><span class="sxs-lookup"><span data-stu-id="f8b56-112">The `GetThreadStaticAddress` method may return one of the following:</span></span>  
  
- <span data-ttu-id="f8b56-113">CORPROF_E_DATAINCOMPLETE HRESULT, если заданному статическому полю не назначен адрес в указанном контексте.</span><span class="sxs-lookup"><span data-stu-id="f8b56-113">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
- <span data-ttu-id="f8b56-114">Адреса объектов, которые могут находиться в куче сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="f8b56-114">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="f8b56-115">Эти адреса могут стать недействительными после сборки мусора, поэтому после завершения профилирования сборщиком мусора не следует считать, что они являются допустимыми.</span><span class="sxs-lookup"><span data-stu-id="f8b56-115">These addresses may become invalid after garbage collection, so after garbage collection profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="f8b56-116">Перед завершением конструктора класса класса возвратит `GetThreadStaticAddress` CORPROF_E_DATAINCOMPLETE для всех его статических полей, хотя некоторые статические поля уже могут быть инициализированы и корневыми объектами сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="f8b56-116">Before a class’s class constructor is completed, `GetThreadStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8b56-117">Требования</span><span class="sxs-lookup"><span data-stu-id="f8b56-117">Requirements</span></span>  

 <span data-ttu-id="f8b56-118">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f8b56-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8b56-119">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f8b56-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f8b56-120">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f8b56-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f8b56-121">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8b56-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8b56-122">См. также</span><span class="sxs-lookup"><span data-stu-id="f8b56-122">See also</span></span>

- [<span data-ttu-id="f8b56-123">Интерфейс ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="f8b56-123">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="f8b56-124">Интерфейс ICorProfilerInfo2</span><span class="sxs-lookup"><span data-stu-id="f8b56-124">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
