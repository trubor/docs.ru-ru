---
description: 'Дополнительные сведения о методе: ICorProfilerInfo3:: GetThreadStaticAddress2'
title: Метод ICorProfilerInfo3::GetThreadStaticAddress2
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo3.GetThreadStaticAddress2 Method
api_location:
- Mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo3::GetThreadStaticAddress2
helpviewer_keywords:
- ICorProfilerInfo3::GetThreadStaticAddress2 method [.NET Framework profiling]
- GetThreadStaticAddress2 method [.NET Framework profiling]
ms.assetid: a9608861-ae64-4467-8a73-be05ad34beac
topic_type:
- apiref
ms.openlocfilehash: 6734996435206f9e0c837eba39df1ad81677e54b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794550"
---
# <a name="icorprofilerinfo3getthreadstaticaddress2-method"></a><span data-ttu-id="1c2ad-103">Метод ICorProfilerInfo3::GetThreadStaticAddress2</span><span class="sxs-lookup"><span data-stu-id="1c2ad-103">ICorProfilerInfo3::GetThreadStaticAddress2 Method</span></span>

<span data-ttu-id="1c2ad-104">Возвращает адрес указанного поля статического потока, которое находится в области действия заданного потока и домена приложения.</span><span class="sxs-lookup"><span data-stu-id="1c2ad-104">Gets the address of the specified thread-static field that is in the scope of the specified thread and application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c2ad-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="1c2ad-105">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadStaticAddress2(  
                [in] ClassID classId,  
                [in] mdFieldDef fieldToken,  
                [in] AppDomainID appDomainId,  
                [in] ThreadID threadId,  
                [out] void **ppAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1c2ad-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="1c2ad-106">Parameters</span></span>  

 `classId`  
 <span data-ttu-id="1c2ad-107">окне Идентификатор класса, содержащего запрошенное статическое поле потока.</span><span class="sxs-lookup"><span data-stu-id="1c2ad-107">[in] The ID of the class that contains the requested thread-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="1c2ad-108">окне Токен метаданных для запрошенного статического поля потока.</span><span class="sxs-lookup"><span data-stu-id="1c2ad-108">[in] The metadata token for the requested thread-static field.</span></span>  
  
 `appDomainId`  
 <span data-ttu-id="1c2ad-109">[in] Идентификатор домена приложения.</span><span class="sxs-lookup"><span data-stu-id="1c2ad-109">[in] The ID of the application domain.</span></span>  
  
 `threadId`  
 <span data-ttu-id="1c2ad-110">окне Идентификатор потока, который является областью для запрошенного статического поля.</span><span class="sxs-lookup"><span data-stu-id="1c2ad-110">[in] The ID of the thread that is the scope for the requested static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="1c2ad-111">заполняет Указатель на адрес статического поля, находящихся в указанном потоке.</span><span class="sxs-lookup"><span data-stu-id="1c2ad-111">[out] A pointer to the address of the static field that is within the specified thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1c2ad-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="1c2ad-112">Remarks</span></span>  

 <span data-ttu-id="1c2ad-113">`GetThreadStaticAddress2`Метод может вернуть одно из следующих данных:</span><span class="sxs-lookup"><span data-stu-id="1c2ad-113">The `GetThreadStaticAddress2` method may return one of the following:</span></span>  
  
- <span data-ttu-id="1c2ad-114">CORPROF_E_DATAINCOMPLETE HRESULT, если заданному статическому полю не назначен адрес в указанном контексте.</span><span class="sxs-lookup"><span data-stu-id="1c2ad-114">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
- <span data-ttu-id="1c2ad-115">Адреса объектов, которые могут находиться в куче сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="1c2ad-115">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="1c2ad-116">Эти адреса могут стать недействительными после сборки мусора, поэтому после сборки мусора профилировщики не должны считать, что они являются допустимыми.</span><span class="sxs-lookup"><span data-stu-id="1c2ad-116">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="1c2ad-117">Перед завершением конструктора класса класса возвратит `GetThreadStaticAddress2` CORPROF_E_DATAINCOMPLETE для всех его статических полей, хотя некоторые статические поля уже могут быть инициализированы и корневыми объектами сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="1c2ad-117">Before a class’s class constructor is completed, `GetThreadStaticAddress2` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
 <span data-ttu-id="1c2ad-118">Метод [ICorProfilerInfo2:: жетсреадстатикаддресс](icorprofilerinfo2-getthreadstaticaddress-method.md) аналогичен `GetThreadStaticAddress2` методу, но не принимает аргумент домена приложения.</span><span class="sxs-lookup"><span data-stu-id="1c2ad-118">The [ICorProfilerInfo2::GetThreadStaticAddress](icorprofilerinfo2-getthreadstaticaddress-method.md) method is similar to the `GetThreadStaticAddress2` method, but does not accept an application domain argument.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c2ad-119">Требования</span><span class="sxs-lookup"><span data-stu-id="1c2ad-119">Requirements</span></span>  

 <span data-ttu-id="1c2ad-120">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1c2ad-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c2ad-121">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1c2ad-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1c2ad-122">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1c2ad-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1c2ad-123">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c2ad-123">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c2ad-124">См. также</span><span class="sxs-lookup"><span data-stu-id="1c2ad-124">See also</span></span>

- [<span data-ttu-id="1c2ad-125">Интерфейс ICorProfilerInfo3</span><span class="sxs-lookup"><span data-stu-id="1c2ad-125">ICorProfilerInfo3 Interface</span></span>](icorprofilerinfo3-interface.md)
- [<span data-ttu-id="1c2ad-126">Профилирующие интерфейсы</span><span class="sxs-lookup"><span data-stu-id="1c2ad-126">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="1c2ad-127">Профилирование</span><span class="sxs-lookup"><span data-stu-id="1c2ad-127">Profiling</span></span>](index.md)
