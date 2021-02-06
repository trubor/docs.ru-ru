---
description: 'Дополнительные сведения о методе ICorProfilerInfo:: GetILFunctionBody'
title: Метод ICorProfilerInfo::GetILFunctionBody
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetILFunctionBody
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetILFunctionBody
helpviewer_keywords:
- GetILFunctionBody method [.NET Framework profiling]
- ICorProfilerInfo::GetILFunctionBody method [.NET Framework profiling]
ms.assetid: e29b46bc-5fdc-4894-b0c2-619df4b65ded
topic_type:
- apiref
ms.openlocfilehash: 7294592d1a2747dc10f44d1206561a9a1662ce7b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99647483"
---
# <a name="icorprofilerinfogetilfunctionbody-method"></a><span data-ttu-id="8461a-103">Метод ICorProfilerInfo::GetILFunctionBody</span><span class="sxs-lookup"><span data-stu-id="8461a-103">ICorProfilerInfo::GetILFunctionBody Method</span></span>

<span data-ttu-id="8461a-104">Возвращает указатель на тело метода в коде на языке MSIL, начиная с его заголовка.</span><span class="sxs-lookup"><span data-stu-id="8461a-104">Gets a pointer to the body of a method in Microsoft intermediate language (MSIL) code, starting at its header.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8461a-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="8461a-105">Syntax</span></span>  
  
```cpp  
HRESULT GetILFunctionBody(  
    [in]  ModuleID    moduleId,  
    [in]  mdMethodDef methodId,  
    [out] LPCBYTE     *ppMethodHeader,  
    [out] ULONG       *pcbMethodSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8461a-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="8461a-106">Parameters</span></span>  

 `moduleId`  
 <span data-ttu-id="8461a-107">окне Идентификатор модуля, в котором находится функция.</span><span class="sxs-lookup"><span data-stu-id="8461a-107">[in] The ID of the module in which the function resides.</span></span>  
  
 `methodId`  
 <span data-ttu-id="8461a-108">окне Токен метаданных для метода.</span><span class="sxs-lookup"><span data-stu-id="8461a-108">[in] The metadata token for the method.</span></span>  
  
 `ppMethodHeader`  
 <span data-ttu-id="8461a-109">заполняет Указатель на заголовок метода.</span><span class="sxs-lookup"><span data-stu-id="8461a-109">[out] A pointer to the method's header.</span></span>  
  
 `pcbMethodSize`  
 <span data-ttu-id="8461a-110">заполняет Целое число, указывающее размер метода.</span><span class="sxs-lookup"><span data-stu-id="8461a-110">[out] An integer that specifies the size of the method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8461a-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="8461a-111">Remarks</span></span>  

 <span data-ttu-id="8461a-112">Метод ограничивается модулем, в котором он находится.</span><span class="sxs-lookup"><span data-stu-id="8461a-112">A method is scoped by the module in which it lives.</span></span> <span data-ttu-id="8461a-113">Поскольку `GetILFunctionBody` метод предназначен для предоставления средству доступа к коду MSIL до того, как он будет загружен средой CLR, он использует маркер метаданных метода для поиска нужного экземпляра.</span><span class="sxs-lookup"><span data-stu-id="8461a-113">Because the `GetILFunctionBody` method is designed to give a tool access to the MSIL code before it has been loaded by the common language runtime (CLR), it uses the metadata token of the method to find the desired instance.</span></span>  
  
 <span data-ttu-id="8461a-114">`GetILFunctionBody` может возвращать CORPROF_E_FUNCTION_NOT_IL HRESULT, если `methodId` указывает на метод без какого-либо кода MSIL (например, абстрактный метод или метод вызова платформы).</span><span class="sxs-lookup"><span data-stu-id="8461a-114">`GetILFunctionBody` can return a CORPROF_E_FUNCTION_NOT_IL HRESULT if the `methodId` points to a method without any MSIL code (such as an abstract method, or a platform invoke (PInvoke) method).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8461a-115">Требования</span><span class="sxs-lookup"><span data-stu-id="8461a-115">Requirements</span></span>  

 <span data-ttu-id="8461a-116">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8461a-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8461a-117">**Заголовок:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8461a-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8461a-118">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8461a-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8461a-119">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8461a-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8461a-120">См. также</span><span class="sxs-lookup"><span data-stu-id="8461a-120">See also</span></span>

- [<span data-ttu-id="8461a-121">Интерфейс ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="8461a-121">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
