---
description: 'Дополнительные сведения о методе: ICorDebugModule:: Name'
title: Метод ICorDebugModule::GetName
ms.date: 03/30/2017
api_name:
- ICorDebugModule.GetName
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule::GetName
helpviewer_keywords:
- ICorDebugModule::GetName method [.NET Framework debugging]
- GetName method, ICorDebugModule interface [.NET Framework debugging]
ms.assetid: db499637-7ba9-421e-b8b1-35856995e80b
topic_type:
- apiref
ms.openlocfilehash: 0f81271b2be283621027f4c835b6f220a383d771
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99660204"
---
# <a name="icordebugmodulegetname-method"></a><span data-ttu-id="112f0-103">Метод ICorDebugModule::GetName</span><span class="sxs-lookup"><span data-stu-id="112f0-103">ICorDebugModule::GetName Method</span></span>

<span data-ttu-id="112f0-104">Возвращает имя файла модуля.</span><span class="sxs-lookup"><span data-stu-id="112f0-104">Gets the file name of the module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="112f0-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="112f0-105">Syntax</span></span>  
  
```cpp
HRESULT GetName(  
    [in] ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="112f0-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="112f0-106">Parameters</span></span>  

 `cchname`  
 <span data-ttu-id="112f0-107">[in] Размер массива `szName`.</span><span class="sxs-lookup"><span data-stu-id="112f0-107">[in] The size of the `szName` array.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="112f0-108">окне Указатель на длину возвращаемого имени.</span><span class="sxs-lookup"><span data-stu-id="112f0-108">[in] A pointer to the length of the returned name.</span></span>  
  
 `szName`  
 <span data-ttu-id="112f0-109">заполняет Массив, в котором хранится возвращаемое имя.</span><span class="sxs-lookup"><span data-stu-id="112f0-109">[out] An array that stores the returned name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="112f0-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="112f0-110">Remarks</span></span>  

 <span data-ttu-id="112f0-111">`GetName`Метод возвращает S_OK HRESULT, если имя файла модуля совпадает с именем на диске.</span><span class="sxs-lookup"><span data-stu-id="112f0-111">The `GetName` method returns an S_OK HRESULT if the module's file name matches the name on disk.</span></span> <span data-ttu-id="112f0-112">`GetName` Возвращает S_FALSE HRESULT, если имя является составным, например, для динамического или в памяти модуля.</span><span class="sxs-lookup"><span data-stu-id="112f0-112">`GetName` returns an S_FALSE HRESULT if the name is fabricated, such as for a dynamic or in-memory module.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="112f0-113">Требования</span><span class="sxs-lookup"><span data-stu-id="112f0-113">Requirements</span></span>  

 <span data-ttu-id="112f0-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="112f0-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="112f0-115">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="112f0-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="112f0-116">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="112f0-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="112f0-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="112f0-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="112f0-118">См. также</span><span class="sxs-lookup"><span data-stu-id="112f0-118">See also</span></span>
