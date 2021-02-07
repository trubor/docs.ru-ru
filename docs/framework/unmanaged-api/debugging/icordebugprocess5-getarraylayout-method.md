---
description: 'Дополнительные сведения о методе: метод ICorDebugProcess5:: Жетаррайлайаут'
title: Метод ICorDebugProcess5::GetArrayLayout
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.GetArrayLayout
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::GetArrayLayout
helpviewer_keywords:
- ICorDebugProcess5::GetArrayLayout method [.NET Framework debugging]
- GetArrayLayout method, ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: 9a7393b9-9735-43c6-8616-afb103c432fd
topic_type:
- apiref
ms.openlocfilehash: c82b296da3a367f5307240225a560af67a56c866
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99746403"
---
# <a name="icordebugprocess5getarraylayout-method"></a><span data-ttu-id="a7008-103">Метод ICorDebugProcess5::GetArrayLayout</span><span class="sxs-lookup"><span data-stu-id="a7008-103">ICorDebugProcess5::GetArrayLayout Method</span></span>

<span data-ttu-id="a7008-104">Предоставляет сведения о структуре типов массивов.</span><span class="sxs-lookup"><span data-stu-id="a7008-104">Provides information about the layout of array types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7008-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="a7008-105">Syntax</span></span>  
  
```cpp  
HRESULT GetArrayLayout(    [in] COR_TYPEID id,     [out] COR_ARRAY_LAYOUT *pLayout);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a7008-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="a7008-106">Parameters</span></span>  

 `id`  
 <span data-ttu-id="a7008-107">окне Токен [COR_TYPEID](cor-typeid-structure.md) , указывающий массив, макет которого требуется.</span><span class="sxs-lookup"><span data-stu-id="a7008-107">[in] A [COR_TYPEID](cor-typeid-structure.md) token that specifies the array whose layout is desired.</span></span>  
  
 `pLayout`  
 <span data-ttu-id="a7008-108">заполняет Указатель на структуру [COR_ARRAY_LAYOUT](cor-array-layout-structure.md) , содержащую сведения о макете массива в памяти.</span><span class="sxs-lookup"><span data-stu-id="a7008-108">[out] A pointer to a [COR_ARRAY_LAYOUT](cor-array-layout-structure.md) structure that contains information about the layout of the array in memory.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a7008-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="a7008-109">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7008-110">Требования</span><span class="sxs-lookup"><span data-stu-id="a7008-110">Requirements</span></span>  

 <span data-ttu-id="a7008-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a7008-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a7008-112">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a7008-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a7008-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a7008-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a7008-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a7008-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7008-115">См. также</span><span class="sxs-lookup"><span data-stu-id="a7008-115">See also</span></span>

- [<span data-ttu-id="a7008-116">Интерфейс ICorDebugProcess5</span><span class="sxs-lookup"><span data-stu-id="a7008-116">ICorDebugProcess5 Interface</span></span>](icordebugprocess5-interface.md)
- [<span data-ttu-id="a7008-117">Интерфейсы отладки</span><span class="sxs-lookup"><span data-stu-id="a7008-117">Debugging Interfaces</span></span>](debugging-interfaces.md)
