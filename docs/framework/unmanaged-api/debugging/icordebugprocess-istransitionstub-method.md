---
description: 'Дополнительные сведения о методе: ICorDebugProcess:: IsTransitionStub'
title: Метод ICorDebugProcess::IsTransitionStub
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.IsTransitionStub
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::IsTransitionStub
helpviewer_keywords:
- ICorDebugProcess::IsTransitionStub method [.NET Framework debugging]
- IsTransitionStub method [.NET Framework debugging]
ms.assetid: f7653317-7e48-4163-be03-f50f1a4b0f70
topic_type:
- apiref
ms.openlocfilehash: 0da8527538c2573b1ec0d26f8711644fe8fcca2a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99782004"
---
# <a name="icordebugprocessistransitionstub-method"></a><span data-ttu-id="419f9-103">Метод ICorDebugProcess::IsTransitionStub</span><span class="sxs-lookup"><span data-stu-id="419f9-103">ICorDebugProcess::IsTransitionStub Method</span></span>

<span data-ttu-id="419f9-104">Возвращает значение, указывающее, находится ли адрес в заглушке, что приведет к переходу в управляемый код.</span><span class="sxs-lookup"><span data-stu-id="419f9-104">Gets a value that indicates whether an address is inside a stub that will cause a transition to managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="419f9-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="419f9-105">Syntax</span></span>  
  
```cpp  
HRESULT IsTransitionStub(  
    [in]  CORDB_ADDRESS address,  
    [out] BOOL *pbTransitionStub);  
```  
  
## <a name="parameters"></a><span data-ttu-id="419f9-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="419f9-106">Parameters</span></span>  

 `address`  
 <span data-ttu-id="419f9-107">окне `CORDB_ADDRESS` Значение, указывающее рассматриваемый адрес.</span><span class="sxs-lookup"><span data-stu-id="419f9-107">[in] A `CORDB_ADDRESS` value that specifies the address in question.</span></span>  
  
 `pbTransitionStub`  
 <span data-ttu-id="419f9-108">заполняет Указатель на логическое значение, равное, `true` если указанный адрес находится внутри заглушки, которая приведет к переходу в управляемый код; в противном случае `pbTransitionStub` — \* `false` .</span><span class="sxs-lookup"><span data-stu-id="419f9-108">[out] A pointer to a Boolean value that is `true` if the specified address is inside a stub that will cause a transition to managed code; otherwise \*`pbTransitionStub` is `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="419f9-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="419f9-109">Remarks</span></span>  

 <span data-ttu-id="419f9-110">`IsTransitionStub`Метод может использоваться неуправляемым кодом пошагового выполнения, чтобы решить, когда следует возвращать контроль пошагового выполнения в управляемое средство Организации.</span><span class="sxs-lookup"><span data-stu-id="419f9-110">The `IsTransitionStub` method can be used by unmanaged stepping code to decide when to return stepping control to the managed stepper.</span></span>  
  
 <span data-ttu-id="419f9-111">Вы также можете идентифицировать заглушки перехода, просмотрев информацию в переносимом исполняемом файле (PE).</span><span class="sxs-lookup"><span data-stu-id="419f9-111">You can also identity transition stubs by looking at information in the portable executable (PE) file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="419f9-112">Требования</span><span class="sxs-lookup"><span data-stu-id="419f9-112">Requirements</span></span>  

 <span data-ttu-id="419f9-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="419f9-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="419f9-114">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="419f9-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="419f9-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="419f9-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="419f9-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="419f9-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
