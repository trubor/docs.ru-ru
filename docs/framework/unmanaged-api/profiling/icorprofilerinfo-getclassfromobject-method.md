---
description: 'Дополнительные сведения о методе ICorProfilerInfo:: GetClassFromObject'
title: Метод ICorProfilerInfo::GetClassFromObject
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetClassFromObject
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetClassFromObject
helpviewer_keywords:
- GetClassFromObject method [.NET Framework profiling]
- ICorProfilerInfo::GetClassFromObject method [.NET Framework profiling]
ms.assetid: b97493fb-713e-49d5-a73e-5688b2ad0700
topic_type:
- apiref
ms.openlocfilehash: 1c0224137c839d167263eefb17e3ae0b3ac29ef3
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99647821"
---
# <a name="icorprofilerinfogetclassfromobject-method"></a><span data-ttu-id="b334b-103">Метод ICorProfilerInfo::GetClassFromObject</span><span class="sxs-lookup"><span data-stu-id="b334b-103">ICorProfilerInfo::GetClassFromObject Method</span></span>

<span data-ttu-id="b334b-104">Возвращает `ClassID` объект объекта, учитывая его свойство `ObjectID` .</span><span class="sxs-lookup"><span data-stu-id="b334b-104">Gets the `ClassID` of an object, given its `ObjectID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b334b-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b334b-105">Syntax</span></span>  
  
```cpp  
HRESULT GetClassFromObject(  
    [in]  ObjectID objectId,  
    [out] ClassID *pClassId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b334b-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="b334b-106">Parameters</span></span>  

 `objectId`  
 <span data-ttu-id="b334b-107">окне Идентификатор объекта, для которого необходимо получить объект `ClassID` .</span><span class="sxs-lookup"><span data-stu-id="b334b-107">[in] The ID of the object for which to get the `ClassID`.</span></span>  
  
 `pClassId`  
 <span data-ttu-id="b334b-108">заполняет Указатель на возвращаемый объект `ClassID` .</span><span class="sxs-lookup"><span data-stu-id="b334b-108">[out] A pointer to the returned `ClassID`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b334b-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="b334b-109">Remarks</span></span>  

 <span data-ttu-id="b334b-110">Значение NULL `pClassId` указывает, что `objectId` имеет тип, который выгружается.</span><span class="sxs-lookup"><span data-stu-id="b334b-110">A null `pClassId` indicates that `objectId` has a type that is unloading.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b334b-111">Требования</span><span class="sxs-lookup"><span data-stu-id="b334b-111">Requirements</span></span>  

 <span data-ttu-id="b334b-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b334b-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b334b-113">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b334b-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b334b-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b334b-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b334b-115">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b334b-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b334b-116">См. также</span><span class="sxs-lookup"><span data-stu-id="b334b-116">See also</span></span>

- [<span data-ttu-id="b334b-117">Интерфейс ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="b334b-117">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
