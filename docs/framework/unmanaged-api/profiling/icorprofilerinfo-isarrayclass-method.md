---
description: 'Дополнительные сведения о методе ICorProfilerInfo:: Исаррайкласс'
title: Метод ICorProfilerInfo::IsArrayClass
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.IsArrayClass
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::IsArrayClass
helpviewer_keywords:
- IsArrayClass method [.NET Framework profiling]
- ICorProfilerInfo::IsArrayClass method [.NET Framework profiling]
ms.assetid: 7f230961-23a6-4d56-ad2d-7a876d65705f
topic_type:
- apiref
ms.openlocfilehash: 1eee0b834c63c3cfe15bd08776214ca8b2ba3f69
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99687237"
---
# <a name="icorprofilerinfoisarrayclass-method"></a><span data-ttu-id="32b76-103">Метод ICorProfilerInfo::IsArrayClass</span><span class="sxs-lookup"><span data-stu-id="32b76-103">ICorProfilerInfo::IsArrayClass Method</span></span>

<span data-ttu-id="32b76-104">Определяет, является ли указанный класс классом массива.</span><span class="sxs-lookup"><span data-stu-id="32b76-104">Determines whether the specified class is an array class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32b76-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="32b76-105">Syntax</span></span>  
  
```cpp  
HRESULT IsArrayClass(  
    [in]  ClassID        classId,  
    [out] CorElementType *pBaseElemType,  
    [out] ClassID        *pBaseClassId,  
    [out] ULONG          *pcRank);  
```  
  
## <a name="parameters"></a><span data-ttu-id="32b76-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="32b76-106">Parameters</span></span>  

 `classId`  
 <span data-ttu-id="32b76-107">окне Идентификатор анализируемого класса.</span><span class="sxs-lookup"><span data-stu-id="32b76-107">[in] The ID of the class to be examined.</span></span>  
  
 `pBaseElemType`  
 <span data-ttu-id="32b76-108">заполняет Указатель на значение перечисления Корелементтипе, указывающее тип элементов массива.</span><span class="sxs-lookup"><span data-stu-id="32b76-108">[out] A pointer to a value of the CorElementType enumeration that indicates the type of the array elements.</span></span>  
  
 `pBaseClassId`  
 <span data-ttu-id="32b76-109">заполняет Указатель на идентификатор класса элементов массива, если он доступен.</span><span class="sxs-lookup"><span data-stu-id="32b76-109">[out] A pointer to the class ID of the array elements, when available.</span></span>  
  
 `pcRank`  
 <span data-ttu-id="32b76-110">заполняет Указатель на целое число, указывающее ранг (то есть количество измерений) массива.</span><span class="sxs-lookup"><span data-stu-id="32b76-110">[out] A pointer to an integer that indicates the rank (that is, number of dimensions) of the array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="32b76-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="32b76-111">Remarks</span></span>  

 <span data-ttu-id="32b76-112">Если указанный класс является классом массива, `IsArrayClass` метод возвращает S_OK HRESULT и значения для любых выходных параметров, отличных от NULL.</span><span class="sxs-lookup"><span data-stu-id="32b76-112">If the specified class is an array class, the `IsArrayClass` method returns an S_OK HRESULT and values for any non-null output parameters.</span></span> <span data-ttu-id="32b76-113">В противном случае возвращается S_FALSE.</span><span class="sxs-lookup"><span data-stu-id="32b76-113">Otherwise, it returns S_FALSE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32b76-114">Требования</span><span class="sxs-lookup"><span data-stu-id="32b76-114">Requirements</span></span>  

 <span data-ttu-id="32b76-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="32b76-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32b76-116">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="32b76-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="32b76-117">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="32b76-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="32b76-118">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32b76-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32b76-119">См. также</span><span class="sxs-lookup"><span data-stu-id="32b76-119">See also</span></span>

- [<span data-ttu-id="32b76-120">Интерфейс ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="32b76-120">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
