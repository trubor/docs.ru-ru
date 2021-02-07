---
description: 'Дополнительные сведения о методе: ICorDebugVariableHome:: методом offset'
title: 'Метод ICorDebugVariableHome:: методом offset'
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetOffset
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetOffset
helpviewer_keywords:
- ICorDebugVariableHome::GetOffset method [.NET Framework debugging]
- GetOffset method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: f025c2e5-3f6c-4be8-9ffe-c8b214617dfe
topic_type:
- apiref
ms.openlocfilehash: 48b57856d2825dd2ea9328064a28783b4b36029b
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99728773"
---
# <a name="icordebugvariablehomegetoffset-method"></a><span data-ttu-id="a7feb-103">Метод ICorDebugVariableHome:: методом offset</span><span class="sxs-lookup"><span data-stu-id="a7feb-103">ICorDebugVariableHome::GetOffset Method</span></span>

<span data-ttu-id="a7feb-104">Возвращает смещение от базового регистра для переменной.</span><span class="sxs-lookup"><span data-stu-id="a7feb-104">Gets the offset from the base register for a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7feb-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a7feb-105">Syntax</span></span>  
  
```cpp  
HRESULT GetOffset(  
    [out] LONG *pOffset  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a7feb-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="a7feb-106">Parameters</span></span>  

 `pOffset`  
 <span data-ttu-id="a7feb-107">заполняет Смещение от базового регистра.</span><span class="sxs-lookup"><span data-stu-id="a7feb-107">[out] The offset from the base register.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a7feb-108">Возвращаемое значение</span><span class="sxs-lookup"><span data-stu-id="a7feb-108">Return Value</span></span>  

 <span data-ttu-id="a7feb-109">Метод возвращает следующие значения:</span><span class="sxs-lookup"><span data-stu-id="a7feb-109">The method returns the following values:</span></span>  
  
|<span data-ttu-id="a7feb-110">Значение</span><span class="sxs-lookup"><span data-stu-id="a7feb-110">Value</span></span>|<span data-ttu-id="a7feb-111">Описание</span><span class="sxs-lookup"><span data-stu-id="a7feb-111">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="a7feb-112">Переменная находится в расположении в памяти относительно регистра.</span><span class="sxs-lookup"><span data-stu-id="a7feb-112">The variable is in a register-relative memory location.</span></span>|  
|`E_FAIL`|<span data-ttu-id="a7feb-113">Переменная не находится в расположении в памяти относительно регистра.</span><span class="sxs-lookup"><span data-stu-id="a7feb-113">The variable is not in a register-relative memory location.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a7feb-114">Требования</span><span class="sxs-lookup"><span data-stu-id="a7feb-114">Requirements</span></span>  

 <span data-ttu-id="a7feb-115">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a7feb-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7feb-116">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a7feb-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a7feb-117">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a7feb-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a7feb-118">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7feb-118">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7feb-119">См. также</span><span class="sxs-lookup"><span data-stu-id="a7feb-119">See also</span></span>

- [<span data-ttu-id="a7feb-120">Интерфейс ICorDebugVariableHome</span><span class="sxs-lookup"><span data-stu-id="a7feb-120">ICorDebugVariableHome Interface</span></span>](icordebugvariablehome-interface.md)
