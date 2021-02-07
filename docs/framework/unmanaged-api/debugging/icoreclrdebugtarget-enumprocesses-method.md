---
description: 'Дополнительные сведения о методе: ICoreClrDebugTarget:: EnumProcesses'
title: Метод ICoreClrDebugTarget::EnumProcesses
ms.date: 03/30/2017
api_name:
- ICoreClrDebugTarget.EnumProcesses
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- ICoreClrDebugTarget::EnumProcesses
helpviewer_keywords:
- remote debugging API [Silverlight]
- EnumProcesses method, ICorClrDebugTarget interface [Silverlight debugging]
- ICorClrDebugTarget::EnumProcesses method [Silverlight debugging]
- Silverlight, remote debugging
ms.assetid: e00fd477-4f49-43d3-bd0e-3094824b1136
topic_type:
- apiref
ms.openlocfilehash: 73dc8a2b00f7a57879855158e6b871117d015f3c
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99738043"
---
# <a name="icoreclrdebugtargetenumprocesses-method"></a><span data-ttu-id="be232-103">Метод ICoreClrDebugTarget::EnumProcesses</span><span class="sxs-lookup"><span data-stu-id="be232-103">ICoreClrDebugTarget::EnumProcesses Method</span></span>

<span data-ttu-id="be232-104">Перечисляет процессы, работающие на удаленном компьютере.</span><span class="sxs-lookup"><span data-stu-id="be232-104">Enumerates the processes that are running on a remote computer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="be232-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="be232-105">Syntax</span></span>  
  
```cpp  
HRESULT EnumProcesses (  
       [out]  DWORD*                  pcProcs,
       [out]  CoreClrDebugProcInfo**  ppProcs  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="be232-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="be232-106">Parameters</span></span>  

 `pcProcs`  
 <span data-ttu-id="be232-107">[out] Число процессов, возвращаемых в `ppProcs`.</span><span class="sxs-lookup"><span data-stu-id="be232-107">[out] The number of processes returned in `ppProcs`.</span></span> <span data-ttu-id="be232-108">Это значение может быть 0 (ноль).</span><span class="sxs-lookup"><span data-stu-id="be232-108">This value can be 0 (zero).</span></span>  
  
 `ppProcs`  
 <span data-ttu-id="be232-109">заполняет Массив структур [CoreClrDebugProcInfo](coreclrdebugprocinfo-structure.md) , представляющих процессы, выполняемые на удаленном компьютере.</span><span class="sxs-lookup"><span data-stu-id="be232-109">[out] An array of [CoreClrDebugProcInfo](coreclrdebugprocinfo-structure.md) structures that represent the processes running on the remote computer.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="be232-110">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="be232-110">Return Value</span></span>  

 <span data-ttu-id="be232-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="be232-111">S_OK</span></span>  
 <span data-ttu-id="be232-112">Успешно.</span><span class="sxs-lookup"><span data-stu-id="be232-112">Success.</span></span>  
  
 <span data-ttu-id="be232-113">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="be232-113">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="be232-114">Не удается выделить достаточно памяти для `ppProcs`.</span><span class="sxs-lookup"><span data-stu-id="be232-114">Unable to allocate enough memory for `ppProcs`.</span></span>  
  
 <span data-ttu-id="be232-115">E_FAIL (или другие коды возврата E_)</span><span class="sxs-lookup"><span data-stu-id="be232-115">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="be232-116">Прочие сбои.</span><span class="sxs-lookup"><span data-stu-id="be232-116">Other failures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="be232-117">Remarks</span><span class="sxs-lookup"><span data-stu-id="be232-117">Remarks</span></span>  

 <span data-ttu-id="be232-118">Чтобы освободить память, выделенную этим методом, вызовите метод [ICoreClrDebugTarget:: FreeMemory](icoreclrdebugtarget-freememory-method.md) .</span><span class="sxs-lookup"><span data-stu-id="be232-118">To free the memory that was allocated by this method, call the [ICoreClrDebugTarget::FreeMemory](icoreclrdebugtarget-freememory-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be232-119">Требования</span><span class="sxs-lookup"><span data-stu-id="be232-119">Requirements</span></span>  

 <span data-ttu-id="be232-120">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="be232-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be232-121">**Заголовок:** Кореклрремотедебуггингинтерфацес. h</span><span class="sxs-lookup"><span data-stu-id="be232-121">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="be232-122">**Библиотека:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="be232-122">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="be232-123">**Платформа .NET Framework версии:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="be232-123">**.NET Framework Versions:** 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be232-124">См. также</span><span class="sxs-lookup"><span data-stu-id="be232-124">See also</span></span>

- [<span data-ttu-id="be232-125">Интерфейс ICoreClrDebugTarget</span><span class="sxs-lookup"><span data-stu-id="be232-125">ICoreClrDebugTarget Interface</span></span>](icoreclrdebugtarget-interface.md)
