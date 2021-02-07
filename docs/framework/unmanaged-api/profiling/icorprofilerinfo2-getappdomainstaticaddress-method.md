---
description: 'Дополнительные сведения о методе: ICorProfilerInfo2:: GetAppDomainStaticAddress'
title: Метод ICorProfilerInfo2::GetAppDomainStaticAddress
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetAppDomainStaticAddress
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetAppDomainStaticAddress
helpviewer_keywords:
- ICorProfilerInfo2::GetAppDomainStaticAddress method [.NET Framework profiling]
- GetAppDomainStaticAddress method [.NET Framework profiling]
ms.assetid: 2a9e0ea7-a9e2-4817-b1c4-fcf15b215ea9
topic_type:
- apiref
ms.openlocfilehash: 4ef8511e75a18f7626fa7a30ea194140de051bb2
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99753241"
---
# <a name="icorprofilerinfo2getappdomainstaticaddress-method"></a><span data-ttu-id="a6049-103">Метод ICorProfilerInfo2::GetAppDomainStaticAddress</span><span class="sxs-lookup"><span data-stu-id="a6049-103">ICorProfilerInfo2::GetAppDomainStaticAddress Method</span></span>

<span data-ttu-id="a6049-104">Возвращает адрес указанного поля статического домена приложения, которое находится в области заданного домена приложения.</span><span class="sxs-lookup"><span data-stu-id="a6049-104">Gets the address of the specified application domain-static field that is in the scope of the specified application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6049-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a6049-105">Syntax</span></span>  
  
```cpp  
RESULT GetAppDomainStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [in] AppDomainID appDomainId,  
    [out] void **ppAddress);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a6049-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="a6049-106">Parameters</span></span>  

 `classId`  
 <span data-ttu-id="a6049-107">окне Идентификатор класса, который содержит запрошенное статическое поле домена приложения.</span><span class="sxs-lookup"><span data-stu-id="a6049-107">[in] The class ID of the class that contains the requested application domain-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="a6049-108">окне Токен метаданных для запрошенного статического поля домена приложения.</span><span class="sxs-lookup"><span data-stu-id="a6049-108">[in] The metadata token for the requested application domain-static field.</span></span>  
  
 `appDomainId`  
 <span data-ttu-id="a6049-109">окне Идентификатор домена приложения, который является областью для запрошенного статического поля.</span><span class="sxs-lookup"><span data-stu-id="a6049-109">[in] The ID of the application domain that is the scope for the requested static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="a6049-110">заполняет Указатель на адрес статического поля в пределах указанного домена приложения.</span><span class="sxs-lookup"><span data-stu-id="a6049-110">[out] A pointer to the address of the static field that is within the specified application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a6049-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="a6049-111">Remarks</span></span>  

 <span data-ttu-id="a6049-112">`GetAppDomainStaticAddress`Метод может вернуть одно из следующих данных:</span><span class="sxs-lookup"><span data-stu-id="a6049-112">The `GetAppDomainStaticAddress` method may return one of the following:</span></span>  
  
- <span data-ttu-id="a6049-113">CORPROF_E_DATAINCOMPLETE HRESULT, если заданному статическому полю не назначен адрес в указанном контексте.</span><span class="sxs-lookup"><span data-stu-id="a6049-113">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
- <span data-ttu-id="a6049-114">Адреса объектов, которые могут находиться в куче сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="a6049-114">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="a6049-115">Эти адреса могут стать недействительными после сборки мусора, поэтому после сборки мусора профилировщики не должны считать, что они являются допустимыми.</span><span class="sxs-lookup"><span data-stu-id="a6049-115">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="a6049-116">Перед завершением конструктора класса класса возвратит `GetAppDomainStaticAddress` CORPROF_E_DATAINCOMPLETE для всех его статических полей, хотя некоторые статические поля уже могут быть инициализированы и корневыми объектами сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="a6049-116">Before a class’s class constructor is completed, `GetAppDomainStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6049-117">Требования</span><span class="sxs-lookup"><span data-stu-id="a6049-117">Requirements</span></span>  

 <span data-ttu-id="a6049-118">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a6049-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6049-119">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a6049-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a6049-120">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a6049-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a6049-121">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a6049-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6049-122">См. также</span><span class="sxs-lookup"><span data-stu-id="a6049-122">See also</span></span>

- [<span data-ttu-id="a6049-123">Интерфейс ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="a6049-123">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="a6049-124">Интерфейс ICorProfilerInfo2</span><span class="sxs-lookup"><span data-stu-id="a6049-124">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
