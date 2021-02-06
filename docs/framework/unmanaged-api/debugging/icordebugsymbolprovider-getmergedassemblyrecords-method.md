---
description: 'Дополнительные сведения о методе: метод icordebugsymbolprovider:: Жетмержедассемблирекордс'
title: Метод ICorDebugSymbolProvider::GetMergedAssemblyRecords
ms.date: 03/30/2017
ms.assetid: cc4c510d-550d-4941-af34-81987caf3425
ms.openlocfilehash: f12bb3a49d7b49f9f8916c9d04417340502d44ba
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99659885"
---
# <a name="icordebugsymbolprovidergetmergedassemblyrecords-method"></a><span data-ttu-id="1a0ef-103">Метод ICorDebugSymbolProvider::GetMergedAssemblyRecords</span><span class="sxs-lookup"><span data-stu-id="1a0ef-103">ICorDebugSymbolProvider::GetMergedAssemblyRecords Method</span></span>

<span data-ttu-id="1a0ef-104">Возвращает символьные записи для всех объединенных сборок.</span><span class="sxs-lookup"><span data-stu-id="1a0ef-104">Gets the symbol records for all the merged assemblies.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a0ef-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="1a0ef-105">Syntax</span></span>  
  
```cpp  
HRESULT GetMergedAssemblyRecords(  
   [in] ULONG32 cRequestedRecords,  
   [out] ULONG32 *pcFetchedRecords,  
   [out, size_is(cRequestedRecords), length_is(*pcFetchedRecords)] ICorDebugMergedAssemblyRecord *pRecords[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1a0ef-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="1a0ef-106">Parameters</span></span>  

 `cRequestedRecords`  
 <span data-ttu-id="1a0ef-107">[in] Количество запрошенных символьных записей.</span><span class="sxs-lookup"><span data-stu-id="1a0ef-107">[in] The number of symbol records requested.</span></span>  
  
 `pcFetchedRecords`  
 <span data-ttu-id="1a0ef-108">[out] Указатель на число  символьных записей, полученных при помощи метода.</span><span class="sxs-lookup"><span data-stu-id="1a0ef-108">[out] A pointer to the number of symbol records retrieved by the method.</span></span>  
  
 `pRecords`  
 <span data-ttu-id="1a0ef-109">Указатель на массив объектов [икордебугмержедассемблирекорд](icordebugmergedassemblyrecord-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="1a0ef-109">A pointer to an array of [ICorDebugMergedAssemblyRecord](icordebugmergedassemblyrecord-interface.md) objects.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1a0ef-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="1a0ef-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1a0ef-111">Этот метод доступен только в машинном коде .NET.</span><span class="sxs-lookup"><span data-stu-id="1a0ef-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1a0ef-112">Требования</span><span class="sxs-lookup"><span data-stu-id="1a0ef-112">Requirements</span></span>  

 <span data-ttu-id="1a0ef-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1a0ef-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a0ef-114">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1a0ef-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1a0ef-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1a0ef-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1a0ef-116">**Платформа .NET Framework версии:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1a0ef-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a0ef-117">См. также</span><span class="sxs-lookup"><span data-stu-id="1a0ef-117">See also</span></span>

- [<span data-ttu-id="1a0ef-118">Интерфейс ICorDebugSymbolProvider</span><span class="sxs-lookup"><span data-stu-id="1a0ef-118">ICorDebugSymbolProvider Interface</span></span>](icordebugsymbolprovider-interface.md)
- [<span data-ttu-id="1a0ef-119">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="1a0ef-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
