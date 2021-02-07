---
description: Дополнительные сведения о функции Креатеассембленум
title: Функция CreateAssemblyEnum
ms.date: 03/30/2017
api_name:
- CreateAssemblyEnum
api_location:
- fusion.dll
- clr.dll
- mscorwks.dll
api_type:
- DLLExport
f1_keywords:
- CreateAssemblyEnum
helpviewer_keywords:
- CreateAssemblyEnum function [.NET Framework fusion]
ms.assetid: 3506df38-6cea-42f6-946e-4287863bcfb3
topic_type:
- apiref
ms.openlocfilehash: 47177fcf0cd9e1b492fa89b9fb80c5cdaaced689
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99761146"
---
# <a name="createassemblyenum-function"></a><span data-ttu-id="408f2-103">Функция CreateAssemblyEnum</span><span class="sxs-lookup"><span data-stu-id="408f2-103">CreateAssemblyEnum Function</span></span>

<span data-ttu-id="408f2-104">Возвращает указатель на экземпляр [IAssemblyEnum](iassemblyenum-interface.md) , который может перечислить объекты в сборке с указанным [IAssemblyName](iassemblyname-interface.md).</span><span class="sxs-lookup"><span data-stu-id="408f2-104">Gets a pointer to an [IAssemblyEnum](iassemblyenum-interface.md) instance that can enumerate the objects in the assembly with the specified [IAssemblyName](iassemblyname-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="408f2-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="408f2-105">Syntax</span></span>  
  
```cpp  
HRESULT CreateAssemblyEnum (  
    [out] IAssemblyEnum  **pEnum,  
    [in]  IUnknown       *pUnkReserved,  
    [in]  IAssemblyName  *pName,  
    [in]  DWORD          dwFlags,  
    [in]  LPVOID         pvReserved  
 );  
```  
  
## <a name="parameters"></a><span data-ttu-id="408f2-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="408f2-106">Parameters</span></span>  

 `pEnum`  
 <span data-ttu-id="408f2-107">заполняет Указатель на место в памяти, содержащее запрошенный `IAssemblyEnum` указатель.</span><span class="sxs-lookup"><span data-stu-id="408f2-107">[out] Pointer to a memory location that contains the requested `IAssemblyEnum` pointer.</span></span>  
  
 `pUnkReserved`  
 <span data-ttu-id="408f2-108">окне Зарезервировано для будущего расширения.</span><span class="sxs-lookup"><span data-stu-id="408f2-108">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="408f2-109">`pUnkReserved` должен быть пустой ссылкой.</span><span class="sxs-lookup"><span data-stu-id="408f2-109">`pUnkReserved` must be a null reference.</span></span>  
  
 `pName`  
 <span data-ttu-id="408f2-110">окне Объект `IAssemblyName` запрошенной сборки.</span><span class="sxs-lookup"><span data-stu-id="408f2-110">[in] The `IAssemblyName` of the requested assembly.</span></span> <span data-ttu-id="408f2-111">Это имя используется для фильтрации перечисления.</span><span class="sxs-lookup"><span data-stu-id="408f2-111">This name is used to filter the enumeration.</span></span> <span data-ttu-id="408f2-112">Для перечисления всех сборок в глобальном кэше сборок может быть задано значение null.</span><span class="sxs-lookup"><span data-stu-id="408f2-112">It can be null to enumerate all assemblies in the global assembly cache.</span></span>  
  
 `dwFlags`  
 <span data-ttu-id="408f2-113">окне Флаги для изменения поведения перечислителя.</span><span class="sxs-lookup"><span data-stu-id="408f2-113">[in] Flags for modifying the enumerator's behavior.</span></span> <span data-ttu-id="408f2-114">Этот параметр содержит ровно один бит от перечисления [ASM_CACHE_FLAGS](asm-cache-flags-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="408f2-114">This parameter contains exactly one bit from the [ASM_CACHE_FLAGS](asm-cache-flags-enumeration.md) enumeration.</span></span>  
  
 `pvReserved`  
 <span data-ttu-id="408f2-115">окне Зарезервировано для будущего расширения.</span><span class="sxs-lookup"><span data-stu-id="408f2-115">[in] Reserved for future extensibility.</span></span> <span data-ttu-id="408f2-116">`pvReserved` должен быть пустой ссылкой.</span><span class="sxs-lookup"><span data-stu-id="408f2-116">`pvReserved` must be a null reference.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="408f2-117">Remarks</span><span class="sxs-lookup"><span data-stu-id="408f2-117">Remarks</span></span>  

 <span data-ttu-id="408f2-118">`dwFlags`Параметр содержит ровно один бит из `ASM_CACHE_FLAGS` перечисления.</span><span class="sxs-lookup"><span data-stu-id="408f2-118">The `dwFlags` parameter contains exactly one bit from the `ASM_CACHE_FLAGS` enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="408f2-119">Требования</span><span class="sxs-lookup"><span data-stu-id="408f2-119">Requirements</span></span>  

 <span data-ttu-id="408f2-120">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="408f2-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="408f2-121">**Заголовок:** Fusion. h</span><span class="sxs-lookup"><span data-stu-id="408f2-121">**Header:** Fusion.h</span></span>  
  
 <span data-ttu-id="408f2-122">**Библиотека:** Включается в качестве ресурса в MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="408f2-122">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="408f2-123">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="408f2-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="408f2-124">См. также</span><span class="sxs-lookup"><span data-stu-id="408f2-124">See also</span></span>

- [<span data-ttu-id="408f2-125">Интерфейс IAssemblyEnum</span><span class="sxs-lookup"><span data-stu-id="408f2-125">IAssemblyEnum Interface</span></span>](iassemblyenum-interface.md)
- [<span data-ttu-id="408f2-126">Интерфейс IAssemblyName</span><span class="sxs-lookup"><span data-stu-id="408f2-126">IAssemblyName Interface</span></span>](iassemblyname-interface.md)
- [<span data-ttu-id="408f2-127">Глобальные статические функции Fusion</span><span class="sxs-lookup"><span data-stu-id="408f2-127">Fusion Global Static Functions</span></span>](fusion-global-static-functions.md)
