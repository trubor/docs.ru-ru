---
description: 'Дополнительные сведения о методе: Икордебугмеморибуффер:: resize'
title: Метод ICorDebugMemoryBuffer::GetSize
ms.date: 03/30/2017
ms.assetid: 9ffd5482-268e-4680-9fd1-bfb0b7d66450
ms.openlocfilehash: 7de23dd13a1e0ef841145e3845d7d0052ce3ef9a
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99754044"
---
# <a name="icordebugmemorybuffergetsize-method"></a><span data-ttu-id="3c5bd-103">Метод ICorDebugMemoryBuffer::GetSize</span><span class="sxs-lookup"><span data-stu-id="3c5bd-103">ICorDebugMemoryBuffer::GetSize Method</span></span>

<span data-ttu-id="3c5bd-104">Возвращает размер буфера памяти в байтах.</span><span class="sxs-lookup"><span data-stu-id="3c5bd-104">Gets the size of the memory buffer in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c5bd-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="3c5bd-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbBufferLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3c5bd-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="3c5bd-106">Parameters</span></span>  

 `pcbBufferLength`  
 <span data-ttu-id="3c5bd-107">[out] Указатель на размер буфера памяти.</span><span class="sxs-lookup"><span data-stu-id="3c5bd-107">[out] A pointer to the size of the memory buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3c5bd-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="3c5bd-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3c5bd-109">Этот метод доступен только в машинном коде .NET.</span><span class="sxs-lookup"><span data-stu-id="3c5bd-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c5bd-110">Требования</span><span class="sxs-lookup"><span data-stu-id="3c5bd-110">Requirements</span></span>  

 <span data-ttu-id="3c5bd-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3c5bd-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c5bd-112">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3c5bd-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3c5bd-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3c5bd-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3c5bd-114">**Платформа .NET Framework версии:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c5bd-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c5bd-115">См. также</span><span class="sxs-lookup"><span data-stu-id="3c5bd-115">See also</span></span>

- [<span data-ttu-id="3c5bd-116">Интерфейс ICorDebugMemoryBuffer</span><span class="sxs-lookup"><span data-stu-id="3c5bd-116">ICorDebugMemoryBuffer Interface</span></span>](icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="3c5bd-117">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="3c5bd-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
