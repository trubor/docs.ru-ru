---
description: 'Дополнительные сведения о методе: ICorProfilerInfo7:: GetInMemorySymbolsLength'
title: 'Метод ICorProfilerInfo7:: GetInMemorySymbolsLength'
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo7.GetInMemorySymbolsLength
api_location:
- mscorwks.dll
- icorprof.idl
api_type:
- COM
ms.assetid: d62c4a4c-8a62-45aa-8f01-a8387cf36159
ms.openlocfilehash: 5d96b17e8abbd023f2d050eff3f121a871a94754
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99737120"
---
# <a name="icorprofilerinfo7getinmemorysymbolslength-method"></a><span data-ttu-id="73341-103">Метод ICorProfilerInfo7:: GetInMemorySymbolsLength</span><span class="sxs-lookup"><span data-stu-id="73341-103">ICorProfilerInfo7::GetInMemorySymbolsLength Method</span></span>

<span data-ttu-id="73341-104">[Поддерживается в .NET Framework 4.6.1 и более поздних версиях.]</span><span class="sxs-lookup"><span data-stu-id="73341-104">[Supported in the .NET Framework 4.6.1 and later versions]</span></span>  
  
 <span data-ttu-id="73341-105">Возвращает длину потока символов в памяти.</span><span class="sxs-lookup"><span data-stu-id="73341-105">Returns the length of an in-memory symbol stream.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73341-106">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="73341-106">Syntax</span></span>  
  
```cpp  
HRESULT GetInMemorySymbolsLength(  
        [in] ModuleID moduleId,  
        [out] DWORD* pCountSymbolBytes  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="73341-107">Параметры</span><span class="sxs-lookup"><span data-stu-id="73341-107">Parameters</span></span>  

 `moduleId`  
 <span data-ttu-id="73341-108">окне Идентификатор модуля, содержащего поток в памяти.</span><span class="sxs-lookup"><span data-stu-id="73341-108">[in] The identifier of the module containing the in-memory stream.</span></span>  
  
 <span data-ttu-id="73341-109">пкаунтсимболбитес</span><span class="sxs-lookup"><span data-stu-id="73341-109">pCountSymbolBytes</span></span>  
 <span data-ttu-id="73341-110">заполняет Указатель на значение, `DWORD` которое при возврате метода содержит длину потока в байтах.</span><span class="sxs-lookup"><span data-stu-id="73341-110">[out] A pointer to a `DWORD` value that, when the method returns, contains the length of the stream in bytes.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="73341-111">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="73341-111">Return Value</span></span>  

 <span data-ttu-id="73341-112">Метод возвращает значение `S_OK` , если длина потока памяти может быть определена, даже если она равна нулю (0).</span><span class="sxs-lookup"><span data-stu-id="73341-112">The method returns `S_OK` if the length of the memory stream can be determined, even if it is zero (0).</span></span>  
  
 <span data-ttu-id="73341-113">Метод возвращает значение, `CORPROF_E_MODULE_IS_DYNAMIC` Если метод был создан с помощью <xref:System.Reflection.Emit?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="73341-113">The method returns `CORPROF_E_MODULE_IS_DYNAMIC` if the method was created using <xref:System.Reflection.Emit?displayProperty=nameWithType>.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="73341-114">Remarks</span><span class="sxs-lookup"><span data-stu-id="73341-114">Remarks</span></span>  

 <span data-ttu-id="73341-115">Если модуль содержит символы в памяти, длина потока помещается в `pCountSymbolBytes` .</span><span class="sxs-lookup"><span data-stu-id="73341-115">If the module has in-memory symbols, the length of the stream is placed in `pCountSymbolBytes`.</span></span> <span data-ttu-id="73341-116">Если у модуля нет символов в памяти, то `*pCountSymbolBytes = 0` .</span><span class="sxs-lookup"><span data-stu-id="73341-116">If the module doesn't have in-memory     symbols, `*pCountSymbolBytes = 0`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="73341-117">Текущая реализация не поддерживает отражение. Emit.</span><span class="sxs-lookup"><span data-stu-id="73341-117">The current implementation does not support Reflection.Emit.</span></span> <span data-ttu-id="73341-118">Если модуль был создан с помощью отражения. Emit, метод возвращает значение `CORPROF_E_MODULE_IS_DYNAMIC` .</span><span class="sxs-lookup"><span data-stu-id="73341-118">If the module was created by using Reflection.Emit, the method returns `CORPROF_E_MODULE_IS_DYNAMIC`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73341-119">Требования</span><span class="sxs-lookup"><span data-stu-id="73341-119">Requirements</span></span>  

 <span data-ttu-id="73341-120">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73341-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73341-121">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="73341-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="73341-122">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="73341-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="73341-123">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73341-123">**.NET Framework Versions:** [!INCLUDE[net_current_v461plus](../../../../includes/net-current-v461plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73341-124">См. также</span><span class="sxs-lookup"><span data-stu-id="73341-124">See also</span></span>

- [<span data-ttu-id="73341-125">Интерфейс ICorProfilerInfo7</span><span class="sxs-lookup"><span data-stu-id="73341-125">ICorProfilerInfo7 Interface</span></span>](icorprofilerinfo7-interface.md)
