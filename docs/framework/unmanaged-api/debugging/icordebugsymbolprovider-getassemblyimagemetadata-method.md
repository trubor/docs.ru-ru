---
description: 'Дополнительные сведения о методе: метод icordebugsymbolprovider:: GetAssemblyImageMetadata'
title: Метод ICorDebugSymbolProvider::GetAssemblyImageMetadata
ms.date: 03/30/2017
ms.assetid: c3c9de67-b865-4ecf-b887-1f1d0719a0c0
ms.openlocfilehash: 4abe5cc2b2a31f89e6ca4f8fc643f26eac276515
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99717190"
---
# <a name="icordebugsymbolprovidergetassemblyimagemetadata-method"></a><span data-ttu-id="ada56-103">Метод ICorDebugSymbolProvider::GetAssemblyImageMetadata</span><span class="sxs-lookup"><span data-stu-id="ada56-103">ICorDebugSymbolProvider::GetAssemblyImageMetadata Method</span></span>

<span data-ttu-id="ada56-104">Возвращает метаданные из объединенной сборки.</span><span class="sxs-lookup"><span data-stu-id="ada56-104">Returns the metadata from a merged assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ada56-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="ada56-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAssemblyImageMetadata(  
   [out] ICorDebugMemoryBuffer** ppMemoryBuffer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ada56-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="ada56-106">Parameters</span></span>  

 `ppMemoryBuffer`  
 <span data-ttu-id="ada56-107">заполняет Указатель на адрес объекта [икордебугмеморибуффер](icordebugmemorybuffer-interface.md) , который содержит сведения о размере и адресе метаданных объединенной сборки.</span><span class="sxs-lookup"><span data-stu-id="ada56-107">[out] A pointer to the address of an [ICorDebugMemoryBuffer](icordebugmemorybuffer-interface.md) object that contains information about the size and address of the merged assembly's metadata.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ada56-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="ada56-108">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ada56-109">Этот метод доступен только в машинном коде .NET.</span><span class="sxs-lookup"><span data-stu-id="ada56-109">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ada56-110">Требования</span><span class="sxs-lookup"><span data-stu-id="ada56-110">Requirements</span></span>  

 <span data-ttu-id="ada56-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ada56-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ada56-112">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ada56-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ada56-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ada56-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ada56-114">**Платформа .NET Framework версии:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ada56-114">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ada56-115">См. также</span><span class="sxs-lookup"><span data-stu-id="ada56-115">See also</span></span>

- [<span data-ttu-id="ada56-116">Интерфейс ICorDebugSymbolProvider</span><span class="sxs-lookup"><span data-stu-id="ada56-116">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="ada56-117">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="ada56-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
