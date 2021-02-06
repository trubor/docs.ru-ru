---
description: 'Дополнительные сведения о методе: Икордебугмержедассемблирекорд:: Жетсимпленаме'
title: Метод ICorDebugMergedAssemblyRecord::GetSimpleName
ms.date: 03/30/2017
ms.assetid: bc3410f6-ebca-4bca-9b45-fc38c74fa9cb
ms.openlocfilehash: e77a5cc7df009a5bc55a7eb952ead80e5f81f271
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99650395"
---
# <a name="icordebugmergedassemblyrecordgetsimplename-method"></a><span data-ttu-id="3fcfe-103">Метод ICorDebugMergedAssemblyRecord::GetSimpleName</span><span class="sxs-lookup"><span data-stu-id="3fcfe-103">ICorDebugMergedAssemblyRecord::GetSimpleName Method</span></span>

<span data-ttu-id="3fcfe-104">Получает простое имя сборки.</span><span class="sxs-lookup"><span data-stu-id="3fcfe-104">Gets the simple name of the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3fcfe-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="3fcfe-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSimpleName(  
   [in] ULONG32 cchName,
   [out] ULONG32 *pcchName,
   [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3fcfe-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="3fcfe-106">Parameters</span></span>  

 `cchName`  
 <span data-ttu-id="3fcfe-107">[in] Число символов в буфере `szName`.</span><span class="sxs-lookup"><span data-stu-id="3fcfe-107">[in] The number of characters in the `szName` buffer.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="3fcfe-108">[out] Указатель на число символов, фактически записанных в буфер `szName`.</span><span class="sxs-lookup"><span data-stu-id="3fcfe-108">[out] A pointer to the number of characters actually written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="3fcfe-109">Указатель на массив символов.</span><span class="sxs-lookup"><span data-stu-id="3fcfe-109">A pointer to a character array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3fcfe-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="3fcfe-110">Remarks</span></span>  

 <span data-ttu-id="3fcfe-111">Этот метод возвращает простое имя сборки (например, System.Collections) без расширения имени файла, версии, языка и региональных параметров и токена открытого ключа.</span><span class="sxs-lookup"><span data-stu-id="3fcfe-111">This method retrieves the simple name of an assembly (such as "System.Collections"), without a file extension, version, culture, or public key token.</span></span> <span data-ttu-id="3fcfe-112">Оно соответствует свойству <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> в управляемом коде.</span><span class="sxs-lookup"><span data-stu-id="3fcfe-112">It corresponds to the <xref:System.Reflection.AssemblyName.Name%2A?displayProperty=nameWithType> property in managed code.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3fcfe-113">Этот метод доступен только в машинном коде .NET.</span><span class="sxs-lookup"><span data-stu-id="3fcfe-113">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3fcfe-114">Требования</span><span class="sxs-lookup"><span data-stu-id="3fcfe-114">Requirements</span></span>  

 <span data-ttu-id="3fcfe-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3fcfe-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3fcfe-116">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3fcfe-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3fcfe-117">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3fcfe-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3fcfe-118">**Платформа .NET Framework версии:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3fcfe-118">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fcfe-119">См. также</span><span class="sxs-lookup"><span data-stu-id="3fcfe-119">See also</span></span>

- [<span data-ttu-id="3fcfe-120">Интерфейс ICorDebugMergedAssemblyRecord</span><span class="sxs-lookup"><span data-stu-id="3fcfe-120">ICorDebugMergedAssemblyRecord Interface</span></span>](icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="3fcfe-121">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="3fcfe-121">Debugging Interfaces</span></span>](debugging-interfaces.md)
