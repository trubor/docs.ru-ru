---
description: 'Дополнительные сведения о методе: Икордебуглоадедмодуле:: Name'
title: Метод ICorDebugLoadedModule::GetName
ms.date: 03/30/2017
ms.assetid: 88c304d5-edaa-4c0e-a8e1-144e8a76877e
ms.openlocfilehash: 40a0715b513115177cabac01727ce9166a40d50b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801258"
---
# <a name="icordebugloadedmodulegetname-method"></a><span data-ttu-id="78ce7-103">Метод ICorDebugLoadedModule::GetName</span><span class="sxs-lookup"><span data-stu-id="78ce7-103">ICorDebugLoadedModule::GetName Method</span></span>

<span data-ttu-id="78ce7-104">Получает имя загруженного модуля.</span><span class="sxs-lookup"><span data-stu-id="78ce7-104">Gets the name of the loaded module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78ce7-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="78ce7-105">Syntax</span></span>  
  
```cpp  
HRESULT GetName(  
   [in] ULONG32 cchName,  
   [out] ULONG32 *pcchName,  
   [out, size_is(cchName),  
   length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="78ce7-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="78ce7-106">Parameters</span></span>  

 `cchName`  
 <span data-ttu-id="78ce7-107">[in] Число символов в буфере `szName`.</span><span class="sxs-lookup"><span data-stu-id="78ce7-107">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="78ce7-108">[out] Указатель на число символов, фактически записанных в буфер `szName`.</span><span class="sxs-lookup"><span data-stu-id="78ce7-108">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="78ce7-109">[out] Массив символов, содержащий имя загруженного модуля.</span><span class="sxs-lookup"><span data-stu-id="78ce7-109">[out] An array of characters that contain the name of the loaded module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="78ce7-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="78ce7-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="78ce7-111">Этот метод доступен только в машинном коде .NET.</span><span class="sxs-lookup"><span data-stu-id="78ce7-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78ce7-112">Требования</span><span class="sxs-lookup"><span data-stu-id="78ce7-112">Requirements</span></span>  

 <span data-ttu-id="78ce7-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="78ce7-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78ce7-114">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="78ce7-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="78ce7-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="78ce7-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="78ce7-116">**Платформа .NET Framework версии:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78ce7-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78ce7-117">См. также</span><span class="sxs-lookup"><span data-stu-id="78ce7-117">See also</span></span>

- [<span data-ttu-id="78ce7-118">Интерфейс ICorDebugLoadedModule</span><span class="sxs-lookup"><span data-stu-id="78ce7-118">ICorDebugLoadedModule Interface</span></span>](icordebugloadedmodule-interface.md)
- [<span data-ttu-id="78ce7-119">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="78ce7-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
