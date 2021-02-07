---
description: 'Дополнительные сведения о методе: метод icordebugdatatarget2:: GetImageLocation'
title: Метод ICorDebugDataTarget2::GetImageLocation
ms.date: 03/30/2017
ms.assetid: 696afe71-5852-478d-a33f-b2d2dbc4b91f
ms.openlocfilehash: f79ba89d3ba467c2e81224d64147c2b5dd5db079
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99710495"
---
# <a name="icordebugdatatarget2getimagelocation-method"></a><span data-ttu-id="17714-103">Метод ICorDebugDataTarget2::GetImageLocation</span><span class="sxs-lookup"><span data-stu-id="17714-103">ICorDebugDataTarget2::GetImageLocation Method</span></span>

<span data-ttu-id="17714-104">Возвращает путь для модуля из базового адреса модуля.</span><span class="sxs-lookup"><span data-stu-id="17714-104">Returns the path of a module from the module's base address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17714-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="17714-105">Syntax</span></span>  
  
```cpp  
HRESULT GetImageLocation(    [in] CORDB_ADDRESS baseAddress,  
    [in] ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="17714-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="17714-106">Parameters</span></span>  

 `baseAddress`  
 <span data-ttu-id="17714-107">окне Значение [CORDB_ADDRESS](../common-data-types-unmanaged-api-reference.md) , представляющее базовый адрес модуля.</span><span class="sxs-lookup"><span data-stu-id="17714-107">[in] A [CORDB_ADDRESS](../common-data-types-unmanaged-api-reference.md) value that represents the module's base address.</span></span>  
  
 `cchName`  
 <span data-ttu-id="17714-108">[входной] Число символов в буфере, которые должен получить путь к модулю.</span><span class="sxs-lookup"><span data-stu-id="17714-108">[in] The number of characters in the buffer that is to receive the module path.</span></span>  
  
 `pcchName`  
 <span data-ttu-id="17714-109">[выходной] Указатель на число символов, записанных в буфер `szName`.</span><span class="sxs-lookup"><span data-stu-id="17714-109">[out] A pointer to the number of characters written to the `szName` buffer.</span></span>  
  
 `szName`  
 <span data-ttu-id="17714-110">[выходной] Путь к модулю.</span><span class="sxs-lookup"><span data-stu-id="17714-110">[out] The path of the module.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="17714-111">Remarks</span><span class="sxs-lookup"><span data-stu-id="17714-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="17714-112">Этот метод доступен только в машинном коде .NET.</span><span class="sxs-lookup"><span data-stu-id="17714-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17714-113">Требования</span><span class="sxs-lookup"><span data-stu-id="17714-113">Requirements</span></span>  

 <span data-ttu-id="17714-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="17714-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17714-115">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="17714-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="17714-116">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="17714-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="17714-117">**Платформа .NET Framework версии:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="17714-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17714-118">См. также</span><span class="sxs-lookup"><span data-stu-id="17714-118">See also</span></span>

- [<span data-ttu-id="17714-119">Интерфейс ICorDebugDataTarget2</span><span class="sxs-lookup"><span data-stu-id="17714-119">ICorDebugDataTarget2 Interface</span></span>](icordebugdatatarget2-interface.md)
- [<span data-ttu-id="17714-120">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="17714-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
