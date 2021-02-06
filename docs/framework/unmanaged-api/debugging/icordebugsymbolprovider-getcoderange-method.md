---
description: 'Дополнительные сведения о методе: метод icordebugsymbolprovider:: GetCodeRange'
title: Метод ICorDebugSymbolProvider::GetCodeRange
ms.date: 03/30/2017
ms.assetid: 49a2451f-d250-4e73-aa96-9ff49d9f11c6
ms.openlocfilehash: 98b228be7483e6365815f6b783167b20fb3bcc48
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99659911"
---
# <a name="icordebugsymbolprovidergetcoderange-method"></a><span data-ttu-id="f398e-103">Метод ICorDebugSymbolProvider::GetCodeRange</span><span class="sxs-lookup"><span data-stu-id="f398e-103">ICorDebugSymbolProvider::GetCodeRange Method</span></span>

<span data-ttu-id="f398e-104">Получает начальный адрес метода и размер для указанного относительного виртуального адреса (RVA) в методе.</span><span class="sxs-lookup"><span data-stu-id="f398e-104">Gets the method start address and size given a relative virtual address (RVA) in a method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f398e-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="f398e-105">Syntax</span></span>  
  
```cpp  
HRESULT GetCodeRange(  
   [in] ULONG32 codeRva,
   [out] ULONG32* pCodeStartAddress,
   [out] ULONG32* pCodeSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f398e-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="f398e-106">Parameters</span></span>  

 `codeRva`  
 <span data-ttu-id="f398e-107">[in] Относительный виртуальный адрес (RVA) в методе.</span><span class="sxs-lookup"><span data-stu-id="f398e-107">[in] The relative virtual address (RVA) in a method.</span></span>  
  
 `pCodeStartAddress`  
 <span data-ttu-id="f398e-108">[out] Указатель на начальный адрес метода.</span><span class="sxs-lookup"><span data-stu-id="f398e-108">[out] A pointer to the starting address of the method.</span></span>  
  
 `pCodeSize`  
 <span data-ttu-id="f398e-109">Указатель на размер кода метода (число байтов кода метода).</span><span class="sxs-lookup"><span data-stu-id="f398e-109">A pointer to the method code size (the number of bytes of the method's code).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f398e-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="f398e-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f398e-111">Этот метод доступен только в машинном коде .NET.</span><span class="sxs-lookup"><span data-stu-id="f398e-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f398e-112">Требования</span><span class="sxs-lookup"><span data-stu-id="f398e-112">Requirements</span></span>  

 <span data-ttu-id="f398e-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f398e-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f398e-114">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f398e-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f398e-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f398e-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f398e-116">**Платформа .NET Framework версии:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f398e-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f398e-117">См. также</span><span class="sxs-lookup"><span data-stu-id="f398e-117">See also</span></span>

- [<span data-ttu-id="f398e-118">Интерфейс ICorDebugSymbolProvider</span><span class="sxs-lookup"><span data-stu-id="f398e-118">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="f398e-119">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="f398e-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
