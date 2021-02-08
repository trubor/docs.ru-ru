---
description: 'Дополнительные сведения о: ICorDebug::D Ебугактивепроцесс Method'
title: Метод ICorDebug::DebugActiveProcess
ms.date: 03/30/2017
api_name:
- ICorDebug.DebugActiveProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebug::DebugActiveProcess
helpviewer_keywords:
- DebugActiveProcess method [.NET Framework debugging]
- ICorDebug::DebugActiveProcess method [.NET Framework debugging]
ms.assetid: fdab0ade-7f56-4fa2-b3ef-f7a1d2852bba
topic_type:
- apiref
ms.openlocfilehash: 9c3a212adf962f96fd2c7345fe8b580b6af3b544
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801323"
---
# <a name="icordebugdebugactiveprocess-method"></a><span data-ttu-id="a318d-103">Метод ICorDebug::DebugActiveProcess</span><span class="sxs-lookup"><span data-stu-id="a318d-103">ICorDebug::DebugActiveProcess Method</span></span>

<span data-ttu-id="a318d-104">Присоединяет отладчик к существующему процессу.</span><span class="sxs-lookup"><span data-stu-id="a318d-104">Attaches the debugger to an existing process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a318d-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a318d-105">Syntax</span></span>  
  
```cpp  
HRESULT DebugActiveProcess (  
    [in]  DWORD               id,  
    [in]  BOOL                win32Attach,  
    [out] ICorDebugProcess    **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a318d-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="a318d-106">Parameters</span></span>  

 `id`  
 <span data-ttu-id="a318d-107">окне Идентификатор процесса, к которому должен быть присоединен отладчик.</span><span class="sxs-lookup"><span data-stu-id="a318d-107">[in] The ID of the process to which the debugger is to be attached.</span></span>  
  
 `win32Attach`  
 <span data-ttu-id="a318d-108">окне Логическое значение, которое устанавливается в, `true` Если отладчик должен вести себя в качестве отладчика Win32 для процесса и отправляют неуправляемые обратные вызовы. в противном случае — `false` .</span><span class="sxs-lookup"><span data-stu-id="a318d-108">[in] Boolean value that is set to `true` if the debugger should behave as the Win32 debugger for the process and dispatch the unmanaged callbacks; otherwise, `false`.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="a318d-109">заполняет Указатель на адрес объекта "ICorDebugProcess", который представляет процесс, к которому присоединен отладчик.</span><span class="sxs-lookup"><span data-stu-id="a318d-109">[out] A pointer to the address of an "ICorDebugProcess" object that represents the process to which the debugger has been attached.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a318d-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="a318d-110">Remarks</span></span>  

 <span data-ttu-id="a318d-111">Отладка взаимодействия не поддерживается на платформах Win9x и на платформе, отличной от x86, например на платформах на основе IA-64 и AMD64.</span><span class="sxs-lookup"><span data-stu-id="a318d-111">Interop debugging is not supported on Win9x and non-x86 platforms, such as IA-64-based and AMD64-based platforms.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a318d-112">Требования</span><span class="sxs-lookup"><span data-stu-id="a318d-112">Requirements</span></span>  

 <span data-ttu-id="a318d-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a318d-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a318d-114">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a318d-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a318d-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a318d-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a318d-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a318d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a318d-117">См. также</span><span class="sxs-lookup"><span data-stu-id="a318d-117">See also</span></span>

- [<span data-ttu-id="a318d-118">Интерфейс ICorDebug</span><span class="sxs-lookup"><span data-stu-id="a318d-118">ICorDebug Interface</span></span>](icordebug-interface.md)
