---
description: Дополнительные сведения о функции Креатекордбобжект
title: Функция CreateCordbObject
ms.date: 03/30/2017
api_name:
- CreateCoredbObject
api_location:
- mscordbi_macx86.dll
api_type:
- COM
f1_keywords:
- CreateCordbObject
helpviewer_keywords:
- remote debugging API [Silverlight]
- CreateCordbObject function
- Silverlight, remote debugging
ms.assetid: b259821d-4fa7-464d-85cf-304dfffc8089
topic_type:
- apiref
ms.openlocfilehash: b6a585fc89f780b22f842127e1923414dbb8230f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801479"
---
# <a name="createcordbobject-function"></a><span data-ttu-id="777ae-103">Функция CreateCordbObject</span><span class="sxs-lookup"><span data-stu-id="777ae-103">CreateCordbObject Function</span></span>

<span data-ttu-id="777ae-104">Создает интерфейс отладчика ([ICorDebug](icordebug-interface.md)), который предоставляет функциональные возможности для создания экземпляра управляемого сеанса отладки на удаленном процессе.</span><span class="sxs-lookup"><span data-stu-id="777ae-104">Creates a debugger interface ([ICorDebug](icordebug-interface.md)) that provides functionality for instantiating a managed debugging session on a remote process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="777ae-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="777ae-105">Syntax</span></span>  
  
```cpp  
HRESULT CordbCreateObject (  
       [in]  int         iDebuggerVersion,
       [out] IUnknown**  ppCordb  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="777ae-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="777ae-106">Parameters</span></span>  

 `iDebuggerVersion`  
 <span data-ttu-id="777ae-107">[in] Версия отладчика целевого процесса.</span><span class="sxs-lookup"><span data-stu-id="777ae-107">[in] Debugger version of the target process.</span></span> <span data-ttu-id="777ae-108">Для удаленной отладки этот параметр должен иметь значение CorDebugVersion_2_0.</span><span class="sxs-lookup"><span data-stu-id="777ae-108">This parameter must be CorDebugVersion_2_0 for remote debugging.</span></span>  
  
 `ppCordb`  
 <span data-ttu-id="777ae-109">заполняет Указатель на указатель на объект, который будет приведен к интерфейсу [ICorDebug](icordebug-interface.md) и возвращен.</span><span class="sxs-lookup"><span data-stu-id="777ae-109">[out] Pointer to a pointer to an object that will be cast to an [ICorDebug](icordebug-interface.md) interface and returned.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="777ae-110">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="777ae-110">Return Value</span></span>  

 <span data-ttu-id="777ae-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="777ae-111">S_OK</span></span>  
 <span data-ttu-id="777ae-112">Количество сред CLR в процессе успешно определено, и соответствующие массивы дескрипторов и путей заполнены должным образом.</span><span class="sxs-lookup"><span data-stu-id="777ae-112">The number of CLRs in the process was successfully determined, and the corresponding handle and path arrays were properly filled.</span></span>  
  
 <span data-ttu-id="777ae-113">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="777ae-113">E_INVALIDARG</span></span>  
 <span data-ttu-id="777ae-114">Параметр `ppCordb` имеет значение null, или параметр `iDebuggerVersion` не имеет значение CorDebugVersion_2_0.</span><span class="sxs-lookup"><span data-stu-id="777ae-114">`ppCordb` is null, or `iDebuggerVersion` is not CorDebugVersion_2_0.</span></span>  
  
 <span data-ttu-id="777ae-115">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="777ae-115">E_OUTOFMEMORY</span></span>  
 <span data-ttu-id="777ae-116">Не удается выделить достаточно памяти для `ppCordb`.</span><span class="sxs-lookup"><span data-stu-id="777ae-116">Unable to allocate enough memory for `ppCordb`</span></span>  
  
 <span data-ttu-id="777ae-117">E_FAIL (или другие коды возврата E_)</span><span class="sxs-lookup"><span data-stu-id="777ae-117">E_FAIL (or other E_ return codes)</span></span>  
 <span data-ttu-id="777ae-118">Прочие сбои.</span><span class="sxs-lookup"><span data-stu-id="777ae-118">Other failures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="777ae-119">Remarks</span><span class="sxs-lookup"><span data-stu-id="777ae-119">Remarks</span></span>  

 <span data-ttu-id="777ae-120">Интерфейс [ICorDebug](icordebug-interface.md) , возвращаемый в, `ppCordb` является интерфейсом отладки верхнего уровня для всех управляемых служб отладки.</span><span class="sxs-lookup"><span data-stu-id="777ae-120">The [ICorDebug](icordebug-interface.md) interface that is returned in `ppCordb` is the top-level debugging interface for all managed debugging services.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="777ae-121">Требования</span><span class="sxs-lookup"><span data-stu-id="777ae-121">Requirements</span></span>  

 <span data-ttu-id="777ae-122">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="777ae-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="777ae-123">**Заголовок:** Кореклрремотедебуггингинтерфацес. h</span><span class="sxs-lookup"><span data-stu-id="777ae-123">**Header:** CoreClrRemoteDebuggingInterfaces.h</span></span>  
  
 <span data-ttu-id="777ae-124">**Библиотека:** mscordbi_macx86.dll</span><span class="sxs-lookup"><span data-stu-id="777ae-124">**Library:** mscordbi_macx86.dll</span></span>  
  
 <span data-ttu-id="777ae-125">**Платформа .NET Framework версии:** 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="777ae-125">**.NET Framework Versions:** 3.5 SP1</span></span>
