---
description: 'Дополнительные сведения о методе: метод icordebugdatatarget2:: GetSymbolProviderForImage'
title: Метод ICorDebugDataTarget2::GetSymbolProviderForImage
ms.date: 03/30/2017
ms.assetid: b7c0a2f0-e904-43b3-98e1-d669e8a589e8
ms.openlocfilehash: 7b4493b6c0959dc39d955d7691a22ac6905034b1
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99764389"
---
# <a name="icordebugdatatarget2getsymbolproviderforimage-method"></a><span data-ttu-id="9b33e-103">Метод ICorDebugDataTarget2::GetSymbolProviderForImage</span><span class="sxs-lookup"><span data-stu-id="9b33e-103">ICorDebugDataTarget2::GetSymbolProviderForImage Method</span></span>

<span data-ttu-id="9b33e-104">Возвращает поставщика символов для модуля из базового адреса модуля.</span><span class="sxs-lookup"><span data-stu-id="9b33e-104">Returns the symbol-provider for a module from the base address of that module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b33e-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="9b33e-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSymbolProviderForImage(  
    [in] CORDB_ADDRESS imageBaseAddress,
    [out] ICorDebugSymbolProvider **ppSymProvider  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9b33e-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="9b33e-106">Parameters</span></span>  

 `imageBaseAddress`  
 <span data-ttu-id="9b33e-107">окне Значение [CORDB_ADDRESS](../common-data-types-unmanaged-api-reference.md) , представляющее базовый адрес модуля.</span><span class="sxs-lookup"><span data-stu-id="9b33e-107">[in] A [CORDB_ADDRESS](../common-data-types-unmanaged-api-reference.md) value that represents the base address of a module.</span></span>  
  
 `ppSymProvider`  
 <span data-ttu-id="9b33e-108">заполняет Указатель на адрес объекта [метод icordebugsymbolprovider](icordebugsymbolprovider-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="9b33e-108">[out] A pointer to the address of an [ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md) object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9b33e-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="9b33e-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9b33e-110">Этот метод доступен только в машинном коде .NET.</span><span class="sxs-lookup"><span data-stu-id="9b33e-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9b33e-111">Требования</span><span class="sxs-lookup"><span data-stu-id="9b33e-111">Requirements</span></span>  

 <span data-ttu-id="9b33e-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9b33e-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9b33e-113">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9b33e-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9b33e-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9b33e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9b33e-115">**Платформа .NET Framework версии:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9b33e-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9b33e-116">См. также</span><span class="sxs-lookup"><span data-stu-id="9b33e-116">See also</span></span>

- [<span data-ttu-id="9b33e-117">Интерфейс ICorDebugDataTarget2</span><span class="sxs-lookup"><span data-stu-id="9b33e-117">ICorDebugDataTarget2 Interface</span></span>](icordebugdatatarget2-interface.md)
- [<span data-ttu-id="9b33e-118">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="9b33e-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
