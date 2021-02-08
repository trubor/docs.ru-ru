---
description: 'Дополнительные сведения о методе ICorProfilerInfo:: Жетобжектсизе'
title: Метод ICorProfilerInfo::GetObjectSize
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetObjectSize
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetObjectSize
helpviewer_keywords:
- GetObjectSize method [.NET Framework profiling]
- ICorProfilerInfo::GetObjectSize method [.NET Framework profiling]
ms.assetid: 9f02e763-73f7-42cb-a41c-f78499d9482c
topic_type:
- apiref
ms.openlocfilehash: c762b43e87c6f25b301f3f677728ca8cbe19b138
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99788635"
---
# <a name="icorprofilerinfogetobjectsize-method"></a><span data-ttu-id="d808d-103">Метод ICorProfilerInfo::GetObjectSize</span><span class="sxs-lookup"><span data-stu-id="d808d-103">ICorProfilerInfo::GetObjectSize Method</span></span>

<span data-ttu-id="d808d-104">Возвращает размер указанного объекта.</span><span class="sxs-lookup"><span data-stu-id="d808d-104">Gets the size of a specified object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d808d-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d808d-105">Syntax</span></span>  
  
```cpp  
HRESULT GetObjectSize(  
    [in]  ObjectID objectId,  
    [out] ULONG  *pcSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d808d-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="d808d-106">Parameters</span></span>  

 `objectId`  
 <span data-ttu-id="d808d-107">окне Идентификатор объекта.</span><span class="sxs-lookup"><span data-stu-id="d808d-107">[in] The ID of the object.</span></span>  
  
 `pcSize`  
 <span data-ttu-id="d808d-108">заполняет Указатель на размер объекта в байтах.</span><span class="sxs-lookup"><span data-stu-id="d808d-108">[out] A pointer to the object's size, in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d808d-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="d808d-109">Remarks</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d808d-110">Этот метод устарел.</span><span class="sxs-lookup"><span data-stu-id="d808d-110">This method is obsolete.</span></span> <span data-ttu-id="d808d-111">Он Возвращает COR_E_OVERFLOW для объектов размером более 4 ГБ на 64-разрядных платформах.</span><span class="sxs-lookup"><span data-stu-id="d808d-111">It returns COR_E_OVERFLOW for objects greater than 4GB on 64-bit platforms.</span></span> <span data-ttu-id="d808d-112">Используйте вместо этого метод  [метод icorprofilerinfo4:: GetObjectSize2](icorprofilerinfo4-getobjectsize2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="d808d-112">Use the  [ICorProfilerInfo4::GetObjectSize2](icorprofilerinfo4-getobjectsize2-method.md) method instead.</span></span>  
  
 <span data-ttu-id="d808d-113">Различные объекты одних и тех же типов часто имеют одинаковый размер.</span><span class="sxs-lookup"><span data-stu-id="d808d-113">Different objects of the same types often have the same size.</span></span> <span data-ttu-id="d808d-114">Однако некоторые типы, такие как массивы или строки, могут иметь разные размеры для каждого объекта.</span><span class="sxs-lookup"><span data-stu-id="d808d-114">However, some types, such as arrays or strings, may have a different size for each object.</span></span>  
  
 <span data-ttu-id="d808d-115">Размер, возвращаемый `GetObjectSize` методом, не включает заполнение выравнивания, которое может появиться после того, как объект находится в куче сборки мусора.</span><span class="sxs-lookup"><span data-stu-id="d808d-115">The size returned by the `GetObjectSize` method does not include any alignment padding that may appear after the object is on the garbage collection heap.</span></span> <span data-ttu-id="d808d-116">При использовании `GetObjectSize` метода для перехода от объекта к объекту в куче сборки мусора при необходимости добавьте заполнение выравнивания вручную.</span><span class="sxs-lookup"><span data-stu-id="d808d-116">If you use the `GetObjectSize` method to advance from object to object on the garbage collection heap, add alignment padding manually, as necessary.</span></span>  
  
- <span data-ttu-id="d808d-117">В 32-разрядных Windows, COR_PRF_GC_GEN_0, COR_PRF_GC_GEN_1 и COR_PRF_GC_GEN_2 использовать 4-байтовый выравнивание, а COR_PRF_GC_LARGE_OBJECT_HEAP использует 8-байтное выравнивание.</span><span class="sxs-lookup"><span data-stu-id="d808d-117">On 32-bit Windows, COR_PRF_GC_GEN_0, COR_PRF_GC_GEN_1, and COR_PRF_GC_GEN_2 use 4-byte alignment, and COR_PRF_GC_LARGE_OBJECT_HEAP uses 8-byte alignment.</span></span>  
  
- <span data-ttu-id="d808d-118">В 64-разрядной Windows выравнивание всегда равно 8 байтам.</span><span class="sxs-lookup"><span data-stu-id="d808d-118">On 64-bit Windows, the alignment is always 8 bytes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d808d-119">Требования</span><span class="sxs-lookup"><span data-stu-id="d808d-119">Requirements</span></span>  

 <span data-ttu-id="d808d-120">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d808d-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d808d-121">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d808d-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d808d-122">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d808d-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d808d-123">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d808d-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d808d-124">См. также</span><span class="sxs-lookup"><span data-stu-id="d808d-124">See also</span></span>

- [<span data-ttu-id="d808d-125">Интерфейс ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="d808d-125">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
