---
description: 'Дополнительные сведения о методе: Икордебугмержедассемблирекорд:: GetPublicKey'
title: Метод ICorDebugMergedAssemblyRecord::GetPublicKey
ms.date: 03/30/2017
ms.assetid: 6f4e78ba-082b-489d-8b58-4c35fbcc7a5b
ms.openlocfilehash: 15175b0d02773bcbce46bfaec9ce1de3021b7dde
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801102"
---
# <a name="icordebugmergedassemblyrecordgetpublickey-method"></a><span data-ttu-id="95b1e-103">Метод ICorDebugMergedAssemblyRecord::GetPublicKey</span><span class="sxs-lookup"><span data-stu-id="95b1e-103">ICorDebugMergedAssemblyRecord::GetPublicKey Method</span></span>

<span data-ttu-id="95b1e-104">Возвращает открытый ключ сборки.</span><span class="sxs-lookup"><span data-stu-id="95b1e-104">Gets the assembly's public key.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="95b1e-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="95b1e-105">Syntax</span></span>  
  
```cpp  
HRESULT GetPublicKey(  
   [in] ULONG32 cbPublicKey,
   [out] ULONG32 *pcbPublicKey,
   [out, size_is(cbPublicKey), length_is(*pcbPublicKey)] BYTE pbPublicKey[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="95b1e-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="95b1e-106">Parameters</span></span>  

 `cbPublicKey`  
 <span data-ttu-id="95b1e-107">[in] Максимальное число байтов в массиве `pbPublicKey`.</span><span class="sxs-lookup"><span data-stu-id="95b1e-107">[in] The maximum number of bytes in the `pbPublicKey` array.</span></span>  
  
 `pcbPublicKey`  
 <span data-ttu-id="95b1e-108">[out] Указатель на фактическое число байтов, записанных в массив `pbPublicKey`.</span><span class="sxs-lookup"><span data-stu-id="95b1e-108">[out] A pointer to the actual number of bytes written to the `pbPublicKey` array.</span></span>  
  
 `pbPublicKey`  
 <span data-ttu-id="95b1e-109">[out] Указатель на массив байтов, содержащий открытый ключ сборки.</span><span class="sxs-lookup"><span data-stu-id="95b1e-109">[out] A pointer to a byte array that contains the assembly's public key.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="95b1e-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="95b1e-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="95b1e-111">Этот метод доступен только в машинном коде .NET.</span><span class="sxs-lookup"><span data-stu-id="95b1e-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="95b1e-112">Требования</span><span class="sxs-lookup"><span data-stu-id="95b1e-112">Requirements</span></span>  

 <span data-ttu-id="95b1e-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="95b1e-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="95b1e-114">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="95b1e-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="95b1e-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="95b1e-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="95b1e-116">**Платформа .NET Framework версии:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="95b1e-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95b1e-117">См. также</span><span class="sxs-lookup"><span data-stu-id="95b1e-117">See also</span></span>

- [<span data-ttu-id="95b1e-118">Интерфейс ICorDebugMergedAssemblyRecord</span><span class="sxs-lookup"><span data-stu-id="95b1e-118">ICorDebugMergedAssemblyRecord Interface</span></span>](icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="95b1e-119">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="95b1e-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
