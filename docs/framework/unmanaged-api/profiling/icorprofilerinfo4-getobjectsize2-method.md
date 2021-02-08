---
description: 'Дополнительные сведения о методе: метод icorprofilerinfo4:: GetObjectSize2'
title: Метод ICorProfilerInfo4::GetObjectSize2
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.GetObjectSize2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::GetObjectSize2
helpviewer_keywords:
- GetObjectSize2 method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::GetObjectSize2 method [.NET Framework profiling]
ms.assetid: 4a3e43ed-3ee3-4395-ab14-f78b903be13e
topic_type:
- apiref
ms.openlocfilehash: 986c3d99501e21feec95dd3b6014f8d11d809704
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794528"
---
# <a name="icorprofilerinfo4getobjectsize2-method"></a><span data-ttu-id="d024a-103">Метод ICorProfilerInfo4::GetObjectSize2</span><span class="sxs-lookup"><span data-stu-id="d024a-103">ICorProfilerInfo4::GetObjectSize2 Method</span></span>

<span data-ttu-id="d024a-104">Возвращает размер указанного объекта.</span><span class="sxs-lookup"><span data-stu-id="d024a-104">Returns the size of a specified object.</span></span> <span data-ttu-id="d024a-105">Заменяет метод [ICorProfilerInfo:: жетобжектсизе](icorprofilerinfo-getobjectsize-method.md) , сообщая размеры объектов, размер которых больше, чем может быть выражено в `ULONG` .</span><span class="sxs-lookup"><span data-stu-id="d024a-105">Replaces the [ICorProfilerInfo::GetObjectSize](icorprofilerinfo-getobjectsize-method.md) method by reporting sizes of objects that are larger than what can be expressed in a `ULONG`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d024a-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d024a-106">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectSize2(  
    [in]  ObjectID objectId,  
    [out] SIZE_T *pcSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d024a-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="d024a-107">Parameters</span></span>  

 `objectId`  
 <span data-ttu-id="d024a-108">окне Идентификатор объекта.</span><span class="sxs-lookup"><span data-stu-id="d024a-108">[in] The ID of the object.</span></span>  
  
 `pcSize`  
 <span data-ttu-id="d024a-109">заполняет Указатель на размер объекта в байтах.</span><span class="sxs-lookup"><span data-stu-id="d024a-109">[out] A pointer to the object's size, in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d024a-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="d024a-110">Remarks</span></span>  

 <span data-ttu-id="d024a-111">Различные объекты одних и тех же типов часто имеют одинаковый размер.</span><span class="sxs-lookup"><span data-stu-id="d024a-111">Different objects of the same types often have the same size.</span></span> <span data-ttu-id="d024a-112">Однако некоторые типы, такие как массивы или строки, могут иметь разные размеры для каждого объекта.</span><span class="sxs-lookup"><span data-stu-id="d024a-112">However, some types, such as arrays or strings, may have a different size for each object.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d024a-113">Требования</span><span class="sxs-lookup"><span data-stu-id="d024a-113">Requirements</span></span>  

 <span data-ttu-id="d024a-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d024a-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d024a-115">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d024a-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d024a-116">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d024a-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d024a-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d024a-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d024a-118">См. также</span><span class="sxs-lookup"><span data-stu-id="d024a-118">See also</span></span>

- [<span data-ttu-id="d024a-119">Интерфейс ICorProfilerInfo4</span><span class="sxs-lookup"><span data-stu-id="d024a-119">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
