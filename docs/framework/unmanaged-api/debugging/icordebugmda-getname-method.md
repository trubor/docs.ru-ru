---
description: 'Дополнительные сведения о методе: ICorDebugMDA:: Name'
title: Метод ICorDebugMDA::GetName
ms.date: 03/30/2017
api_name:
- ICorDebugMDA.GetName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA::GetName
helpviewer_keywords:
- ICorDebugMDA::GetName method [.NET Framework debugging]
- GetName method, ICorDebugMDA interface [.NET Framework debugging]
ms.assetid: 885bf5e8-00b7-4cd7-9d8d-e720d47918c4
topic_type:
- apiref
ms.openlocfilehash: 4ea39f062071073684a20d8f60875fbaaab43a2f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801172"
---
# <a name="icordebugmdagetname-method"></a><span data-ttu-id="1aeb5-103">Метод ICorDebugMDA::GetName</span><span class="sxs-lookup"><span data-stu-id="1aeb5-103">ICorDebugMDA::GetName Method</span></span>

<span data-ttu-id="1aeb5-104">Возвращает строку, содержащую имя помощника по отладке управляемого кода (MDA), представленного [ICorDebugMDA](icordebugmda-interface.md).</span><span class="sxs-lookup"><span data-stu-id="1aeb5-104">Gets a string containing the name of the managed debugging assistant (MDA) represented by [ICorDebugMDA](icordebugmda-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1aeb5-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="1aeb5-105">Syntax</span></span>  
  
```cpp  
HRESULT GetName (  
    [in] ULONG32   cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
        WCHAR      szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1aeb5-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="1aeb5-106">Parameters</span></span>  

 `cchName`  
 <span data-ttu-id="1aeb5-107">[in] Размер массива `szName`.</span><span class="sxs-lookup"><span data-stu-id="1aeb5-107">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="1aeb5-108">заполняет Указатель на длину имени.</span><span class="sxs-lookup"><span data-stu-id="1aeb5-108">[out] A pointer to the length of the name.</span></span>  
  
 `szName`  
 <span data-ttu-id="1aeb5-109">заполняет Массив, в котором сохраняется имя.</span><span class="sxs-lookup"><span data-stu-id="1aeb5-109">[out] An array in which to store the name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1aeb5-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="1aeb5-110">Remarks</span></span>  

 <span data-ttu-id="1aeb5-111">Имена MDA являются уникальными значениями.</span><span class="sxs-lookup"><span data-stu-id="1aeb5-111">MDA names are unique values.</span></span> <span data-ttu-id="1aeb5-112">Этот `GetName` метод является удобной альтернативой производительности для получения XML-потока и извлечения имени из потока на основе схемы.</span><span class="sxs-lookup"><span data-stu-id="1aeb5-112">The `GetName` method is a convenient performance alternative to getting the XML stream and extracting the name from the stream based on the schema.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1aeb5-113">Требования</span><span class="sxs-lookup"><span data-stu-id="1aeb5-113">Requirements</span></span>  

 <span data-ttu-id="1aeb5-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1aeb5-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1aeb5-115">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1aeb5-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1aeb5-116">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1aeb5-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1aeb5-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1aeb5-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1aeb5-118">См. также</span><span class="sxs-lookup"><span data-stu-id="1aeb5-118">See also</span></span>

- [<span data-ttu-id="1aeb5-119">Интерфейс ICorDebugMDA</span><span class="sxs-lookup"><span data-stu-id="1aeb5-119">ICorDebugMDA Interface</span></span>](icordebugmda-interface.md)
- [<span data-ttu-id="1aeb5-120">Диагностика ошибок посредством управляемых помощников по отладке</span><span class="sxs-lookup"><span data-stu-id="1aeb5-120">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
