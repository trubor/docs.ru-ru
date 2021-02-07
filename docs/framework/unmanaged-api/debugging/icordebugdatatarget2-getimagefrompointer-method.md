---
description: 'Дополнительные сведения о методе: метод icordebugdatatarget2:: Жетимажефромпоинтер'
title: Метод ICorDebugDataTarget2::GetImageFromPointer
ms.date: 03/30/2017
ms.assetid: 939cabe1-b647-4090-b662-eeec23c6c58d
ms.openlocfilehash: bcf73fa522072707a7b08d90965fcd38188c2bb5
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99764402"
---
# <a name="icordebugdatatarget2getimagefrompointer-method"></a><span data-ttu-id="e9087-103">Метод ICorDebugDataTarget2::GetImageFromPointer</span><span class="sxs-lookup"><span data-stu-id="e9087-103">ICorDebugDataTarget2::GetImageFromPointer Method</span></span>

<span data-ttu-id="e9087-104">Возвращает базовый адрес и размер модуля из адреса в этом модуле.</span><span class="sxs-lookup"><span data-stu-id="e9087-104">Returns the module base address and size from an address in that module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9087-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="e9087-105">Syntax</span></span>  
  
```cpp  
HRESULT GetImageFromPointer(  
   [in] CORDB_ADDRESS addr,
   [out] CORDB_ADDRESS *pImageBase,
   [out] ULONG32 *pSize  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e9087-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="e9087-106">Parameters</span></span>  

 `addr`  
 <span data-ttu-id="e9087-107">Значение [CORDB_ADDRESS](../common-data-types-unmanaged-api-reference.md) , представляющее адрес в модуле.</span><span class="sxs-lookup"><span data-stu-id="e9087-107">A [CORDB_ADDRESS](../common-data-types-unmanaged-api-reference.md) value that represents an address in a module.</span></span>  
  
 `pImageBase`  
 <span data-ttu-id="e9087-108">заполняет Значение [CORDB_ADDRESS](../common-data-types-unmanaged-api-reference.md) , представляющее базовый адрес модуля.</span><span class="sxs-lookup"><span data-stu-id="e9087-108">[out] A [CORDB_ADDRESS](../common-data-types-unmanaged-api-reference.md) value that represents the module's base address.</span></span>  
  
 `pSize`  
 <span data-ttu-id="e9087-109">Указатель на размер модуля.</span><span class="sxs-lookup"><span data-stu-id="e9087-109">A pointer to the module size.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e9087-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="e9087-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e9087-111">Этот метод доступен только в машинном коде .NET.</span><span class="sxs-lookup"><span data-stu-id="e9087-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9087-112">Требования</span><span class="sxs-lookup"><span data-stu-id="e9087-112">Requirements</span></span>  

 <span data-ttu-id="e9087-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e9087-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9087-114">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e9087-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e9087-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e9087-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e9087-116">**Платформа .NET Framework версии:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9087-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9087-117">См. также</span><span class="sxs-lookup"><span data-stu-id="e9087-117">See also</span></span>

- [<span data-ttu-id="e9087-118">Интерфейс ICorDebugDataTarget2</span><span class="sxs-lookup"><span data-stu-id="e9087-118">ICorDebugDataTarget2 Interface</span></span>](icordebugdatatarget2-interface.md)
- [<span data-ttu-id="e9087-119">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="e9087-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
