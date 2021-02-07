---
description: 'Дополнительные сведения о методе: ICorProfilerInfo2:: GetStaticFieldInfo'
title: Метод ICorProfilerInfo2::GetStaticFieldInfo
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetStaticFieldInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetStaticFieldInfo
helpviewer_keywords:
- ICorProfilerInfo2::GetStaticFieldInfo method [.NET Framework profiling]
- GetStaticFieldInfo method [.NET Framework profiling]
ms.assetid: fc663e76-e23f-49a8-bdd5-52cdf1a3b2b3
topic_type:
- apiref
ms.openlocfilehash: 1acde9d5ad1a35b11cb036bced99c1909f0b6b04
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99716362"
---
# <a name="icorprofilerinfo2getstaticfieldinfo-method"></a><span data-ttu-id="ff387-103">Метод ICorProfilerInfo2::GetStaticFieldInfo</span><span class="sxs-lookup"><span data-stu-id="ff387-103">ICorProfilerInfo2::GetStaticFieldInfo Method</span></span>

<span data-ttu-id="ff387-104">Возвращает значение, указывающее тип статического объекта, который применяется к указанному полю.</span><span class="sxs-lookup"><span data-stu-id="ff387-104">Gets a value that indicates the kind of static that applies to the specified field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ff387-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ff387-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStaticFieldInfo (  
    [in] ClassID               classId,  
    [in] mdFieldDef            fieldToken,  
    [out] COR_PRF_STATIC_TYPE  *pFieldInfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ff387-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="ff387-106">Parameters</span></span>  

 `classId`  
 <span data-ttu-id="ff387-107">окне Идентификатор класса, в котором определено статическое поле.</span><span class="sxs-lookup"><span data-stu-id="ff387-107">[in] The ID of the class in which the static field is defined.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="ff387-108">окне Маркер метаданных для статического поля.</span><span class="sxs-lookup"><span data-stu-id="ff387-108">[in] The metadata token for the static field.</span></span>  
  
 `pFieldInfo`  
 <span data-ttu-id="ff387-109">заполняет Указатель на значение перечисления [COR_PRF_STATIC_TYPE](cor-prf-static-type-enumeration.md) , указывающее, является ли указанное поле статическим, и, если это так, тип статического, применяемого к полю.</span><span class="sxs-lookup"><span data-stu-id="ff387-109">[out] A pointer to a value of the [COR_PRF_STATIC_TYPE](cor-prf-static-type-enumeration.md) enumeration that indicates whether the specified field is static, and if so, the kind of static that applies to the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ff387-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="ff387-110">Remarks</span></span>  

 <span data-ttu-id="ff387-111">Эти сведения можно использовать для определения функции, вызываемой для получения адреса статического поля.</span><span class="sxs-lookup"><span data-stu-id="ff387-111">This information can be used to determine which function to call to get the address of the static field.</span></span>  
  
 <span data-ttu-id="ff387-112">Код профилировщика должен по-прежнему проверять метаданные для статического поля, чтобы убедиться, что он действительно имеет адрес.</span><span class="sxs-lookup"><span data-stu-id="ff387-112">The profiler code should still check the metadata for a static field to ensure that it actually has an address.</span></span> <span data-ttu-id="ff387-113">Статические литералы (константы) существуют только в метаданных и не имеют адреса.</span><span class="sxs-lookup"><span data-stu-id="ff387-113">Static literals (that is, constants) exist only in the metadata and do not have an address.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ff387-114">Требования</span><span class="sxs-lookup"><span data-stu-id="ff387-114">Requirements</span></span>  

 <span data-ttu-id="ff387-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ff387-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ff387-116">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ff387-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ff387-117">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ff387-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ff387-118">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ff387-118">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ff387-119">См. также</span><span class="sxs-lookup"><span data-stu-id="ff387-119">See also</span></span>

- [<span data-ttu-id="ff387-120">Интерфейс ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="ff387-120">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="ff387-121">Интерфейс ICorProfilerInfo2</span><span class="sxs-lookup"><span data-stu-id="ff387-121">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
