---
description: 'Дополнительные сведения о методе: метод icordebugsymbolprovider:: GetTypeProps'
title: Метод ICorDebugSymbolProvider::GetTypeProps
ms.date: 03/30/2017
ms.assetid: 35ac4140-91ea-4c77-b1c4-1daf41986ca5
ms.openlocfilehash: b6a4a5a68e1e377fa839940832dfc49574009641
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99659664"
---
# <a name="icordebugsymbolprovidergettypeprops-method"></a><span data-ttu-id="da8eb-103">Метод ICorDebugSymbolProvider::GetTypeProps</span><span class="sxs-lookup"><span data-stu-id="da8eb-103">ICorDebugSymbolProvider::GetTypeProps Method</span></span>

<span data-ttu-id="da8eb-104">Возвращает сведения о свойствах типа, такие как число сигнатур его универсальных параметров, для указанного относительного виртуального адреса (RVA) в таблице VTable.</span><span class="sxs-lookup"><span data-stu-id="da8eb-104">Returns information about a type's properties, such as the number of signature of its generic parameters, given a relative virtual address (RVA) in a vtable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da8eb-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="da8eb-105">Syntax</span></span>  
  
```cpp  
HRESULT GetTypeProps(  
   [in]  ULONG32 vtableRva,  
   [in]  ULONG32 cbSignature,  
   [out] ULONG32 *pcbSignature,  
   [out, size_is(cbSignature), length_is(*pcbSignature)] BYTE signature[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="da8eb-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="da8eb-106">Parameters</span></span>  

 `tableRva`  
 <span data-ttu-id="da8eb-107">[in] Относительный виртуальный адрес (RVA) в VTable.</span><span class="sxs-lookup"><span data-stu-id="da8eb-107">[in] A relative virtual address (RVA) in a vtable.</span></span>  
  
 `cbSignature`  
 <span data-ttu-id="da8eb-108">[in] Размер массива `signature`.</span><span class="sxs-lookup"><span data-stu-id="da8eb-108">[in] The size of the `signature` array.</span></span> <span data-ttu-id="da8eb-109">См. раздел «Примечания».</span><span class="sxs-lookup"><span data-stu-id="da8eb-109">See the Remarks section.</span></span>  
  
 `pcbSignature`  
 <span data-ttu-id="da8eb-110">[out] Указатель на размер возвращаемого массива `signature`.</span><span class="sxs-lookup"><span data-stu-id="da8eb-110">[out] [out] A pointer to the size of the returned `signature` array.</span></span>  
  
 `signature`  
 <span data-ttu-id="da8eb-111">[out] Буфер, в котором хранятся сигнатуры TypeSpec для всех универсальных параметров.</span><span class="sxs-lookup"><span data-stu-id="da8eb-111">[out] A buffer that holds the typespec signatures of all generic parameters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="da8eb-112">Remarks</span><span class="sxs-lookup"><span data-stu-id="da8eb-112">Remarks</span></span>  

 <span data-ttu-id="da8eb-113">Чтобы получить требуемый размер `signature` массива типа, задайте `cbSignature` для аргумента значение 0 и `signature` **значение NULL**.</span><span class="sxs-lookup"><span data-stu-id="da8eb-113">To get the required size of the type's `signature` array, set the `cbSignature` argument to 0 and `signature` to **null**.</span></span> <span data-ttu-id="da8eb-114">После возврата метода параметр `pcbSignature` будет содержать число байт, требуемое для массива `signature`.</span><span class="sxs-lookup"><span data-stu-id="da8eb-114">When the method returns, `pcbSignature` will contain the number of bytes required for the `signature` array.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="da8eb-115">Этот метод доступен только в машинном коде .NET.</span><span class="sxs-lookup"><span data-stu-id="da8eb-115">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da8eb-116">Требования</span><span class="sxs-lookup"><span data-stu-id="da8eb-116">Requirements</span></span>  

 <span data-ttu-id="da8eb-117">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="da8eb-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da8eb-118">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="da8eb-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="da8eb-119">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="da8eb-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="da8eb-120">**Платформа .NET Framework версии:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da8eb-120">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da8eb-121">См. также</span><span class="sxs-lookup"><span data-stu-id="da8eb-121">See also</span></span>

- [<span data-ttu-id="da8eb-122">Метод GetMethodProps</span><span class="sxs-lookup"><span data-stu-id="da8eb-122">GetMethodProps Method</span></span>](icordebugsymbolprovider-getmethodprops-method.md)
- [<span data-ttu-id="da8eb-123">Интерфейс ICorDebugSymbolProvider</span><span class="sxs-lookup"><span data-stu-id="da8eb-123">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="da8eb-124">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="da8eb-124">Debugging Interfaces</span></span>](debugging-interfaces.md)
