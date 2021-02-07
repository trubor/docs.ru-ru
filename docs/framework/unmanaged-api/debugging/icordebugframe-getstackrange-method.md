---
description: 'Дополнительные сведения: метод ICorDebugFrame:: GetStackRange'
title: Метод ICorDebugFrame::GetStackRange
ms.date: 03/30/2017
api_name:
- ICorDebugFrame.GetStackRange
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFrame::GetStackRange
helpviewer_keywords:
- GetStackRange method, ICorDebugFrame interface [.NET Framework debugging]
- ICorDebugFrame::GetStackRange method [.NET Framework debugging]
ms.assetid: fab037cb-fda6-40fb-9367-921e435dd5a0
topic_type:
- apiref
ms.openlocfilehash: 1f1278e0c00addc3c14f4e1c8d3ed5aad0381526
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99692905"
---
# <a name="icordebugframegetstackrange-method"></a><span data-ttu-id="66a96-103">Метод ICorDebugFrame::GetStackRange</span><span class="sxs-lookup"><span data-stu-id="66a96-103">ICorDebugFrame::GetStackRange Method</span></span>

<span data-ttu-id="66a96-104">Возвращает диапазон абсолютных адресов этого кадра стека.</span><span class="sxs-lookup"><span data-stu-id="66a96-104">Gets the absolute address range of this stack frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66a96-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="66a96-105">Syntax</span></span>  
  
```cpp  
HRESULT GetStackRange (  
    [out] CORDB_ADDRESS      *pStart,
    [out] CORDB_ADDRESS      *pEnd  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="66a96-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="66a96-106">Parameters</span></span>  

 `pStart`  
 <span data-ttu-id="66a96-107">заполняет Указатель на объект `CORDB_ADDRESS` , указывающий начальный адрес кадра стека, представленного этим `ICorDebugFrame` объектом.</span><span class="sxs-lookup"><span data-stu-id="66a96-107">[out] A pointer to a `CORDB_ADDRESS` that specifies the starting address of the stack frame represented by this `ICorDebugFrame` object.</span></span>  
  
 `pEnd`  
 <span data-ttu-id="66a96-108">заполняет Указатель на объект `CORDB_ADDRESS` , указывающий конечный адрес кадра стека, представленного этим `ICorDebugFrame` объектом.</span><span class="sxs-lookup"><span data-stu-id="66a96-108">[out] A pointer to a `CORDB_ADDRESS` that specifies the ending address of the stack frame represented by this `ICorDebugFrame` object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="66a96-109">Remarks</span><span class="sxs-lookup"><span data-stu-id="66a96-109">Remarks</span></span>  

 <span data-ttu-id="66a96-110">Диапазон адресов стека полезен для пиеЦинг вместе чередующихся трассировок стека, собранных из нескольких ядер отладки.</span><span class="sxs-lookup"><span data-stu-id="66a96-110">The address range of the stack is useful for piecing together interleaved stack traces gathered from multiple debugging engines.</span></span> <span data-ttu-id="66a96-111">Числовой диапазон не предоставляет сведений о содержимом кадра стека.</span><span class="sxs-lookup"><span data-stu-id="66a96-111">The numeric range provides no information about the contents of the stack frame.</span></span> <span data-ttu-id="66a96-112">Он имеет смысл только для сравнения расположений в кадрах стека.</span><span class="sxs-lookup"><span data-stu-id="66a96-112">It is meaningful only for comparison of stack frame locations.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66a96-113">Требования</span><span class="sxs-lookup"><span data-stu-id="66a96-113">Requirements</span></span>  

 <span data-ttu-id="66a96-114">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="66a96-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="66a96-115">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="66a96-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="66a96-116">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="66a96-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="66a96-117">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="66a96-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
