---
description: 'Дополнительные сведения о методе: метод icordebugsymbolprovider:: Жетассемблимажебитес'
title: Метод ICorDebugSymbolProvider::GetAssemblyImageBytes
ms.date: 03/30/2017
ms.assetid: 3db215aa-e180-4f70-8d23-6d5a0ffbc8e5
ms.openlocfilehash: 2e08b23e35913e8767135d75d28ff66efc890565
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99717281"
---
# <a name="icordebugsymbolprovidergetassemblyimagebytes-method"></a><span data-ttu-id="9009f-103">Метод ICorDebugSymbolProvider::GetAssemblyImageBytes</span><span class="sxs-lookup"><span data-stu-id="9009f-103">ICorDebugSymbolProvider::GetAssemblyImageBytes Method</span></span>

<span data-ttu-id="9009f-104">Считывает данные из объединенной сборки для указанного относительного виртуального адреса (RVA) в объединенной сборке.</span><span class="sxs-lookup"><span data-stu-id="9009f-104">Reads data from a merged assembly given a relative virtual address (RVA) in the merged assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9009f-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="9009f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyImageBytes(  
   [in] CORDB_ADDRESS rva,
   [in] ULONG32 length,
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9009f-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="9009f-106">Parameters</span></span>  

 `rva`  
 <span data-ttu-id="9009f-107">[in] Относительный виртуальный адрес (RVA) в объединенной сборке.</span><span class="sxs-lookup"><span data-stu-id="9009f-107">[in] A relative virtual address (RVA) in a merged assembly.</span></span>  
  
 `length`  
 <span data-ttu-id="9009f-108">Число байт для чтения из объединенной сборки.</span><span class="sxs-lookup"><span data-stu-id="9009f-108">The number of bytes to read from the merged assembly.</span></span>  
  
 `ppMemoryBuffer`  
 <span data-ttu-id="9009f-109">Указатель на адрес объекта [икордебугмеморибуффер](icordebugmemorybuffer-interface.md) , который содержит сведения о буфере памяти с объединенными метаданными сборки.</span><span class="sxs-lookup"><span data-stu-id="9009f-109">A pointer to the address of an [ICorDebugMemoryBuffer](icordebugmemorybuffer-interface.md) object that contains information about the memory buffer with merged assembly metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9009f-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="9009f-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9009f-111">Этот метод доступен только в машинном коде .NET.</span><span class="sxs-lookup"><span data-stu-id="9009f-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9009f-112">Требования</span><span class="sxs-lookup"><span data-stu-id="9009f-112">Requirements</span></span>  

 <span data-ttu-id="9009f-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9009f-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9009f-114">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9009f-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9009f-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9009f-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9009f-116">**Платформа .NET Framework версии:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9009f-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9009f-117">См. также</span><span class="sxs-lookup"><span data-stu-id="9009f-117">See also</span></span>

- [<span data-ttu-id="9009f-118">Интерфейс ICorDebugSymbolProvider</span><span class="sxs-lookup"><span data-stu-id="9009f-118">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="9009f-119">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="9009f-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
