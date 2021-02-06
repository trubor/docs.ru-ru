---
description: 'Дополнительные сведения о методе: метод icordebugsymbolprovider:: Жетмесодпропс'
title: Метод ICorDebugSymbolProvider::GetMethodProps
ms.date: 03/30/2017
ms.assetid: 8f836b80-b7a5-460b-bf76-5f0e45652aea
ms.openlocfilehash: 53a329426ecadfe5559c0e6a08ffbd250163e177
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99659729"
---
# <a name="icordebugsymbolprovidergetmethodprops-method"></a><span data-ttu-id="91bec-103">Метод ICorDebugSymbolProvider::GetMethodProps</span><span class="sxs-lookup"><span data-stu-id="91bec-103">ICorDebugSymbolProvider::GetMethodProps Method</span></span>

<span data-ttu-id="91bec-104">Возвращает сведения о свойствах метода, такие как токен метаданных метода и сведения о его универсальных параметрах, для указанного относительного виртуального адреса (RVA) в этом методе.</span><span class="sxs-lookup"><span data-stu-id="91bec-104">Returns information about method properties, such as the method's metadata token and information about its generic parameters, given a relative virtual address (RVA) in that method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="91bec-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="91bec-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMethodProps(  
   [in]  ULONG32 codeRva,  
   [out] mdToken *pMethodToken,  
   [out] ULONG32 *pcGenericParams,  
   [in]  ULONG32 cbSignature,  
   [out] ULONG32 *pcbSignature,  
   [out, size_is(cbSignature), length_is(*pcbSignature)] BYTE signature[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="91bec-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="91bec-106">Parameters</span></span>  

 `codeRVA`  
 <span data-ttu-id="91bec-107">[in] Относительный виртуальный адрес в методе, сведения о котором требуется извлечь.</span><span class="sxs-lookup"><span data-stu-id="91bec-107">[in] A relative virtual address in the method about which information is to be retrieved.</span></span>  
  
 `pMethodToken`  
 <span data-ttu-id="91bec-108">[out] Указатель на токен метаданных метода.</span><span class="sxs-lookup"><span data-stu-id="91bec-108">[out] A pointer to the method's metadata token.</span></span>  
  
 `pcGenericParams`  
 <span data-ttu-id="91bec-109">[out] Указатель на количество универсальных параметров, связанных с данным методом.</span><span class="sxs-lookup"><span data-stu-id="91bec-109">[out] A pointer to the number of generic parameters associated with this method.</span></span>  
  
 `cbSignature`  
 <span data-ttu-id="91bec-110">[in] Размер массива `signature`.</span><span class="sxs-lookup"><span data-stu-id="91bec-110">[in] The size of the `signature` array.</span></span> <span data-ttu-id="91bec-111">См. раздел «Примечания».</span><span class="sxs-lookup"><span data-stu-id="91bec-111">See the Remarks section.</span></span>  
  
 `pcbSignature`  
 <span data-ttu-id="91bec-112">[out] Указатель на размер возвращаемого массива `signature`.</span><span class="sxs-lookup"><span data-stu-id="91bec-112">[out] A pointer to the size of the returned `signature` array.</span></span>  
  
 `signature`  
 <span data-ttu-id="91bec-113">[out] Буфер, в котором хранятся сигнатуры TypeSpec для всех универсальных параметров.</span><span class="sxs-lookup"><span data-stu-id="91bec-113">[out] A buffer that holds the typespec signatures of all generic parameters.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="91bec-114">Remarks</span><span class="sxs-lookup"><span data-stu-id="91bec-114">Remarks</span></span>  

 <span data-ttu-id="91bec-115">Чтобы получить требуемый размер `signature` массива метода, присвойте `cbSignature` аргументу значение 0 и `signature` **значение NULL**.</span><span class="sxs-lookup"><span data-stu-id="91bec-115">To get the required size of the method's `signature` array, set the `cbSignature` argument to 0 and `signature` to **null**.</span></span> <span data-ttu-id="91bec-116">После возврата метода параметр `pcbSignature` будет содержать число байт, требуемое для массива `signature`.</span><span class="sxs-lookup"><span data-stu-id="91bec-116">When the method returns, `pcbSignature` will contain the number of bytes required for the `signature` array.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="91bec-117">Этот метод доступен только в машинном коде .NET.</span><span class="sxs-lookup"><span data-stu-id="91bec-117">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="91bec-118">Требования</span><span class="sxs-lookup"><span data-stu-id="91bec-118">Requirements</span></span>  

 <span data-ttu-id="91bec-119">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="91bec-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="91bec-120">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="91bec-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="91bec-121">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="91bec-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="91bec-122">**Платформа .NET Framework версии:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="91bec-122">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="91bec-123">См. также</span><span class="sxs-lookup"><span data-stu-id="91bec-123">See also</span></span>

- [<span data-ttu-id="91bec-124">Метод GetTypeProps</span><span class="sxs-lookup"><span data-stu-id="91bec-124">GetTypeProps Method</span></span>](icordebugsymbolprovider-gettypeprops-method.md)
- [<span data-ttu-id="91bec-125">Интерфейс ICorDebugSymbolProvider</span><span class="sxs-lookup"><span data-stu-id="91bec-125">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="91bec-126">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="91bec-126">Debugging Interfaces</span></span>](debugging-interfaces.md)
