---
description: 'Дополнительные сведения о методе: ICoreClrDebugTarget:: EnumRuntimes'
title: Метод ICoreClrDebugTarget::EnumRuntimes
ms.date: 03/30/2017
api_name:
- ICoreClrDebugTarget.EnumRuntimes
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- ICoreClrDebugTarget::EnumRuntimes
helpviewer_keywords:
- remote debugging API [Silverlight]
- ICorClrDebugTarget::EnumRuntimes method [Silverlight debugging]
- EnumRuntimes method, ICoreClrDebugTarget interface [Silverlight debugging]
- Silverlight, remote debugging
ms.assetid: 316df866-442d-40cc-b049-45e8adcb65d1
topic_type:
- apiref
ms.openlocfilehash: 675747106b2acec2e8be3fcdf15831958bea7c7c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99794628"
---
# <a name="icoreclrdebugtargetenumruntimes-method"></a><span data-ttu-id="b4db0-103">Метод ICoreClrDebugTarget::EnumRuntimes</span><span class="sxs-lookup"><span data-stu-id="b4db0-103">ICoreClrDebugTarget::EnumRuntimes Method</span></span>

<span data-ttu-id="b4db0-104">Перечисляет среды CLR в указанном процессе, который выполняется на удаленном компьютере.</span><span class="sxs-lookup"><span data-stu-id="b4db0-104">Enumerates the common language runtimes (CLRs) in the specified process that is running on a remote computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4db0-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="b4db0-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumRuntimes (  
      [in] DWORD       dwInternalProcessID,  
      [out] DWORD*     pcRuntimes,  
      [out] CoreClrDebugRuntimeInfo**    ppRuntimes  
    );  
```  
  
## <a name="parameters"></a><span data-ttu-id="b4db0-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="b4db0-106">Parameters</span></span>  

 `dwInternalProcessID`  
 <span data-ttu-id="b4db0-107">[in] Внутренний идентификатор процесса, для которого требуется перечислить среды выполнения.</span><span class="sxs-lookup"><span data-stu-id="b4db0-107">[in] The internal process ID of the process for which you want to enumerate runtimes.</span></span> <span data-ttu-id="b4db0-108">Это будет `m_dwInternalID` из соответствующего [CoreClrDebugProcInfo](coreclrdebugprocinfo-structure.md).</span><span class="sxs-lookup"><span data-stu-id="b4db0-108">This will be `m_dwInternalID` from the corresponding [CoreClrDebugProcInfo](coreclrdebugprocinfo-structure.md).</span></span>  
  
 `pcRuntimes`  
 <span data-ttu-id="b4db0-109">[out] Число сред выполнения, возвращаемых в `ppRuntimes`.</span><span class="sxs-lookup"><span data-stu-id="b4db0-109">[out] The number of runtimes returned in `ppRuntimes`.</span></span> <span data-ttu-id="b4db0-110">Это значение может быть 0 (ноль).</span><span class="sxs-lookup"><span data-stu-id="b4db0-110">This value can be 0 (zero).</span></span>  
  
 `ppRuntimes`  
 <span data-ttu-id="b4db0-111">заполняет Массив структур [кореклрдебугрунтимеинфо](coreclrdebugruntimeinfo-structure.md) , представляющих среды выполнения, загруженные в удаленном целевом процессе.</span><span class="sxs-lookup"><span data-stu-id="b4db0-111">[out] An array of [CoreClrDebugRuntimeInfo](coreclrdebugruntimeinfo-structure.md) structures that represent the runtimes loaded in the remote target process.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b4db0-112">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="b4db0-112">Return Value</span></span>  

 <span data-ttu-id="b4db0-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="b4db0-113">S_OK</span></span>  
 <span data-ttu-id="b4db0-114">Успешно.</span><span class="sxs-lookup"><span data-stu-id="b4db0-114">Success.</span></span>  
  
 <span data-ttu-id="b4db0-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="b4db0-115">S_FALSE</span></span>  
 <span data-ttu-id="b4db0-116">`dwInternalProcessID` не соответствует ни одному процессу, который выполняется на компьютере, возможно потому, что этот процесс был завершен.</span><span class="sxs-lookup"><span data-stu-id="b4db0-116">`dwInternalProcessID` does not match any process that is running on the computer, probably because the process was terminated.</span></span> <span data-ttu-id="b4db0-117">`pcRuntimes` и `ppRuntimes` будут иметь значение null.</span><span class="sxs-lookup"><span data-stu-id="b4db0-117">`pcRuntimes` and `ppRuntimes` will be null.</span></span>  
  
 <span data-ttu-id="b4db0-118">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="b4db0-118">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="b4db0-119">Не удается выделить достаточно памяти для `ppRuntimes`.</span><span class="sxs-lookup"><span data-stu-id="b4db0-119">Unable to allocate enough memory for `ppRuntimes`.</span></span>  
  
 <span data-ttu-id="b4db0-120">E_FAIL (или другие коды возврата E_)</span><span class="sxs-lookup"><span data-stu-id="b4db0-120">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="b4db0-121">Прочие сбои.</span><span class="sxs-lookup"><span data-stu-id="b4db0-121">Other failures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b4db0-122">Remarks</span><span class="sxs-lookup"><span data-stu-id="b4db0-122">Remarks</span></span>  

 <span data-ttu-id="b4db0-123">Чтобы освободить память, выделенную этим методом, вызовите метод [ICoreClrDebugTarget:: FreeMemory](icoreclrdebugtarget-freememory-method.md) .</span><span class="sxs-lookup"><span data-stu-id="b4db0-123">To free the memory that was allocated by this method, call the [ICoreClrDebugTarget::FreeMemory](icoreclrdebugtarget-freememory-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4db0-124">Требования</span><span class="sxs-lookup"><span data-stu-id="b4db0-124">Requirements</span></span>  

 <span data-ttu-id="b4db0-125">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b4db0-125">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4db0-126">**Заголовок:** Кореклрремотедебуггингинтерфацес. h</span><span class="sxs-lookup"><span data-stu-id="b4db0-126">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="b4db0-127">**Библиотека:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="b4db0-127">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="b4db0-128">**Платформа .NET Framework версии:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="b4db0-128">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4db0-129">См. также</span><span class="sxs-lookup"><span data-stu-id="b4db0-129">See also</span></span>

- [<span data-ttu-id="b4db0-130">Интерфейс ICoreClrDebugTarget</span><span class="sxs-lookup"><span data-stu-id="b4db0-130">ICoreClrDebugTarget Interface</span></span>](icoreclrdebugtarget-interface.md)
