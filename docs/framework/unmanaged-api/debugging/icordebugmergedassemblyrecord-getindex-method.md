---
description: 'Дополнительные сведения о методе: Икордебугмержедассемблирекорд:: with index'
title: Метод ICorDebugMergedAssemblyRecord::GetIndex
ms.date: 03/30/2017
ms.assetid: 98701444-b9bc-4978-9548-89ac3394147d
ms.openlocfilehash: f3a51c5ed5edacc9678c965ac385d0969e2ee8a7
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99801115"
---
# <a name="icordebugmergedassemblyrecordgetindex-method"></a><span data-ttu-id="3ae80-103">Метод ICorDebugMergedAssemblyRecord::GetIndex</span><span class="sxs-lookup"><span data-stu-id="3ae80-103">ICorDebugMergedAssemblyRecord::GetIndex Method</span></span>

<span data-ttu-id="3ae80-104">Возвращает индекс префикса сборки.</span><span class="sxs-lookup"><span data-stu-id="3ae80-104">Gets the assembly's prefix index.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ae80-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="3ae80-105">Syntax</span></span>  
  
```cpp  
HRESULT GetIndex(  
   [out] ULONG32 *pIndex  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3ae80-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="3ae80-106">Parameters</span></span>  

 `pIndex`  
 <span data-ttu-id="3ae80-107">[out] Указатель на индекс префикса.</span><span class="sxs-lookup"><span data-stu-id="3ae80-107">[out] A pointer to the prefix index.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3ae80-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="3ae80-108">Remarks</span></span>  

 <span data-ttu-id="3ae80-109">Индекс префикса используется для предотвращения конфликтов имен в типе объединенных метаданных.</span><span class="sxs-lookup"><span data-stu-id="3ae80-109">The prefix index is used to prevent name collisions in the merged metadata type names.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3ae80-110">Этот метод доступен только в машинном коде .NET.</span><span class="sxs-lookup"><span data-stu-id="3ae80-110">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3ae80-111">Требования</span><span class="sxs-lookup"><span data-stu-id="3ae80-111">Requirements</span></span>  

 <span data-ttu-id="3ae80-112">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3ae80-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3ae80-113">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3ae80-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3ae80-114">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3ae80-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3ae80-115">**Платформа .NET Framework версии:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3ae80-115">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ae80-116">См. также</span><span class="sxs-lookup"><span data-stu-id="3ae80-116">See also</span></span>

- [<span data-ttu-id="3ae80-117">Интерфейс ICorDebugMergedAssemblyRecord</span><span class="sxs-lookup"><span data-stu-id="3ae80-117">ICorDebugMergedAssemblyRecord Interface</span></span>](icordebugmergedassemblyrecord-interface.md)
- [<span data-ttu-id="3ae80-118">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="3ae80-118">Debugging Interfaces</span></span>](debugging-interfaces.md)
