---
description: 'Дополнительные сведения о методе ICorProfilerInfo:: Жетмодулеметадата'
title: Метод ICorProfilerInfo::GetModuleMetaData
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetModuleMetaData
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetModuleMetaData
helpviewer_keywords:
- GetModuleMetaData method [.NET Framework profiling]
- ICorProfilerInfo::GetModuleMetaData method [.NET Framework profiling]
ms.assetid: 7a439d92-348a-44dd-b60f-cad7cba56379
topic_type:
- apiref
ms.openlocfilehash: ff0fb0563b041fcb3cf63438874724c8236d6081
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99647184"
---
# <a name="icorprofilerinfogetmodulemetadata-method"></a><span data-ttu-id="bb3a7-103">Метод ICorProfilerInfo::GetModuleMetaData</span><span class="sxs-lookup"><span data-stu-id="bb3a7-103">ICorProfilerInfo::GetModuleMetaData Method</span></span>

<span data-ttu-id="bb3a7-104">Возвращает экземпляр интерфейса метаданных, сопоставляемый с указанным модулем.</span><span class="sxs-lookup"><span data-stu-id="bb3a7-104">Gets a metadata interface instance that maps to the specified module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb3a7-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="bb3a7-105">Syntax</span></span>  
  
```cpp  
HRESULT GetModuleMetaData(  
    [in]  ModuleID moduleId,  
    [in]  DWORD    dwOpenFlags,  
    [in]  REFIID   riid,  
    [out] IUnknown **ppOut);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bb3a7-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="bb3a7-106">Parameters</span></span>  

 `moduleId`  
 <span data-ttu-id="bb3a7-107">окне Идентификатор модуля, с которым будет сопоставлен экземпляр интерфейса.</span><span class="sxs-lookup"><span data-stu-id="bb3a7-107">[in] The ID of the module to which the interface instance will be mapped.</span></span>  
  
 `dwOpenFlags`  
 <span data-ttu-id="bb3a7-108">окне Значение перечисления [коропенфлагс](../metadata/coropenflags-enumeration.md) , указывающее режим открытия файлов манифеста.</span><span class="sxs-lookup"><span data-stu-id="bb3a7-108">[in] A value of the [CorOpenFlags](../metadata/coropenflags-enumeration.md) enumeration that specifies the mode for opening manifest files.</span></span> <span data-ttu-id="bb3a7-109">Допустимы только `ofRead` `ofWrite` биты и `ofNoTransform` .</span><span class="sxs-lookup"><span data-stu-id="bb3a7-109">Only the `ofRead`, `ofWrite` and `ofNoTransform` bits are valid.</span></span>  
  
 `riid`  
 <span data-ttu-id="bb3a7-110">окне Идентификатор ссылки (GUID) интерфейса метаданных, экземпляр которого будет извлечен.</span><span class="sxs-lookup"><span data-stu-id="bb3a7-110">[in] The reference ID (GUID) of the metadata interface whose instance will be retrieved.</span></span> <span data-ttu-id="bb3a7-111">Список интерфейсов см. в разделе [интерфейсы метаданных](../metadata/metadata-interfaces.md) .</span><span class="sxs-lookup"><span data-stu-id="bb3a7-111">See [Metadata Interfaces](../metadata/metadata-interfaces.md) for a list of the interfaces.</span></span>  
  
 `ppOut`  
 <span data-ttu-id="bb3a7-112">заполняет Указатель на адрес экземпляра интерфейса метаданных.</span><span class="sxs-lookup"><span data-stu-id="bb3a7-112">[out] A pointer to the address of the metadata interface instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bb3a7-113">Remarks</span><span class="sxs-lookup"><span data-stu-id="bb3a7-113">Remarks</span></span>  

 <span data-ttu-id="bb3a7-114">Можно запросить открытие метаданных в режиме чтения/записи, но это приведет к более медленному выполнению метаданных программы, так как изменения метаданных не могут быть оптимизированы по мере их постановки в компилятор.</span><span class="sxs-lookup"><span data-stu-id="bb3a7-114">You may ask for the metadata to be opened in read/write mode, but this will result in slower metadata execution of the program, because changes made to the metadata cannot be optimized as they were from the compiler.</span></span>  
  
 <span data-ttu-id="bb3a7-115">Некоторые модули (например, модули ресурсов) не имеют метаданных.</span><span class="sxs-lookup"><span data-stu-id="bb3a7-115">Some modules (such as resource modules) have no metadata.</span></span> <span data-ttu-id="bb3a7-116">В этих случаях `GetModuleMetaData` возвращает значение HRESULT, равное S_FALSE, и значение NULL в \* `ppOut` .</span><span class="sxs-lookup"><span data-stu-id="bb3a7-116">In those cases, `GetModuleMetaData` will return an HRESULT value of S_FALSE, and a null in \*`ppOut`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb3a7-117">Требования</span><span class="sxs-lookup"><span data-stu-id="bb3a7-117">Requirements</span></span>  

 <span data-ttu-id="bb3a7-118">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bb3a7-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb3a7-119">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="bb3a7-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="bb3a7-120">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bb3a7-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bb3a7-121">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb3a7-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb3a7-122">См. также</span><span class="sxs-lookup"><span data-stu-id="bb3a7-122">See also</span></span>

- [<span data-ttu-id="bb3a7-123">Интерфейс ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="bb3a7-123">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
