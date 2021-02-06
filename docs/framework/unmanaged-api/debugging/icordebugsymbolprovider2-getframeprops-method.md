---
description: 'Дополнительные сведения о методе: ICorDebugSymbolProvider2:: Жетфрамепропс'
title: Метод ICorDebugSymbolProvider2::GetFrameProps
ms.date: 03/30/2017
ms.assetid: f07b73f3-188d-43a9-8f7d-44dce2f1ddb7
ms.openlocfilehash: c0286e423f8f395568ad4df94fac38a7ef91c6bd
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99659560"
---
# <a name="icordebugsymbolprovider2getframeprops-method"></a><span data-ttu-id="7adbe-103">Метод ICorDebugSymbolProvider2::GetFrameProps</span><span class="sxs-lookup"><span data-stu-id="7adbe-103">ICorDebugSymbolProvider2::GetFrameProps Method</span></span>

<span data-ttu-id="7adbe-104">Возвращает начальный относительный виртуальный адрес метода и родительского фрейма для указанного относительного виртуального адреса кода.</span><span class="sxs-lookup"><span data-stu-id="7adbe-104">Returns the method starting relative virtual address of a method and the parent frame given a code relative virtual address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7adbe-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="7adbe-105">Syntax</span></span>  
  
```cpp  
HRESULT GetFrameProps(  
   [in] ULONG32 codeRva,  
   [out] ULONG32 *pCodeStartRva,  
   [out] ULONG32 *pParentFrameStartRva  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7adbe-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="7adbe-106">Parameters</span></span>  

 `codeRva`  
 <span data-ttu-id="7adbe-107">[in] Относительный виртуальный адрес кода.</span><span class="sxs-lookup"><span data-stu-id="7adbe-107">[in] A code relative virtual address.</span></span>  
  
 `pCodeStartRva`  
 <span data-ttu-id="7adbe-108">[out] Указатель на начальный относительный виртуальный адрес метода.</span><span class="sxs-lookup"><span data-stu-id="7adbe-108">[out] A pointer to the method's starting relative virtual address.</span></span>  
  
 `pParentFrameStartRva`  
 <span data-ttu-id="7adbe-109">[out] Указатель на начальный относительный виртуальный адрес фрейма.</span><span class="sxs-lookup"><span data-stu-id="7adbe-109">[out] A pointer to the frame's starting relative virtual address.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7adbe-110">Remarks</span><span class="sxs-lookup"><span data-stu-id="7adbe-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7adbe-111">Этот метод доступен только в машинном коде .NET.</span><span class="sxs-lookup"><span data-stu-id="7adbe-111">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7adbe-112">Требования</span><span class="sxs-lookup"><span data-stu-id="7adbe-112">Requirements</span></span>  

 <span data-ttu-id="7adbe-113">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7adbe-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7adbe-114">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7adbe-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7adbe-115">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7adbe-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7adbe-116">**Платформа .NET Framework версии:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7adbe-116">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7adbe-117">См. также</span><span class="sxs-lookup"><span data-stu-id="7adbe-117">See also</span></span>

- [<span data-ttu-id="7adbe-118">Интерфейс ICorDebugSymbolProvider2</span><span class="sxs-lookup"><span data-stu-id="7adbe-118">ICorDebugSymbolProvider2 Interface</span></span>](icordebugsymbolprovider2-interface.md)
- [<span data-ttu-id="7adbe-119">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="7adbe-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
