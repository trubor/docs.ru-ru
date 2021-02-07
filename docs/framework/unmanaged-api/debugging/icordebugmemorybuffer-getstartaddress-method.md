---
description: 'Дополнительные сведения о методе: Икордебугмеморибуффер:: Жетстартаддресс'
title: Метод ICorDebugMemoryBuffer::GetStartAddress
ms.date: 03/30/2017
ms.assetid: f804d9ab-8c88-44f0-b278-5fcca7f87726
ms.openlocfilehash: 46720d70b8a1019e712b577b24dec5d4c3d5a31d
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99722715"
---
# <a name="icordebugmemorybuffergetstartaddress-method"></a><span data-ttu-id="d9906-103">Метод ICorDebugMemoryBuffer::GetStartAddress</span><span class="sxs-lookup"><span data-stu-id="d9906-103">ICorDebugMemoryBuffer::GetStartAddress Method</span></span>

<span data-ttu-id="d9906-104">Возвращает начальный адрес буфера памяти.</span><span class="sxs-lookup"><span data-stu-id="d9906-104">Gets the starting address of the memory buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9906-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="d9906-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStartAddress(  
   [out] LPCVOID *address  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d9906-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="d9906-106">Parameters</span></span>  

 `address`  
 <span data-ttu-id="d9906-107">[out] Указатель на начальный адрес буфера памяти.</span><span class="sxs-lookup"><span data-stu-id="d9906-107">[out] A pointer to the starting address of the memory buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d9906-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="d9906-108">Remarks</span></span>  
  
> [!WARNING]
> <span data-ttu-id="d9906-109">Этот метод доступен только в машинном коде .NET.</span><span class="sxs-lookup"><span data-stu-id="d9906-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9906-110">Требования</span><span class="sxs-lookup"><span data-stu-id="d9906-110">Requirements</span></span>  

 <span data-ttu-id="d9906-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d9906-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9906-112">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d9906-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d9906-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d9906-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d9906-114">**Платформа .NET Framework версии:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9906-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9906-115">См. также</span><span class="sxs-lookup"><span data-stu-id="d9906-115">See also</span></span>

- [<span data-ttu-id="d9906-116">Интерфейс ICorDebugMemoryBuffer</span><span class="sxs-lookup"><span data-stu-id="d9906-116">ICorDebugMemoryBuffer Interface</span></span>](icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="d9906-117">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="d9906-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
