---
description: 'Дополнительные сведения о методе: ICorDebugReferenceValue::D ереференце'
title: Метод ICorDebugReferenceValue::Dereference
ms.date: 03/30/2017
api_name:
- ICorDebugReferenceValue.Dereference
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugReferenceValue::Dereference
helpviewer_keywords:
- ICorDebugReferenceValue::Dereference method [.NET Framework debugging]
- Dereference method [.NET Framework debugging]
ms.assetid: 5ec8cf76-3deb-4ce6-9a49-77a4c35d80b9
topic_type:
- apiref
ms.openlocfilehash: af225f746a9c67a90a7ad73046cd03401e4ba735
ms.sourcegitcommit: ddf7edb67715a5b9a45e3dd44536dabc153c1de0
ms.translationtype: MT
ms.contentlocale: ru-RU
ms.lasthandoff: 02/06/2021
ms.locfileid: "99691111"
---
# <a name="icordebugreferencevaluedereference-method"></a><span data-ttu-id="4a657-103">Метод ICorDebugReferenceValue::Dereference</span><span class="sxs-lookup"><span data-stu-id="4a657-103">ICorDebugReferenceValue::Dereference Method</span></span>

<span data-ttu-id="4a657-104">Возвращает объект, на который указывает ссылка.</span><span class="sxs-lookup"><span data-stu-id="4a657-104">Gets the object that is referenced.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a657-105">Синтаксис</span><span class="sxs-lookup"><span data-stu-id="4a657-105">Syntax</span></span>  
  
```cpp  
HRESULT Dereference (  
    [out] ICorDebugValue  **ppValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4a657-106">Параметры</span><span class="sxs-lookup"><span data-stu-id="4a657-106">Parameters</span></span>  

 `ppValue`  
 <span data-ttu-id="4a657-107">заполняет Указатель на адрес ICorDebugValue, представляющий объект, на который указывает объект ICorDebugReferenceValue.</span><span class="sxs-lookup"><span data-stu-id="4a657-107">[out] A pointer to the address of an ICorDebugValue that represents the object to which this ICorDebugReferenceValue object points.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4a657-108">Remarks</span><span class="sxs-lookup"><span data-stu-id="4a657-108">Remarks</span></span>  

 <span data-ttu-id="4a657-109">`ICorDebugValue`Объект допустим только в том случае, если его ссылка еще не была отключена.</span><span class="sxs-lookup"><span data-stu-id="4a657-109">The `ICorDebugValue` object is valid only while its reference has not yet been disabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a657-110">Требования</span><span class="sxs-lookup"><span data-stu-id="4a657-110">Requirements</span></span>  

 <span data-ttu-id="4a657-111">**Платформы:** см. раздел [Требования к системе](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4a657-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a657-112">**Заголовок:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4a657-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4a657-113">**Библиотека:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4a657-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4a657-114">**Платформа .NET Framework версии:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a657-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
