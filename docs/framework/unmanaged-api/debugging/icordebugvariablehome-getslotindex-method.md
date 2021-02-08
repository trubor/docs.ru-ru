---
description: 'Дополнительные сведения о методе: ICorDebugVariableHome:: GetSlotIndex'
title: 'Метод ICorDebugVariableHome:: GetSlotIndex'
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetSlotIndex
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetSlotIndex
helpviewer_keywords:
- ICorDebugVariableHome::GetSlotIndex method [.NET Framework debugging]
- GetSlotIndex method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: 966da50d-5665-4fff-bf7b-1c72bbadd9a4
topic_type:
- apiref
ms.openlocfilehash: 7f6ee01c2bfcee4c78f8463a7cefac1f90a3295f
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99790650"
---
# <a name="icordebugvariablehomegetslotindex-method"></a><span data-ttu-id="cedf9-103">Метод ICorDebugVariableHome:: GetSlotIndex</span><span class="sxs-lookup"><span data-stu-id="cedf9-103">ICorDebugVariableHome::GetSlotIndex Method</span></span>

<span data-ttu-id="cedf9-104">Возвращает управляемый индекс в виде слота локальной переменной.</span><span class="sxs-lookup"><span data-stu-id="cedf9-104">Gets the managed slot-index of a local variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cedf9-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="cedf9-105">Syntax</span></span>  
  
```cpp  
HRESULT GetSlotIndex(  
    [out] ULONG32 *pSlotIndex  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cedf9-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="cedf9-106">Parameters</span></span>  

 `pSlotIndex`  
 <span data-ttu-id="cedf9-107">заполняет Указатель на индекс в виде слота локальной переменной.</span><span class="sxs-lookup"><span data-stu-id="cedf9-107">[out] A pointer to the slot-index of a local variable.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cedf9-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="cedf9-108">Return Value</span></span>  

 <span data-ttu-id="cedf9-109">Метод возвращает следующие значения.</span><span class="sxs-lookup"><span data-stu-id="cedf9-109">The method returns the following values.</span></span>  
  
|<span data-ttu-id="cedf9-110">Значение</span><span class="sxs-lookup"><span data-stu-id="cedf9-110">Value</span></span>|<span data-ttu-id="cedf9-111">Описание</span><span class="sxs-lookup"><span data-stu-id="cedf9-111">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="cedf9-112">Вызов метода вернул значение индекса слота в `pSlotIndex` .</span><span class="sxs-lookup"><span data-stu-id="cedf9-112">The method call returned a slot-index value in `pSlotIndex`.</span></span>|  
|`E_FAIL`|<span data-ttu-id="cedf9-113">Текущий экземпляр [ICorDebugVariableHome](icordebugvariablehome-interface.md) представляет аргумент функции.</span><span class="sxs-lookup"><span data-stu-id="cedf9-113">The current [ICorDebugVariableHome](icordebugvariablehome-interface.md) instance represents a function argument.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cedf9-114">Remarks</span><span class="sxs-lookup"><span data-stu-id="cedf9-114">Remarks</span></span>  

 <span data-ttu-id="cedf9-115">Чтобы получить метаданные для этой локальной переменной, можно использовать индекс Slot.</span><span class="sxs-lookup"><span data-stu-id="cedf9-115">The slot-index can be used to retrieve the metadata for this local variable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cedf9-116">Требования</span><span class="sxs-lookup"><span data-stu-id="cedf9-116">Requirements</span></span>  

 <span data-ttu-id="cedf9-117">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cedf9-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cedf9-118">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cedf9-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cedf9-119">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cedf9-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cedf9-120">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cedf9-120">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cedf9-121">См. также</span><span class="sxs-lookup"><span data-stu-id="cedf9-121">See also</span></span>

- [<span data-ttu-id="cedf9-122">Интерфейс ICorDebugVariableHome</span><span class="sxs-lookup"><span data-stu-id="cedf9-122">ICorDebugVariableHome Interface</span></span>](icordebugvariablehome-interface.md)
