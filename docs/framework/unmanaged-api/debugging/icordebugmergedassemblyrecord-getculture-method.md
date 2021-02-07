---
description: 'Дополнительные сведения о методе: Икордебугмержедассемблирекорд:: DataCulture'
title: Метод ICorDebugMergedAssemblyRecord::GetCulture
ms.date: 03/30/2017
ms.assetid: 030b2f8c-8c21-40b7-855d-3afa78975a17
ms.openlocfilehash: f530bb68a1e7e4c4bff53b8f3046f6ae9ca42aab
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754008"
---
# <a name="icordebugmergedassemblyrecordgetculture-method"></a><span data-ttu-id="54478-103">Метод ICorDebugMergedAssemblyRecord::GetCulture</span><span class="sxs-lookup"><span data-stu-id="54478-103">ICorDebugMergedAssemblyRecord::GetCulture Method</span></span>

<span data-ttu-id="54478-104">Возвращает строку с названием языка и региональных параметров сборки.</span><span class="sxs-lookup"><span data-stu-id="54478-104">Gets the culture name string of the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54478-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="54478-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCulture(  
   [in] ULONG32 cchCulture,
   [out] ULONG32 *pcchCulture,
   [out, size_is(cchCulture), length_is(*pcchCulture)] WCHAR szCulture[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="54478-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="54478-106">Parameters</span></span>  

 `cchCulture`  
 <span data-ttu-id="54478-107">[in] Число символов в буфере `szCulture`.</span><span class="sxs-lookup"><span data-stu-id="54478-107">[in] The number of characters in the `szCulture` buffer.</span></span>  
  
 `pcchCulture`  
 <span data-ttu-id="54478-108">[выходной] Число символов, фактически записанных в буфер `szCulture`.</span><span class="sxs-lookup"><span data-stu-id="54478-108">[out] The number of characters actually written to the `szCulture` buffer.</span></span>  
  
 `szCulture`  
 <span data-ttu-id="54478-109">[выходной] Массив символов, содержащий название языка и региональных параметров.</span><span class="sxs-lookup"><span data-stu-id="54478-109">[out] A character array that contains the culture name.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="54478-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="54478-110">Remarks</span></span>  

 <span data-ttu-id="54478-111">Название языка и региональных параметров — это уникальная строка, определяющая язык и региональные параметры, например "en-US" (для английского языка (США)) или "neutral" (для нейтрального языка и региональных параметров).</span><span class="sxs-lookup"><span data-stu-id="54478-111">The culture name is a unique string that identifies a culture, such as "en-US" (for the English (United States) culture), or "neutral" (for a neutral culture).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="54478-112">Этот метод доступен только в машинном коде .NET.</span><span class="sxs-lookup"><span data-stu-id="54478-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="54478-113">Требования</span><span class="sxs-lookup"><span data-stu-id="54478-113">Requirements</span></span>  

 <span data-ttu-id="54478-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="54478-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54478-115">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="54478-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="54478-116">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="54478-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="54478-117">**Платформа .NET Framework версии:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="54478-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54478-118">См. также</span><span class="sxs-lookup"><span data-stu-id="54478-118">See also</span></span>

- [<span data-ttu-id="54478-119">Интерфейс ICorDebugMergedAssemblyRecord</span><span class="sxs-lookup"><span data-stu-id="54478-119">ICorDebugMergedAssemblyRecord Interface</span></span>](icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="54478-120">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="54478-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
