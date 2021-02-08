---
description: 'Дополнительные сведения о методе: ICorDebugMDA:: GetXML'
title: Метод ICorDebugMDA::GetXML
ms.date: 03/30/2017
api_name:
- ICorDebugMDA.GetXML
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA::GetXML
helpviewer_keywords:
- ICorDebugMDA::GetXML method [.NET Framework debugging]
- GetXML method [.NET Framework debugging]
ms.assetid: 29746b24-3766-4255-8813-0426c45e73e5
topic_type:
- apiref
ms.openlocfilehash: fa506e6e8f306271f10a7a715af9b8bc6a80c1d6
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801141"
---
# <a name="icordebugmdagetxml-method"></a><span data-ttu-id="ee902-103">Метод ICorDebugMDA::GetXML</span><span class="sxs-lookup"><span data-stu-id="ee902-103">ICorDebugMDA::GetXML Method</span></span>

<span data-ttu-id="ee902-104">Возвращает полный XML-поток, связанный с помощником по отладке управляемого кода (MDA), представленным [ICorDebugMDA](icordebugmda-interface.md).</span><span class="sxs-lookup"><span data-stu-id="ee902-104">Gets the full XML stream associated with the managed debugging assistant (MDA) represented by [ICorDebugMDA](icordebugmda-interface.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ee902-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ee902-105">Syntax</span></span>  
  
```cpp  
HRESULT GetXML (  
    [in] ULONG32   cchName,  
    [out] ULONG32  *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)]  
        WCHAR      szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ee902-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="ee902-106">Parameters</span></span>  

 `cchName`  
 <span data-ttu-id="ee902-107">[in] Размер массива `szName`.</span><span class="sxs-lookup"><span data-stu-id="ee902-107">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="ee902-108">заполняет Указатель на длину XML-потока.</span><span class="sxs-lookup"><span data-stu-id="ee902-108">[out] A pointer to the length of the XML stream.</span></span>  
  
 `szName`  
 <span data-ttu-id="ee902-109">заполняет Массив, в котором хранится XML-поток.</span><span class="sxs-lookup"><span data-stu-id="ee902-109">[out] An array in which to store the XML stream.</span></span> <span data-ttu-id="ee902-110">Массив может быть пустым.</span><span class="sxs-lookup"><span data-stu-id="ee902-110">The array may be empty.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ee902-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="ee902-111">Remarks</span></span>  

 <span data-ttu-id="ee902-112">`GetXML`Метод может повлиять на производительность в зависимости от размера соответствующего потока XML.</span><span class="sxs-lookup"><span data-stu-id="ee902-112">The `GetXML` method can potentially affect performance, depending on the size of the associated XML stream.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ee902-113">Требования</span><span class="sxs-lookup"><span data-stu-id="ee902-113">Requirements</span></span>  

 <span data-ttu-id="ee902-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ee902-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee902-115">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ee902-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ee902-116">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ee902-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ee902-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ee902-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee902-118">См. также</span><span class="sxs-lookup"><span data-stu-id="ee902-118">See also</span></span>

- [<span data-ttu-id="ee902-119">Интерфейс ICorDebugMDA</span><span class="sxs-lookup"><span data-stu-id="ee902-119">ICorDebugMDA Interface</span></span>](icordebugmda-interface.md)
- [<span data-ttu-id="ee902-120">Диагностика ошибок посредством управляемых помощников по отладке</span><span class="sxs-lookup"><span data-stu-id="ee902-120">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
