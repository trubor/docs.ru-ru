---
description: 'Дополнительные сведения о методе: ICorDebugMDA:: Description'
title: Метод ICorDebugMDA::GetDescription
ms.date: 03/30/2017
api_name:
- ICorDebugMDA.GetDescription
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA::GetDescription
helpviewer_keywords:
- GetDescription method [.NET Framework debugging]
- ICorDebugMDA::GetDescription method [.NET Framework debugging]
ms.assetid: 01d1b481-ca67-4712-8744-d342ec0df639
topic_type:
- apiref
ms.openlocfilehash: 75ee7d0b912c9f0039acc872173f2cbad25fff38
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801206"
---
# <a name="icordebugmdagetdescription-method"></a><span data-ttu-id="554b6-103">Метод ICorDebugMDA::GetDescription</span><span class="sxs-lookup"><span data-stu-id="554b6-103">ICorDebugMDA::GetDescription Method</span></span>

<span data-ttu-id="554b6-104">Возвращает строку, содержащую описание помощника по отладке управляемого кода (MDA), представленного [ICorDebugMDA](icordebugmda-interface.md).</span><span class="sxs-lookup"><span data-stu-id="554b6-104">Gets a string containing the description of the managed debugging assistant (MDA) represented by [ICorDebugMDA](icordebugmda-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="554b6-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="554b6-105">Syntax</span></span>  
  
```cpp  
HRESULT GetDescription (  
    [in] ULONG32   cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
        WCHAR      szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="554b6-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="554b6-106">Parameters</span></span>  

 `cchName`  
 <span data-ttu-id="554b6-107">окне Размер строкового буфера, в котором будет храниться описание.</span><span class="sxs-lookup"><span data-stu-id="554b6-107">[in] The size of the string buffer that will store the description.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="554b6-108">заполняет Указатель на число байтов, возвращенных в буфере строк.</span><span class="sxs-lookup"><span data-stu-id="554b6-108">[out] A pointer to the number of bytes returned in the string buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="554b6-109">заполняет Строковый буфер, содержащий описание MDA.</span><span class="sxs-lookup"><span data-stu-id="554b6-109">[out] A string buffer containing the description of the MDA.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="554b6-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="554b6-110">Remarks</span></span>  

 <span data-ttu-id="554b6-111">Строка может иметь нулевую длину.</span><span class="sxs-lookup"><span data-stu-id="554b6-111">The string can be zero in length.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="554b6-112">Требования</span><span class="sxs-lookup"><span data-stu-id="554b6-112">Requirements</span></span>  

 <span data-ttu-id="554b6-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="554b6-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="554b6-114">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="554b6-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="554b6-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="554b6-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="554b6-116">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="554b6-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="554b6-117">См. также</span><span class="sxs-lookup"><span data-stu-id="554b6-117">See also</span></span>

- [<span data-ttu-id="554b6-118">Интерфейс ICorDebugMDA</span><span class="sxs-lookup"><span data-stu-id="554b6-118">ICorDebugMDA Interface</span></span>](icordebugmda-interface.md)
- [<span data-ttu-id="554b6-119">Диагностика ошибок посредством управляемых помощников по отладке</span><span class="sxs-lookup"><span data-stu-id="554b6-119">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
